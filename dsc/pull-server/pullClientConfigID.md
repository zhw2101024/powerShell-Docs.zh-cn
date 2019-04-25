---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 在 PowerShell 5.0 及更高版本中使用配置 ID 设置请求客户端
ms.openlocfilehash: 14db98d240bc87aca3ee985db08c14b7c65d8bb8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079483"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a>在 PowerShell 5.0 及更高版本中使用配置 ID 设置请求客户端

> 适用于：Windows PowerShell 5.0

> [!IMPORTANT]
> 请求服务器（Windows 功能 DSC-Service）是 Windows Server 的一个受支持组件，不过目前没有提供新功能的计划。 建议开始将托管客户端转换至 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)（包括 Windows Server 上的请求服务器以外的功能）或[此处](pullserver.md#community-solutions-for-pull-service)列出的社区解决方案之一。

设置请求客户端之前，应设置请求服务器。 虽然此顺序不是必需的，不过它帮助进行故障排除，并帮助确保注册成功。 若要设置请求服务器，可以使用以下指南：

- [设置 DSC SMB 拉取服务器](pullServerSmb.md)
- [设置 DSC HTTP 拉取服务器](pullServer.md)

每个目标节点都可以配置为下载配置、资源，甚至是报告其状态。 以下各部分演示如何使用 SMB 共享或 HTTP DSC 请求服务器配置请求客户端。 节点的 LCM 刷新时，它会访问配置的位置以下载任何已分配的配置。 如果有任何所需资源在节点上不存在，则它会自动从配置的位置下载它们。 如果使用[报表服务器](reportServer.md)配置节点，则它随后会报告操作的状态。

> [!NOTE]
> 本主题适用于 PowerShell 5.0。 有关在 PowerShell 4.0 中设置请求客户端的信息，请参阅[在 PowerShell 4.0 中使用配置 ID 设置请求客户端](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>配置请求客户端 LCM

执行以下任何示例会创建名为 PullClientConfigID 的新输出文件夹，并在其中放入元配置 MOF 文件。 在本例中，会将元配置 MOF 文件命名为 `localhost.meta.mof`。

若要应用配置，请调用 **Set-DscLocalConfigurationManager** cmdlet，并将 **Path** 设置为元配置 MOF 文件的位置。 例如：

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>配置 ID

以下示例将 LCM 的 ConfigurationID 属性设置为之前为此目的创建的 Guid。 LCM 使用 **ConfigurationID** 在请求服务器上查找相应配置。 请求服务器上的配置 MOF 文件必须命名为 `ConfigurationID.mof`，其中 *ConfigurationID* 是目标节点上 LCM 的 **ConfigurationID** 属性值。 有关详细信息，请参阅[将配置发布到请求服务器 (v4/v5)](publishConfigs.md)。

可以使用以下示例，或使用 [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet 创建随机 Guid。

```powershell
[System.Guid]::NewGuid()
```

有关在环境中使用 Guid 的详细信息，请参阅[规划 Guid](/powershell/dsc/secureserver#guids)。

## <a name="set-up-a-pull-client-to-download-configurations"></a>设置请求客户端以下载配置

必须在“请求”模式下配置每个客户端，并向其提供存储其配置的请求服务器 url。 若要执行此操作，必须为本地配置管理器 (LCM) 配置所需信息。 若要配置 LCM，可创建一个使用 **DSCLocalConfigurationManager** 特性修饰的特殊类型配置。 有关配置 LCM 的详细信息，请参阅[配置本地配置管理器](../managing-nodes/metaConfig.md)。

### <a name="http-dsc-pull-server"></a>HTTP DSC 请求服务器

下面的脚本将 LCM 配置为从名为“CONTOSO-PullSrv”的服务器请求配置。

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }
    }
}
PullClientConfigID
```

在该脚本中，**ConfigurationRepositoryWeb** 块定义了请求服务器。 ServerUrl 指定 DSC 请求的 url

### <a name="smb-share"></a>SMB 共享

下面的脚本将 LCM 配置为从 SMB 共享 `\\SMBPullServer\Pull` 请求配置。

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Pull'
        }
    }
}
PullClientConfigID
```

在该脚本中，ConfigurationRepositoryShare 块定义请求服务器（在此例中只是 SMB 共享）。

## <a name="set-up-a-pull-client-to-download-resources"></a>设置请求客户端以下载资源

如果你在 LCM 配置中只指定 ConfigurationRepositoryWeb 或 ConfigurationRepositoryShare 块（如前面的示例所示），则请求客户端会从用于检索配置的相同位置请求资源。 还可以为资源指定不同的位置。 若要将资源位置指定为单独的服务器，请使用 ResourceRepositoryWeb 块。 若要将资源位置指定为 SMB 共享，请使用 ResourceRepositoryShare 块。

> [!NOTE]
> 可以将 ConfigurationRepositoryWeb 与 ResourceRepositoryShare，或是 ConfigurationRepositoryShare 与 ResourceRepositoryWeb 组合使用。 下面未显示这类用法的示例。

### <a name="http-dsc-pull-server"></a>HTTP DSC 请求服务器

以下元配置将请求客户端配置为从 CONTOSO-PullSrv 获取其配置，并从 CONTOSO-ResourceSrv 获取其资源。

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a>SMB 共享

下面的示例演示一个元配置，它将客户端设置为从 SMB 共享 `\\SMBPullServer\Configurations` 请求配置，并从 SMB 共享 `\\SMBPullServer\Resources` 请求资源。

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Configurations'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

#### <a name="automatically-download-resources-in-push-mode"></a>在推送模式下自动下载资源

从 PowerShell 5.0 开始，请求客户端可以从 SMB 共享下载模块，即使是针对推送模式进行配置也是如此。 这在不想设置请求服务器的情形中特别有用。 ResourceRepositoryShare 块可以在不指定 ConfigurationRepositoryShare 的情况下进行使用。 下面的示例演示一个元配置，它将客户端设置为从 SMB 共享 `\\SMBPullServer\Resources` 请求资源。 向节点推送配置时，它会从指定共享自动下载任何所需资源。

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

## <a name="set-up-a-pull-client-to-report-status"></a>设置请求客户端以报告状态

默认情况下，节点不会向已配置的请求服务器发送报告。 虽然你可以将一个请求服务器用于配置、资源和报告，但必须创建 **ReportRepositoryWeb** 块来设置报表。

### <a name="http-dsc-pull-server"></a>HTTP DSC 请求服务器

下面的示例展示了将客户端设置为请求配置和资源并将报表数据发送到一个请求服务器的元配置。

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

若要指定报表服务器，请使用 **ReportRepositoryWeb** 块。 报表服务器不能为 SMB 服务器。
以下元配置将请求客户端配置为从 **CONTOSO-PullSrv** 获取其配置、从 **CONTOSO-ResourceSrv** 获取资源、将状态报告发送到 **CONTOSO-ReportSrv**：

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a>SMB 共享

报表服务器不能为 SMB 共享。

## <a name="next-steps"></a>后续步骤

配置请求客户端之后，可以使用以下指南执行后续步骤：

- [将配置发布到拉取服务器 (v4/v5)](publishConfigs.md)
- [打包资源并将其上传到拉取服务器 (v4)](package-upload-resources.md)

## <a name="see-also"></a>另请参阅

* [使用配置名称设置请求客户端](pullClientConfigNames.md)
