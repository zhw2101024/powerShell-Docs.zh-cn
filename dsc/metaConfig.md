---
title:   配置本地配置管理器
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# 配置本地配置管理器

> 适用于：Windows PowerShell 5.0

本地配置管理器 (LCM) 是 Windows PowerShell Desired State Configuration (DSC) 的引擎。 LCM 在每个目标节点上运行，负责分析和执行发送到节点的配置。 它还负责 DSC 的许多方面，包括以下各方面。

* 确定刷新模式（推送或请求）。
* 指定节点请求和执行配置的频率。
* 将节点与请求服务器相关联。
* 指定部分配置。

使用特殊类型的配置将 LCM 配置为指定以上各行为。 以下各节介绍如何配置 LCM。

> **注意**：本主题适用于 Windows PowerShell 5.0 中引入的 LCM。 有关在 Windows PowerShell 4.0 中配置 LCM 的信息，请参阅 [Windows PowerShell 4.0 Desired State Configuration 本地配置管理器](metaconfig4.md)。

## 编写和执行 LCM 配置

若要配置 LCM，你需要创建并运行特殊类型的配置。 若要指定 LCM 配置，你可以使用 DscLocalConfigurationManager 特性。 下面演示将 LCM 设置为推送模式的简单配置。

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

调用和运行配置来创建配置 MOF，与常规配置类似（有关创建配置 MOF 的信息，请参阅[编译配置](configurations.md#compiling-the-configuration)）。 与常规配置不同的是，不通过调用 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet 来执行 LCM 配置。 而是通过调用 [Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) cmdlet，将路径作为参数提供给配置 MOF。 执行配置后，可以通过调用 [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) cmdlet 查看 LCM 的属性。

LCM 配置只能包含有限组资源的块。 在上面的示例中，调用的唯一资源名为 **Settings**。 其他可用资源有：

* **ConfigurationRepositoryWeb**：指定用于配置的 HTTP 请求服务器。 
* **ConfigurationRepositoryShare**：指定用于配置的 SMB 请求服务器。
* **ResourceRepositoryWeb**：指定用于模块的 HTTP 请求服务器。
* **ResourceRepositoryShare**：指定用于模块的 SMB 请求服务器。
* **ReportServerWeb**：指定将报告发送到的 HTTP 请求服务器。
* **PartialConfiguration**：指定部分配置。

## 基本设置

不通过指定请求服务器和部分配置 LCM 的所有属性，而是在 **Settings** 块中进行配置。 **Settings** 块中提供下列属性。

|  属性  |  类型  |  说明   | 
|----------- |------- |--------------- | 
| ConfigurationModeFrequencyMins| UInt32| 检查和应用当前配置的时间间隔（以分钟为单位）。 如果将 ConfigurationMode 属性设置为 ApplyOnly，则将忽略此属性。 默认值为 15。 <br> __注意__：此属性的值必须是 __RefreshFrequencyMins__ 属性值的倍数，或者 __RefreshFrequencyMins__ 属性值必须为此属性值的倍数。| 
| RebootNodeIfNeeded| 布尔| 将此设置为 __$true__，可在应用要求重启的设置后自动重启节点。 否则，你必须为要求重启的配置手动重启节点。 默认值为 __$false__。| 
| ConfigurationMode| 字符串 | 指定 LCM 实际如何将配置应用到目标节点。 可能的值为__“ApplyOnly”__、__“ApplyandMonitior”（默认值）__和__“ApplyandAutoCorrect”__。 <ul><li>__ApplyOnly__：DSC 将应用配置，但若未向目标节点推送新配置或从服务器请求新配置，则它不会执行任何进一步操作。 首次应用新配置后，DSC 不会检查是否偏离以前配置的状态。</li><li> __ApplyAndMonitor__：这是默认值。 LCM 将应用任意新配置。 首次应用新配置后，如果目标节点偏离期望状态，则 DSC 将在日志中报告差异。</li><li>__ApplyAndAutoCorrect__：DSC 将应用任何新配置。 首次应用新配置后，如果目标节点偏离适当状态，则 DSC 将在日志中报告差异然后重新应用当前配置。</li></ul>| 
| ActionAfterReboot| 字符串| 指定在应用配置期间重启后进行什么操作。 可能的值为__“ContinueConfiguration”（默认值）__和__“StopConfiguration”__。 <ul><li> __ContinueConfiguration__：在计算机重新启动后继续应用当前配置。</li><li>__StopConfiguration__：在计算机重新启动后停止当前配置。</li></ul>| 
| RefreshMode| 字符串| 指定 LCM 如何获取配置。 可能的值为__“Disabled”__、__“Push”（默认值）__和__“Pull”__。 <ul><li>__Disabled__：DSC 配置对该节点禁用。</li><li> __Push__：通过调用 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet 启动配置。 将配置立即应用到节点。 这是默认值。</li><li>__Pull：__将节点配置为从请求服务器定期检查配置。 如果此属性被设置为 __Pull__，你必须在 __ConfigurationRepositoryWeb__ 或 __ConfigurationRepositoryShare__ 块中指定请求服务器。 有关请求服务器的详细信息，请参阅[设置 DSC 请求服务器](pullServer.md)。</li></ul>| 
| CertificateID| 字符串| 指定访问配置时用于保护凭据的证书的 GUID。 更多详细信息，请参阅 [Want to secure credentials in Windows PowerShell Desired State Configuration?（希望在 Windows PowerShell Desired State Configuration 中保护凭据？）](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx)。| 
| ConfigurationID| 字符串| 用于标识请求模式下要从请求服务器获取的配置文件的 GUID。 如果配置 MOF 名为 ConfigurationID.mof，则节点将在请求服务器上请求配置。<br> __注意：__如果设置此属性，将无法使用 __RegistryKey__ 将节点注册到请求服务器。 有关详细信息，请参阅[使用配置名称设置请求客户端](pullClientConfigNames.md)。| 
| RefreshFrequencyMins| Uint32| LCM 按此时间间隔（以分钟为单位）检查请求服务器以获取更新的配置。 如果 LCM 未配置为请求模式，则将忽略此值。 默认值为 30。<br> __注意__：此属性的值必须是 __ConfigurationModeFrequencyMins__ 属性值的倍数，或者 __ConfigurationModeFrequencyMins__ 属性值必须为此属性值的倍数。| 
| AllowModuleOverwrite| 布尔| 若允许从配置服务器下载的新配置覆盖目标节点上的旧配置，则为 __$TRUE__。 否则为 $FALSE。| 
| DebugMode| 字符串| 可能的值为 __None（默认）__、__ForceModuleImport__ 和 __All__。 <ul><li>设置为 __None__ 可以使用缓存的资源。 这是默认值，应在生产方案中使用。</li><li>设置为 __ForceModuleImport__ 会导致 LCM 重载所有 DSC 资源模块，即使这些模块之前已被加载并缓存，也是如此。 这会影响 DSC 操作的性能，因为将在使用时重新加载每个模块。 通常在调试资源时使用此值</li><li>在此版本中，__All__ 等同于 __ForceModuleImport__</li></ul> |
| ConfigurationDownloadManagers| CimInstance[]| 已过时。 使用 __ConfigurationRepositoryWeb__ 和 __ConfigurationRepositoryShare__ 块定义配置请求服务器。| 
| ResourceModuleManagers| CimInstance[]| 已过时。 使用 __ResourceRepositoryWeb__ 和 __ResourceRepositoryShare__ 块定义资源请求服务器。| 
| ReportManagers| CimInstance[]| 已过时。 使用 __ReportServerWeb__ 块定义报表请求服务器。| 
| PartialConfigurations| CimInstance| 未实现。 不使用。| 
| StatusRetentionTimeInDays | UInt32| LCM 保留当前配置状态的天数。| 

## 请求服务器

请求服务器是一个 OData Web 服务或作为 DSC 文件的中心位置使用的 SMB 共享。 LCM 配置支持定义以下类型的请求服务器：

* **配置服务器**：DSC 配置的存储库。 使用 **ConfigurationRepositoryWeb**（基于 Web 的服务器）和 **ConfigurationRepositoryShare**（基于 SMB 的服务器）块定义配置服务器。
* 资源服务器 - 打包为 PowerShell 模块的 DSC 资源存储库。 使用 **ResourceRepositoryWeb**（基于 Web 的服务器）和 **ResourceRepositoryShare**（基于 SMB 的服务器）块定义资源服务器。
* 报表服务器 - DSC 将报表数据发送到的服务。 使用 **ReportServerWeb** 块定义报表服务器。 报表服务器必须是 Web 服务。

有关设置和使用请求服务器的信息，请参阅[设置 DSC 请求服务器](pullServer.md)。

## 配置服务器块

要定义基于 Web 的配置服务器，请创建 **ConfigurationRepositoryWeb** 块。 **ConfigurationRepositoryWeb** 定义以下属性。

|属性|类型|说明|
|---|---|---| 
|AllowUnsecureConnection|布尔|设置为 **$TRUE** 以允许无需身份验证即可从节点连接到服务器。 设置为 **$FALSE** 以要求进行身份验证。|
|CertificateID|字符串|表示用于向服务器进行身份验证的证书的 GUID。|
|ConfigurationNames|string[]|目标节点将请求的配置名称的数组。 仅当通过 **RegistrationKey** 将节点注册到请求服务器后，才使用这些操作。 有关详细信息，请参阅[使用配置名称设置请求客户端](pullClientConfigNames.md)。|
|RegistrationKey|字符串|用于将节点注册到请求服务器的 GUID。 有关详细信息，请参阅[使用配置名称设置请求客户端](pullClientConfigNames.md)。|
|ServerURL|字符串|配置服务器的 URL。|

要定义基于 SMB 的配置服务器，请创建 **ConfigurationRepositoryShare** 块。 **ConfigurationRepositoryShare** 定义以下属性。

|属性|类型|说明|
|---|---|---|
|凭据|MSFT_Credential|用于对 SMB 共享进行身份验证的凭据。|
|SourcePath|字符串|SMB 共享的路径。|

## 资源服务器块

若要定义基于 Web 的资源服务器，请创建 **ResourceRepositoryWeb** 块。 **ResourceRepositoryWeb** 定义以下属性。

|属性|类型|说明|
|---|---|---|
|AllowUnsecureConnection|布尔|设置为 **$TRUE** 以允许无需身份验证即可从节点连接到服务器。 设置为 **$FALSE** 以要求进行身份验证。|
|CertificateID|字符串|表示用于向服务器进行身份验证的证书的 GUID。|
|RegistrationKey|字符串|用于将节点标识到请求服务器的 GUID。 有关详细信息，请参阅“如何将节点注册到 DSC 请求服务器”。|
|ServerURL|字符串|配置服务器的 URL。|
 
若要定义的基于 SMB 的资源服务器，请创建 **ResourceRepositoryShare** 块。 **ResourceRepositoryShare** 定义以下属性。

|属性|类型|说明|
|---|---|---|
|凭据|MSFT_Credential|用于对 SMB 共享进行身份验证的凭据。|
|SourcePath|字符串|SMB 共享的路径。|

## 报表服务器块

报表服务器必须是 OData Web 服务。 若要定义报表服务器，请创建 **ReportServerWeb** 块。 **ReportServerWeb** 定义以下属性。

|属性|类型|说明|
|---|---|---| 
|AllowUnsecureConnection|布尔|设置为 **$TRUE** 以允许无需身份验证即可从节点连接到服务器。 设置为 **$FALSE** 以要求进行身份验证。|
|CertificateID|字符串|表示用于向服务器进行身份验证的证书的 GUID。|
|RegistrationKey|字符串|用于将节点标识到请求服务器的 GUID。 有关详细信息，请参阅“如何将节点注册到 DSC 请求服务器”。|
|ServerURL|字符串|配置服务器的 URL。|

## 部分配置

若要定义部分配置，请创建 **PartialConfiguration** 块。 有关部分配置的详细信息，请参阅 [DSC 部分配置](partialConfigs.md)。 **PartialConfiguration** 定义以下属性。

|属性|类型|说明|
|---|---|---| 
|ConfigurationSource|string[]|以前在 **ConfiguratoinRepositoryWeb** 和 **ConfigurationRepositoryShare** 块中定义的配置服务器名称数组，将从其中请求部分配置。|
|DependsOn|string{}|应用此部分配置之前必须完成的其他配置名称的列表。|
|说明|字符串|用于描述部分配置的文本。|
|ExclusiveResources|string[]|此部分配置专用的资源数组。|
|RefreshMode|字符串|指定 LCM 如何获取此部分配置。 可能的值为__“Disabled”__、__“Push”（默认值）__和__“Pull”__。 <ul><li>__Disabled__：禁用此部分配置。</li><li> __Push__：通过调用 [Publish-DscConfiguration](https://technet.microsoft.com/en-us/library/mt517875.aspx) cmdlet 将部分配置推送到节点。 从服务器推送或请求该节点的所有部分配置后，可以通过调用 `Start-DscConfiguration –UseExisting` 来启动配置。 这是默认值。</li><li>__Pull：__将节点配置为从请求服务器定期检查部分配置。 如果将此属性设置为 __Pull__，则必须在 __ConfigurationSource__ 属性中指定请求服务器。 有关请求服务器的详细信息，请参阅[设置 DSC 请求服务器](pullServer.md)。</li></ul>|
|ResourceModuleSource|string[]|可从中下载此部分配置所需资源的资源服务器的名称数组。 这些名称必须表示之前在 **ResourceRepositoryWeb** 和 **ResourceRepositoryShare** 块中定义的资源服务器。|

## 另请参阅 

### 概念
[Windows PowerShell Desired State Configuration 概述](overview.md)
 
[设置 DSC 请求服务器](pullServer.md) 

[Windows PowerShell 4.0 Desired State Configuration 本地配置管理器](metaConfig4.md) 

### 其他资源
[Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) 

[使用配置名称设置请求客户端](pullClientConfigNames.md) 



<!--HONumber=Jun16_HO3-->


