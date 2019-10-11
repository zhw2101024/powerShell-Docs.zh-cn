---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 在 PowerShell 4.0 中使用配置 ID 设置拉取客户端
ms.openlocfilehash: 9259c624c8725f7d76f61e9ad7caa42e1bfa308c
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71955144"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a>在 PowerShell 4.0 中使用配置 ID 设置拉取客户端

>适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

> [!IMPORTANT]
> 请求服务器（Windows 功能 DSC-Service）是 Windows Server 的一个受支持组件，不过目前没有提供新功能的计划  。 建议开始将托管客户端转换至 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)（包括 Windows Server 上的请求服务器以外的功能）或[此处](pullserver.md#community-solutions-for-pull-service)列出的社区解决方案之一。

设置请求客户端之前，应设置请求服务器。 虽然此顺序不是必需的，不过它帮助进行故障排除，并帮助确保注册成功。 若要设置请求服务器，可以使用以下指南：

- [设置 DSC SMB 拉取服务器](pullServerSmb.md)
- [设置 DSC HTTP 拉取服务器](pullServer.md)

每个目标节点都可以配置为下载配置、资源，甚至是报告其状态。 以下各部分演示如何使用 SMB 共享或 HTTP DSC 请求服务器配置请求客户端。 节点的 LCM 刷新时，它会访问配置的位置以下载任何已分配的配置。 如果有任何所需资源在节点上不存在，则它会自动从配置的位置下载它们。 如果使用[报表服务器](reportServer.md)配置节点，则它随后会报告操作的状态。

## <a name="configure-the-pull-client-lcm"></a>配置请求客户端 LCM

执行以下任何示例会创建名为 PullClientConfigID  的新输出文件夹，并在其中放入元配置 MOF 文件。 在本例中，会将元配置 MOF 文件命名为 `localhost.meta.mof`。

若要应用配置，请调用 **Set-DscLocalConfigurationManager** cmdlet，并将 **Path** 设置为元配置 MOF 文件的位置。 例如：

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>配置 ID

以下示例将 LCM 的 ConfigurationID  属性设置为之前为此目的创建的 Guid  。 LCM 使用 **ConfigurationID** 在请求服务器上查找相应配置。 请求服务器上的配置 MOF 文件必须命名为 `ConfigurationID.mof`，其中 *ConfigurationID* 是目标节点上 LCM 的 **ConfigurationID** 属性值。 有关详细信息，请参阅[将配置发布到请求服务器 (v4/v5)](publishConfigs.md)。

可以使用以下示例创建随机 Guid  。

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a>设置请求客户端以下载配置

必须在“请求”  模式下配置每个客户端，并向其提供存储其配置的请求服务器 url。 若要执行此操作，必须为本地配置管理器 (LCM) 配置所需信息。 若要配置 LCM，你需要创建一个具有 LocalConfigurationManager  块的特殊类型配置。 有关配置 LCM 的详细信息，请参阅[配置本地配置管理器](../managing-nodes/metaConfig4.md)。

## <a name="http-dsc-pull-server"></a>HTTP DSC 请求服务器

如果拉取服务器被设置为 Web 服务，请将 DownloadManagerName  设置为 WebDownloadManager  。  WebDownloadManager 要求你指定指向 DownloadManagerCustomData  键的 ServerUrl  。 还可以指定 AllowUnsecureConnection  的值，如下面的示例中所示。 下面的脚本将 LCM 配置为从名为“PullServer”的服务器请求配置。

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = "TRUE"}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a>SMB 共享

如果拉取服务器被设置为 SMB 文件共享，而不是 Web 服务，请将 DownloadManagerName  设置为 DscFileDownloadManager  ，而不是 WebDownLoadManager  。  DscFileDownloadManager 要求你指定 DownloadManagerCustomData  中的 SourcePath  属性。 下面的脚本将 LCM 配置为从“CONTOSO-SERVER”服务器上的“SmbDscShare”SMB 共享请求配置。

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    }
}
PullClientConfigId -Output "."
```

## <a name="next-steps"></a>后续步骤

配置请求客户端之后，可以使用以下指南执行后续步骤：

- [将配置发布到拉取服务器 (v4/v5)](publishConfigs.md)
- [打包资源并将其上传到拉取服务器 (v4)](package-upload-resources.md)

## <a name="see-also"></a>另请参阅

- [设置 DSC Web 拉取服务器](pullServer.md)
- [设置 DSC SMB 拉取服务器](pullServerSMB.md)
