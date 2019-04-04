---
ms.date: 05/17/2018
keywords: powershell, 核心
title: PowerShell 6.0 的重大更改
ms.openlocfilehash: d25cf07baa11040af57f330feede44635c00c551
ms.sourcegitcommit: f268dce5b5e72be669be0c6634b8db11369bbae2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58623919"
---
# <a name="breaking-changes-for-powershell-60"></a>PowerShell 6.0 的重大更改

## <a name="features-no-longer-available-in-powershell-core"></a>PowerShell Core 中不再可用的功能

### <a name="powershell-workflow"></a>PowerShell 工作流

[PowerShell 工作流][workflow]是基于可为长时间运行或并行化任务创建可靠 runbook 的 [Windows Workflow Foundation (WF)][workflow-foundation] 生成的 Windows PowerShell 中的一项功能。

由于缺少对 .NET Core 中的 Windows Workflow Foundation 的支持，我们将不继续在 PowerShell Core 中支持 PowerShell 工作流。

将来，我们希望使用 PowerShell 语言启用本机并行/并发，而无需使用 PowerShell 工作流。

[workflow]: https://docs.microsoft.com/powershell/scripting/core-powershell/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a>自定义管理单元

[PowerShell 管理单元][snapin]是 PowerShell 社区中未广泛采用的 PowerShell 模块的前身。

鉴于支持管理单元的复杂性及其缺乏在社区中的使用，我们不再支持 PowerShell Core 中的自定义管理单元。

现在，这将中断 Windows 和 Windows Server 中的 `ActiveDirectory` 和 `DnsClient` 模块。

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a>WMI v1 cmdlet

鉴于支持两个基于 WMI 的模块集的复杂性，我们从 PowerShell Core 中删除 WMI v1 cmdlet：

- `Get-WmiObject`
- `Invoke-WmiMethod`
- `Register-WmiEvent`
- `Set-WmiInstance`

我们转为建议使用 CIM（也称为 WMI v2）cmdlet，它们提供了与新功能及经过重新设计的语法相同的功能：

- `Get-CimAssociatedInstance`
- `Get-CimClass`
- `Get-CimInstance`
- `Get-CimSession`
- `Invoke-CimMethod`
- `New-CimInstance`
- `New-CimSession`
- `New-CimSessionOption`
- `Register-CimIndicationEvent`
- `Remove-CimInstance`
- `Remove-CimSession`
- `Set-CimInstance`

### <a name="microsoftpowershelllocalaccounts"></a>Microsoft.PowerShell.LocalAccounts

由于使用了不受支持的 API 而从 PowerShell Core 中删除 `Microsoft.PowerShell.LocalAccounts`，直至找到更佳解决方案。

### <a name="-computer-cmdlets"></a>`*-Computer` cmdlet

由于使用了不受支持的 API，从 PowerShell Core 中删除了以下 cmdlet，直至找到更佳解决方案。

- Add-Computer
- Checkpoint-Computer
- Remove-Computer
- Restore-Computer

### <a name="-counter-cmdlets"></a>`*-Counter` cmdlet

由于使用了不受支持的 API 而从 PowerShell Core 中删除 `*-Counter`，直至找到更佳解决方案。

### <a name="-eventlog-cmdlets"></a>`*-EventLog` cmdlet

由于使用了不受支持的 API 而从 PowerShell Core 中了删除 `*-EventLog`。 直到找到更佳解决方案。 `Get-WinEvent` 和 `Create-WinEvent` 可用于在 Windows 上获取和创建事件。

## <a name="enginelanguage-changes"></a>引擎/语言更改

### <a name="rename-powershellexe-to-pwshexe-5101httpsgithubcompowershellpowershellissues5101"></a>将 `powershell.exe` 重命名为 `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)

为了向用户提供在 Windows 上调用 PowerShell Core（而不是 Windows PowerShell）的确定方法，PowerShell Core 二进制文件在 Windows 上已更改为 `pwsh.exe`，在非 Windows 平台上已更改为 `pwsh`。

