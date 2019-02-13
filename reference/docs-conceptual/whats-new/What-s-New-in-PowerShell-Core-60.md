---
title: PowerShell Core 6.0 中的最近更新
description: PowerShell Core 6.0 中发布的新功能和更改
ms.date: 08/06/2018
ms.openlocfilehash: 83c104d838db9d86fe1d485e92245a9c8f2d2057
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676863"
---
# <a name="whats-new-in-powershell-core-60"></a>PowerShell Core 6.0 中的最近更新

[PowerShell Core 6.0][github] 是为异类环境和混合云而构建的跨平台（Windows、macOS 和 Linux）且开源的新版 PowerShell。

## <a name="moved-from-net-framework-to-net-core"></a>从 .NET Framework 移动到 .NET Core

PowerShell Core 使用 [.NET Core 2.0][] 作为其运行时。
.NET Core 2.0 支持 PowerShell Core 在多平台（Windows、macOS 和 Linux）上运行。
PowerShell Core 还公开 .NET Core 2.0 所提供以用于 PowerShell cmdlet 和脚本的 API 集合。

Windows PowerShell 使用 .NET Framework 运行时承载 PowerShell 引擎。
这意味着 Windows PowerShell 公开由 .NET Framework 提供的 API 集。

.NET Core 和 .NET Framework 之间共享的 API 定义为 [.NET Standard][] 的一部分。

