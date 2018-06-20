---
ms.date: 10/12/2017
keywords: dsc,powershell,配置,安装程序
title: 在早期版本的 Windows PowerShell 中配置本地配置管理器
ms.openlocfilehash: 05e315539e51e31b5a496e8c595ac3695d9a0c97
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189374"
---
# <a name="configuring-the-local-configuration-manager-in-previous-versions-of-windows-powershell"></a>在早期版本的 Windows PowerShell 中配置本地配置管理器

>适用于：Windows PowerShell 4.0

**有关 Windows PowerShell 5.0 和更高版本的信息，请参阅[配置本地配置管理器](metaConfig.md)。**

本地配置管理器是 Windows PowerShell Desired State Configuration (DSC) 引擎。
它在所有的目标节点上运行，负责调用 DSC 配置脚本中包含的配置资源。
本主题列出了本地配置管理器的属性，并介绍如何在目标节点上修改本地配置管理器设置。

## <a name="local-configuration-manager-properties"></a>本地配置管理器属性

以下列出了可以设置或检索的本地配置管理器属性。

- **AllowModuleOverwrite**：控制是否允许从配置服务下载的新配置覆盖目标节点上的旧配置。 可能的值为 True 和 False。
- **CertificateID**：用于保护在配置中传递的凭据的证书指纹。 更多详细信息，请参阅 [Want to secure credentials in Windows PowerShell Desired State Configuration?（希望在 Windows PowerShell Desired State Configuration 中保护凭据？）](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx)。
- **ConfigurationID**：指示用于从请求服务获取特定配置文件的 GUID。 GUID 可确保访问正确的配置文件。
- **ConfigurationMode**：指定本地配置管理器实际如何将配置应用到目标节点。 可以有下列值：
  - **ApplyOnly**：使用此选项，DSC 将应用配置，但在检测到新配置之前不会执行任何进一步操作。检测新配置的方式可以是向目标节点直接发送新配置；也可以是连接请求服务后，DSC 检查请求服务时发现新配置。 如果目标节点的配置偏离，则不执行任何操作。
  - **ApplyAndMonitor**：使用此选项（默认），DSC 会应用任何由你直接发送到目标节点的或者在请求服务上发现的新配置。 此后，如果目标节点的配置偏离配置文件，DSC 将在日志中报告差异。 有关 DSC 日志记录的详细信息，请参阅 [Using Event Logs to Diagnose Errors in Desired State Configuration（在 Desired State Configuration 中使用事件日志诊断错误）](http://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx)。
  - **ApplyAndAutoCorrect**：使用此选项，DSC 会应用任何由你直接发送到目标节点的或者在请求服务上发现的新配置。 此后，如果目标节点的配置偏离配置文件，DSC 将在日志中报告差异，并尝试调整目标节点配置，使其与配置文件相容。
- **ConfigurationModeFrequencyMins**：表示 DSC 的后台应用程序尝试在目标节点上执行当前配置的频率（以分钟为单位）。 默认值为 15。 可将此值设置为与 RefreshMode 结合使用。 当 RefreshMode 设置为 PULL 时，目标节点按 RefreshFrequencyMins 所设置的时间间隔与配置服务联系并下载当前配置。 无论 RefreshMode 值如何，一致性引擎都会在由 ConfigurationModeFrequencyMins 设置的时间间隔将下载的最新配置应用到目标节点。 RefreshFrequencyMins 应设置为 ConfigurationModeFrequencyMins 的整倍数。
- **Credential**：指示访问远程资源（例如联系配置服务）所需的凭据（与 Get-Credential 相同）。
- **DownloadManagerCustomData**：表示包含特定于下载管理器的自定义数据的数组。
- **DownloadManagerName**：指示配置和模块下载管理器的名称。
- **RebootNodeIfNeeded**：目标节点上的某些配置更改可能要求重启该节点才能应用这些更改。 如果值为 **True**，则此属性将在配置应用完成后立即重启节点，而不会发出进一步警告。 如果值为 **False**（默认值），则将完成配置，但必须手动重启节点才能使更改生效。
- **RefreshFrequencyMins**：设置请求服务后使用。 表示本地配置管理器联系请求服务下载当前配置的频率（以分钟为单位）。 可将此值设置为与 ConfigurationModeFrequencyMins 结合使用。 当 RefreshMode 设置为 PULL 时，目标节点按 RefreshFrequencyMins 所设置的时间间隔与请求服务联系并下载当前配置。 一致性引擎将在由 ConfigurationModeFrequencyMins 设置的时间间隔将下载的最新配置应用到目标节点。 若 RefreshFrequencyMins 未设置为 ConfigurationModeFrequencyMins 的整倍数，系统将会向上进行舍入。 默认值为 30。
- **RefreshMode**：可能的值为 **Push**（默认值）和 **Pull**。 在“推送”配置下，必须在每个目标节点上放置配置文件（可使用任何客户端计算机进行此操作）。 在“请求”模式下，必须为本地配置管理器设置请求服务，以便其联系和访问配置文件。

### <a name="example-of-updating-local-configuration-manager-settings"></a>更新本地配置管理器设置的示例

可以通过在节点块内包含 **LocalConfigurationManager** 块来更新目标节点的本地配置管理器设置，如以下示例中所示。

```powershell
Configuration ExampleConfig
{
    Node “Server001”
    {
        LocalConfigurationManager
        {
            ConfigurationID = "646e48cb-3082-4a12-9fd9-f71b9a562d4e"
            ConfigurationModeFrequencyMins = 45
            ConfigurationMode = "ApplyAndAutocorrect"
            RefreshMode = "Pull"
            RefreshFrequencyMins = 90
            DownloadManagerName = "WebDownloadManager"
            DownloadManagerCustomData = (@{ServerUrl="https://$PullService/psdscpullserver.svc"})
            CertificateID = "71AA68562316FE3F73536F1096B85D66289ED60E"
            Credential = $cred
            RebootNodeIfNeeded = $true
            AllowModuleOverwrite = $false
        }
# One or more resource blocks can be added here
    }
}

# The following line invokes the configuration and creates a file called Server001.meta.mof at the specified path
ExampleConfig -OutputPath "c:\users\public\dsc"
```

运行以上示例中的脚本将生成一个 MOF 文件，它指定并存储了所需设置。
若要应用这些设置，可以使用 **Set-DscLocalConfigurationManager** cmdlet，如以下示例中所示。

```powershell
Set-DscLocalConfigurationManager -Path "c:\users\public\dsc"
```

> **注意**：调用以上示例中的配置时，必须为 **Path** 参数指定与 **OutputPath** 参数相同的路径。

若要查看当前本地配置管理器设置，可以使用 **Get-DscLocalConfigurationManager** cmdlet。
如果不带任何参数调用此 cmdlet，默认情况下它将获取其运行于的节点上的本地配置管理器设置。
若要指定另一个节点，请将 **CimSession** 参数用于此 cmdlet。