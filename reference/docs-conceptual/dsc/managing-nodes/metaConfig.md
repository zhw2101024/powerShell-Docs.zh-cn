---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 配置本地配置管理器
ms.openlocfilehash: 606cf77ddc3865749e900753aba7c41b66424450
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953844"
---
# <a name="configuring-the-local-configuration-manager"></a>配置本地配置管理器

> 适用于：Windows PowerShell 5.0

本地配置管理器 (LCM) 是 Desired State Configuration (DSC) 的引擎。
LCM 在每个目标节点上运行，负责分析和执行发送到节点的配置。
它还负责 DSC 的许多方面，包括以下各方面。

- 确定刷新模式（推送或请求）。
- 指定节点请求和执行配置的频率。
- 将节点与请求服务相关联。
- 指定部分配置。

使用特殊类型的配置将 LCM 配置为指定以上各行为。
以下各节介绍如何配置 LCM。

Windows PowerShell 5.0 引入了全新的设置来管理本地配置管理器。
有关在 Windows PowerShell 4.0 中配置 LCM 的信息，请参阅[在早期版本的 Windows PowerShell 中配置本地配置管理器](metaconfig4.md)。

## <a name="writing-and-enacting-an-lcm-configuration"></a>编写和执行 LCM 配置

若要配置 LCM，请创建并运行应用 LCM 设置的特殊类型的配置。
若要指定 LCM 配置，你可以使用 DscLocalConfigurationManager 特性。
下面演示将 LCM 设置为推送模式的简单配置。

```powershell
[DSCLocalConfigurationManager()]
configuration LCMConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
        }
    }
}
```