缩短的名称也与非 Windows 平台上 shell 的命名一致。

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193httpsgithubcompowershellpowershellissues5193"></a>不要将换行符插入到输出（表除外）[#5193](https://github.com/PowerShell/PowerShell/issues/5193)

以前，输出与控制台的宽度对齐，并且在控制台的端宽度添加换行符，这意味着如果重新设置终端的大小，输出不会按预期重格式化。 这一更改不适用于表格，因为换行符是保持列对齐所必需的。

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432httpsgithubcompowershellpowershellissues5432"></a>对具有值类型元素类型的集合，跳过 null 元素检查 [#5432](https://github.com/PowerShell/PowerShell/issues/5432)

对于 `Mandatory` 参数及 `ValidateNotNull` 和 `ValidateNotNullOrEmpty` 属性，如果集合的元素类型是值类型，则跳过 null 元素检查。

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369httpsgithubcompowershellpowershellissues5369"></a>更改 `$OutputEncoding` 以使用 `UTF-8 NoBOM` 编码，而不使用 ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)

以前的编码 ASCII（7 位）在某些情况下会导致输出的错误更改。 此更改将使 `UTF-8 NoBOM` 成为默认设置，从而保留具有大多数工具和操作系统支持的编码的 Unicode 输出。

### <a name="remove-allscope-from-most-default-aliases-5268httpsgithubcompowershellpowershellissues5268"></a>从大多数默认别名中删除 `AllScope` [#5268](https://github.com/PowerShell/PowerShell/issues/5268)

为了加快作用域创建，从大多数默认别名中删除了 `AllScope`。 保留 `AllScope` 供查找速度更快的几个常用别名使用。

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113httpsgithubcompowershellpowershellissues5113"></a>`-Verbose` 和 `-Debug` 不再替代 `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)

以前，如果已指定 `-Verbose` 或 `-Debug`，则它会替代 `$ErrorActionPreference` 的行为。 进行此更改后，`-Verbose` 和 `-Debug` 不再影响 `$ErrorActionPreference` 的行为。

## <a name="cmdlet-changes"></a>Cmdlet 更改

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320httpsgithubcompowershellpowershellissues5320"></a>在没有返回任何数据时，Invoke-RestMethod 不返回有用的信息。 [#5320](https://github.com/PowerShell/PowerShell/issues/5320)

当 API 仅返回 `null` 时，Invoke-RestMethod 将其序列化为字符串 `"null"`，而不是 `$null`。 此项更改修复了 `Invoke-RestMethod` 中的逻辑，以便将有效的单个值 JSON `null` 文本正确序列化为 `$null`。

### <a name="remove--computername-from--computer-cmdlets-5277httpsgithubcompowershellpowershellissues5277"></a>从 `*-Computer` cmdlet 中删除 `-ComputerName` [#5277](https://github.com/PowerShell/PowerShell/issues/5277)

由于 CoreFX 中的 RPC 远程处理出现问题（特别是在非 Windows 平台上）以及为确保在 PowerShell 中获得一致的远程处理体验，已将 `-ComputerName` 参数从 `\*-Computer` cmdlet 中删除。 改为使用 `Invoke-Command` 作为远程执行 cmdlet 的方法。

### <a name="remove--computername-from--service-cmdlets-5090httpsgithubcompowershellpowershellissues5094"></a>从 `*-Service` cmdlet 中删除 `-ComputerName` [#5090](https://github.com/PowerShell/PowerShell/issues/5094)

为了鼓励一致地使用 PSRP，已将 `-ComputerName` 参数从 `*-Service` cmdlet 中删除。

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197httpsgithubcompowershellpowershellissues5197"></a>如果 `a*b` 实际上不存在，则修复 `Get-Item -LiteralPath a*b` 以返回错误 [#5197](https://github.com/PowerShell/PowerShell/issues/5197)

