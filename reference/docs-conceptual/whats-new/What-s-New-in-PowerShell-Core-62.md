---
title: PowerShell Core 6.2 中的新增功能
description: PowerShell Core 6.2 中发布的新功能和更改
ms.date: 03/28/2019
ms.openlocfilehash: 2f5f5d11ba46d53966093c5e3ed6d0c7d47308d0
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737128"
---
# <a name="whats-new-in-powershell-core-62"></a><span data-ttu-id="8e831-103">PowerShell Core 6.2 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="8e831-103">What's New in PowerShell Core 6.2</span></span>

<span data-ttu-id="8e831-104">PowerShell Core 6.2 版本侧重于性能改进、bug 修复以及可提高质量的较小 cmdlet 和语言增强功能。</span><span class="sxs-lookup"><span data-stu-id="8e831-104">The PowerShell Core 6.2 release focused on performance improvements, bug fixes, and smaller cmdlet and language enhancements that improve the quality.</span></span> <span data-ttu-id="8e831-105">若要查看改进的完整列表，请在 GitHub 上查看我们详细的[更改日志](https://github.com/PowerShell/PowerShell/releases)。</span><span class="sxs-lookup"><span data-stu-id="8e831-105">To see a full list of improvements, check out our detailed [changelogs](https://github.com/PowerShell/PowerShell/releases) on GitHub.</span></span>

## <a name="experimental-features"></a><span data-ttu-id="8e831-106">实验性功能</span><span class="sxs-lookup"><span data-stu-id="8e831-106">Experimental Features</span></span>

<span data-ttu-id="8e831-107">在此之前，我们启用了对[实验性功能][]的支持。</span><span class="sxs-lookup"><span data-stu-id="8e831-107">Previously, we enabled support for [Experimental Features][].</span></span> <span data-ttu-id="8e831-108">6\.2 版本中提供了四个要试用的实验性功能。请提供反馈，以便我们进行改进，并决定该功能是否值得提升到主流状态。</span><span class="sxs-lookup"><span data-stu-id="8e831-108">In the 6.2 release, we have four experimental features to try out. Please provide feedback so we can make improvements and to decide whether the feature is worth promoting to mainstream status.</span></span>

<span data-ttu-id="8e831-109">使用 `Get-ExperimentalFeature` 获取可用的实验性功能列表。</span><span class="sxs-lookup"><span data-stu-id="8e831-109">Use `Get-ExperimentalFeature` to get a list of available experimental features.</span></span> <span data-ttu-id="8e831-110">可以使用 `Enable-ExperimentalFeature` 和 `Disable-ExperimentalFeature` 启用或禁用这些功能。</span><span class="sxs-lookup"><span data-stu-id="8e831-110">You can enable or disable these features with `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature`.</span></span>

### <a name="command-not-found-suggestions"></a><span data-ttu-id="8e831-111">命令未找到建议</span><span class="sxs-lookup"><span data-stu-id="8e831-111">Command Not Found Suggestions</span></span>

<span data-ttu-id="8e831-112">此功能使用模糊匹配来查找可能键入错误的命令或 cmdlet 的建议。</span><span class="sxs-lookup"><span data-stu-id="8e831-112">This feature uses fuzzy matching to find suggestions for commands or cmdlets you may have mistyped.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSCommandNotFoundSuggestion
```

#### <a name="example"></a><span data-ttu-id="8e831-113">示例</span><span class="sxs-lookup"><span data-stu-id="8e831-113">Example</span></span>

<span data-ttu-id="8e831-114">在本例中，拼写错误的 cmdlet 名称与多个建议模糊匹配（从最可能到最不可能）。</span><span class="sxs-lookup"><span data-stu-id="8e831-114">In this example, the misspelled cmdlet name is fuzzy matched to several suggestions from most likely to least likely.</span></span>

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

### <a name="implicit-remoting-batching"></a><span data-ttu-id="8e831-115">隐式远程处理批处理</span><span class="sxs-lookup"><span data-stu-id="8e831-115">Implicit Remoting Batching</span></span>

<span data-ttu-id="8e831-116">在管道中使用[隐式远程处理](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/)时，PowerShell 将独立处理管道中的每个命令。</span><span class="sxs-lookup"><span data-stu-id="8e831-116">When using [implicit remoting](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) in a pipeline, PowerShell treats each command in the pipeline independently.</span></span> <span data-ttu-id="8e831-117">在管道执行过程中，对象在客户端和远程系统之间重复序列化和 `de-serialized`。</span><span class="sxs-lookup"><span data-stu-id="8e831-117">Objects are repeatedly serialized and `de-serialized` between the client and remote system over the execution of the pipeline.</span></span>

<span data-ttu-id="8e831-118">PowerShell 使用该功能分析管道，以确定该命令是否可以安全运行，以及它是否存在于目标系统中。</span><span class="sxs-lookup"><span data-stu-id="8e831-118">With this feature, PowerShell analyzes the pipeline to determine if the command is safe to run and it exists on the target system.</span></span> <span data-ttu-id="8e831-119">如果为 true，PowerShell 将远程执行整个管道，并且只将结果序列化和 `de-serializes` 返回给客户端。</span><span class="sxs-lookup"><span data-stu-id="8e831-119">When true, PowerShell executes the entire pipeline remotely and only serializes and `de-serializes` the results back to the client.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSImplicitRemotingBatching
```

<span data-ttu-id="8e831-120">在 localhost 上实际测试 `Get-Process | Sort-Object` 的时间从 10-15 秒减少到 20-30 毫秒  。</span><span class="sxs-lookup"><span data-stu-id="8e831-120">A real-world test of `Get-Process | Sort-Object` over localhost decreases from 10-15 seconds to 20-30 **milliseconds**.</span></span> <span data-ttu-id="8e831-121">该功能只需在客户端上启用。</span><span class="sxs-lookup"><span data-stu-id="8e831-121">The feature only needs to be enabled on the client.</span></span> <span data-ttu-id="8e831-122">不需要在服务器上进行任何更改。</span><span class="sxs-lookup"><span data-stu-id="8e831-122">No changes are required on the server.</span></span>

### <a name="temp-drive"></a><span data-ttu-id="8e831-123">临时驱动器</span><span class="sxs-lookup"><span data-stu-id="8e831-123">Temp Drive</span></span>

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

<span data-ttu-id="8e831-124">如果在不同操作系统上使用 PowerShell Core，会发现在 Windows、macOS 和 Linux 上用于查找临时目录的环境变量是不同的！</span><span class="sxs-lookup"><span data-stu-id="8e831-124">If you're using PowerShell Core on different operating systems, you'll discover that the environment variable for finding the temporary directory is different on Windows, macOS, and Linux!</span></span> <span data-ttu-id="8e831-125">借助此功能，可获得一个名为 `Temp:` 的 [PSDrive][]，它将自动映射到你正在使用的操作系统的临时文件夹。</span><span class="sxs-lookup"><span data-stu-id="8e831-125">With this feature, you get a [PSDrive][] called `Temp:` that is automatically mapped to the temporary folder for the operating system you are using.</span></span>

#### <a name="example"></a><span data-ttu-id="8e831-126">示例</span><span class="sxs-lookup"><span data-stu-id="8e831-126">Example</span></span>

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> Get-Content Temp:/hello.txt
Hello World!
```

<span data-ttu-id="8e831-127">注意，本机文件命令（如 Linux 上的 `ls`）不能识别 PSDrive，因此看不到此 `Temp:` 驱动器。</span><span class="sxs-lookup"><span data-stu-id="8e831-127">Be aware that native file commands (like `ls` on Linux) are not aware of PSDrives and won't see this `Temp:` drive.</span></span>

### <a name="abbreviation-expansion"></a><span data-ttu-id="8e831-128">缩写扩展</span><span class="sxs-lookup"><span data-stu-id="8e831-128">Abbreviation Expansion</span></span>

<span data-ttu-id="8e831-129">PowerShell cmdlet 应具有描述性名词。</span><span class="sxs-lookup"><span data-stu-id="8e831-129">PowerShell cmdlets are expected to have descriptive nouns.</span></span> <span data-ttu-id="8e831-130">这将导致更难键入的长名称。</span><span class="sxs-lookup"><span data-stu-id="8e831-130">This results in long names that are more difficult to type.</span></span> <span data-ttu-id="8e831-131">该功能允许只键入 cmdlet 的大写字符，并使用 Tab 自动补全查找匹配项。</span><span class="sxs-lookup"><span data-stu-id="8e831-131">This feature allows you to just type the uppercase characters of the cmdlet and use tab-completion to find a match.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSUseAbbreviationExpansion
```

#### <a name="example"></a><span data-ttu-id="8e831-132">示例</span><span class="sxs-lookup"><span data-stu-id="8e831-132">Example</span></span>

```powershell
PS> i-arsavsf
```

<span data-ttu-id="8e831-133">如果按 Tab 键，并安装了 Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) 模块，它将自动完成为：</span><span class="sxs-lookup"><span data-stu-id="8e831-133">If you hit tab, and have the Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) module installed, it will autocomplete to:</span></span>

