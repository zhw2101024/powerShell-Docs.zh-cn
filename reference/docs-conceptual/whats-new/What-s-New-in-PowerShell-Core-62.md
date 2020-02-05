---
title: PowerShell Core 6.2 中的新增功能
description: PowerShell Core 6.2 中发布的新功能和更改
ms.date: 03/28/2019
ms.openlocfilehash: 98dd97b064e11509bf97e68e0a312e6b34b5d2bc
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995482"
---
# <a name="whats-new-in-powershell-core-62"></a>PowerShell Core 6.2 中的新增功能

PowerShell Core 6.2 版本侧重于性能改进、bug 修复以及可提高质量的较小 cmdlet 和语言增强功能。 若要查看改进的完整列表，请在 GitHub 上查看我们详细的[更改日志](https://github.com/PowerShell/PowerShell/releases)。

## <a name="experimental-features"></a>实验性功能

在此之前，我们启用了对[实验性功能][]的支持。 6\.2 版本中提供了四个要试用的实验性功能。请提供反馈，以便我们进行改进，并决定该功能是否值得提升到主流状态。

使用 `Get-ExperimentalFeature` 获取可用的实验性功能列表。 可以使用 `Enable-ExperimentalFeature` 和 `Disable-ExperimentalFeature` 启用或禁用这些功能。

### <a name="command-not-found-suggestions"></a>命令未找到建议

此功能使用模糊匹配来查找可能键入错误的命令或 cmdlet 的建议。

```powershell
Enable-ExperimentalFeature -Name PSCommandNotFoundSuggestion
```

#### <a name="example"></a>示例

在本例中，拼写错误的 cmdlet 名称与多个建议模糊匹配（从最可能到最不可能）。

```powershell
Get-Commnd
```

```Output
Get-Commnd : The term 'Get-Commnd' is not recognized as the name of a cmdlet, function, script file, or operable program.
Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-Commnd
+ ~~~~~~~~~~
+ CategoryInfo          : ObjectNotFound: (Get-Commnd:String) [], CommandNotFoundException
+ FullyQualifiedErrorId : CommandNotFoundException


Suggestion [4,General]: The most similar commands are: Get-Command, Get-Content, Get-Job, Get-Module, Get-Event, Get-Host, Get-Member, Get-Item, Set-Content.
```

### <a name="implicit-remoting-batching"></a>隐式远程处理批处理

在管道中使用[隐式远程处理](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/)时，PowerShell 将独立处理管道中的每个命令。 在管道执行过程中，对象在客户端和远程系统之间重复序列化和 `de-serialized`。

PowerShell 使用该功能分析管道，以确定该命令是否可以安全运行，以及它是否存在于目标系统中。 如果为 true，PowerShell 将远程执行整个管道，并且只将结果序列化和 `de-serializes` 返回给客户端。

```powershell
Enable-ExperimentalFeature -Name PSImplicitRemotingBatching
```

在 localhost 上实际测试 `Get-Process | Sort-Object` 的时间从 10-15 秒减少到 20-30 毫秒  。 该功能只需在客户端上启用。 不需要在服务器上进行任何更改。

### <a name="temp-drive"></a>临时驱动器

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

如果在不同操作系统上使用 PowerShell Core，会发现在 Windows、macOS 和 Linux 上用于查找临时目录的环境变量是不同的！ 借助此功能，可获得一个名为 `Temp:` 的 [PSDrive][]，它将自动映射到你正在使用的操作系统的临时文件夹。

#### <a name="example"></a>示例

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> Get-Content Temp:/hello.txt
Hello World!
```

注意，本机文件命令（如 Linux 上的 `ls`）不能识别 PSDrive，因此看不到此 `Temp:` 驱动器。

### <a name="abbreviation-expansion"></a>缩写扩展

PowerShell cmdlet 应具有描述性名词。 这将导致更难键入的长名称。 该功能允许只键入 cmdlet 的大写字符，并使用 Tab 自动补全查找匹配项。

```powershell
Enable-ExperimentalFeature -Name PSUseAbbreviationExpansion
```

#### <a name="example"></a>示例

```powershell
PS> i-arsavsf
```

如果按 Tab 键，并安装了 Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) 模块，它将自动完成为：

```Output
PS> Import-AzRecoveryServicesAsrVaultSettingsFile
```

> [!NOTE]
> 此功能旨在以交互方式使用。 不能执行 cmdlet 的缩写形式。
> 此功能不能替代别名。

## <a name="breaking-changes"></a>重大更改

- 修复 `Write-Output` 中的 `-NoEnumerate` 行为，使之与 Windows PowerShell 一致。 (#9069)
- 使 `Join-String -InputObject 1,2,3` 结果等于 `1,2,3 | Join-String` 结果 (#8611)（感谢 @sethvs！）
- 将 `-Stable` 添加到 `Sort-Object` 和相关测试 (#7862)（感谢 @KirkMunro！）
- 改进 `Start-Sleep` cmdlet 以接受秒的小数部分 (#8537)（感谢 @Prototyyppi！）
- 将 Hashtable 更改为在所有区域性中使用 OrdinalIgnoreCase 作为 `case-insensitive` (#8566)
- 修复 `Import-Csv` 中的 LiteralPath  以绑定到 `Get-ChildItem` 输出 (#8277)（感谢 @iSazonov！）
- 如果在 `Import-Csv` 中使用双引号分隔符，则不再跳过没有名称的列 (#7899)（感谢 @Topping！）
- `Get-ExperimentalFeature` 不再具有 `-ListAvailable` 开关 (#8318)
- 调试参数现将 `$DebugPreference` 设置为“继续”  而不是“查询”  (#8195)（感谢 @KirkMunro！）
- 如果在与 pwsh 一起使用的非交互式、重定向、编码命令中指定 `-OutputFormat`，则采用该指定项 (#8115)
- 在尝试从 GAC 加载程序集之前，先从模块基路径加载程序集 (#8073)
- 从 Linux 预览包中删除波形符 (#8244)
- 先移动处理 `-WorkingDirectory` 再处理配置文件 (#8079)
- 不要在 Unix 上添加 `PATHEXT` 环境变量 (#7697)（感谢 @iSazonov！）

## <a name="known-issues"></a>已知问题

- 在 Windows IOT ARM 平台上进行的远程处理存在模块加载问题。 请参阅 (#8053)

## <a name="general-updates-and-fixes"></a>常规更新和修补程序

- 在区分大小写的文件系统上为文件和文件夹启用不区分大小写的 Tab 自动补全 (#8128)
- 公开 PSVersionInfo.PSVersion 和 PSVersionInfo.PSEdition (#8054)（感谢 @KirkMunro！）
- 在 `catch{ }` 块中为 `$_` / `$PSItem` 添加类型推理 (#8020)（感谢 @vexx32！）
- 修复静态方法调用类型推理 (#8018)（感谢 @SeeminglyScience！）
- 为 `Select-Object`、`Group-Object`、PSObject  和 Hashtable  创建推理类型 (#7231)（感谢 @powercode！）
- 支持使用 `ByRef-like` 类型参数的调用方法 (#7721)
- 处理 Windows PowerShell 模块路径已在环境的 PSModulePath 中的情况 (#7727)
- 通过存储纯文本来启用适用于非 Windows 的 `SecureString` cmdlet (#9199)
- 使用 securestring 导入 clixml 时，改进非 Windows 上的错误消息 (#7997)
- 将参数 ReplyTo 添加到 `Send-MailMessage` (#8727)（感谢 @replicaJunction！）
- 将已过时的消息添加到 `Send-MailMessage` (#9178)
- 修复 `Restart-Computer`，以便在 WinRM 不存在时使用 `localhost` (#9160)
- 正在托管 PowerShell 时，使 `Start-Job` 引发终止错误 (#9128)
- 为 ushort、uint、ulong 和短文本添加 C# 样式类型加速器和后缀 (#7813)（感谢 @vexx32！）
- 为数字文本添加了新后缀 - 请参阅 [about_Numeric_Literals][] (#7901)（感谢 @vexx32！）
- 当 SupportsShouldProcess 未设置为“true”时，正确地报告影响级别 (#8209)（感谢 @vexx32！）
- 修复 Web Cmdlet 中的请求字符集问题 (#8742)（感谢 @markekraus！）
- 修复 Web Cmdlet 中预期的 `100-continue` 问题 (#8679)（感谢 @markekraus！）
- 修复 Web Cmdlet 中的文件阻塞性问题 (#7676)（感谢 @Claustn！）
- 修复 `Invoke-RestMethod` 中的代码页分析问题 (#8694)（感谢 @markekraus！）
- 重构 `ConvertTo-Json` 以将 JsonObject.ConvertToJson 公开为公共 API (#8682)
- 使用 -Depth 在 `ConvertFrom-Json` 中添加可配置的最大深度 (#8199)（感谢 @louistio！）
- 在 `ConvertTo-Json` cmdlet 中添加 EscapeHandling 参数 (#7775)（感谢 @iSazonov！）
- 将 `-CustomPipeName` 添加到 pwsh 和 `Enter-PSHostProcess` (#8889)
- 使用 `New-Item` 在 Windows 上启用创建相对符号链接 (#8783)
- 允许 Windows 用户在开发人员模式下创建符号链接，而不需要提升 (#8534)
- 启用 `Write-Information` 以接受 `$null` (#8774)
- 使用 MAML 帮助内容修复高级函数的 `Get-Help` (#8353)
- 当只声明一个参数时，使用 -Parameter 修复 `Get-Help` PSTypeName 问题 (#8754)（感谢 @pougetat！）
- 针对在 ScriptBlock 上执行的 `Get-Help` 进行令牌计算修复，以获得注释帮助。 (#8238)（感谢 @hubuk！）
- 更改 `Get-Help` cmdlet -Parameter 参数，以便它接受字符串数组 (#8454)（感谢 @sethvs！）
- 如果 PAGER 路径包含空格，则对其进行解析 (#8571)（感谢 @pougetat！）
- 在“help”函数中添加 `less` 的使用提示，以指导用户如何退出 (#7998)
- 在 `Format-Hex` cmdlet 中添加支持枚举和 char 类型 (#8191)（感谢 @iSazonov！）
- 从 `Format-Hex` 中删除 ShouldProcess (#8178)
- 将新 Offset 和 Count 参数添加到 `Format-Hex` 并重构 cmdlet (#7877)（感谢 @iSazonov！）
- 允许“name”作为 `ConvertTo-Html` 中“label”的别名键，允许“width”条目为整数 (#8426)（感谢 @mklement0！）
- 使基于脚本块计算的属性在 `ConvertTo-Html` 中再次起作用 (#8427)（感谢 @mklement0！）
- 添加 cmdlet `Join-String` 以从管道输入创建文本 (#7660)（感谢 @powercode！）
- 修复 `Join-String` cmdlet FormatString 参数逻辑 (#8449)（感谢 @sethvs！）
- 将 `Clear-Host` 更改回使用 `$RAWUI` 并清除以进行远程操作 (#8609)
- 更改 `Clear-Host` 以简单地调用 `[console]::clear`，并从 Unix 中删除清晰别名 (#8603)
- 修复 `Import-Csv` 中的 LiteralPath 以绑定到 `Get-ChildItem` 输出 (#8277)（感谢 @iSazonov！）
- help 函数不应为 AliasHelpInfo 使用寻呼程序 (#8552)
- 将 `-UseMinimalHeader` 添加到 `Start-Transcript` 以最小化脚本标头 (#8402)（感谢 @lukexjeremy！）
- 添加 `Enable-ExperimentalFeature` 和 `Disable-ExperimentalFeature` cmdlet (#8318)
- 如果 logman.exe 可用，则公开 PSDiagnostics  中的所有 cmdlet (#8366)
- 在 `non-Windows` 平台上从 `New-PSDrive` 删除 Persist  参数 (#8291)（感谢 @lukexjeremy！）
- 添加对 `cd +` 的支持 (#7206)（感谢 @bergmeister！）
- 使 `Set-Location -LiteralPath` 能够使用名为 - 和 + 的文件夹 (#8089)
- 当给定空路径值或 `$null` 路径值时，`Test-Path` 返回 `$false` (#8080)（感谢 @vexx32！）
- 允许返回动态参数，即使路径不匹配任何提供程序 (#7957)
- 在 Unix 平台上支持 `Get-PSHostProcessInfo` 和 `Enter-PSHostProcess` (#8232)
- 减少 `Get-Content` cmdlet 中的分配 (#8103)（感谢 @iSazonov！）
- 允许 `Add-Content` 在编写内容时与其他工具共享读取访问 (#8091)
- 在将某个容器设定为目标时，`Get/Add-Content` 引发改进错误 (#7823)（感谢 @kvprasoon！）
- 将 `-Name`、`-NoUserOverrides` 和 `-ListAvailable` 参数添加到 `Get-Culture` cmdlet (#7702)（感谢 @iSazonov！）
- 为完成 Encoding  参数添加统一属性。 (#7732)（感谢 @ThreeFive-O！）
- 允许注册代码页的数字 Id 和名称出现在 Encoding  参数中 (#7636)（感谢 @iSazonov！）
- 使用通配符字符修复 `Rename-Item -Path` (#7398)（感谢 @kwkam！）
- 当使用 `Start-Transcript` 且文件存在时，清空文件而不是将其删除 (#8131)（感谢 @paalbra！）
- 通过 FileAccess.Read  和 FileShare.Read  使 `Add-Type` 显式成为开放源代码文件 (#7915)（感谢 @IISResetMe！）
- 修复最新 Windows 的 `Enter-PSSession -ContainerId` (#7883)
- 请确保 NestedModules  属性由 `Test-ModuleManifest` 填充 (#7859)
- 将 `%F` case 添加到 `Get-Date` -UFormat (#7630)（感谢 @britishben！）
- 修复 `Set-Service -Status Stopped` 以停止具有依赖项的服务 (#5525)（感谢 @zhenggu！）

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals
[实验性功能]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