以前，给定通配符的 `-LiteralPath` 将其视为与 `-Path` 相同，如果该通配符未找到任何文件，则会以无提示方式退出。 正确的行为应该是 `-LiteralPath` 是文本，因此，如果文件不存在，它应显示错误。 更改就是将与 `-Literal` 一起使用的通配符视作文本。

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134httpsgithubcompowershellpowershellissues5134"></a>当类型信息以 CSV 显示时，`Import-Csv` 应在导入时应用 `PSTypeNames` [#5134](https://github.com/PowerShell/PowerShell/issues/5134)

以前，使用 `Export-CSV` 导出的对象（带有使用 `ConvertFrom-Csv` 导入的 `TypeInformation`）已不保留类型信息。 此更改会将类型信息添加到 `PSTypeNames` 成员（若可从 CSV 文件中获得）。

### <a name="-notypeinformation-should-be-default-on-export-csv-5131httpsgithubcompowershellpowershellissues5131"></a>`-NoTypeInformation` 在 `Export-Csv` 上应为默认设置 [#5131](https://github.com/PowerShell/PowerShell/issues/5131)

此更改旨在解决客户对 `Export-CSV` 的默认行为的反馈，以包括类型信息。

以前，该 cmdlet 将输出一条注释作为包含对象的类型名称的第一行。 此更改是为了默认取消此行为，因为大多数工具不理解该行为。 使用 `-IncludeTypeInformation` 以保留以前的行为。

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112httpsgithubcompowershellpowershellissues5112"></a>通过未加密的连接发送 `-Credential` 时，Web Cmdlet 应发出警告 [#5112](https://github.com/PowerShell/PowerShell/issues/5112)

使用 HTTP 时，包括密码在内的内容将以明文形式发送。 此更改默认不允许此操作，并且如果以不安全的方式传递凭据，则返回错误。 用户可以使用 `-AllowUnencryptedAuthentication` 开关来绕过此操作。

## <a name="api-changes"></a>API 更改

### <a name="remove-addtypecommandbase-class-5407httpsgithubcompowershellpowershellissues5407"></a>删除 `AddTypeCommandBase` 类 [#5407](https://github.com/PowerShell/PowerShell/issues/5407)

从 `Add-Type` 删除 `AddTypeCommandBase` 类以提高性能。 此类仅供 Add-Type cmdlet 使用，不应影响用户。

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080httpsgithubcompowershellpowershellissues5080"></a>将带有参数 `-Encoding` 的 cmdlet 统一为 `System.Text.Encoding` 类型 [#5080](https://github.com/PowerShell/PowerShell/issues/5080)

`-Encoding` 值 `Byte` 已从文件系统提供程序 cmdlet 中删除。 新参数 `-AsByteStream` 现可用于指定需要一个字节流作为输入，或用于指定输出是一个字节流。

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055httpsgithubcompowershellpowershellissues5055"></a>为空和 null `-UFormat` 参数添加更好的错误消息 [#5055](https://github.com/PowerShell/PowerShell/issues/5055)

以前，在将空格式字符串传递到 `-UFormat` 时，会出现毫无用处的错误消息。 已添加一个更具描述性的错误。

### <a name="clean-up-console-code-4995httpsgithubcompowershellpowershellissues4995"></a>清理控制台代码 [#4995](https://github.com/PowerShell/PowerShell/issues/4995)

已删除以下功能，因为它们在 PowerShell Core 中不受支持，也没有计划添加支持，因为它们出于适用于 Windows PowerShell 旧版的原因而存在：`-psconsolefile` 开关和代码、`-importsystemmodules` 开关和代码以及字体更改代码。

### <a name="removed-runspaceconfiguration-support-4942httpsgithubcompowershellpowershellissues4942"></a>已删除 `RunspaceConfiguration` 支持 [#4942](https://github.com/PowerShell/PowerShell/issues/4942)