```Output
PS> Import-AzRecoveryServicesAsrVaultSettingsFile
```

> [!NOTE]
> <span data-ttu-id="8e831-134">此功能旨在以交互方式使用。</span><span class="sxs-lookup"><span data-stu-id="8e831-134">This feature is intended to be used interactively.</span></span> <span data-ttu-id="8e831-135">不能执行 cmdlet 的缩写形式。</span><span class="sxs-lookup"><span data-stu-id="8e831-135">Abbreviated forms of cmdlets can't be executed.</span></span>
> <span data-ttu-id="8e831-136">此功能不能替代别名。</span><span class="sxs-lookup"><span data-stu-id="8e831-136">This feature is not a replacement for aliases.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="8e831-137">重大更改</span><span class="sxs-lookup"><span data-stu-id="8e831-137">Breaking Changes</span></span>

- <span data-ttu-id="8e831-138">修复 `Write-Output` 中的 `-NoEnumerate` 行为，使之与 Windows PowerShell 一致。</span><span class="sxs-lookup"><span data-stu-id="8e831-138">Fix `-NoEnumerate` behavior in `Write-Output` to be consistent with Windows PowerShell.</span></span> <span data-ttu-id="8e831-139">(#9069)</span><span class="sxs-lookup"><span data-stu-id="8e831-139">(#9069)</span></span>
- <span data-ttu-id="8e831-140">使 `Join-String -InputObject 1,2,3` 结果等于 `1,2,3 | Join-String` 结果 (#8611)（感谢 @sethvs！）</span><span class="sxs-lookup"><span data-stu-id="8e831-140">Make `Join-String -InputObject 1,2,3` result equal to `1,2,3 | Join-String` result (#8611) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="8e831-141">将 `-Stable` 添加到 `Sort-Object` 和相关测试 (#7862)（感谢 @KirkMunro！）</span><span class="sxs-lookup"><span data-stu-id="8e831-141">Add `-Stable` to `Sort-Object` and related tests (#7862) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="8e831-142">改进 `Start-Sleep` cmdlet 以接受秒的小数部分 (#8537)（感谢 @Prototyyppi！）</span><span class="sxs-lookup"><span data-stu-id="8e831-142">Improve `Start-Sleep` cmdlet to accept fractional seconds (#8537) (Thanks @Prototyyppi!)</span></span>
- <span data-ttu-id="8e831-143">将 Hashtable 更改为在所有区域性中使用 OrdinalIgnoreCase 作为 `case-insensitive` (#8566)</span><span class="sxs-lookup"><span data-stu-id="8e831-143">Change hashtable to use OrdinalIgnoreCase to be `case-insensitive` in all Cultures (#8566)</span></span>
- <span data-ttu-id="8e831-144">修复 `Import-Csv` 中的 LiteralPath  以绑定到 `Get-ChildItem` 输出 (#8277)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="8e831-144">Fix **LiteralPath** in `Import-Csv` to bind to `Get-ChildItem` output (#8277) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="8e831-145">如果在 `Import-Csv` 中使用双引号分隔符，则不再跳过没有名称的列 (#7899)（感谢 @Topping！）</span><span class="sxs-lookup"><span data-stu-id="8e831-145">No longer skips a column without name if double quote delimiter is used in `Import-Csv` (#7899) (Thanks @Topping!)</span></span>
- <span data-ttu-id="8e831-146">`Get-ExperimentalFeature` 不再具有 `-ListAvailable` 开关 (#8318)</span><span class="sxs-lookup"><span data-stu-id="8e831-146">`Get-ExperimentalFeature` no longer has `-ListAvailable` switch (#8318)</span></span>
- <span data-ttu-id="8e831-147">调试参数现将 `$DebugPreference` 设置为“继续”  而不是“查询”  (#8195)（感谢 @KirkMunro！）</span><span class="sxs-lookup"><span data-stu-id="8e831-147">Debug parameter now sets `$DebugPreference` to **Continue** instead of **Inquire** (#8195) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="8e831-148">如果在与 pwsh 一起使用的非交互式、重定向、编码命令中指定 `-OutputFormat`，则采用该指定项 (#8115)</span><span class="sxs-lookup"><span data-stu-id="8e831-148">Honor `-OutputFormat` if specified in non-interactive, redirected, encoded command used with pwsh (#8115)</span></span>
- <span data-ttu-id="8e831-149">在尝试从 GAC 加载程序集之前，先从模块基路径加载程序集 (#8073)</span><span class="sxs-lookup"><span data-stu-id="8e831-149">Load assembly from module base path before trying to load from the GAC (#8073)</span></span>
- <span data-ttu-id="8e831-150">从 Linux 预览包中删除波形符 (#8244)</span><span class="sxs-lookup"><span data-stu-id="8e831-150">Remove tilde from Linux preview packages (#8244)</span></span>
- <span data-ttu-id="8e831-151">先移动处理 `-WorkingDirectory` 再处理配置文件 (#8079)</span><span class="sxs-lookup"><span data-stu-id="8e831-151">Move processing of `-WorkingDirectory` before processing of profiles (#8079)</span></span>
- <span data-ttu-id="8e831-152">不要在 Unix 上添加 `PATHEXT` 环境变量 (#7697)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="8e831-152">Do not add `PATHEXT` environment variable on Unix (#7697) (Thanks @iSazonov!)</span></span>

## <a name="known-issues"></a><span data-ttu-id="8e831-153">已知问题</span><span class="sxs-lookup"><span data-stu-id="8e831-153">Known Issues</span></span>

- <span data-ttu-id="8e831-154">在 Windows IOT ARM 平台上进行的远程处理存在模块加载问题。</span><span class="sxs-lookup"><span data-stu-id="8e831-154">Remoting on Windows IOT ARM platforms has an issue loading modules.</span></span> <span data-ttu-id="8e831-155">请参阅 (#8053)</span><span class="sxs-lookup"><span data-stu-id="8e831-155">See (#8053)</span></span>

## <a name="general-updates-and-fixes"></a><span data-ttu-id="8e831-156">常规更新和修补程序</span><span class="sxs-lookup"><span data-stu-id="8e831-156">General Updates and Fixes</span></span>

- <span data-ttu-id="8e831-157">在区分大小写的文件系统上为文件和文件夹启用不区分大小写的 Tab 自动补全 (#8128)</span><span class="sxs-lookup"><span data-stu-id="8e831-157">Enable case-insensitive tab completion for files and folders on case-sensitive filesystem (#8128)</span></span>
- <span data-ttu-id="8e831-158">公开 PSVersionInfo.PSVersion 和 PSVersionInfo.PSEdition (#8054)（感谢 @KirkMunro！）</span><span class="sxs-lookup"><span data-stu-id="8e831-158">Make PSVersionInfo.PSVersion and PSVersionInfo.PSEdition public (#8054) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="8e831-159">在 `catch{ }` 块中为 `$_` / `$PSItem` 添加类型推理 (#8020)（感谢 @vexx32！）</span><span class="sxs-lookup"><span data-stu-id="8e831-159">Add Type Inference for `$_` / `$PSItem` in `catch{ }` blocks (#8020) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="8e831-160">修复静态方法调用类型推理 (#8018)（感谢 @SeeminglyScience！）</span><span class="sxs-lookup"><span data-stu-id="8e831-160">Fix static method invocation type inference (#8018) (Thanks @SeeminglyScience!)</span></span>
- <span data-ttu-id="8e831-161">为 `Select-Object`、`Group-Object`、PSObject  和 Hashtable  创建推理类型 (#7231)（感谢 @powercode！）</span><span class="sxs-lookup"><span data-stu-id="8e831-161">Create inferred types for `Select-Object`, `Group-Object`, **PSObject** and **Hashtable** (#7231) (Thanks @powercode!)</span></span>
- <span data-ttu-id="8e831-162">支持使用 `ByRef-like` 类型参数的调用方法 (#7721)</span><span class="sxs-lookup"><span data-stu-id="8e831-162">Support calling method with `ByRef-like` type parameters (#7721)</span></span>
- <span data-ttu-id="8e831-163">处理 Windows PowerShell 模块路径已在环境的 PSModulePath 中的情况 (#7727)</span><span class="sxs-lookup"><span data-stu-id="8e831-163">Handle the case where the Windows PowerShell module path is already in the environment's PSModulePath (#7727)</span></span>
- <span data-ttu-id="8e831-164">通过存储纯文本来启用适用于非 Windows 的 `SecureString` cmdlet (#9199)</span><span class="sxs-lookup"><span data-stu-id="8e831-164">Enable `SecureString` cmdlets for non-Windows by storing the plain text (#9199)</span></span>
- <span data-ttu-id="8e831-165">使用 securestring 导入 clixml 时，改进非 Windows 上的错误消息 (#7997)</span><span class="sxs-lookup"><span data-stu-id="8e831-165">Improve error message on non-Windows when importing clixml with securestring (#7997)</span></span>
- <span data-ttu-id="8e831-166">将参数 ReplyTo 添加到 `Send-MailMessage` (#8727)（感谢 @replicaJunction！）</span><span class="sxs-lookup"><span data-stu-id="8e831-166">Adding parameter ReplyTo to `Send-MailMessage` (#8727) (Thanks @replicaJunction!)</span></span>
- <span data-ttu-id="8e831-167">将已过时的消息添加到 `Send-MailMessage` (#9178)</span><span class="sxs-lookup"><span data-stu-id="8e831-167">Add Obsolete message to `Send-MailMessage` (#9178)</span></span>
- <span data-ttu-id="8e831-168">修复 `Restart-Computer`，以便在 WinRM 不存在时使用 `localhost` (#9160)</span><span class="sxs-lookup"><span data-stu-id="8e831-168">Fix `Restart-Computer` to work on `localhost` when WinRM is not present (#9160)</span></span>
- <span data-ttu-id="8e831-169">正在托管 PowerShell 时，使 `Start-Job` 引发终止错误 (#9128)</span><span class="sxs-lookup"><span data-stu-id="8e831-169">Make `Start-Job` throw terminating error when PowerShell is being hosted (#9128)</span></span>
- <span data-ttu-id="8e831-170">为 ushort、uint、ulong 和短文本添加 C# 样式类型加速器和后缀 (#7813)（感谢 @vexx32！）</span><span class="sxs-lookup"><span data-stu-id="8e831-170">Add C# style type accelerators and suffixes for ushort, uint, ulong, and short literals (#7813) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="8e831-171">为数字文本添加了新后缀 - 请参阅 [about_Numeric_Literals][] (#7901)（感谢 @vexx32！）</span><span class="sxs-lookup"><span data-stu-id="8e831-171">Added new suffixes for numeric literals - see [about_Numeric_Literals][] (#7901) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="8e831-172">当 SupportsShouldProcess 未设置为“true”时，正确地报告影响级别 (#8209)（感谢 @vexx32！）</span><span class="sxs-lookup"><span data-stu-id="8e831-172">Correctly Report impact level when SupportsShouldProcess is not set to 'true' (#8209) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="8e831-173">修复 Web Cmdlet 中的请求字符集问题 (#8742)（感谢 @markekraus！）</span><span class="sxs-lookup"><span data-stu-id="8e831-173">Fix Request Charset Issues in Web Cmdlets (#8742) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="8e831-174">修复 Web Cmdlet 中预期的 `100-continue` 问题 (#8679)（感谢 @markekraus！）</span><span class="sxs-lookup"><span data-stu-id="8e831-174">Fix Expect `100-continue` issue with Web Cmdlets (#8679) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="8e831-175">修复 Web Cmdlet 中的文件阻塞性问题 (#7676)（感谢 @Claustn！）</span><span class="sxs-lookup"><span data-stu-id="8e831-175">Fix file blocking issue with web cmdlets (#7676) (Thanks @Claustn!)</span></span>
- <span data-ttu-id="8e831-176">修复 `Invoke-RestMethod` 中的代码页分析问题 (#8694)（感谢 @markekraus！）</span><span class="sxs-lookup"><span data-stu-id="8e831-176">Fix code page parsing issue in `Invoke-RestMethod` (#8694) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="8e831-177">重构 `ConvertTo-Json` 以将 JsonObject.ConvertToJson 公开为公共 API (#8682)</span><span class="sxs-lookup"><span data-stu-id="8e831-177">Refactor `ConvertTo-Json` to expose JsonObject.ConvertToJson as a public API (#8682)</span></span>
- <span data-ttu-id="8e831-178">使用 -Depth 在 `ConvertFrom-Json` 中添加可配置的最大深度 (#8199)（感谢 @louistio！）</span><span class="sxs-lookup"><span data-stu-id="8e831-178">Add configurable maximum depth in `ConvertFrom-Json` with -Depth (#8199) (Thanks @louistio!)</span></span>
- <span data-ttu-id="8e831-179">在 `ConvertTo-Json` cmdlet 中添加 EscapeHandling 参数 (#7775)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="8e831-179">Add EscapeHandling parameter in `ConvertTo-Json` cmdlet (#7775) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="8e831-180">将 `-CustomPipeName` 添加到 pwsh 和 `Enter-PSHostProcess` (#8889)</span><span class="sxs-lookup"><span data-stu-id="8e831-180">Add `-CustomPipeName` to pwsh and `Enter-PSHostProcess` (#8889)</span></span>
- <span data-ttu-id="8e831-181">使用 `New-Item` 在 Windows 上启用创建相对符号链接 (#8783)</span><span class="sxs-lookup"><span data-stu-id="8e831-181">Enable creating relative symbolic links on Windows with `New-Item` (#8783)</span></span>
- <span data-ttu-id="8e831-182">允许 Windows 用户在开发人员模式下创建符号链接，而不需要提升 (#8534)</span><span class="sxs-lookup"><span data-stu-id="8e831-182">Allow Windows users in developer mode to create symlinks without elevation (#8534)</span></span>
- <span data-ttu-id="8e831-183">启用 `Write-Information` 以接受 `$null` (#8774)</span><span class="sxs-lookup"><span data-stu-id="8e831-183">Enable `Write-Information` to accept `$null` (#8774)</span></span>
- <span data-ttu-id="8e831-184">使用 MAML 帮助内容修复高级函数的 `Get-Help` (#8353)</span><span class="sxs-lookup"><span data-stu-id="8e831-184">Fix `Get-Help` for advanced functions with MAML help content (#8353)</span></span>
- <span data-ttu-id="8e831-185">当只声明一个参数时，使用 -Parameter 修复 `Get-Help` PSTypeName 问题 (#8754)（感谢 @pougetat！）</span><span class="sxs-lookup"><span data-stu-id="8e831-185">Fix `Get-Help` PSTypeName issue with -Parameter when only one parameter is declared (#8754) (Thanks @pougetat!)</span></span>
- <span data-ttu-id="8e831-186">针对在 ScriptBlock 上执行的 `Get-Help` 进行令牌计算修复，以获得注释帮助。</span><span class="sxs-lookup"><span data-stu-id="8e831-186">Token calculation fix for `Get-Help` executed on ScriptBlock for comment help.</span></span> <span data-ttu-id="8e831-187">(#8238)（感谢 @hubuk！）</span><span class="sxs-lookup"><span data-stu-id="8e831-187">(#8238) (Thanks @hubuk!)</span></span>
- <span data-ttu-id="8e831-188">更改 `Get-Help` cmdlet -Parameter 参数，以便它接受字符串数组 (#8454)（感谢 @sethvs！）</span><span class="sxs-lookup"><span data-stu-id="8e831-188">Change `Get-Help` cmdlet -Parameter parameter so it accepts string arrays (#8454) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="8e831-189">如果 PAGER 路径包含空格，则对其进行解析 (#8571)（感谢 @pougetat！）</span><span class="sxs-lookup"><span data-stu-id="8e831-189">Resolve PAGER if its path contains spaces (#8571) (Thanks @pougetat!)</span></span>
- <span data-ttu-id="8e831-190">在“help”函数中添加 `less` 的使用提示，以指导用户如何退出 (#7998)</span><span class="sxs-lookup"><span data-stu-id="8e831-190">Add prompt to the use of `less` in the function 'help' to instruct user how to quit (#7998)</span></span>
- <span data-ttu-id="8e831-191">在 `Format-Hex` cmdlet 中添加支持枚举和 char 类型 (#8191)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="8e831-191">Add support enum and char types in `Format-Hex` cmdlet (#8191) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="8e831-192">从 `Format-Hex` 中删除 ShouldProcess (#8178)</span><span class="sxs-lookup"><span data-stu-id="8e831-192">Remove ShouldProcess from `Format-Hex` (#8178)</span></span>
- <span data-ttu-id="8e831-193">将新 Offset 和 Count 参数添加到 `Format-Hex` 并重构 cmdlet (#7877)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="8e831-193">Add new Offset and Count parameters to `Format-Hex` and refactor the cmdlet (#7877) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="8e831-194">允许“name”作为 `ConvertTo-Html` 中“label”的别名键，允许“width”条目为整数 (#8426)（感谢 @mklement0！）</span><span class="sxs-lookup"><span data-stu-id="8e831-194">Allow 'name' as an alias key for 'label' in `ConvertTo-Html`, allow the 'width' entry to be an integer (#8426) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="8e831-195">使基于脚本块计算的属性在 `ConvertTo-Html` 中再次起作用 (#8427)（感谢 @mklement0！）</span><span class="sxs-lookup"><span data-stu-id="8e831-195">Make scriptblock based calculated properties work again in `ConvertTo-Html` (#8427) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="8e831-196">添加 cmdlet `Join-String` 以从管道输入创建文本 (#7660)（感谢 @powercode！）</span><span class="sxs-lookup"><span data-stu-id="8e831-196">Add cmdlet `Join-String` for creating text from pipeline input (#7660) (Thanks @powercode!)</span></span>
- <span data-ttu-id="8e831-197">修复 `Join-String` cmdlet FormatString 参数逻辑 (#8449)（感谢 @sethvs！）</span><span class="sxs-lookup"><span data-stu-id="8e831-197">Fix `Join-String` cmdlet FormatString parameter logic (#8449) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="8e831-198">将 `Clear-Host` 更改回使用 `$RAWUI` 并清除以进行远程操作 (#8609)</span><span class="sxs-lookup"><span data-stu-id="8e831-198">Change `Clear-Host` back to using `$RAWUI` and clear to work over remoting (#8609)</span></span>
- <span data-ttu-id="8e831-199">更改 `Clear-Host` 以简单地调用 `[console]::clear`，并从 Unix 中删除清晰别名 (#8603)</span><span class="sxs-lookup"><span data-stu-id="8e831-199">Change `Clear-Host` to simply called `[console]::clear` and remove clear alias from Unix (#8603)</span></span>
- <span data-ttu-id="8e831-200">修复 `Import-Csv` 中的 LiteralPath 以绑定到 `Get-ChildItem` 输出 (#8277)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="8e831-200">Fix LiteralPath in `Import-Csv` to bind to `Get-ChildItem` output (#8277) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="8e831-201">help 函数不应为 AliasHelpInfo 使用寻呼程序 (#8552)</span><span class="sxs-lookup"><span data-stu-id="8e831-201">help function shouldn't use pager for AliasHelpInfo (#8552)</span></span>
- <span data-ttu-id="8e831-202">将 `-UseMinimalHeader` 添加到 `Start-Transcript` 以最小化脚本标头 (#8402)（感谢 @lukexjeremy！）</span><span class="sxs-lookup"><span data-stu-id="8e831-202">Add `-UseMinimalHeader` to `Start-Transcript` to minimize transcript header (#8402) (Thanks @lukexjeremy!)</span></span>
- <span data-ttu-id="8e831-203">添加 `Enable-ExperimentalFeature` 和 `Disable-ExperimentalFeature` cmdlet (#8318)</span><span class="sxs-lookup"><span data-stu-id="8e831-203">Add `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature` cmdlets (#8318)</span></span>
- <span data-ttu-id="8e831-204">如果 logman.exe 可用，则公开 PSDiagnostics  中的所有 cmdlet (#8366)</span><span class="sxs-lookup"><span data-stu-id="8e831-204">Expose all cmdlets from **PSDiagnostics** if logman.exe is available (#8366)</span></span>
- <span data-ttu-id="8e831-205">在 `non-Windows` 平台上从 `New-PSDrive` 删除 Persist  参数 (#8291)（感谢 @lukexjeremy！）</span><span class="sxs-lookup"><span data-stu-id="8e831-205">Remove **Persist** parameter from `New-PSDrive` on `non-Windows` platform (#8291) (Thanks @lukexjeremy!)</span></span>
- <span data-ttu-id="8e831-206">添加对 `cd +` 的支持 (#7206)（感谢 @bergmeister！）</span><span class="sxs-lookup"><span data-stu-id="8e831-206">Add support for `cd +` (#7206) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="8e831-207">使 `Set-Location -LiteralPath` 能够使用名为 - 和 + 的文件夹 (#8089)</span><span class="sxs-lookup"><span data-stu-id="8e831-207">Enable `Set-Location -LiteralPath` to work with folders named - and + (#8089)</span></span>
- <span data-ttu-id="8e831-208">当给定空路径值或 `$null` 路径值时，`Test-Path` 返回 `$false` (#8080)（感谢 @vexx32！）</span><span class="sxs-lookup"><span data-stu-id="8e831-208">`Test-Path` returns `$false` when given an empty or `$null` path value (#8080) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="8e831-209">允许返回动态参数，即使路径不匹配任何提供程序 (#7957)</span><span class="sxs-lookup"><span data-stu-id="8e831-209">Allow dynamic parameter to be returned even if path does not match any provider (#7957)</span></span>
- <span data-ttu-id="8e831-210">在 Unix 平台上支持 `Get-PSHostProcessInfo` 和 `Enter-PSHostProcess` (#8232)</span><span class="sxs-lookup"><span data-stu-id="8e831-210">Support `Get-PSHostProcessInfo` and `Enter-PSHostProcess` on Unix platforms (#8232)</span></span>
- <span data-ttu-id="8e831-211">减少 `Get-Content` cmdlet 中的分配 (#8103)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="8e831-211">Reduce allocations in `Get-Content` cmdlet (#8103) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="8e831-212">允许 `Add-Content` 在编写内容时与其他工具共享读取访问 (#8091)</span><span class="sxs-lookup"><span data-stu-id="8e831-212">Enable `Add-Content` to share read access with other tools while writing content (#8091)</span></span>
- <span data-ttu-id="8e831-213">在将某个容器设定为目标时，`Get/Add-Content` 引发改进错误 (#7823)（感谢 @kvprasoon！）</span><span class="sxs-lookup"><span data-stu-id="8e831-213">`Get/Add-Content` throws improved error when targeting a container (#7823) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="8e831-214">将 `-Name`、`-NoUserOverrides` 和 `-ListAvailable` 参数添加到 `Get-Culture` cmdlet (#7702)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="8e831-214">Add `-Name`, `-NoUserOverrides` and `-ListAvailable` parameters to `Get-Culture` cmdlet (#7702) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="8e831-215">为完成 Encoding  参数添加统一属性。</span><span class="sxs-lookup"><span data-stu-id="8e831-215">Add unified attribute for completion for **Encoding** parameter.</span></span> <span data-ttu-id="8e831-216">(#7732)（感谢 @ThreeFive-O！）</span><span class="sxs-lookup"><span data-stu-id="8e831-216">(#7732) (Thanks @ThreeFive-O!)</span></span>
- <span data-ttu-id="8e831-217">允许注册代码页的数字 Id 和名称出现在 Encoding  参数中 (#7636)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="8e831-217">Allow numeric Ids and name of registered code pages in **Encoding** parameters (#7636) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="8e831-218">使用通配符字符修复 `Rename-Item -Path` (#7398)（感谢 @kwkam！）</span><span class="sxs-lookup"><span data-stu-id="8e831-218">Fix `Rename-Item -Path` with wildcard char (#7398) (Thanks @kwkam!)</span></span>
- <span data-ttu-id="8e831-219">当使用 `Start-Transcript` 且文件存在时，清空文件而不是将其删除 (#8131)（感谢 @paalbra！）</span><span class="sxs-lookup"><span data-stu-id="8e831-219">When using `Start-Transcript` and file exists, empty file rather than deleting (#8131) (Thanks @paalbra!)</span></span>
- <span data-ttu-id="8e831-220">通过 FileAccess.Read  和 FileShare.Read  使 `Add-Type` 显式成为开放源代码文件 (#7915)（感谢 @IISResetMe！）</span><span class="sxs-lookup"><span data-stu-id="8e831-220">Make `Add-Type` open source files with **FileAccess.Read** and **FileShare.Read** explicitly (#7915) (Thanks @IISResetMe!)</span></span>
- <span data-ttu-id="8e831-221">修复最新 Windows 的 `Enter-PSSession -ContainerId` (#7883)</span><span class="sxs-lookup"><span data-stu-id="8e831-221">Fix `Enter-PSSession -ContainerId` for the latest Windows (#7883)</span></span>
- <span data-ttu-id="8e831-222">请确保 NestedModules  属性由 `Test-ModuleManifest` 填充 (#7859)</span><span class="sxs-lookup"><span data-stu-id="8e831-222">Ensure **NestedModules** property gets populated by `Test-ModuleManifest` (#7859)</span></span>
- <span data-ttu-id="8e831-223">将 `%F` case 添加到 `Get-Date` -UFormat (#7630)（感谢 @britishben！）</span><span class="sxs-lookup"><span data-stu-id="8e831-223">Add `%F` case to `Get-Date` -UFormat (#7630) (Thanks @britishben!)</span></span>
- <span data-ttu-id="8e831-224">修复 `Set-Service -Status Stopped` 以停止具有依赖项的服务 (#5525)（感谢 @zhenggu！）</span><span class="sxs-lookup"><span data-stu-id="8e831-224">Fix `Set-Service -Status Stopped` to stop services with dependencies (#5525) (Thanks @zhenggu!)</span></span>

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals
[实验性功能]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[Experimental Features]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