有关这将如何影响 PowerShell Core 和 Windows PowerShell 之间模块/脚本兼容性的详细信息，请参阅 [Windows PowerShell 向后兼容性](#backwards-compatibility-with-windows-powershell).

## <a name="support-for-macos-and-linux"></a>支持 macOS 和 Linux

PowerShell 现在官方支持 macOS 和 Linux，包括：

- Windows 7、8.1 和 10
- Windows Server 2008 R2、2012 R2、2016
- [Windows Server 半年频道][semi-annual]
- Ubuntu 14.04、16.04 和 17.04
- Debian 8.7+ 和 9
- CentOS 7
- Red Hat Enterprise Linux 7
- OpenSUSE 42.2
- Fedora 25、26
- macOS 10.12+

我们社区也为以下平台提供包，但是它们不受正式支持：

- Arch Linux
- Kali Linux
- AppImage（可在多个 Linux 平台上运行）

我们还对以下平台提供试验版本（不受支持）：

- ARM32/ARM64 上的 Windows
- Raspbian (Stretch)

为提高在非 Windows 系统上上的运行性能，已对 PowerShell Core 6.0 作出众多更改。
其中一些是重大更改，这些更改也会影响 Windows。
其他更改仅存在或适用于非 Windows 版的 PowerShell。

- 添加对 Unix 平台上本机命令通配的支持。
- `more` 功能适用于 Linux `$PAGER` 并默认为 `less`。
  这意味着现可将通配符用于本机二进制文件/命令（例如 `ls *.txt`）。 (#3463)
- 处理本机 命令参数时，尾部反斜杠将自动转义。 (#4965)
- 在非 Windows 平台上运行 PowerShell 时，请忽略 `-ExecutionPolicy` 切换，因为当前不支持脚本签名。 (#3481)
- 已修复 ConsoleHost，以支持 Unix 平台上的 `NoEcho`。 (#3801)
- 已修复 `Get-Help` 以支持 Unix 平台上的区分大小写模式匹配。 (#3852)
- 已向包添加 `powershell` 说明手册。

### <a name="logging"></a>日志记录

在 macOS 上，PowerShell 使用本机 `os_log` API 登录到 Apple [统一登录系统][os_log]。
在 Linux 上，PowerShell 使用 [Syslog][] 这种通用登录解决方案。

### <a name="filesystem"></a>Filesystem

已在 macOS 和 Linux 上作出众多更改，从而支持传统上不受 Windows 支持的文件名字符：

- cmdlet 的路径现已为斜杠不可知类型（/ 和 \ 皆用作目录分隔符）
- 现已符合和默认使用 XDG 基目录规范：
  - Linux/macOS 配置文件路径位于 `~/.config/powershell/profile.ps1`
  - 历史记录保存路径位于 `~/.local/share/powershell/PSReadline/ConsoleHost_history.txt`
  - 用户模块路径位于 `~/.local/share/powershell/Modules`
- 支持 Unix 上包含冒号的文件名称和文件夹名称。 (#4959)
- 支持具有逗号的脚本名称或完整路径。 (#4136)（感谢 [@TimCurwick](https://github.com/TimCurwick)！）
- 检测何时使用 `-LiteralPath` 阻止导航 cmdlet 的通配符扩展。 (#5038)
- 已更新 `Get-ChildItem`，使之更类似于 *nix `ls -R` 和 Windows `DIR /S` 本机命令。
  `Get-ChildItem` 现在返回递归搜索期间遇到的符号链接，并且不会搜索这些链接指向的目录。 (#3780)

### <a name="case-sensitivity"></a>区分大小写

保留大小写时，Linux 和 macOS 通常区分大小写，而 Windows 不区分大小写。
PowerShell 通常不区分大小写。

例如，环境变量在 macOS 和 Linux 上区分大小写，所以 `PSModulePath` 环境变量的大小写已被标准化。 (#3255) `Import-Module` 在使用文件路径确定模块名称时不区分大小写。 (#5097)

## <a name="support-for-side-by-side-installations"></a>支持并行安装

单独从 Windows PowerShell 安装、配置和执行 PowerShell Core。
PowerShell Core 具有一个“可移植”ZIP 包。
使用 ZIP 包可在磁盘任意位置安装任意版本，包括将 PowerShell 作为依赖项的应用程序的本地位置。
并行安装使测试 PowerShell 新版本和随时间推移而迁移现有脚本变得更简单。
并行安装还支持向后兼容性，因为脚本可以固定到其所需的特定版本。

> [!NOTE]
> 默认情况下，Windows 上基于 MSI 的安装程序执行就地更新安装。
>

## <a name="renamed-powershellexe-to-pwshexe"></a>已将 `powershell(.exe)` 重命名为 `pwsh(.exe)`

PowerShell Core 的二进制名称已从 `powershell(.exe)` 更改为 `pwsh(.exe)`。
此更改为用户提供一个决定性方法，从而可在计算机上运行 PowerShell Core 以支持并行 Windows PowerShell 和 PowerShell Core 安装。
`pwsh` 字符长度更短，且更容易输入。

将 `powershell.exe` 重命名为 `pwsh(.exe)` 后的其他更改：

- 已将第一个位置参数从 `-Command` 更改为 `-File`。
  此更改修复了 `#!`（亦称为 shebang）在非 Windows 平台上非 PowerShell shell 内执行的 PowerShell 脚本 中的使用问题。
  这还意味着无需指定 `-File` 即可运行 `pwsh foo.ps1` 或 `pwsh fooScript` 等命令。
  但是，尝试运行 `pwsh.exe -Command Get-Command` 等命令时，此更改会要求显示指定 `-c` 或 `-Command`。 (#4019)
- PowerShell Core 接受 `-i`（或 `-Interactive`）切换表示交互式 shell。 (#3558) 这使 PowerShell 可用作 Unix 平台上的默认 shell。
- 已将参数 `-importsystemmodules` 和 `-psconsoleFile` 从 `pwsh.exe` 中删除。 (#4995)
- 已更改 `pwsh -version` 和 `pwsh.exe` 内置帮助，以与其他本机工具保持统一。 (#4958 & #4931)（感谢 [@iSazonov](https://github.com/iSazonov)）
- `-File` 和 `-Command` 的无效参数错误消息以及退出代码与 Unix 标准一致 (#4573)
- 已在 Windows 上添加 `-WindowStyle` 参数。 (#4573) 同样，非 Windows 平台上基于包的安装更新现为就地更新。

## <a name="backwards-compatibility-with-windows-powershell"></a>Windows PowerShell 向后兼容

PowerShell Core 的目标是尽可能兼容 Windows PowerShell。
PowerShell Core 使用 [.NET Standard][] 2.0 提供与现有 .NET 程序集的二进制兼容性。
许多 PowerShell 模块依赖这些程序集（通常为 DLL），而 .NET Standard 可使这些模块继续适用于 .NET Core。
PowerShell Core 还包含一个启发式方法，通过该方法可在常用文件夹（例如全局程序集缓存通常所位于的磁盘位置）中查找 .NET Framework DLL 依赖项。

如需详细了解 .NET Standard，请参阅 [.NET 博客][]、本 [YouTube][] 视频以及 GitHub 上的本篇[常见问题][]。

我们希望确保 PowerShell 语言和“内置”模块（例如 `Microsoft.PowerShell.Management`、`Microsoft.PowerShell.Utility` 等）与它们在 Windows PowerShell 中具有相同的作用，为此，我们已付出诸多努力。
在许多情况下，通过社区的帮助，我们已添加了一些新功能和针对 cmdlet 的 bug 修补程序。
在某些情况下，由于基础 .NET 层中缺失依赖项，因此功能已被删除或者不可用。

大多随附 Windows 的模块（例如 `DnsClient`、`Hyper-V``NetTCPIP`、`Storage` 等）以及其他一些 Microsoft 产品（包括 Azure 和 Office）尚未显式移植到 .NET Core。
PowerShell 团队正与这些产品组以及团队开展协作，以验证并将现有模块迁移到 PowerShell Core。
通过使用 .NET Standard 和 [CDXML][]，其中许多传统 Windows PowerShell 模块看似确实可在 PowerShell Core 中运行，但是它们尚未经过正式验证，且不受正式支持。

通过安装 [`WindowsPSModulePath`][windowspsmodulepath] 模块，可将 Windows PowerShell `PSModulePath` 附加到 PowerShell Core `PSModulePath`，从而可使用 Windows PowerShell 模块。

首先，从 PowerShell 库安装 `WindowsPSModulePath` 模块：

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

安装此模块后，运行 `Add-WindowsPSModulePath` cmdlet 以将 Windows PowerShell `PSModulePath` 添加到 PowerShell Core：

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="docker-support"></a>Docker 支持

PowerShell Core 已对我们支持的所有主要平台（包括多个 Linux 发行版、Windows Server Core 和 Nano Server）添加了 Docker 容器支持。

关于完整列表，请查看 [`microsoft/powershell` Docker Hub][docker-hub] 上对的标记。
有关 Docker 和 PowerShell Core 的详细信息，请参阅 GitHub 上的 [Docker][]。

## <a name="ssh-based-powershell-remoting"></a>基于 SSH 的 PowerShell 远程处理

除基于 WinRM 的传统 PSRP 外，PowerShell 远程处理协议 (PSRP) 现在还使用安全外壳 (SSH) 协议。

这意味着你可以使用 `Enter-PSSession` 和 `New-PSSession` 等 cmdlet，并可使用 SSH 进行身份验证。
仅需使用基于 OpenSSH 的 SSH 服务器将 PowerShell 注册为子系统即可，并且可以通过传统 `PSSession` 语义使用基于 SSH 的身份验证机制（例如密码或私钥）。

如需详细了解如何配置和使用基于 SSH 的远程处理，请参阅[通过 SSH 进行 PowerShell 远程处理][ssh-remoting]。

## <a name="default-encoding-is-utf-8-without-a-bom-except-for-new-modulemanifest"></a>默认编码为 UTF-8（不使用 BOM），但 New-ModuleManifest 除外

以前，`Get-Content`、`Set-Content` 等 Windows PowerShell cmdlet 使用不同的编码，例如 ASCII 和 UTF-16。
混合使用未指定编码的 cmdlet 时，编码默认的变动会导致问题。

非 Windows 平台通常使用不具有字节顺序标记 (BOM) 的 UTF-8 作为文本文件的默认编码。
目前越来越多的 Windows 应用程序和工具避免使用 UTF-16，而是趋向于采用无 BOM 式 的 UTF-8 编码。
PowerShell Core 更改默认编码以符合更广泛的生态系统。

这意味着所有使用 `-Encoding` 参数的内置 cmdlet 均默认使用 `UTF8NoBOM` 值。
以下 cmdlet 受此更改影响：

- Add-Content
- Export-Clixml
- Export-Csv
- Export-PSSession
- Format-Hex
- Get-Content
- Import-Csv
- Out-File
- Select-String
- Send-MailMessage
- Set-Content

以上 cmdlet 也已经过更新，因此 `-Encoding` 参数会普遍接受 `System.Text.Encoding`。

`$OutputEncoding` 的默认值也已更改为 UTF-8。

作为最佳做法，应该使用 `-Encoding` 参数在脚本中显示设置编码以生成确定的跨平台行为。

`New-ModuleManifest` cmdlet 没有 Encoding 参数。 如果模块清单 (.psd1) 文件是使用 `New-ModuleManifest` cmdlet 创建而成，清单编码视环境而定：如果是在 Linux 上运行的 PowerShell Core，编码为 UTF-8（不使用 BOM）；否则，编码为 UTF-16（使用 BOM）。 (#3940)

## <a name="support-backgrounding-of-pipelines-with-ampersand--3360"></a>有 `&` 的管道的支持背景 (#3360)

将 `&` 置于管道末尾会导致管道作为 PowerShell 作业运行。
管道在后台运行时会返回作业对象。
管道作为作业运行后，所有标准 `*-Job` cmdlet 均可以用来管理该作业。
此管道中使用的变量（特定于进程的变量除外）自动复制到该作业，从而使 `Copy-Item $foo $bar &` 正常运行。
该作业还会在当前目录而不是用户主目录中运行。
有关 PowerShell 作业的详细信息，请参阅 [about_Jobs](https://msdn.microsoft.com/powershell/reference/6/about/about_jobs)。

## <a name="semantic-versioning"></a>语义化版本控制

- 已使 `SemanticVersion` 与 `SemVer 2.0` 兼容。 (#5037)（感谢 [@iSazonov](https://github.com/iSazonov)）
- 为与 SemVer 符合，已将 `New-ModuleManifest` 中的默认 `ModuleVersion` 更改为 `0.0.1`。 (#4842)（感谢 [@LDSpits](https://github.com/LDSpits)）
- 已添加 `semver` 作为 `System.Management.Automation.SemanticVersion` 的类型加速器。 (#4142)（感谢 [@oising](https://github.com/oising)！）
- 已支持比较 `SemanticVersion` 实例和仅使用 `Major` 和 `Minor` 版本值构建的 `Version` 实例。

## <a name="language-updates"></a>语言更新

- 实现 Unicode 转义分析，由此用户可使用 Unicode 字符作为参数、字符串或变量名称。 (#3958)（感谢 [@rkeithhill](https://github.com/rkeithhill)！）
- 已为 ESC 添加新的转义字符：`` `e``
- 已添加将枚举转换为字符串的支持 (#4318)（感谢 [@KirkMunro](https://github.com/KirkMunro)！）
- 已修复将单个元素数组转换为泛型集合的问题。 (#3170)
- 已向 `..` 运算符添加字符范围重载，因此 `'a'..'z'` 会从“A”到“Z”返回字符。 (#5026)（感谢 [@IISResetMe](https://github.com/IISResetMe)）
- 已修复变量赋值，从而避免覆盖只读变量
- 对脚本 cmdlet 加点时会将自动变量的局部变量推送到“DottedScopes”(#4709)
- 支持在拆分运算符中使用“Singleline, Multiline”选项 (#4721)（感谢 [@iSazonov](https://github.com/iSazonov)）

## <a name="engine-updates"></a>引擎更新

- `$PSVersionTable` 具有四个新属性：
  - `PSEdition`：该属性在 PowerShell Core 上设为 `Core`，在 Windows PowerShell 上设为 `Desktop`
  - `GitCommitId`：这是 Git 分支的 Git 提交 ID 或在其中生成 PowerShell 的标记。
    在已发布版本中，它可能与 `PSVersion` 相同。
  - `OS`：这是 `[System.Runtime.InteropServices.RuntimeInformation]::OSDescription` 返回的 OS 版本字符串
  - `Platform`：该属性由 `[System.Environment]::OSVersion.Platform` 返回。它在 Windows 上设置为 `Win32NT`，在 macOS 上为 `Unix`，在 Linux 上为 `Unix`。
- 已从 `$PSVersionTable` 删除 `BuildVersion` 属性。
  此属性与 Windows 内部版本密切相关。
  我们建议使用 `GitCommitId` 检索 PowerShell Core 的确切内部版本。 (#3877)（感谢 [@iSazonov](https://github.com/iSazonov)！）
- 已从 `$PSVersionTable` 删除 `ClrVersion` 属性。
  此属性与 .NET Core 不相关，.NET Core 中此前保留该属性仅是针对一些不适用于 PowerShell 的特定旧用途。
- 已添加三个新自动变量，用以确定特定 OS 中是否正在运行 PowerShell：`$IsWindows`、`$IsMacOs` 和 `$IsLinux`。
- 已将 `GitCommitId` 添加到 PowerShell Core 横幅。
  现在启动 PowerShell 时无需运行 `$PSVersionTable` 即可获取版本！ (#3916)（感谢 [@iSazonov](https://github.com/iSazonov)！）
- 已在 `$PSHome` 中添加名为 `powershell.config.json` 的 JSON 配置文件，用以存储某些启动之前所需的设置（例如 `ExecutionPolicy`）。
- 运行 Windows EXE 时请勿阻止管道
- 已支持 COM 集合的枚举。 (#4553)

## <a name="cmdlet-updates"></a>Cmdlet 更新

### <a name="new-cmdlets"></a>新 cmdlet

- 已将 `Get-Uptime` 添加到 `Microsoft.PowerShell.Utility`。
- 添加 `Remove-Alias` 命令。 (#5143)（感谢 [@PowershellNinja](https://github.com/PowershellNinja)）
- 已将 `Remove-Service` 添加到管理模块。 (#4858)（感谢 [@joandrsn](https://github.com/joandrsn)）

### <a name="web-cmdlets"></a>Web cmdlet

- 已添加对 web cmdlet 的证书身份验证支持。 (#4646)（感谢 [@markekraus](https://github.com/markekraus)）
- 已将内容标头支持添加至 web cmdlet。 (#4494 & #4640)（感谢 [@markekraus](https://github.com/markekraus)）
- 已将多链接标头支持添加到 Web Cmdlet。 (#5265)（感谢 [@markekraus](https://github.com/markekraus)！）
- 支持 web cmdlet 中的链接标头分页 (#3828)
  - 对于 `Invoke-WebRequest`，当响应包括链接标头时，我们创建一个 RelationLink 属性作为表示 URL 和 `rel` 属性的字典，并确保 URL 是绝对的，从而使其更易于开发人员使用。
  - 对于 `Invoke-RestMethod`，当响应包括链接标头时，我们公开 `-FollowRelLink` 切换以自动跟踪 `next` `rel` 链接，直至其不再存在或者选中可选的 `-MaximumFollowRelLink` 参数值。
- 已向 web cmdlet 添加 `-CustomMethod` 参数，从而支持非标准方法谓词。 (#3142)（感谢 [@Lee303](https://github.com/Lee303)！）
- 已向 Web Cmdlet 添加 `SslProtocol` 支持。 (#5329)（感谢 [@markekraus](https://github.com/markekraus)！）
- 已向 web cmdlet 添加 Multipart 支持。 (#4782)（感谢 [@markekraus](https://github.com/markekraus)）
- 已向 web cmdlet 添加 `-NoProxy`，从而使其忽略系统范围的代理设置。 (#3447)（感谢 [@TheFlyingCorpse](https://github.com/TheFlyingCorpse)！）
- Web Cmdlet 的用户代理现在会报告 OS 平台 (#4937)（感谢 [@LDSpits](https://github.com/LDSpits)）
- 已将 `-SkipHeaderValidation` 切换添加至 web cmdlet，无需验证标头值即可添加标头。 (#4085)
- 现支持 web cmdlet 不必验证服务器的 HTTPS 证书（如果需要）。
- 已将身份验证参数添加到 web cmdlet。 (#5052)（感谢 [@markekraus](https://github.com/markekraus)）
  - 添加`-Authentication`提供三个选项：基本、 OAuth 和 Bearer。
  - 已添加 `-Token`，以便获取 OAuth 和 Bearer 选项的持有者令牌。
  - 已添加 `-AllowUnencryptedAuthentication`，以便绕过对除 HTTPS 以外的任何传输方案所提供的身份验证。
- 已将 `-ResponseHeadersVariable` 添加至 `Invoke-RestMethod`以便支持捕获响应标头。 (#4888)（感谢 [@markekraus](https://github.com/markekraus)）
- 修复 web cmdlet，以在响应状态代码不成功时将 HTTP 响应包含在异常中。 (#3201)
- 已将 web cmdlet `UserAgent` 从 `WindowsPowerShell` 更改为 `PowerShell`。 (#4914)（感谢 [@markekraus](https://github.com/markekraus)）
- 已将显式 `ContentType` 检测添加到 `Invoke-RestMethod` (#4692)
- 已修复 web cmdlet `-SkipHeaderValidation`，以便可适用于非标准用户代理标头。 (#4479 & #4512)（感谢 [@markekraus](https://github.com/markekraus)）

### <a name="json-cmdlets"></a>JSON cmdlet

- 已将 `-AsHashtable` 添加到 `ConvertFrom-Json` 以返回 `Hashtable`。 (#5043)（感谢 [@bergmeister](https://github.com/bergmeister)！）
- 使用具有 `ConvertTo-Json` 输出的更美观的格式化程序。 (#2787)（感谢 @kittholland！）
- 已将 `Jobject` 序列化支持添加到 `ConvertTo-Json`。 (#5141)
- 已修复 `ConvertFrom-Json`，以便从管道对共同构建完整 JSON 字符串的字符数组进行反序列化。
  这修复了某些情况下换行符中断 JSON 分析的问题。 (#3823)
- 已删除为 `System.Array` 定义的 `AliasProperty "Count"`。
  这删除了某些 `ConvertFrom-Json` 输出上的外部 `Count` 属性。 (#3231)（感谢 [@PetSerAl](https://github.com/PetSerAl)！）

### <a name="csv-cmdlets"></a>CSV cmdlet

- 添加了对 `Import-Csv` 和 `ConvertFrom-Csv` 的 `PSTypeName` 支持。 (#5389)（感谢 [@markekraus](https://github.com/markekraus)！）
- `Import-Csv` 现已支持将 `CR`、`LF` 和 `CRLF` 作为行分隔符。 (#5363)（感谢 [@iSazonov](https://github.com/iSazonov)！）
- `-NoTypeInformation` 现在作为 `Export-Csv` 和 `ConvertTo-Csv` 上的默认值。 (#5164)（感谢 [@markekraus](https://github.com/markekraus)）

### <a name="service-cmdlets"></a>服务 cmdlet

- 将属性 `UserName`、`Description`、`DelayedAutoStart`、`BinaryPathName` 和 `StartupType` 添加到 `Get-Service` 返回的 `ServiceController` 对象。 (#4907)（感谢 [@joandrsn](https://github.com/joandrsn)）
- 添加了在 `Set-Service` 命令上设置属性的功能。 (#4844)（感谢 [@joandrsn](https://github.com/joandrsn)）

### <a name="other-cmdlets"></a>其他 cmdlet

- 已将参数添加到 `Get-ChildItem` 所调用的 `-FollowSymlink` 中，它按需遍历 symlink，并检查链接循环。 (#4020)
- 更新 `Add-Type` 以支持 `CSharpVersion7`。 (#3933)（感谢 [@iSazonov](https://github.com/iSazonov)）
- 删除由于使用不受支持的 API 而产生的 `Microsoft.PowerShell.LocalAccounts` 模块，直至找到更佳解决方案。 (#4302)
- 删除由于使用不受支持的 API 而在 `Microsoft.PowerShell.Diagnostics` 中产生的 `*-Counter`，直至找到更佳解决方案。 (#4303)
- 添加对 `Invoke-Item -Path <folder>` 的支持。 (#4262)
- 将 `-Extension` 和 `-LeafBase` 切换添加到 `Split-Path`，从而可拆分文件名扩展名和文件名其余部分之间的路径。 (#2721)（感谢 [@powercode](https://github.com/powercode)！）
- 已将参数 `-Top` 和 `-Bottom` 添加到顶部/底部 N 排序的 `Sort-Object`
- 通过将 `CodeProperty "Parent"` 添加到 `System.Diagnostics.Process` 公开进程的父进程。 (#2850)（感谢 [@powercode](https://github.com/powercode)！）
- 对于 `Get-Process` 的内存列使用 MB 而不是 KB
- 为 `Out-String` 添加了 `-NoNewLine` 切换。 (#5056)（感谢 [@raghav710](https://github.com/raghav710)）
- `Move-Item` cmdlet 遵循 `-Include`、`-Exclude` 和 `-Filter` 参数。 (#3878)
- 允许将 `*` 用于 `Remove-Item` 的注册表路径中。 (#4866)
- 已将 `-Title` 添加到 `Get-Credential`，并统一化跨平台之间的提示体验。
- 已将 `-TimeOut` 参数添加到 `Test-Connection`。 (#2492)
- `Get-AuthenticodeSignature` cmdlet 现可获取文件签名时间戳。 (#4061)
- 已从 `Get-Help` 中删除不受支持的 `-ShowWindow` 切换。 (#4903)
- 修复了 `Get-Content -Delimiter`，使得所返回的数组元素中不包含分隔符 (#3706)（感谢 [@mklement0](https://github.com/mklement0)）
- 将 `Meta`、`Charset` 和 `Transitional` 参数添加到 `ConvertTo-HTML` (#4184)（感谢 [@ergo3114](https://github.com/ergo3114)）
- 将 `WindowsUBR` 和 `WindowsVersion` 属性添加到 `Get-ComputerInfo` 结果
- 将 `-Group` 参数添加到 `Get-Verb`
- 将 `ShouldProcess` 支持添加到 `New-FileCatalog` 和 `Test-FileCatalog`（修复了 `-WhatIf` 和 `-Confirm`）。 (#3074)（感谢 [@iSazonov](https://github.com/iSazonov)！）
- 将 `-WhatIf` 切换添加到 `Start-Process` cmdlet (#4735)（感谢 [@sarithsutha](https://github.com/sarithsutha)）
- 将 `ValidateNotNullOrEmpty` 添加到多个现有参数。

## <a name="tab-completion"></a>Tab 自动补全

- 改进了基于运行时变量值的 tab 自动补全中的类型推理。 (#2744)（感谢 [@powercode](https://github.com/powercode)！）这支持在类似如下的情况中进行 tab 自动补全：

  ```powershell
  $p = Get-Process
  $p | Foreach-Object Prio<tab>
  ```

- 为 `Select-Object` 的 `-Property` 添加了 Hashtable tab 自动补全。 (#3625)（感谢 [@powercode](https://github.com/powercode)）
- 对 `-ExcludeProperty` 和 `Select-Object` 的 `-ExpandProperty` 支持参数自动补全。 (#3443)（感谢 [@iSazonov](https://github.com/iSazonov)！）
- 修复了 tab 自动补全中的 bug，以使 `native.exe --<tab>` 调用到本机完成程序。 (#3633)（感谢 [@powercode](https://github.com/powercode)！）

## <a name="breaking-changes"></a>重大更改

我们在 PowerShell Core 6.0 中引入大量重大更改。
若要了解其详细信息，请参阅 [PowerShell Core 6.0 中的重大更改][breaking-changes]。

## <a name="debugging"></a>调试

- 支持 `Invoke-Command -ComputerName` 的远程步进调试。 (#3015)
- 在 PowerShell Core 中启用绑定器调试登录

## <a name="filesystem-updates"></a>Filesystem 更新

- 支持从 UNC 路径使用 Filesystem 提供程序。 ($4998)
- `Split-Path` 现在适用于 UNC 根
- 没有参数的 `cd` 现在表现为 `cd ~`
- 修复了 PowerShell Core，以允许使用长度超过 260 字符的路径。 (#3960)

## <a name="bug-fixes-and-performance-improvements"></a>Bug 修复和性能改进

我们已对 PowerShell 多方面作出众多性能改进，涉及方面包含启动时间、各种内置 cmdlet以及与本机二进制文件的交互。

我们还修复 PowerShell Core 中的众多 bug。
有关修复和更改的完整列表，请查看 GitHub 上的 [changelog][]。

## <a name="telemetry"></a>遥测

- PowerShell Core 6.0 将遥测添加到控制台主机以报告两个值 (#3620)：
  - OS 平台 (`$PSVersionTable.OSDescription`)
  - PowerShell 确切版本 (`$PSVersionTable.GitCommitId`)

如果想选择退出此遥测，只需使用以下值之一创建 `POWERSHELL_TELEMETRY_OPTOUT` 环境变量：`true`、`1` 或 `yes`。
创建该变量会绕过所有遥测，即便在首次运行 PowerShell 之前也不例外。
我们还计划将此遥测数据和从遥测中收集的见解公开在[社区仪表盘][community-dashboard]中。
如需详细了解我们如何使用此数据，请阅读本[博客文章][telemetry-blog]。

[github]: https://github.com/PowerShell/PowerShell
[.NET Core 2.0]: https://docs.microsoft.com/dotnet/core/
[.NET Standard]: https://docs.microsoft.com/dotnet/standard/net-standard
[os_log]: https://developer.apple.com/documentation/os/logging
[Syslog]: https://en.wikipedia.org/wiki/Syslog
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[breaking-changes]: breaking-changes-ps6.md
[changelog]: https://github.com/PowerShell/PowerShell/tree/master/CHANGELOG.md
[community-dashboard]: https://aka.ms/PSGitHubBI
[telemetry-blog]: https://blogs.msdn.microsoft.com/powershell/2017/01/31/powershell-open-source-community-dashboard/
[.NET Standard]: https://docs.microsoft.com/dotnet/standard/net-standard
[.NET 博客]: https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard
[YouTube]: https://www.youtube.com/watch?v=YI4MurjfMn8&list=PLRAdsfhKI4OWx321A_pr-7HhRNk7wOLLY
[常见问题]: https://github.com/dotnet/standard/blob/master/docs/faq.md
[CDXML]: https://msdn.microsoft.com/library/jj542525(v=vs.85).aspx
[docker-hub]: https://hub.docker.com/r/microsoft/powershell/
[docker]: https://github.com/PowerShell/PowerShell/tree/master/docker
[windowspsmodulepath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