以前，在使用 API 以编程方式创建 PowerShell 运行空间时，可以使用旧版 [`RunspaceConfiguration`][runspaceconfig] 或较新的 [`InitialSessionState`][iss]。 此更改不再支持 `RunspaceConfiguration` 并仅支持 `InitialSessionState`。

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923httpsgithubcompowershellpowershellissues4923"></a>`CommandInvocationIntrinsics.InvokeScript` 将参数绑定到 `$input` 而不是 `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)

形参的位置不正确会导致将实参作为输入而不是实参进行传递。

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903httpsgithubcompowershellpowershellissues4903"></a>从 `Get-Help` 中删除不受支持的 `-showwindow` 开关 [#4903](https://github.com/PowerShell/PowerShell/issues/4903)

`-showwindow` 依赖于 WPF，这在 CoreCLR 上不受支持。

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866httpsgithubcompowershellpowershellissues4866"></a>允许为 `Remove-Item` 在注册表路径中使用 * [#4866](https://github.com/PowerShell/PowerShell/issues/4866)

以前，给定通配符的 `-LiteralPath` 将其视为与 `-Path` 相同，如果该通配符未找到任何文件，则会以无提示方式退出。 正确的行为应该是 `-LiteralPath` 是文本，因此，如果文件不存在，它应显示错误。 更改就是将与 `-Literal` 一起使用的通配符视作文本。

### <a name="fix-set-service-failing-test-4802httpsgithubcompowershellpowershellissues4802"></a>修复 `Set-Service` 失败测试 [#4802](https://github.com/PowerShell/PowerShell/issues/4802)

以前，如果使用了 `New-Service -StartupType foo`，则忽略 `foo`，并使用一些默认的启动类型创建服务。 此更改是以显式方式来为无效启动类型引发错误。

### <a name="rename-isosx-to-ismacos-4700httpsgithubcompowershellpowershellissues4700"></a>将 `$IsOSX` 重命名为 `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)

PowerShell 中的命名应与我们的命名保持一致，并符合 Apple 对 macOS 而不是 OSX 的使用。 但是，出于可读性考虑，我们一直保持 Pascal 大小写格式。

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573httpsgithubcompowershellpowershellissues4573"></a>在将无效脚本传递到 -File 时，使错误消息保持一致，在传递不确定的参数时提示更好的错误 [#4573](https://github.com/PowerShell/PowerShell/issues/4573)

更改 `pwsh.exe` 的退出代码以与 Unix 约定保持一致

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302httpsgithubcompowershellpowershellissues4302-4303httpsgithubcompowershellpowershellissues4303"></a>从 `Diagnostics` 模块删除 `LocalAccount` 和 cmdlet。 [#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)

由于不受支持的 API，会删除 `LocalAccounts` 模块和 `Diagnostics` 模块中的 `Counter` cmdlet，直到找到更好的解决方案。

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036httpsgithubcompowershellpowershellissues4036"></a>使用 bool 参数执行 PowerShell 脚本不起作用 [#4036](https://github.com/PowerShell/PowerShell/issues/4036)

以前，使用 powershell.exe（现在使用 pwsh.exe）执行 PowerShell 脚本，使用 `-File` 无法将 `$true`/`$false` 作为参数值进行传递。 添加了支持将 `$true`/`$false` 作为参数的解析值。 由于当前记录的语法不起作用，也支持开关值。

### <a name="remove-clrversion-property-from-psversiontable-4027httpsgithubcompowershellpowershellissues4027"></a>从 `$PSVersionTable` 删除 `ClrVersion` 属性 [#4027](https://github.com/PowerShell/PowerShell/issues/4027)

`$PSVersionTable` 的 `ClrVersion` 属性对 CoreCLR 用处不大，最终用户不应使用该值来确定兼容性。

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019httpsgithubcompowershellpowershellissues4019"></a>将 `powershell.exe` 的位置参数从 `-Command` 更改为 `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)

