---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 设置请求客户端使用配置名称在 PowerShell 5.0 及更高版本
ms.openlocfilehash: fd038a105da7a83ecad9b571e611b65c8ec847b3
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400897"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a>设置请求客户端使用配置名称在 PowerShell 5.0 及更高版本

> 适用于：Windows PowerShell 5.0

> [!IMPORTANT]
> 请求服务器（Windows 功能 DSC-Service）是 Windows Server 的一个受支持组件，不过目前没有提供新功能的计划。 建议开始将托管客户端转换至 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)（包括 Windows Server 上的请求服务器以外的功能）或[此处](pullserver.md#community-solutions-for-pull-service)列出的社区解决方案之一。

设置请求客户端之前, 应设置请求服务器。 但此顺序不是必需的它帮助进行故障排除，并帮助您确保注册成功。 若要设置请求服务器，可以使用以下指南：

- [设置 DSC SMB 拉取服务器](pullServerSmb.md)
- [设置 DSC HTTP 拉取服务器](pullServer.md)

每个目标节点可以配置为下载的配置，资源，并甚至报告其状态。 以下各节显示如何使用 SMB 共享或 HTTP DSC 请求服务器配置请求客户端。 节点的 LCM 刷新时，它将访问配置的位置下载任何已分配的配置。 如果在节点上不存在任何所需的资源，因此它将自动从配置的位置下载它们。 如果使用配置节点[报表服务器](reportServer.md)，然后，它将报告操作的状态。

> **注意**：本主题适用于 PowerShell 5.0。
有关设置请求客户端在 PowerShell 4.0 中的信息，请参阅[设置请求客户端在 PowerShell 4.0 中使用配置 ID](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>配置请求客户端 LCM

执行任何下面的示例创建名为的新输出文件夹**PullClientConfigName**并放入元配置 MOF 文件。 在本例中，会将元配置 MOF 文件命名为 `localhost.meta.mof`。

若要应用配置，请调用 **Set-DscLocalConfigurationManager** cmdlet，并将 **Path** 设置为元配置 MOF 文件的位置。 例如：

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a>配置名称

以下集示例**ConfigurationName**为此目的创建的以前编译配置的名称将 LCM 的属性。 **ConfigurationName** LCM 使用请求服务器上查找相应的配置。 请求服务器上的配置 MOF 文件必须命名为`<ConfigurationName>.mof`，在这种情况下，"ClientConfig.mof"。 有关详细信息，请参阅[请求服务器 (v4/v5) 的发布配置](publishConfigs.md)。

## <a name="set-up-a-pull-client-to-download-configurations"></a>设置请求客户端下载配置

必须在配置每个客户端**拉取**模式和存储其配置为其提供拉取服务器 url。 若要执行此操作，必须为本地配置管理器 (LCM) 配置所需信息。 若要配置 LCM，可创建一个使用 **DSCLocalConfigurationManager** 特性修饰的特殊类型配置。 有关配置 LCM 的详细信息，请参阅[配置本地配置管理器](../managing-nodes/metaConfig.md)。

下面的脚本将 LCM 配置为从名为“CONTOSO-PullSrv”的服务器请求配置。

- 在该脚本中，**ConfigurationRepositoryWeb** 块定义了请求服务器。 **ServerURL** 属性为请求服务器指定终结点。

- **RegistrationKey** 属性是请求服务器的所有客户端节点与该请求服务器之间的共享密钥。 请求服务器上的文件中存储了相同的值。
  > **注意**：注册密钥仅适用于**web**请求服务器。 对于 SMB 请求服务器，仍必须使用 ConfigurationID。
  > 有关使用 **ConfigurationID** 配置请求服务器的信息，请参阅[使用配置 ID 设置请求客户端](pullClientConfigId.md)

- **ConfigurationNames** 属性是指定用于客户端节点的配置的名称的数组。
  >**注意：** 如果在 ConfigurationNames 中指定多个值，则必须也在你的配置中指定 PartialConfiguration 块。
  >有关部分配置的信息，请参阅 [PowerShell Desired State Configuration 部分配置](partialConfigs.md)。

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-download-resources"></a>设置请求客户端下载资源

如果仅指定**ConfigurationRepositoryWeb**或**ConfigurationRepositoryShare**块 （如在前面的示例） 在 LCM 配置中，请求客户端将请求从相同的资源".mof"文件存储的位置。 此外可以指定不同的客户端可下载资源的位置。 若要指定资源服务器，请使用 **ResourceRepositoryWeb**（适用于 Web 请求服务器）或 **ResourceRepositoryShare**（适用于 SMB 请求服务器）块。

下面的示例显示了将客户端设置以从请求的服务器，并从 SMB 共享的资源下载配置的元配置。

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ResourceRepositoryShare SMBResources
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-report-status"></a>设置请求客户端报告状态

用于配置、 资源和报告，可以使用一个请求服务器。 未配置报告的客户端默认情况下。 若要配置客户端报告状态，您必须创建**ReportRepositoryWeb**块。 下面的示例展示了将客户端设置为请求配置和资源并将报表数据发送到一个请求服务器的元配置。

> [!NOTE]
> 报表服务器不能为 SMB 共享。

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a>另请参阅

* [使用配置 ID 设置请求客户端](PullClientConfigNames.md)
* [设置 DSC Web 请求服务器](pullServer.md)
