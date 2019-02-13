---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 设置请求客户端在 PowerShell 4.0 中使用配置 Id
ms.openlocfilehash: 9adc767e91ff19d373c122a0d493e7b8703d5476
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676267"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a>设置请求客户端在 PowerShell 4.0 中使用配置 Id

>适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

> [!IMPORTANT]
> 请求服务器（Windows 功能 DSC-Service）是 Windows Server 的一个受支持组件，不过目前没有提供新功能的计划。 建议开始将托管客户端转换至 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)（包括 Windows Server 上的请求服务器以外的功能）或[此处](pullserver.md#community-solutions-for-pull-service)列出的社区解决方案之一。

设置请求客户端之前, 应设置请求服务器。 但此顺序不是必需的它帮助进行故障排除，并帮助您确保注册成功。 若要设置请求服务器，可以使用以下指南：

- [设置 DSC SMB 拉取服务器](pullServerSmb.md)
- [设置 DSC HTTP 拉取服务器](pullServer.md)

每个目标节点可以配置为下载的配置，资源，并甚至报告其状态。 以下各节显示如何使用 SMB 共享或 HTTP DSC 请求服务器配置请求客户端。 节点的 LCM 刷新时，它将访问配置的位置下载任何已分配的配置。 如果在节点上不存在任何所需的资源，因此它将自动从配置的位置下载它们。 如果使用配置节点[报表服务器](reportServer.md)，然后，它将报告操作的状态。

## <a name="configure-the-pull-client-lcm"></a>配置请求客户端 LCM

执行任何下面的示例创建名为的新输出文件夹**PullClientConfigID**并放入元配置 MOF 文件。 在本例中，会将元配置 MOF 文件命名为 `localhost.meta.mof`。

若要应用配置，请调用 **Set-DscLocalConfigurationManager** cmdlet，并将 **Path** 设置为元配置 MOF 文件的位置。 例如：

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>配置 ID

下面一组示例**ConfigurationID**属性将 lcm **Guid** ，之前创建实现此目的。 LCM 使用 **ConfigurationID** 在请求服务器上查找相应配置。 请求服务器上的配置 MOF 文件必须命名为 `ConfigurationID.mof`，其中 *ConfigurationID* 是目标节点上 LCM 的 **ConfigurationID** 属性值。 有关详细信息，请参阅[请求服务器 (v4/v5) 的发布配置](publishConfigs.md)。

您可以创建一个随机**Guid**使用下面的示例。

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a>设置请求客户端下载配置

必须在配置每个客户端**拉取**模式和存储其配置为其提供拉取服务器 url。 若要执行此操作，必须为本地配置管理器 (LCM) 配置所需信息。 若要配置 LCM，你创建的特殊类型的配置，与**LocalConfigurationManager**块。 有关配置 LCM 的详细信息，请参阅[配置本地配置管理器](../managing-nodes/metaConfig4.md)。

## <a name="http-dsc-pull-server"></a>HTTP DSC 请求服务器

如果请求服务器设置为 web 服务，则设置**DownloadManagerName**到**WebDownloadManager**。 **WebDownloadManager**要求您指定**ServerUrl**到**DownloadManagerCustomData**密钥。 此外可以指定的值**AllowUnsecureConnection**，如下面的示例。 下面的脚本将 LCM 配置为从名为“PullServer”的服务器请求配置。

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
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a>SMB 共享

如果请求服务器设置为 SMB 文件共享，而不是 web 服务，则设置**DownloadManagerName**到**DscFileDownloadManager**而不是**WebDownLoadManager**. **DscFileDownloadManager**要求您指定**SourcePath**中的属性**DownloadManagerCustomData**。 下面的脚本将 LCM 配置为从“CONTOSO-SERVER”服务器上的“SmbDscShare”SMB 共享请求配置。

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

配置请求客户端之后，可以使用以下指南以执行后续步骤：

- [将配置发布到拉取服务器 (v4/v5)](publishConfigs.md)
- [打包资源并将其上传到拉取服务器 (v4)](package-upload-resources.md)

## <a name="see-also"></a>另请参阅

- [设置 DSC web 请求服务器](pullServer.md)
- [设置 DSC SMB 拉取服务器](pullServerSMB.md)