在非 Windows 平台上启用 PowerShell 的整个使用。 这意味着，在基于 Unix 的系统上，可以创建脚本可执行文件，以自动调用 PowerShell 而不是显式调用 `pwsh`。 这也意味着，现在可以执行诸如 `powershell foo.ps1` 或 `powershell fooScript` 的操作，而无需指定 `-File`。 但是，此更改现在要求在尝试执行诸如 `powershell.exe Get-Command` 的操作时，显式指定 `-c` 或 `-Command`。

### <a name="implement-unicode-escape-parsing-3958httpsgithubcompowershellpowershellissues3958"></a>实现 Unicode 转义分析 [#3958](https://github.com/PowerShell/PowerShell/issues/3958)

将 `` `u####`` 或 `` `u{####}`` 转换为相应的 Unicode 字符。 若要输出文本 `` `u``，转义反引号：``` ``u```。

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940httpsgithubcompowershellpowershellissues3940"></a>在非 Windows 平台上将 `New-ModuleManifest` 编码更改为 `UTF8NoBOM` [#3940](https://github.com/PowerShell/PowerShell/issues/3940)

以前，`New-ModuleManifest` 创建带有 BOM 的 UTF-16 格式的 psd1 清单，这为 Linux 工具带来了一个问题。 这一重大更改将 `New-ModuleManifest` 的编码更改为非 Windows 平台中的 UTF（无 BOM）。

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780httpsgithubcompowershellpowershellissues3780"></a>防止 `Get-ChildItem` 递归到符号链接中 (#1875)。 [#3780](https://github.com/PowerShell/PowerShell/issues/3780)

此更改使 `Get-ChildItem` 更符合 Unix `ls -r` 和 Windows `dir /s` 本机命令。 如上述命令一样，该 cmdlet 显示在递归期间找到的目录的符号链接，但不会递归到它们中。

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706httpsgithubcompowershellpowershellissues3706"></a>修复 `Get-Content -Delimiter` 以便不在返回的行中包含分隔符 [#3706](https://github.com/PowerShell/PowerShell/issues/3706)

以前，使用 `Get-Content -Delimiter` 时的输出不一致且不方便，因为它需要进一步处理数据才能删除分隔符。 此更改删除返回行中的分隔符。

### <a name="implement-format-hex-in-c-3320httpsgithubcompowershellpowershellissues3320"></a>使用 C# 实现 Format-Hex [#3320](https://github.com/PowerShell/PowerShell/issues/3320)

`-Raw` 参数现在是一个“no-op”（因为它不执行任何操作）。 今后，所有输出将显示数字的真实表示，其中包含其类型的所有字节（`-Raw` 参数在执行此更改之前正式执行的操作）。

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319httpsgithubcompowershellpowershellissues3319"></a>作为默认 shell 的 PowerShell 对脚本命令不起作用 [#3319](https://github.com/PowerShell/PowerShell/issues/3319)

在 Unix 上，对于交互式 shell 而言，shell 通常会接受 `-i`，许多工具都期待这一行为（例如，`script`，以及在将 PowerShell 设置为默认 shell 时），并使用 `-i` 开关来调用 shell。 此更改具有突破性，因为 `-i` 以前可用作速记以匹配 `-inputformat`，它现在需要使用 `-in`。

### <a name="typo-fix-in-get-computerinfo-property-name-3167httpsgithubcompowershellpowershellissues3167"></a>Get-ComputerInfo 属性名中的拼写错误修复 [#3167](https://github.com/PowerShell/PowerShell/issues/3167)

`BiosSerialNumber` 被错误地拼写为 `BiosSeralNumber`，并被更改为正确的拼写。

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024httpsgithubcompowershellpowershellissues3024"></a>添加 `Get-StringHash` 和 `Get-FileHash` cmdlet [#3024](https://github.com/PowerShell/PowerShell/issues/3024)

此更改是 CoreFX 不支持的一些哈希算法，因此它们将不再可用：

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672httpsgithubcompowershellpowershellissues2672"></a>在传递 $null 返回所有对象而不是错误时在 `Get-*` cmdlet 上添加验证 [#2672](https://github.com/PowerShell/PowerShell/issues/2672)

将 `$null` 传递给以下任何项，现在会引发错误：

- `Get-Credential -UserName`
- `Get-Event -SourceIdentifier`
- `Get-EventSubscriber -SourceIdentifier`
- `Get-Help -Name`
- `Get-PSBreakpoint -Script`
- `Get-PSProvider -PSProvider`
- `Get-PSSessionConfiguration -Name`
- `Get-PSSnapin -Name`
- `Get-Runspace -Name`
- `Get-RunspaceDebug -RunspaceName`
- `Get-Service -Name`
- `Get-TraceSource -Name`
- `Get-Variable -Name`
- `Get-WmiObject -Class`
- `Get-WmiObject -Property`

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482httpsgithubcompowershellpowershellissues2482"></a>在 `Import-Csv` 中添加支持 W3C 扩展日志文件格式 [#2482](https://github.com/PowerShell/PowerShell/issues/2482)

以前，`Import-Csv` cmdlet 不能用于直接导入采用 W3C 扩展日志格式的日志文件，并且需要执行其他操作。 进行此更改后，支持 W3C 扩展日志格式。

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035httpsgithubcompowershellpowershellissues2035"></a>PS 函数中 `ValueFromRemainingArguments` 的参数绑定问题 [#2035](https://github.com/PowerShell/PowerShell/issues/2035)

`ValueFromRemainingArguments` 现在返回一些值作为数组，而不是本身是数组的单个值。

### <a name="buildversion-is-removed-from-psversiontable-1415httpsgithubcompowershellpowershellissues1415"></a>从 `$PSVersionTable` 中删除 `BuildVersion` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)

从 `$PSVersionTable` 中删除 `BuildVersion` 属性。 此属性与 Windows 内部版本相关。 我们建议使用 `GitCommitId` 检索 PowerShell Core 的确切内部版本。

### <a name="changes-to-web-cmdlets"></a>对 Web Cmdlet 的更改

Web Cmdlet 的基础 .NET API 已更改为 `System.Net.Http.HttpClient`。 此更改提供了许多好处。 但是，此更改以及缺乏与 Internet Explorer 的互操作性导致了 `Invoke-WebRequest` 和 `Invoke-RestMethod` 中的几次重大更改。

- `Invoke-WebRequest` 现在仅支持基本 HTML 分析。 `Invoke-WebRequest` 始终返回一个 `BasicHtmlWebResponseObject` 对象。 已删除 `ParsedHtml` 和 `Forms` 属性。
- `BasicHtmlWebResponseObject.Headers` 值现在是 `String[]` 而不是 `String`。
- `BasicHtmlWebResponseObject.BaseResponse` 现在是一个 `System.Net.Http.HttpResponseMessage` 对象。
- Web Cmdlet 异常上的 `Response` 属性现在是一个 `System.Net.Http.HttpResponseMessage` 对象。
- 对于 `-Headers` 和 `-UserAgent` 参数，严格的 RFC 标头分析是默认设置。 这可以使用 `-SkipHeaderValidation` 绕过。
- 不再支持 `file://` 和 `ftp://` URI 方案。
- 不再采用 `System.Net.ServicePointManager` 设置。
- 目前在 macOS 上尚无基于证书的身份验证。
- 通过 `http://` URI 使用 `-Credential` 将导致错误。 使用 `https://` URI 或提供 `-AllowUnencryptedAuthentication` 参数来阻止此错误。
- 现在当重定向尝试超过提供的限制时，`-MaximumRedirection` 会生成终止错误时，而不是返回最后一次重定向的结果。
