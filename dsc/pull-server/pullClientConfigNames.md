---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 在 PowerShell 5.0 及更高版本中使用配置名称设置请求客户端
ms.openlocfilehash: d591e2a757130ccecaf4eaf9f363f607fca82b93
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079381"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a>在 PowerShell 5.0 及更高版本中使用配置名称设置请求客户端

> 适用于：Windows PowerShell 5.0

> [!IMPORTANT]
> 请求服务器（Windows 功能 DSC-Service）是 Windows Server 的一个受支持组件，不过目前没有提供新功能的计划。 建议开始将托管客户端转换至 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)（包括 Windows Server 上的请求服务器以外的功能）或[此处](pullserver.md#community-solutions-for-pull-service)列出的社区解决方案之一。

设置请求客户端之前，应设置请求服务器。 虽然此顺序不是必需的，不过它帮助进行故障排除，并帮助确保注册成功。 若要设置请求服务器，可以使用以下指南：

- [设置 DSC SMB 拉取服务器](pullServerSmb.md)
- [设置 DSC HTTP 拉取服务器](pullServer.md)

每个目标节点都可以配置为下载配置、资源，甚至是报告其状态。 以下各部分演示如何使用 SMB 共享或 HTTP DSC 请求服务器配置请求客户端。 节点的 LCM 刷新时，它会访问配置的位置以下载任何已分配的配置。 如果有任何所需资源在节点上不存在，则它会自动从配置的位置下载它们。 如果使用[报表服务器](reportServer.md)配置节点，则它随后会报告操作的状态。

> [!NOTE]
> 本主题适用于 PowerShell 5.0。
> 有关在 PowerShell 4.0 中设置请求客户端的信息，请参阅[在 PowerShell 4.0 中使用配置 ID 设置请求客户端](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>配置请求客户端 LCM

执行以下任何示例会创建名为 PullClientConfigName 的新输出文件夹，并在其中放入元配置 MOF 文件。 在本例中，会将元配置 MOF 文件命名为 `localhost.meta.mof`。

若要应用配置，请调用 **Set-DscLocalConfigurationManager** cmdlet，并将 **Path** 设置为元配置 MOF 文件的位置。 例如：

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a>配置名称

以下示例将 LCM 的 ConfigurationName 属性设置为针对此用途创建的以前编译的配置名称。 LCM 使用 ConfigurationName 在请求服务器上查找相应配置。 请求服务器上的配置 MOF 文件必须命名为 `<ConfigurationName>.mof`（在此例中为“ClientConfig.mof”）。 有关详细信息，请参阅[将配置发布到请求服务器 (v4/v5)](publishConfigs.md)。

## <a name="set-up-a-pull-client-to-download-configurations"></a>设置请求客户端以下载配置

必须在“请求”模式下配置每个客户端，并向其提供存储其配置的请求服务器 url。 若要执行此操作，必须为本地配置管理器 (LCM) 配置所需信息。 若要配置 LCM，可创建一个使用 **DSCLocalConfigurationManager** 特性修饰的特殊类型配置。 有关配置 LCM 的详细信息，请参阅[配置本地配置管理器](../managing-nodes/metaConfig.md)。

下面的脚本将 LCM 配置为从名为“CONTOSO-PullSrv”的服务器请求配置。

- 在该脚本中，**ConfigurationRepositoryWeb** 块定义了请求服务器。 **ServerURL** 属性为请求服务器指定终结点。

- **RegistrationKey** 属性是请求服务器的所有客户端节点与该请求服务器之间的共享密钥。 请求服务器上的文件中存储了相同的值。
  > [!NOTE]
  > 注册密钥仅适用于 Web 请求服务器。 对于 SMB 请求服务器，仍必须使用 ConfigurationID。
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

## <a name="set-up-a-pull-client-to-download-resources"></a>设置请求客户端以下载资源

如果你在 LCM 配置中只指定 ConfigurationRepositoryWeb 或 ConfigurationRepositoryShare 块（如前面的示例所示），则请求客户端会从存储“.mof”文件的相同位置请求资源。 还可以指定客户端可以下载资源的不同位置。 若要指定资源服务器，请使用 **ResourceRepositoryWeb**（适用于 Web 请求服务器）或 **ResourceRepositoryShare**（适用于 SMB 请求服务器）块。

下面的示例演示一个元配置，它将客户端设置为从请求服务器下载配置，并从 SMB 共享下载资源。

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

## <a name="set-up-a-pull-client-to-report-status"></a>设置请求客户端以报告状态

可以将单个请求服务器用于配置、资源和报告。 默认情况下不会为客户端配置报告。 若要配置客户端以报告状态，必须创建 ReportRepositoryWeb 块。 下面的示例展示了将客户端设置为请求配置和资源并将报表数据发送到一个请求服务器的元配置。

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
