---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 设置请求客户端使用配置 Id 在 PowerShell 5.0 及更高版本
ms.openlocfilehash: 8d8cf478f9127e1b7005d1b9e832e84b11612c9c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400773"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a>设置请求客户端使用配置 Id 在 PowerShell 5.0 及更高版本

> 适用于：Windows PowerShell 5.0

> [!IMPORTANT]
> 请求服务器（Windows 功能 DSC-Service）是 Windows Server 的一个受支持组件，不过目前没有提供新功能的计划。 建议开始将托管客户端转换至 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)（包括 Windows Server 上的请求服务器以外的功能）或[此处](pullserver.md#community-solutions-for-pull-service)列出的社区解决方案之一。

设置请求客户端之前, 应设置请求服务器。 但此顺序不是必需的它帮助进行故障排除，并帮助您确保注册成功。 若要设置请求服务器，可以使用以下指南：

- [设置 DSC SMB 拉取服务器](pullServerSmb.md)
- [设置 DSC HTTP 拉取服务器](pullServer.md)

每个目标节点可以配置为下载的配置，资源，并甚至报告其状态。 以下各节显示如何使用 SMB 共享或 HTTP DSC 请求服务器配置请求客户端。 节点的 LCM 刷新时，它将访问配置的位置下载任何已分配的配置。 如果在节点上不存在任何所需的资源，因此它将自动从配置的位置下载它们。 如果使用配置节点[报表服务器](reportServer.md)，然后，它将报告操作的状态。

> **注意**：本主题适用于 PowerShell 5.0。 有关在 PowerShell 4.0 中设置请求客户端的信息，请参阅[在 PowerShell 4.0 中使用配置 ID 设置请求客户端](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>配置请求客户端 LCM

执行任何下面的示例创建名为的新输出文件夹**PullClientConfigID**并放入元配置 MOF 文件。 在本例中，会将元配置 MOF 文件命名为 `localhost.meta.mof`。

若要应用配置，请调用 **Set-DscLocalConfigurationManager** cmdlet，并将 **Path** 设置为元配置 MOF 文件的位置。 例如：

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>配置 ID

以下集示例**ConfigurationID**属性将 lcm **Guid** ，之前创建实现此目的。 LCM 使用 **ConfigurationID** 在请求服务器上查找相应配置。 请求服务器上的配置 MOF 文件必须命名为 `ConfigurationID.mof`，其中 *ConfigurationID* 是目标节点上 LCM 的 **ConfigurationID** 属性值。 有关详细信息请参阅[请求服务器 (v4/v5) 的发布配置](publishConfigs.md)。

您可以创建一个随机**Guid**使用的示例，或通过使用[新建 Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet。

```powershell
[System.Guid]::NewGuid()
```

有关使用详细信息**Guid**在环境中，请参阅[规划 Guid](/powershell/dsc/secureserver#guids)。

## <a name="set-up-a-pull-client-to-download-configurations"></a>设置请求客户端下载配置

必须在配置每个客户端**拉取**模式和存储其配置为其提供拉取服务器 url。 若要执行此操作，必须为本地配置管理器 (LCM) 配置所需信息。 若要配置 LCM，可创建一个使用 **DSCLocalConfigurationManager** 特性修饰的特殊类型配置。 有关配置 LCM 的详细信息，请参阅[配置本地配置管理器](../managing-nodes/metaConfig.md)。

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

在该脚本中，**ConfigurationRepositoryWeb** 块定义了请求服务器。 **ServerUrl**指定 DSC 拉取的 url

### <a name="smb-share"></a>SMB 共享

以下脚本将 LCM 请求配置为从 SMB 共享`\\SMBPullServer\Pull`。

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

在脚本中， **ConfigurationRepositoryShare**块定义请求服务器，在这种情况下，即只是 SMB 共享。

## <a name="set-up-a-pull-client-to-download-resources"></a>设置请求客户端下载资源

如果仅指定**ConfigurationRepositoryWeb**或**ConfigurationRepositoryShare**块 （与前面的示例） 在 LCM 配置中，请求客户端将请求从同一个资源它将检索其配置的位置。 此外可以指定不同的资源的位置。 若要指定资源位置作为单独的服务器，请使用**ResourceRepositoryWeb**块。 若要指定资源位置为 SMB 共享，请使用**ResourceRepositoryShare**块。

> [!NOTE]
> 你可以组合**ConfigurationRepositoryWeb**与**ResourceRepositoryShare**或**ConfigurationRepositoryShare**与**ResourceRepositoryWeb**. 下面未显示的此示例。

### <a name="http-dsc-pull-server"></a>HTTP DSC 请求服务器

以下元配置将请求客户端以获取从其配置**Contoso-pullsrv**和从其资源**Contoso-resourcesrv**。

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

下面的示例演示从 SMB 共享请求配置为将客户端设置的元配置`\\SMBPullServer\Configurations`，并从 SMB 共享的资源`\\SMBPullServer\Resources`。

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

#### <a name="automatically-download-resources-in-push-mode"></a>自动下载在推送模式下的资源

从 PowerShell 5.0 开始，请求客户端可以下载模块从 SMB 共享，即使为配置**推送**模式。 这是情况下不需要设置拉取服务器中尤其有用。 **ResourceRepositoryShare**而无需指定可使用块**ConfigurationRepositoryShare**。 下面的示例显示了将客户端设置提取资源从 SMB 共享的元配置`\\SMBPullServer\Resources`。 当该节点是**按下**配置时，它将自动下载任何所需的资源，从指定的共享。

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

## <a name="set-up-a-pull-client-to-report-status"></a>设置请求客户端报告状态

默认情况下，节点不会向已配置的请求服务器发送报表。 虽然你可以将一个请求服务器用于配置、资源和报告，但必须创建 **ReportRepositoryWeb** 块来设置报表。

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

配置请求客户端之后，可以使用以下指南以执行后续步骤：

- [将配置发布到拉取服务器 (v4/v5)](publishConfigs.md)
- [打包资源并将其上传到拉取服务器 (v4)](package-upload-resources.md)

## <a name="see-also"></a>另请参阅

* [使用配置名称设置请求客户端](pullClientConfigNames.md)