将设置应用于 LCM 的过程与应用 DSC 配置的过程类似。
创建 LCM 配置、将其编译为 MOF 文件，然后应用于节点。
与 DSC 配置不同的是，不通过调用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet 来执行 LCM 配置。
而是通过调用 [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)，将路径作为参数提供给 LCM 配置 MOF。
执行 LCM 配置后，可以通过调用 [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet 查看 LCM 的属性。

LCM 配置只能包含有限组资源的块。
在上面的示例中，调用的唯一资源名为 **Settings**。
其他可用资源有：

* **ConfigurationRepositoryWeb**：指定用于配置的 HTTP 请求服务。
* **ConfigurationRepositoryShare**：指定用于配置的 SMB 共享。
* **ResourceRepositoryWeb**：指定用于模块的 HTTP 请求服务。
* **ResourceRepositoryShare**：指定用于模块的 SMB 共享。
* **ReportServerWeb**：指定将报告发送到的 HTTP 请求服务。
* **PartialConfiguration**：提供数据以启用部分配置。

## <a name="basic-settings"></a>基本设置

不通过指定请求服务终结点/路径和部分配置 LCM 的所有属性，而是在 Settings  块中进行配置。
**Settings** 块中提供下列属性。

|  属性  |  类型  |  说明   |
|----------- |------- |--------------- |
| ActionAfterReboot| 字符串| 指定在应用配置期间重启后进行什么操作。 可取值为 __ContinueConfiguration__ 和 __StopConfiguration__。 <ul><li> __ContinueConfiguration__：在计算机重新启动后继续应用当前配置。 此为默认值</li><li>__StopConfiguration__：在计算机重新启动后停止当前配置。</li></ul>|
| AllowModuleOverwrite| 布尔| 若允许从请求服务下载的新配置覆盖目标节点上的旧配置，则为 __$TRUE__。 否则为 $FALSE。|
| CertificateID| 字符串| 用于保护在配置中传递的凭据的证书指纹。 更多详细信息，请参阅 [Want to secure credentials in Windows PowerShell Desired State Configuration?（希望在 Windows PowerShell Desired State Configuration 中保护凭据？）](https://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx)。 <br> __注意：__ 如果使用 Azure 自动化 DSC 请求服务，则会自动进行管理。|
| ConfigurationDownloadManagers| CimInstance[]| 已过时。 使用 __ConfigurationRepositoryWeb__ 和 __ConfigurationRepositoryShare__ 块定义配置请求服务终结点。|
| ConfigurationID| 字符串| 用于向后兼容早期版本的请求服务。 用于标识要从请求服务获取的配置文件的 GUID。 如果配置 MOF 名为 ConfigurationID.mof，那么节点将在请求服务上请求配置。<br> __注意：__ 如果设置此属性，将无法使用 RegistrationKey 将节点注册到请求服务  。 有关详细信息，请参阅[使用配置名称设置请求客户端](../pull-server/pullClientConfigNames.md)。|
| ConfigurationMode| 字符串 | 指定 LCM 实际如何将配置应用到目标节点。 可能的值为 __ApplyOnly__、__ApplyAndMonitor__ 和 __ApplyAndAutoCorrect__。 <ul><li>__ApplyOnly__：DSC 将应用配置，但若未向目标节点推送新配置或从服务请求新配置，则它不会执行任何进一步操作。 首次应用新配置后，DSC 不会检查是否偏离以前配置的状态。 请注意，__ApplyOnly__ 生效前，DSC 将尝试应用配置，直到成功为止。 </li><li> __ApplyAndMonitor__：这是默认值。 LCM 将应用任意新配置。 首次应用新配置后，如果目标节点偏离期望状态，则 DSC 将在日志中报告差异。 请注意，__ApplyAndMonitor__ 生效前，DSC 将尝试应用配置，直到成功为止。</li><li>__ApplyAndAutoCorrect__：DSC 将应用任何新配置。 首次应用新配置后，如果目标节点偏离适当状态，则 DSC 将在日志中报告差异然后重新应用当前配置。</li></ul>|
| ConfigurationModeFrequencyMins| UInt32| 检查和应用当前配置的时间间隔（以分钟为单位）。 如果将 ConfigurationMode 属性设置为 ApplyOnly，则将忽略此属性。 默认值为 15。|
| DebugMode| 字符串| 可取值为 __None__、__ForceModuleImport__ 和 __All__。 <ul><li>设置为 __None__ 可以使用缓存的资源。 这是默认值，应在生产方案中使用。</li><li>设置为 __ForceModuleImport__ 会导致 LCM 重载所有 DSC 资源模块，即使这些模块之前已被加载并缓存，也是如此。 这会影响 DSC 操作的性能，因为将在使用时重新加载每个模块。 通常在调试资源时使用此值</li><li>在此版本中，__All__ 等同于 __ForceModuleImport__</li></ul> |
| RebootNodeIfNeeded| 布尔| 将此设置为 `$true` 可使资源使用 `$global:DSCMachineStatus` 标志重新启动节点。 否则，你必须为要求重启的配置手动重启节点。 默认值为 `$false`。 若要在通过 DSC 以外的其他配置（例如 Windows Installer）执行重启条件时使用此设置，请将此设置和 [ComputerManagementDsc](https://github.com/PowerShell/ComputerManagementDsc) 模块中的 __PendingReboot__ 资源组合使用。|
| RefreshMode| 字符串| 指定 LCM 如何获取配置。 可取值为 __Disabled__、__Push__ 和 __Pull__。 <ul><li>__Disabled__：DSC 配置对该节点禁用。</li><li> __Push__：通过调用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet 启动配置。 将配置立即应用到节点。 这是默认值。</li><li>__Pull：__ 将节点配置为从请求服务或 SMB 路径定期检查配置。 如果此属性被设置为 __Pull__，则必须在 __ConfigurationRepositoryWeb__ 或 __ConfigurationRepositoryShare__ 块中指定 HTTP（服务）或 SMB（共享）路径。</li></ul>|
| RefreshFrequencyMins| Uint32| LCM 按此时间间隔（以分钟为单位）检查请求服务以获取更新的配置。 如果 LCM 未配置为请求模式，则将忽略此值。 默认值为 30。|
| ReportManagers| CimInstance[]| 已过时。 使用 __ReportServerWeb__ 块定义终结点，以将报告数据发送到请求服务。|
| ResourceModuleManagers| CimInstance[]| 已过时。 使用 __ResourceRepositoryWeb__ 和 __ResourceRepositoryShare__ 块分别定义请求服务 HTTP 终结点和 SMB 路径。|
| PartialConfigurations| CimInstance| 未实现。 不使用。|
| StatusRetentionTimeInDays | UInt32| LCM 保留当前配置状态的天数。|

> [!NOTE]
> LCM 基于以下条件启动 ConfigurationModeFrequencyMins  周期：
>
> - 使用 `Set-DscLocalConfigurationManager` 应用新的元配置
> - 计算机重新启动
>
> 对于计时器进程遇到故障的任何状况，会在 30 秒内检测到该状况，并且会重新启动周期。
> 并发操作可能会延迟周期启动，如果此操作的持续时间超过配置的频率，则下一个计时器不会启动。
>
> 例如，元配置以 15 分钟请求频率进行配置，请求会在 T1 进行。  节点未在 16 分钟内完成工作。  第一个 15 分钟周期会被忽略，下一个请求会在 T1+15+15 进行。

## <a name="pull-service"></a>请求服务

LCM 配置支持定义以下类型的请求服务终结点：

- **配置服务器**：DSC 配置的存储库。 使用 **ConfigurationRepositoryWeb**（对于基于 Web 的服务器）和 **ConfigurationRepositoryShare**（对于基于 SMB 的服务器）块定义配置服务器。
- **资源服务器**：打包为 PowerShell 模块的 DSC 资源存储库。 使用 **ResourceRepositoryWeb**（对于基于 Web 的服务器）和 **ResourceRepositoryShare**（对于基于 SMB 的服务器）块定义资源服务器。
- **报表服务器**：DSC 将报表数据发送到的服务。 使用 **ReportServerWeb** 块定义报表服务器。 报表服务器必须是 Web 服务。

有关请求服务的更多详细信息，请参阅 [Desired State Configuration 请求服务](../pull-server/pullServer.md)。

## <a name="configuration-server-blocks"></a>配置服务器块

若要定义基于 Web 的配置服务器，请创建 **ConfigurationRepositoryWeb** 块。
**ConfigurationRepositoryWeb** 定义以下属性。

|属性|类型|说明|
|---|---|---|
|AllowUnsecureConnection|布尔|设置为 **$TRUE** 以允许无需身份验证即可从节点连接到服务器。 设置为 **$FALSE** 以要求进行身份验证。|
|CertificateID|字符串|用于向服务器进行身份验证的证书指纹。|
|ConfigurationNames|string[]|目标节点将请求的配置名称的数组。 仅当通过 RegistrationKey  将节点注册到请求服务后，才使用这些操作。 有关详细信息，请参阅[使用配置名称设置请求客户端](../pull-server/pullClientConfigNames.md)。|
|RegistrationKey|字符串|用于将节点注册到请求服务的 GUID。 有关详细信息，请参阅[使用配置名称设置请求客户端](../pull-server/pullClientConfigNames.md)。|
|ServerURL|字符串|配置服务的 URL。|
|ProxyURL*|字符串|要在与配置服务通信时使用的 http 代理的 URL。|
|ProxyCredential*|pscredential|用于 http 代理的凭据。|

> [!NOTE]
> * 在 Windows 版本 1809 及更高版本中受支持。

提供简化本地节点的 ConfigurationRepositoryWeb 值配置的示例脚本 - 请参阅[生成 DSC 元配置](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

要定义基于 SMB 的配置服务器，请创建 **ConfigurationRepositoryShare** 块。
**ConfigurationRepositoryShare** 定义以下属性。

|属性|类型|说明|
|---|---|---|
|凭据|MSFT_Credential|用于对 SMB 共享进行身份验证的凭据。|
|SourcePath|字符串|SMB 共享的路径。|

## <a name="resource-server-blocks"></a>资源服务器块

若要定义基于 Web 的资源服务器，请创建 **ResourceRepositoryWeb** 块。
**ResourceRepositoryWeb** 定义以下属性。

|属性|类型|说明|
|---|---|---|
|AllowUnsecureConnection|布尔|设置为 **$TRUE** 以允许无需身份验证即可从节点连接到服务器。 设置为 **$FALSE** 以要求进行身份验证。|
|CertificateID|字符串|用于向服务器进行身份验证的证书指纹。|
|RegistrationKey|字符串|用于将节点标识到请求服务的 GUID。|
|ServerURL|字符串|配置服务器的 URL。|
|ProxyURL*|字符串|要在与配置服务通信时使用的 http 代理的 URL。|
|ProxyCredential*|pscredential|用于 http 代理的凭据。|

> [!NOTE]
> * 在 Windows 版本 1809 及更高版本中受支持。

提供简化本地节点的 ResourceRepositoryWeb 值配置的示例脚本 - 请参阅[生成 DSC 元配置](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

若要定义的基于 SMB 的资源服务器，请创建 **ResourceRepositoryShare** 块。
**ResourceRepositoryShare** 定义以下属性。

|属性|类型|说明|
|---|---|---|
|凭据|MSFT_Credential|用于对 SMB 共享进行身份验证的凭据。 有关传递凭据的示例，请参阅[设置 DSC SMB 请求服务器](../pull-server/pullServerSMB.md)|
|SourcePath|字符串|SMB 共享的路径。|

## <a name="report-server-blocks"></a>报表服务器块

若要定义报表服务器，请创建 **ReportServerWeb** 块。
报表服务器角色与基于 SMB 的请求服务不兼容。
**ReportServerWeb** 定义以下属性。

|属性|类型|说明|
|---|---|---|
|AllowUnsecureConnection|布尔|设置为 **$TRUE** 以允许无需身份验证即可从节点连接到服务器。 设置为 **$FALSE** 以要求进行身份验证。|
|CertificateID|字符串|用于向服务器进行身份验证的证书指纹。|
|RegistrationKey|字符串|用于将节点标识到请求服务的 GUID。|
|ServerURL|字符串|配置服务器的 URL。|
|ProxyURL*|字符串|要在与配置服务通信时使用的 http 代理的 URL。|
|ProxyCredential*|pscredential|用于 http 代理的凭据。|

> [!NOTE]
> * 在 Windows 版本 1809 及更高版本中受支持。

提供简化本地节点的 ReportServerWeb 值配置的示例脚本 - 请参阅[生成 DSC 元配置](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

## <a name="partial-configurations"></a>部分配置

若要定义部分配置，请创建 **PartialConfiguration** 块。
有关部分配置的详细信息，请参阅 [DSC 部分配置](../pull-server/partialConfigs.md)。
**PartialConfiguration** 定义以下属性。

|属性|类型|说明|
|---|---|---|
|ConfigurationSource|string[]|以前在 ConfigurationRepositoryWeb  和 ConfigurationRepositoryShare  块中定义的配置服务器的名称数组，将从其中拉取部分配置。|
|DependsOn|string{}|应用此部分配置之前必须完成的其他配置名称的列表。|
|说明|字符串|用于描述部分配置的文本。|
|ExclusiveResources|string[]|此部分配置专用的资源数组。|
|RefreshMode|字符串|指定 LCM 如何获取此部分配置。 可取值为 __Disabled__、__Push__ 和 __Pull__。 <ul><li>__Disabled__：禁用此部分配置。</li><li> __Push__：通过调用 [Publish-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet 将部分配置推送到节点。 从服务推送或请求该节点的所有部分配置后，可以通过调用 `Start-DscConfiguration –UseExisting` 来启动配置。 这是默认值。</li><li>__Pull：__ 将节点配置为从拉取服务定期检查部分配置。 如果将此属性设置为 __Pull__，则必须在 __ConfigurationSource__ 属性中指定请求服务。 有关 Azure 自动化请求服务的详细信息，请参阅 [Azure 自动化 DSC 概述](https://docs.microsoft.com/azure/automation/automation-dsc-overview)。</li></ul>|
|ResourceModuleSource|string[]|可从中下载此部分配置所需资源的资源服务器的名称数组。 这些名称必须表示之前在 ResourceRepositoryWeb  和 ResourceRepositoryShare  块中定义的服务终结点。|

__注意：__ Azure 自动化 DSC 支持部分配置，但每个节点只能从每个自动化帐户中请求一个配置。

## <a name="see-also"></a>另请参阅

### <a name="concepts"></a>概念
[Desired State Configuration 概述](../overview/overview.md)

[Azure 自动化 DSC 入门](https://docs.microsoft.com/azure/automation/automation-dsc-getting-started)

### <a name="other-resources"></a>其他资源

[Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)

[使用配置名称设置请求客户端](../pull-server/pullClientConfigNames.md)
