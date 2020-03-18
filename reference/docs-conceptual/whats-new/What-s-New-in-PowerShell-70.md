---
title: PowerShell 7.0 中的新增功能
description: PowerShell 7.0 中发布的新功能和更改
ms.date: 03/04/2020
ms.openlocfilehash: 6915bb70d6e54da86d2b935e3feed8d7f3770ba9
ms.sourcegitcommit: 4a26c05f162c4fa347a9d67e339f8a33e230b9ba
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78404996"
---
# <a name="whats-new-in-powershell-70"></a><span data-ttu-id="b468e-103">PowerShell 7.0 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="b468e-103">What's New in PowerShell 7.0</span></span>

<span data-ttu-id="b468e-104">PowerShell 7.0 是 PowerShell 的一个版本，它开源、跨平台（Windows、macOS 和 Linux）且为管理异类环境和混合云而构建。</span><span class="sxs-lookup"><span data-stu-id="b468e-104">PowerShell 7.0 is an open-source, cross-platform (Windows, macOS, and Linux) edition of PowerShell, built to manage heterogeneous environments and hybrid cloud.</span></span>

<span data-ttu-id="b468e-105">在此版本中，我们引入了一些新功能，包括：</span><span class="sxs-lookup"><span data-stu-id="b468e-105">In this release, we're introducing a number of new features, including:</span></span>

- <span data-ttu-id="b468e-106">使用 `ForEach-Object -Parallel` 实现管道并行化</span><span class="sxs-lookup"><span data-stu-id="b468e-106">Pipeline parallelization with `ForEach-Object -Parallel`</span></span>
- <span data-ttu-id="b468e-107">新运算符：</span><span class="sxs-lookup"><span data-stu-id="b468e-107">New operators:</span></span>
  - <span data-ttu-id="b468e-108">三元运算符：`a ? b : c`</span><span class="sxs-lookup"><span data-stu-id="b468e-108">Ternary operator: `a ? b : c`</span></span>
  - <span data-ttu-id="b468e-109">管道链运算符：`||` 和 `&&`</span><span class="sxs-lookup"><span data-stu-id="b468e-109">Pipeline chain operators: `||` and `&&`</span></span>
  - <span data-ttu-id="b468e-110">空条件运算符：`??` 和 `??=`</span><span class="sxs-lookup"><span data-stu-id="b468e-110">Null conditional operators: `??` and `??=`</span></span>
- <span data-ttu-id="b468e-111">简化且动态的错误视图和 `Get-Error` cmdlet，以便更轻松地调查错误</span><span class="sxs-lookup"><span data-stu-id="b468e-111">A simplified and dynamic error view and `Get-Error` cmdlet for easier investigation of errors</span></span>
- <span data-ttu-id="b468e-112">兼容层，使用户能够在隐式 Windows PowerShell 会话中导入模块</span><span class="sxs-lookup"><span data-stu-id="b468e-112">A compatibility layer that enables users to import modules in an implicit Windows PowerShell session</span></span>
- <span data-ttu-id="b468e-113">自动新版本通知</span><span class="sxs-lookup"><span data-stu-id="b468e-113">Automatic new version notifications</span></span>
- <span data-ttu-id="b468e-114">直接从 PowerShell 7 调用 DSC 资源的功能（实验性）</span><span class="sxs-lookup"><span data-stu-id="b468e-114">The ability to invoke DSC resources directly from PowerShell 7 (experimental)</span></span>

<span data-ttu-id="b468e-115">若要查看功能和修补程序的完整列表，请参阅[更改日志](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.0.md)。</span><span class="sxs-lookup"><span data-stu-id="b468e-115">To see a full list of features and fixes, see the [changelogs](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.0.md).</span></span>

## <a name="where-can-i-install-powershell"></a><span data-ttu-id="b468e-116">可将 PowerShell 安装在何处？</span><span class="sxs-lookup"><span data-stu-id="b468e-116">Where can I install PowerShell?</span></span>

<span data-ttu-id="b468e-117">PowerShell 7 当前支持 x64 上的以下操作系统，包括：</span><span class="sxs-lookup"><span data-stu-id="b468e-117">PowerShell 7 currently supports the following operating systems on x64, including:</span></span>

- <span data-ttu-id="b468e-118">Windows 8.1 和 10</span><span class="sxs-lookup"><span data-stu-id="b468e-118">Windows 8.1, and 10</span></span>
- <span data-ttu-id="b468e-119">Windows Server 2012、2012 R2、2016 和 2019</span><span class="sxs-lookup"><span data-stu-id="b468e-119">Windows Server 2012, 2012 R2, 2016, and 2019</span></span>
- <span data-ttu-id="b468e-120">macOS 10.13+</span><span class="sxs-lookup"><span data-stu-id="b468e-120">macOS 10.13+</span></span>
- <span data-ttu-id="b468e-121">Red Hat Enterprise Linux (RHEL)/CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b468e-121">Red Hat Enterprise Linux (RHEL) / CentOS 7</span></span>
- <span data-ttu-id="b468e-122">Fedora 30+</span><span class="sxs-lookup"><span data-stu-id="b468e-122">Fedora 30+</span></span>
- <span data-ttu-id="b468e-123">Debian 9</span><span class="sxs-lookup"><span data-stu-id="b468e-123">Debian 9</span></span>
- <span data-ttu-id="b468e-124">Ubuntu LTS 16.04+</span><span class="sxs-lookup"><span data-stu-id="b468e-124">Ubuntu LTS 16.04+</span></span>
- <span data-ttu-id="b468e-125">Alpine Linux 3.8+</span><span class="sxs-lookup"><span data-stu-id="b468e-125">Alpine Linux 3.8+</span></span>

<span data-ttu-id="b468e-126">此外，PowerShell 7.0 支持 ARM32 和 ARM64 版的 Debian、Ubuntu 和 ARM64 Alpine Linux。</span><span class="sxs-lookup"><span data-stu-id="b468e-126">Additionally, PowerShell 7.0 supports ARM32 and ARM64 flavors of Debian, Ubuntu, and ARM64 Alpine Linux.</span></span>

<span data-ttu-id="b468e-127">查看首选操作系统 [Windows](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7)、[macOS](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7) 或 [Linux](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7) 的安装说明。</span><span class="sxs-lookup"><span data-stu-id="b468e-127">Check the installation instructions for your preferred operating system [Windows](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7), [macOS](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7), or [Linux](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7).</span></span>

<span data-ttu-id="b468e-128">虽然没有得到正式支持，但社区还提供了 [Arch](https://aur.archlinux.org/packages/powershell/) 和 Kali Linux 的包。</span><span class="sxs-lookup"><span data-stu-id="b468e-128">While not officially supported, the community has also provided packages for [Arch](https://aur.archlinux.org/packages/powershell/) and Kali Linux.</span></span>

> [!NOTE]
> <span data-ttu-id="b468e-129">Debian 10 和 CentOS 8 目前不支持 WinRM 远程处理。</span><span class="sxs-lookup"><span data-stu-id="b468e-129">Debian 10 and CentOS 8 currently do not support WinRM remoting.</span></span> <span data-ttu-id="b468e-130">有关设置基于 SSH 的远程处理的详细信息，请参阅[通过 SSH 进行 PowerShell 远程处理](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core?view=powershell-7)。</span><span class="sxs-lookup"><span data-stu-id="b468e-130">For details on setting up SSH-based remoting, see [PowerShell Remoting over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core?view=powershell-7).</span></span>

<span data-ttu-id="b468e-131">有关支持的操作系统和支持生命周期的最新信息，请参阅 [PowerShell 支持生命周期](/powershell/scripting/powershell-support-lifecycle?view=powershell-7)。</span><span class="sxs-lookup"><span data-stu-id="b468e-131">For more up-to-date information about supported operating systems and support lifecycle, see the [PowerShell Support Lifecycle](/powershell/scripting/powershell-support-lifecycle?view=powershell-7).</span></span>

## <a name="running-powershell-7"></a><span data-ttu-id="b468e-132">运行 PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="b468e-132">Running PowerShell 7</span></span>

<span data-ttu-id="b468e-133">PowerShell 7 安装到新目录，并与 Windows PowerShell 5.1 并行运行。</span><span class="sxs-lookup"><span data-stu-id="b468e-133">PowerShell 7 installs to a new directory and runs side-by-side with Windows PowerShell 5.1.</span></span> <span data-ttu-id="b468e-134">对于 PowerShell Core 6.x，PowerShell 7 是删除 PowerShell Core 6.x 的就地升级。</span><span class="sxs-lookup"><span data-stu-id="b468e-134">For PowerShell Core 6.x, PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>

- <span data-ttu-id="b468e-135">PowerShell 7 安装到 `%programfiles%\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="b468e-135">PowerShell 7 is installed to `%programfiles%\PowerShell\7`</span></span>
- <span data-ttu-id="b468e-136">`%programfiles%\PowerShell\7` 文件夹已添加到 `$env:PATH`</span><span class="sxs-lookup"><span data-stu-id="b468e-136">The `%programfiles%\PowerShell\7` folder is added to `$env:PATH`</span></span>

<span data-ttu-id="b468e-137">PowerShell 7 安装程序包升级以前版本的 PowerShell Core 6.x：</span><span class="sxs-lookup"><span data-stu-id="b468e-137">The PowerShell 7 installer packages upgrade previous versions of PowerShell Core 6.x:</span></span>

- <span data-ttu-id="b468e-138">Windows 上的 PowerShell Core 6.x：`%programfiles%\PowerShell\6` 已替换为 `%programfiles%\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="b468e-138">PowerShell Core 6.x on Windows: `%programfiles%\PowerShell\6` is replaced by `%programfiles%\PowerShell\7`</span></span>
- <span data-ttu-id="b468e-139">Linux：`/opt/microsoft/powershell/6` 已替换为 `/opt/microsoft/powershell/7`</span><span class="sxs-lookup"><span data-stu-id="b468e-139">Linux: `/opt/microsoft/powershell/6` is replaced by `/opt/microsoft/powershell/7`</span></span>
- <span data-ttu-id="b468e-140">macOS：`/usr/local/microsoft/powershell/6` 已替换为 `/usr/local/microsoft/powershell/7`</span><span class="sxs-lookup"><span data-stu-id="b468e-140">macOS: `/usr/local/microsoft/powershell/6` is replaced by `/usr/local/microsoft/powershell/7`</span></span>

> [!NOTE]
> <span data-ttu-id="b468e-141">在 Windows PowerShell 中，用于启动 PowerShell 的可执行文件名为 `powershell.exe`。</span><span class="sxs-lookup"><span data-stu-id="b468e-141">In Windows PowerShell, the executable to launch PowerShell is named `powershell.exe`.</span></span> <span data-ttu-id="b468e-142">在版本 6 及更高版本中，可执行文件将更改为支持并行执行。</span><span class="sxs-lookup"><span data-stu-id="b468e-142">In version 6 and above, the executable is changed to support side-by-side execution.</span></span> <span data-ttu-id="b468e-143">用于启动 PowerShell 7 的新可执行文件为 `pwsh.exe`。</span><span class="sxs-lookup"><span data-stu-id="b468e-143">The new executable to launch PowerShell 7 is `pwsh.exe`.</span></span> <span data-ttu-id="b468e-144">预览版本将就地保留为 `pwsh-preview`，而不是 7 预览目录下的 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="b468e-144">Preview builds will remain in-place as `pwsh-preview` instead of `pwsh` under the 7-preview directory.</span></span>

## <a name="improved-backwards-compatibility-with-windows-powershell"></a><span data-ttu-id="b468e-145">改进了 Windows PowerShell 的向后兼容性</span><span class="sxs-lookup"><span data-stu-id="b468e-145">Improved backwards compatibility with Windows PowerShell</span></span>

<span data-ttu-id="b468e-146">PowerShell 7.0 标记了转移到 .NET Core 3.1 的过程，从而大大改进了现有 Windows PowerShell 模块向后兼容性。</span><span class="sxs-lookup"><span data-stu-id="b468e-146">PowerShell 7.0 marks a move a to .NET Core 3.1, enabling significantly more backwards compatibility with existing Windows PowerShell modules.</span></span> <span data-ttu-id="b468e-147">其中包括 Windows 上需要 GUI 功能（如 `Out-GridView` 和 `Show-Command`）的许多模块以及作为 Windows 的一部分提供的许多角色管理模块。</span><span class="sxs-lookup"><span data-stu-id="b468e-147">This includes many modules on Windows that require GUI functionality like `Out-GridView` and `Show-Command`, as well as many role management modules that ship as part of Windows.</span></span>

<span data-ttu-id="b468e-148">对于 Windows，新开关参数 UseWindowsPowerShell 将添加到 `Import-Module`  。</span><span class="sxs-lookup"><span data-stu-id="b468e-148">For Windows, a new switch parameter **UseWindowsPowerShell** is added to `Import-Module`.</span></span> <span data-ttu-id="b468e-149">此开关会在 PowerShell 7 中创建一个代理模块，该模块使用本地 Windows PowerShell 进程隐式运行该模块中包含的任何 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b468e-149">This switch creates a proxy module in PowerShell 7 that uses a local Windows PowerShell process to implicitly run any cmdlets contained in that module.</span></span> <span data-ttu-id="b468e-150">有关 [Import-Module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7) 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="b468e-150">For more information on [Import-Module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7).</span></span>

<span data-ttu-id="b468e-151">有关哪些 Microsoft 模块适用于 PowerShell 7.0 的详细信息，请参阅[模块兼容性表](https://aka.ms/PSModuleCompat)。</span><span class="sxs-lookup"><span data-stu-id="b468e-151">For more information on which Microsoft modules work with PowerShell 7.0, see the [Module Compatibility Table](https://aka.ms/PSModuleCompat).</span></span>

## <a name="parallel-execution-added-to-foreach-object"></a><span data-ttu-id="b468e-152">添加到 ForEach-Object 的并行执行</span><span class="sxs-lookup"><span data-stu-id="b468e-152">Parallel execution added to ForEach-Object</span></span>

<span data-ttu-id="b468e-153">循环访问集合中的项的 `ForEach-Object` cmdlet 现在使用新的 Parallel 参数实现内置并行  。</span><span class="sxs-lookup"><span data-stu-id="b468e-153">The `ForEach-Object` cmdlet, which iterates items in a collection, now has built-in parallelism with the new **Parallel** parameter.</span></span>

<span data-ttu-id="b468e-154">默认情况下，并行脚本块使用启动并行任务的调用方的当前工作目录。</span><span class="sxs-lookup"><span data-stu-id="b468e-154">By default, parallel script blocks use the current working directory of the caller that started the parallel tasks.</span></span>

<span data-ttu-id="b468e-155">此示例从本地 Windows 计算机上的 5 个系统日志中检索 50,000 个日志条目：</span><span class="sxs-lookup"><span data-stu-id="b468e-155">This example retrieves 50,000 log entries from 5 system logs on a local Windows machine:</span></span>

```powershell
$logNames = 'Security','Application','System','Windows PowerShell','Microsoft-Windows-Store/Operational'

$logEntries = $logNames | ForEach-Object -Parallel {
    Get-WinEvent -LogName $_ -MaxEvents 10000
} -ThrottleLimit 5

$logEntries.Count

50000
```

<span data-ttu-id="b468e-156">Parallel 参数指定为每个输入日志名称并行运行的脚本块  。</span><span class="sxs-lookup"><span data-stu-id="b468e-156">The **Parallel** parameter specifies the script block that is run in parallel for each input log name.</span></span>

<span data-ttu-id="b468e-157">新的 ThrottleLimit 参数限制在给定时间内并行运行的脚本块数量  。</span><span class="sxs-lookup"><span data-stu-id="b468e-157">The new **ThrottleLimit** parameter limits the number of script blocks running in parallel at a given time.</span></span> <span data-ttu-id="b468e-158">默认值为 5。</span><span class="sxs-lookup"><span data-stu-id="b468e-158">The default is 5.</span></span>

<span data-ttu-id="b468e-159">使用 `$_` 变量来表示脚本块中的当前输入对象。</span><span class="sxs-lookup"><span data-stu-id="b468e-159">Use the `$_` variable to represent the current input object in the script block.</span></span> <span data-ttu-id="b468e-160">使用 `$using:` 范围将变量引用传递给正在运行的脚本块。</span><span class="sxs-lookup"><span data-stu-id="b468e-160">Use the `$using:` scope to pass variable references to the running script block.</span></span>

<span data-ttu-id="b468e-161">有关 [ForEach-Object](/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7) 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="b468e-161">For more information about [ForEach-Object](/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7).</span></span>

## <a name="ternary-operator"></a><span data-ttu-id="b468e-162">三元运算符</span><span class="sxs-lookup"><span data-stu-id="b468e-162">Ternary operator</span></span>

<span data-ttu-id="b468e-163">PowerShell 7.0 引入了三元运算符，它的行为类似于简化的 `if-else` 语句。</span><span class="sxs-lookup"><span data-stu-id="b468e-163">PowerShell 7.0 introduces a ternary operator which behaves like a simplified `if-else` statement.</span></span>
<span data-ttu-id="b468e-164">PowerShell 的三元运算符是严格按照 C# 三元运算符语法建模而来的：</span><span class="sxs-lookup"><span data-stu-id="b468e-164">PowerShell's ternary operator is closely modeled from the C# ternary operator syntax:</span></span>

```
<condition> ? <if-true> : <if-false>
```

<span data-ttu-id="b468e-165">始终计算条件表达式，并将其结果转换为布尔以确定下一次计算的分支  ：</span><span class="sxs-lookup"><span data-stu-id="b468e-165">The condition-expression is always evaluated and its result converted to a **Boolean** to determine which branch is evaluated next:</span></span>

- <span data-ttu-id="b468e-166">如果 `<condition>` 表达式为 true，则执行 `<if-true>` 表达式</span><span class="sxs-lookup"><span data-stu-id="b468e-166">The `<if-true>` expression is executed if the `<condition>` expression is true</span></span>
- <span data-ttu-id="b468e-167">如果 `<condition>` 表达式为 false，则执行 `<if-false>` 表达式</span><span class="sxs-lookup"><span data-stu-id="b468e-167">The `<if-false>` expression is executed if the `<condition>` expression is false</span></span>

<span data-ttu-id="b468e-168">例如：</span><span class="sxs-lookup"><span data-stu-id="b468e-168">For example:</span></span>

```powershell
$message = (Test-Path $path) ? "Path exists" : "Path not found"
```

<span data-ttu-id="b468e-169">在此示例中，如果路径存在，则显示“路径存在”  。</span><span class="sxs-lookup"><span data-stu-id="b468e-169">In this example, if the path exists, then **Path exists** is displayed.</span></span> <span data-ttu-id="b468e-170">如果路径不存在，则显示“找不到路径”  。</span><span class="sxs-lookup"><span data-stu-id="b468e-170">If the path does not exist, then **Path not found** is displayed.</span></span>

<span data-ttu-id="b468e-171">有关[关于假设情况](/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-7)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="b468e-171">For more information [About If](/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-7).</span></span>

## <a name="pipeline-chain-operators"></a><span data-ttu-id="b468e-172">管道链运算符</span><span class="sxs-lookup"><span data-stu-id="b468e-172">Pipeline chain operators</span></span>

<span data-ttu-id="b468e-173">PowerShell 7 实施 `&&` 和 `||` 运算符，以有条件地链接管道。</span><span class="sxs-lookup"><span data-stu-id="b468e-173">PowerShell 7 implements the `&&` and `||` operators to conditionally chain pipelines.</span></span> <span data-ttu-id="b468e-174">这些运算符在 PowerShell 中称为“管道链运算符”，与 shell（如 Bash 和 Zsh）中的 AND 和 OR 列表以及 Windows 命令 Shell (cmd.exe) 中的条件处理符号类似    。</span><span class="sxs-lookup"><span data-stu-id="b468e-174">These operators are known in PowerShell as "pipeline chain operators", and are similar to AND and OR lists in shells like **Bash** and **Zsh**, as well as conditional processing symbols in the Windows Command Shell (**cmd.exe**).</span></span>

<span data-ttu-id="b468e-175">如果左侧管道成功，则 `&&` 运算符将执行右侧管道。</span><span class="sxs-lookup"><span data-stu-id="b468e-175">The `&&` operator executes the right-hand pipeline, if the left-hand pipeline succeeded.</span></span> <span data-ttu-id="b468e-176">相反，如果左侧管道失败，则 `||` 运算符将执行右侧管道。</span><span class="sxs-lookup"><span data-stu-id="b468e-176">Conversely, the `||` operator executes the right-hand pipeline if the left-hand pipeline failed.</span></span>

> [!NOTE]
> <span data-ttu-id="b468e-177">这些运算符使用 `$?` 和 `$LASTEXITCODE` 变量来确定管道是否失败。</span><span class="sxs-lookup"><span data-stu-id="b468e-177">These operators use the `$?` and `$LASTEXITCODE` variables to determine if a pipeline failed.</span></span> <span data-ttu-id="b468e-178">这允许你将其与本机命令一起使用，而不只是与 cmdlet 或函数一起使用。</span><span class="sxs-lookup"><span data-stu-id="b468e-178">This allows you to use them with native commands and not just with cmdlets or functions.</span></span>

<span data-ttu-id="b468e-179">此处，第一个命令成功，执行第二个命令：</span><span class="sxs-lookup"><span data-stu-id="b468e-179">Here, the first command succeeds and the second command is executed:</span></span>

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

<span data-ttu-id="b468e-180">此处，第一个命令失败，不执行第二个命令：</span><span class="sxs-lookup"><span data-stu-id="b468e-180">Here, the first command fails, the second is not executed:</span></span>

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

<span data-ttu-id="b468e-181">此处，第一个命令成功，不执行第二个命令：</span><span class="sxs-lookup"><span data-stu-id="b468e-181">Here, the first command succeeds, the second command is not executed:</span></span>

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

<span data-ttu-id="b468e-182">此处，第一个命令失败，因此执行第二个命令：</span><span class="sxs-lookup"><span data-stu-id="b468e-182">Here, the first command fails, so the second command is executed:</span></span>

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error 'Bad'
Second
```

<span data-ttu-id="b468e-183">有关[关于管道链运算符](/powershell/module/microsoft.powershell.core/about/about_pipeline_chain_operators?view=powershell-7)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="b468e-183">For more information [About Pipeline Chain Operators](/powershell/module/microsoft.powershell.core/about/about_pipeline_chain_operators?view=powershell-7).</span></span>

## <a name="null-coalescing-assignment-and-conditional-operators"></a><span data-ttu-id="b468e-184">Null 合并运算符、赋值运算符和条件运算符</span><span class="sxs-lookup"><span data-stu-id="b468e-184">Null-coalescing, assignment, and conditional operators</span></span>

<span data-ttu-id="b468e-185">PowerShell 7 包括 Null 合并运算符 `??`、Null 条件赋值运算符 `??=` 和 Null 条件成员访问运算符 `?.` 和 `?[]`。</span><span class="sxs-lookup"><span data-stu-id="b468e-185">PowerShell 7 includes Null coalescing operator `??`, Null conditional assignment `??=`, and Null conditional member access operators `?.` and `?[]`.</span></span>

### <a name="null-coalescing-operator-"></a><span data-ttu-id="b468e-186">Null 合并运算符 ??</span><span class="sxs-lookup"><span data-stu-id="b468e-186">Null-coalescing Operator ??</span></span>

<span data-ttu-id="b468e-187">如果 null 合并运算符 `??` 不为 null，则它返回其左操作数的值。</span><span class="sxs-lookup"><span data-stu-id="b468e-187">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't null.</span></span>
<span data-ttu-id="b468e-188">否则，它将计算右操作数并返回其结果。</span><span class="sxs-lookup"><span data-stu-id="b468e-188">Otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="b468e-189">如果左操作数的计算结果为非 null，则 `??` 运算符不会计算其右操作数。</span><span class="sxs-lookup"><span data-stu-id="b468e-189">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

```powershell
$x = $null
$x ?? 100
100
```

<span data-ttu-id="b468e-190">在下面的示例中，不会计算右操作数：</span><span class="sxs-lookup"><span data-stu-id="b468e-190">In the following example, the right-hand operand won't be evaluated:</span></span>

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ?? (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-assignment-operator-"></a><span data-ttu-id="b468e-191">Null 条件赋值运算符 ??=</span><span class="sxs-lookup"><span data-stu-id="b468e-191">Null conditional assignment operator ??=</span></span>

<span data-ttu-id="b468e-192">仅当左操作数的计算结果为 null 时，null 条件赋值运算符 `??=` 才会将其右操作数的值赋值给其左操作数。</span><span class="sxs-lookup"><span data-stu-id="b468e-192">The null conditional assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to null.</span></span> <span data-ttu-id="b468e-193">如果左操作数的计算结果为非 null，则 `??=` 运算符不会计算其右操作数。</span><span class="sxs-lookup"><span data-stu-id="b468e-193">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

```powershell
$x = $null
$x ??= 100
$x
100
```

<span data-ttu-id="b468e-194">在下面的示例中，不会计算右操作数：</span><span class="sxs-lookup"><span data-stu-id="b468e-194">In the following example, the right-hand operand won't be evaluated:</span></span>

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ??= (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-member-access-operators--and--experimental"></a><span data-ttu-id="b468e-195">Null 条件成员访问运算符 ?.</span><span class="sxs-lookup"><span data-stu-id="b468e-195">Null conditional member access operators ?.</span></span> <span data-ttu-id="b468e-196">和 ?[]（实验性）</span><span class="sxs-lookup"><span data-stu-id="b468e-196">and ?[] (Experimental)</span></span>

> [!NOTE]
> <span data-ttu-id="b468e-197">这是名为 PSNullConditionalOperators 的实验性功能  。</span><span class="sxs-lookup"><span data-stu-id="b468e-197">This is an experimental feature named **PSNullConditionalOperators**.</span></span> <span data-ttu-id="b468e-198">了解[关于实验性功能](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="b468e-198">Learn more [About Experimental Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).</span></span>

<span data-ttu-id="b468e-199">仅当操作数的计算结果为非 null，null 条件运算符才允许对其操作数进程成员访问 `?.` 或元素访问 `?[]`；否则，将返回 null。</span><span class="sxs-lookup"><span data-stu-id="b468e-199">A null conditional operator permits member access, `?.`, or element access, `?[]`, to its operand only if that operand evaluates to non-null; otherwise, it returns null.</span></span>

> [!NOTE]
> <span data-ttu-id="b468e-200">由于 PowerShell 允许 `?` 作为变量名称的一部分，因此使用这些运算符需要变量名称的形式规范。</span><span class="sxs-lookup"><span data-stu-id="b468e-200">Since PowerShell allows `?` to be part of the variable name, formal specification of the variable name is required for using these operators.</span></span> <span data-ttu-id="b468e-201">因此，使用 `{}` 将变量名称括起来（如 `${a}`）或 `?` 是变量名称 `${a?}` 的一部分时需要形式规范。</span><span class="sxs-lookup"><span data-stu-id="b468e-201">So it is required to use `{}` around the variable names like `${a}` or when `?` is part of the variable name `${a?}`.</span></span>

<span data-ttu-id="b468e-202">在下面的示例中，将返回成员属性 Status 的值  ：</span><span class="sxs-lookup"><span data-stu-id="b468e-202">In the following example, the value of the member property **Status** is returned:</span></span>

```powershell
$Service = Get-Service -Name 'bits'
${Service}?.status
Stopped
```

<span data-ttu-id="b468e-203">以下示例将返回 null，而不尝试访问成员名称 Status  ：</span><span class="sxs-lookup"><span data-stu-id="b468e-203">The following example will return null, without trying to access the member name **Status**:</span></span>

```powershell
$service = $Null
${Service}?.status
```

<span data-ttu-id="b468e-204">同样，使用 `?[]`，将返回元素的值：</span><span class="sxs-lookup"><span data-stu-id="b468e-204">Similarly, using `?[]`, the value of the element will be returned:</span></span>

```powershell
$a = 1..10
${a}?[0]
1
```

<span data-ttu-id="b468e-205">如果操作数为 null，则不会访问元素并返回 null：</span><span class="sxs-lookup"><span data-stu-id="b468e-205">And when the operand is null, the element isn't accessed and null is returned:</span></span>

```powershell
$a = $null
${a}?[0]
```

<span data-ttu-id="b468e-206">有关 [About_Operators](/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7) 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="b468e-206">For more information [About_Operators](/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7).</span></span>

## <a name="new-view-conciseview-and-cmdlet-get-error"></a><span data-ttu-id="b468e-207">新视图 ConciseView 和 cmdlet Get-Error</span><span class="sxs-lookup"><span data-stu-id="b468e-207">New view ConciseView and cmdlet Get-Error</span></span>

<span data-ttu-id="b468e-208">通过新的默认视图 ConciseView，改进了错误消息的显示，从而提高交互式错误和脚本错误的可读性  。</span><span class="sxs-lookup"><span data-stu-id="b468e-208">The display of error messages has been improved to enhance the readability of interactive and script errors with a new default view **ConciseView**.</span></span> <span data-ttu-id="b468e-209">视图通过首选项变量 `$ErrorView` 可供用户选择。</span><span class="sxs-lookup"><span data-stu-id="b468e-209">The views are user-selectable through the preference variable `$ErrorView`.</span></span>

<span data-ttu-id="b468e-210">使用 ConciseView  ，如果错误不是源自脚本或分析器错误，则它是单行错误消息：</span><span class="sxs-lookup"><span data-stu-id="b468e-210">With **ConciseView**, if an error is not from a script or parser error, then it's a single line error message:</span></span>

```powershell
Get-Childitem -Path c:\NotReal
```

```Output
Get-ChildItem: Cannot find path 'C:\NotReal' because it does not exist
```

<span data-ttu-id="b468e-211">如果在脚本执行期间发生错误或者错误是分析错误，则 PowerShell 将返回一条多行错误消息，其中包含错误、指针以及显示错误在该行中的位置的错误消息。</span><span class="sxs-lookup"><span data-stu-id="b468e-211">If the error occurs during script execution or is a parsing error, PowerShell returns a multiline error message that contains the error, a pointer and error message showing where the error is in that line.</span></span> <span data-ttu-id="b468e-212">如果终端不支持 ANSI 颜色转义序列 (VT100)，则不会显示颜色。</span><span class="sxs-lookup"><span data-stu-id="b468e-212">If the terminal doesn't support ANSI color escape sequences (VT100), then colors are not displayed.</span></span>

![脚本中的错误显示](./media/What-s-New-in-PowerShell-70/myscript-error.png)

<span data-ttu-id="b468e-214">PowerShell 7 中的默认视图是 ConciseView  。</span><span class="sxs-lookup"><span data-stu-id="b468e-214">The default view in PowerShell 7 is **ConciseView**.</span></span> <span data-ttu-id="b468e-215">上一个默认视图是 NormalView  ，通过设置首选项变量 `$ErrorView` 可供用户选择。</span><span class="sxs-lookup"><span data-stu-id="b468e-215">The previous default view was **NormalView** and is user selectable by setting the preference variable `$ErrorView`.</span></span>

```powershell
$ErrorView = 'NormalView' # Sets the error view to NormalView
$ErrorView = 'ConciseView' # Sets the error view to ConciseView
```

> [!NOTE]
> <span data-ttu-id="b468e-216">向 `$Host.PrivateData` 添加新属性 ErrorAccentColor，以支持更改错误消息的主题色  。</span><span class="sxs-lookup"><span data-stu-id="b468e-216">A new property **ErrorAccentColor** is added to `$Host.PrivateData` to support changing the accent color of the error message.</span></span>

<span data-ttu-id="b468e-217">新 cmdlet `Get-Error` 在需要时提供完全限定的错误的完整详细视图。</span><span class="sxs-lookup"><span data-stu-id="b468e-217">A new cmdlet `Get-Error` provides complete detailed view of the fully qualified error when desired.</span></span>
<span data-ttu-id="b468e-218">默认情况下，该 cmdlet 将显示所发生的最后一个错误的完整详细信息（包括内部异常）。</span><span class="sxs-lookup"><span data-stu-id="b468e-218">By default the cmdlet displays the full details, including inner exceptions, of the last error that occurred.</span></span>

![Get-Error 中的显示](./media/What-s-New-in-PowerShell-70/myscript-geterror.png)

<span data-ttu-id="b468e-220">`Get-Error` cmdlet 使用内置变量 `$Error` 支持来自管道的输入。</span><span class="sxs-lookup"><span data-stu-id="b468e-220">The `Get-Error` cmdlet supports input from the pipeline using the built-in variable `$Error`.</span></span>
<span data-ttu-id="b468e-221">`Get-Error` 显示所有管道错误。</span><span class="sxs-lookup"><span data-stu-id="b468e-221">`Get-Error` displays all piped errors.</span></span>

```powershell
$Error | Get-Error
```

<span data-ttu-id="b468e-222">`Get-Error` cmdlet 支持最新参数，允许你指定当前会话中要显示的错误数  。</span><span class="sxs-lookup"><span data-stu-id="b468e-222">The `Get-Error` cmdlet supports the **Newest** parameter, allowing you to specify how many errors from the current session you wish displayed.</span></span>

```powershell
Get-Error -Newest 3 # Displays the lst three errors that occurred in the session
```

<span data-ttu-id="b468e-223">有关 [Get-Error](/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7) 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="b468e-223">For more information about [Get-Error](/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7).</span></span>

## <a name="new-version-notification"></a><span data-ttu-id="b468e-224">新版本通知</span><span class="sxs-lookup"><span data-stu-id="b468e-224">New version notification</span></span>

<span data-ttu-id="b468e-225">PowerShell 7 使用更新通知提醒用户是否存在 PowerShell 更新。</span><span class="sxs-lookup"><span data-stu-id="b468e-225">PowerShell 7 uses update notifications to alert users to the existence of updates to PowerShell.</span></span>
<span data-ttu-id="b468e-226">PowerShell 每天查询一次联机服务，以确定是否提供较新版本。</span><span class="sxs-lookup"><span data-stu-id="b468e-226">Once per day, PowerShell queries an online service to determine if a newer version is available.</span></span>

> [!NOTE]
> <span data-ttu-id="b468e-227">在给定的 24 小时内的第一次会话期间进行更新检查。</span><span class="sxs-lookup"><span data-stu-id="b468e-227">The update check happens during the first session in a given 24-hour period.</span></span> <span data-ttu-id="b468e-228">出于性能原因，更新检查将在会话开始后的 3 秒内启动。</span><span class="sxs-lookup"><span data-stu-id="b468e-228">For performance reasons, the update check starts 3 seconds after the session begins.</span></span> <span data-ttu-id="b468e-229">通知仅在后续会话开始时显示。</span><span class="sxs-lookup"><span data-stu-id="b468e-229">The notification is shown only on the start of subsequent sessions.</span></span>

<span data-ttu-id="b468e-230">默认情况下，PowerShell 订阅两个不同通知通道之一，具体取决于其版本/分支。</span><span class="sxs-lookup"><span data-stu-id="b468e-230">By default, PowerShell subscribes to one of two different notification channels depending on its version/branch.</span></span> <span data-ttu-id="b468e-231">受支持的正式发布 (GA) 版 PowerShell 仅返回已更新 GA 版本的通知。</span><span class="sxs-lookup"><span data-stu-id="b468e-231">Supported, Generally Available (GA) versions of PowerShell only return notifications for updated GA releases.</span></span> <span data-ttu-id="b468e-232">预览版和候选发布 (RC) 版本会通知预览版、RC 和 GA 版本的更新。</span><span class="sxs-lookup"><span data-stu-id="b468e-232">Preview and Release Candidate (RC) releases notify of updates to preview, RC, and GA releases.</span></span>

<span data-ttu-id="b468e-233">可以使用 `$Env:POWERSHELL_UPDATECHECK` 环境变量更改更新通知行为。</span><span class="sxs-lookup"><span data-stu-id="b468e-233">The update notification behavior can be changed using the `$Env:POWERSHELL_UPDATECHECK` environment variable.</span></span> <span data-ttu-id="b468e-234">支持以下值：</span><span class="sxs-lookup"><span data-stu-id="b468e-234">The following values are supported:</span></span>

- <span data-ttu-id="b468e-235">“默认”即与不定义 `$Env:POWERSHELL_UPDATECHECK` 相同 </span><span class="sxs-lookup"><span data-stu-id="b468e-235">**Default** is the same as not defining `$Env:POWERSHELL_UPDATECHECK`</span></span>
  - <span data-ttu-id="b468e-236">GA 版本通知 GA 版本的更新</span><span class="sxs-lookup"><span data-stu-id="b468e-236">GA releases notify of updates to GA releases</span></span>
  - <span data-ttu-id="b468e-237">预览版/RC 版本通知 GA 版本和预览版的更新</span><span class="sxs-lookup"><span data-stu-id="b468e-237">Preview/RC releases notify of updates to GA and preview releases</span></span>
- <span data-ttu-id="b468e-238"> “关闭”即关闭更新通知功能</span><span class="sxs-lookup"><span data-stu-id="b468e-238">**Off** turns off the update notification feature</span></span>
- <span data-ttu-id="b468e-239"> “LTS”仅通知长期服务 (LTS) GA 版本的更新</span><span class="sxs-lookup"><span data-stu-id="b468e-239">**LTS** only notifies of updates to long-term-servicing (LTS) GA releases</span></span>

> [!NOTE]
> <span data-ttu-id="b468e-240">环境变量 `$Env:POWERSHELL_UPDATECHECK` 在首次设置之前不存在。</span><span class="sxs-lookup"><span data-stu-id="b468e-240">The environment variable `$Env:POWERSHELL_UPDATECHECK` does not exist until it is set for the first time.</span></span>

<span data-ttu-id="b468e-241">若要仅为 `LTS` 版本设置版本通知，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="b468e-241">To set the version notification for `LTS` releases only:</span></span>

```powershell
$Env:POWERSHELL_UPDATECHECK = 'LTS'
```

<span data-ttu-id="b468e-242">若要为 `Default` 行为设置版本通知，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="b468e-242">To set the version notification to the `Default` behavior:</span></span>

```powershell
$Env:POWERSHELL_UPDATECHECK = 'Default'
```

<span data-ttu-id="b468e-243">有关[关于更新通知](/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="b468e-243">For more information [About Update Notifications](/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7).</span></span>

## <a name="new-dsc-resource-support-with-invoke-dscresource-experimental"></a><span data-ttu-id="b468e-244">使用 Invoke-DSCResource 的新 DSC 资源支持（实验性）</span><span class="sxs-lookup"><span data-stu-id="b468e-244">New DSC Resource support with Invoke-DSCResource (Experimental)</span></span>

> [!NOTE]
> <span data-ttu-id="b468e-245">这是名为 PSDesiredStateConfiguration.InvokeDscResource 的实验性功能  。</span><span class="sxs-lookup"><span data-stu-id="b468e-245">This is an experimental feature named **PSDesiredStateConfiguration.InvokeDscResource**.</span></span> <span data-ttu-id="b468e-246">了解[关于实验性功能](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="b468e-246">Learn more [About Experimental Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).</span></span>

<span data-ttu-id="b468e-247">`Invoke-DscResource` cmdlet 运行指定的 PowerShell 所需状态配置 (DSC) 资源的方法。</span><span class="sxs-lookup"><span data-stu-id="b468e-247">The `Invoke-DscResource` cmdlet runs a method of a specified PowerShell Desired State Configuration (DSC) resource.</span></span>

<span data-ttu-id="b468e-248">此 cmdlet 直接调用 DSC 资源，而无需创建配置文档。</span><span class="sxs-lookup"><span data-stu-id="b468e-248">This cmdlet invokes a DSC resource directly, without creating a configuration document.</span></span> <span data-ttu-id="b468e-249">使用此 cmdlet，配置管理产品可以使用 DSC 资源来管理 Windows 或 Linux。</span><span class="sxs-lookup"><span data-stu-id="b468e-249">Using this cmdlet, configuration management products can manage Windows or Linux by using DSC resources.</span></span> <span data-ttu-id="b468e-250">在启用调试的情况下运行 DSC 引擎时，此 cmdlet 还可用于调试资源。</span><span class="sxs-lookup"><span data-stu-id="b468e-250">This cmdlet also enables debugging of resources when the DSC engine is running with debugging enabled.</span></span>

<span data-ttu-id="b468e-251">此命令调用名为“Log”的资源的 Set 方法，并指定 Message 属性   。</span><span class="sxs-lookup"><span data-stu-id="b468e-251">This command invokes the **Set** method of a resource named Log and specifies a **Message** property.</span></span>

```powershell
Invoke-DscResource -Name Log -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Message = 'Hello World'
}
```

<span data-ttu-id="b468e-252">有关 [Invoke-DSCResource](/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7) 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="b468e-252">For more information about [Invoke-DSCResource](/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7).</span></span>

## <a name="breaking-changes-and-improvements"></a><span data-ttu-id="b468e-253">重大更改和改进</span><span class="sxs-lookup"><span data-stu-id="b468e-253">Breaking Changes and Improvements</span></span>

### <a name="breaking-changes"></a><span data-ttu-id="b468e-254">重大更改</span><span class="sxs-lookup"><span data-stu-id="b468e-254">Breaking Changes</span></span>

- <span data-ttu-id="b468e-255">使更新通知支持 LTS 和默认通道 (#11132)</span><span class="sxs-lookup"><span data-stu-id="b468e-255">Make update notification support LTS and default channels (#11132)</span></span>
- <span data-ttu-id="b468e-256">更新 Test-Connection，使其工作方式更类似于 Windows PowerShell 中的命令 (#10697)（感谢 @vexx32！）</span><span class="sxs-lookup"><span data-stu-id="b468e-256">Update Test-Connection to work more like the one in Windows PowerShell (#10697) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="b468e-257">保留 $?</span><span class="sxs-lookup"><span data-stu-id="b468e-257">Preserve $?</span></span> <span data-ttu-id="b468e-258">对于 ParenExpression、SubExpression 和 ArrayExpression (#11040)</span><span class="sxs-lookup"><span data-stu-id="b468e-258">for ParenExpression, SubExpression and ArrayExpression (#11040)</span></span>
- <span data-ttu-id="b468e-259">在 Start-Job 中将工作目录设置为当前目录 (#10920)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-259">Set working directory to current directory in Start-Job (#10920) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="b468e-260">使 $PSCulture 一致地反映会话中区域性更改 (#10138)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-260">Make $PSCulture consistently reflect in-session culture changes (#10138) (Thanks @iSazonov!)</span></span>

### <a name="engine-updates-and-fixes"></a><span data-ttu-id="b468e-261">引擎更新和修补程序</span><span class="sxs-lookup"><span data-stu-id="b468e-261">Engine Updates and Fixes</span></span>

- <span data-ttu-id="b468e-262">远程方案的断点 API 的改进 (#11312)</span><span class="sxs-lookup"><span data-stu-id="b468e-262">Improvements in breakpoint APIs for remote scenarios (#11312)</span></span>
- <span data-ttu-id="b468e-263">修复泄漏到其他运行空间的 PowerShell 类定义 (#11273)</span><span class="sxs-lookup"><span data-stu-id="b468e-263">Fix PowerShell class definition leaking into another Runspace (#11273)</span></span>
- <span data-ttu-id="b468e-264">修复由 7.0.0-Preview1 中添加的 FirstOrDefault 基元引起的格式设置回归 (#11258)</span><span class="sxs-lookup"><span data-stu-id="b468e-264">Fix a regression in formatting caused by the FirstOrDefault primitive added in 7.0.0-Preview1 (#11258)</span></span>
- <span data-ttu-id="b468e-265">要在 PS7 遥测中跟踪的其他 Microsoft 模块 (#10751)</span><span class="sxs-lookup"><span data-stu-id="b468e-265">Additional Microsoft Modules to track in PS7 Telemetry (#10751)</span></span>
- <span data-ttu-id="b468e-266">使已批准的功能成为非实验性功能 (#11303)</span><span class="sxs-lookup"><span data-stu-id="b468e-266">Make approved features non-experimental (#11303)</span></span>
- <span data-ttu-id="b468e-267">更新 ConciseView 以使用 TargetObject（如果适用）(#11075)</span><span class="sxs-lookup"><span data-stu-id="b468e-267">Update ConciseView to use TargetObject if applicable (#11075)</span></span>
- <span data-ttu-id="b468e-268">修复 CompletionCompleters 公共方法中的 NullReferenceException (#11274)</span><span class="sxs-lookup"><span data-stu-id="b468e-268">Fix NullReferenceException in CompletionCompleters public methods (#11274)</span></span>
- <span data-ttu-id="b468e-269">修复非 Windows 平台上的单元线程状态检查 (#11301)</span><span class="sxs-lookup"><span data-stu-id="b468e-269">Fix apartment thread state check on non-Windows platforms (#11301)</span></span>
- <span data-ttu-id="b468e-270">更新设置 PSModulePath 以连接进程和计算机环境变量 (#11276)</span><span class="sxs-lookup"><span data-stu-id="b468e-270">Update setting PSModulePath to concatenate the process and machine environment variables (#11276)</span></span>
- <span data-ttu-id="b468e-271">将 .NET Core 升级到 3.1.0 (#11260)</span><span class="sxs-lookup"><span data-stu-id="b468e-271">Bump .NET Core to 3.1.0 (#11260)</span></span>
- <span data-ttu-id="b468e-272">修复 $env:PATH 前面的 $PSHOME 检测 (#11141)</span><span class="sxs-lookup"><span data-stu-id="b468e-272">Fix detection of $PSHOME in front of $env:PATH (#11141)</span></span>
- <span data-ttu-id="b468e-273">允许 pwsh 继承 $env:PSModulePath 并允许 powershell.exe 正确启动 (#11057)</span><span class="sxs-lookup"><span data-stu-id="b468e-273">Allow pwsh to inherit $env:PSModulePath and enable powershell.exe to start correctly (#11057)</span></span>
- <span data-ttu-id="b468e-274">迁移到 .NET Core 3.1 预览版 1 (#10798)</span><span class="sxs-lookup"><span data-stu-id="b468e-274">Move to .NET Core 3.1 preview 1 (#10798)</span></span>
- <span data-ttu-id="b468e-275">在文件系统提供程序中重构重新分析标记检查 (#10431)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-275">Refactor reparse tag checks in file system provider (#10431) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="b468e-276">将 CR 和新行替换为脚本日志记录中的 0x23CE 字符 (#10616)</span><span class="sxs-lookup"><span data-stu-id="b468e-276">Replace CR and new line with a 0x23CE character in script logging (#10616)</span></span>
- <span data-ttu-id="b468e-277">通过从 AppDomain.CurrentDomain.ProcessExit 中取消注册事件处理程序来修复资源泄漏 (#10626)</span><span class="sxs-lookup"><span data-stu-id="b468e-277">Fix a resource leak by unregistering the event handler from AppDomain.CurrentDomain.ProcessExit (#10626)</span></span>
- <span data-ttu-id="b468e-278">添加对 ActionPreference.Break 的支持，以便在生成调试、错误、信息、进度、详细消息或警告消息时中断以进入调试程序 (#8205)（感谢 @KirkMunro！）</span><span class="sxs-lookup"><span data-stu-id="b468e-278">Add support to ActionPreference.Break to break into debugger when Debug, Error, Information, Progress, Verbose or Warning messages are generated (#8205) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="b468e-279">允许在 PowerShell Core 内启用控制面板加载项，而无需指定 .CPL 扩展。</span><span class="sxs-lookup"><span data-stu-id="b468e-279">Enable starting control panel add-ins within PowerShell Core without specifying .CPL extension.</span></span> <span data-ttu-id="b468e-280">(#9828)</span><span class="sxs-lookup"><span data-stu-id="b468e-280">(#9828)</span></span>

### <a name="general-cmdlet-updates-and-fixes"></a><span data-ttu-id="b468e-281">常规 Cmdlet 更新和修补程序</span><span class="sxs-lookup"><span data-stu-id="b468e-281">General Cmdlet Updates and Fixes</span></span>

- <span data-ttu-id="b468e-282">修复 Raspbian 上有关 UnixStat 实验性功能中设置文件更改日期的问题 (#11313)</span><span class="sxs-lookup"><span data-stu-id="b468e-282">Fix for issue on Raspbian for setting date of file changes in UnixStat Experimental Feature (#11313)</span></span>
- <span data-ttu-id="b468e-283">将 -AsPlainText 添加到 ConvertFrom-SecureString (#11142)</span><span class="sxs-lookup"><span data-stu-id="b468e-283">Add -AsPlainText to ConvertFrom-SecureString (#11142)</span></span>
- <span data-ttu-id="b468e-284">为 WinCompat 添加了 WindowsPS 版本检查 (#11148)</span><span class="sxs-lookup"><span data-stu-id="b468e-284">Added WindowsPS version check for WinCompat (#11148)</span></span>
- <span data-ttu-id="b468e-285">修复某些 WinCompat 方案中的错误报告 (#11259)</span><span class="sxs-lookup"><span data-stu-id="b468e-285">Fix error-reporting in some WinCompat scenarios (#11259)</span></span>
- <span data-ttu-id="b468e-286">添加本机二进制解析程序 (#11032)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-286">Add native binary resolver (#11032) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="b468e-287">更新字符宽度的计算以正确遵循 CJK 字符 (#11262)</span><span class="sxs-lookup"><span data-stu-id="b468e-287">Update calculation of char width to respect CJK chars correctly (#11262)</span></span>
- <span data-ttu-id="b468e-288">添加适用于 macOS 的 Unblock-File (#11137)</span><span class="sxs-lookup"><span data-stu-id="b468e-288">Add Unblock-File for macOS (#11137)</span></span>
- <span data-ttu-id="b468e-289">修复 Get-PSCallStack 中的回归 (#11210)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-289">Fix regression in Get-PSCallStack (#11210) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="b468e-290">使用作业 cmdlet 时删除 ScheduledJob 模块的自动加载 (#11194)</span><span class="sxs-lookup"><span data-stu-id="b468e-290">Remove autoloading of the ScheduledJob module when using Job cmdlets (#11194)</span></span>
- <span data-ttu-id="b468e-291">将 OutputType 添加到 Get-Error cmdlet 并保留原始类型名称 (#10856)</span><span class="sxs-lookup"><span data-stu-id="b468e-291">Add OutputType to Get-Error cmdlet and preserve original typenames (#10856)</span></span>
- <span data-ttu-id="b468e-292">修复 SupportsVirtualTerminal 属性中的空引用 (#11105)</span><span class="sxs-lookup"><span data-stu-id="b468e-292">Fix null reference in SupportsVirtualTerminal property (#11105)</span></span>
- <span data-ttu-id="b468e-293">在 Get-WinEvent 中添加限制检查 (#10648)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-293">Add limit check in Get-WinEvent (#10648) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="b468e-294">修复命令运行时，以便 StopUpstreamCommandsException 不会填充到 -ErrorVariable 中 (#10840)</span><span class="sxs-lookup"><span data-stu-id="b468e-294">Fix command runtime so StopUpstreamCommandsException doesn't get populated in -ErrorVariable (#10840)</span></span>
- <span data-ttu-id="b468e-295">将本机命令的输出编码设置为 [Console]::OutputEncoding (#10824)</span><span class="sxs-lookup"><span data-stu-id="b468e-295">Set the output encoding to [Console]::OutputEncoding for native commands (#10824)</span></span>
- <span data-ttu-id="b468e-296">支持示例中的多行代码块 (#10776)（感谢 @Greg-Smulko！）</span><span class="sxs-lookup"><span data-stu-id="b468e-296">Support multi-line code blocks in examples (#10776) (Thanks @Greg-Smulko!)</span></span>
- <span data-ttu-id="b468e-297">将 Culture 参数添加到 Select-String cmdlet (#10943)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-297">Add Culture parameter to Select-String cmdlet (#10943) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="b468e-298">修复带有尾随反斜杠的 Start-Job 工作目录路径 (#11041)</span><span class="sxs-lookup"><span data-stu-id="b468e-298">Fix Start-Job working directory path with trailing backslash (#11041)</span></span>
- <span data-ttu-id="b468e-299">ConvertFrom-Json：默认展开集合 (#10861)（感谢 @danstur！）</span><span class="sxs-lookup"><span data-stu-id="b468e-299">ConvertFrom-Json: Unwrap collections by default (#10861) (Thanks @danstur!)</span></span>
- <span data-ttu-id="b468e-300">将 Group-Object cmdlet 的区分大小写的哈希表与 -CaseSensitive 和 -AsHashtable 开关一起使用 (#11030)（感谢 @vexx32！）</span><span class="sxs-lookup"><span data-stu-id="b468e-300">Use case-sensitive Hashtable for Group-Object cmdlet with -CaseSensitive and -AsHashtable switches (#11030) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="b468e-301">如果在重新生成路径以具有正确的大小写时未能枚举文件，则处理异常 (#11014)</span><span class="sxs-lookup"><span data-stu-id="b468e-301">Handle exception if enumerating files fails when rebuilding path to have correct casing (#11014)</span></span>
- <span data-ttu-id="b468e-302">修复 ConciseView 以显示活动，而不是 myCommand (#11007)</span><span class="sxs-lookup"><span data-stu-id="b468e-302">Fix ConciseView to show Activity instead of myCommand (#11007)</span></span>
- <span data-ttu-id="b468e-303">允许 Web cmdlet 忽略 HTTP 错误状态 (#10466)（感谢 @vdamewood！）</span><span class="sxs-lookup"><span data-stu-id="b468e-303">Allow web cmdlets to ignore HTTP error statuses (#10466) (Thanks @vdamewood!)</span></span>
- <span data-ttu-id="b468e-304">修复多个 CommandInfo 到 Get-Command 的管道传递 (#10929)</span><span class="sxs-lookup"><span data-stu-id="b468e-304">Fix piping of more than one CommandInfo to Get-Command (#10929)</span></span>
- <span data-ttu-id="b468e-305">重新添加适用于 Windows 的 Get-Counter cmdlet (#10933)</span><span class="sxs-lookup"><span data-stu-id="b468e-305">Add back Get-Counter cmdlet for Windows (#10933)</span></span>
- <span data-ttu-id="b468e-306">使 ConvertTo-Json 将 [AutomationNull]::Value 和 [NullString]::Value 视为 $null (#10957)</span><span class="sxs-lookup"><span data-stu-id="b468e-306">Make ConvertTo-Json treat [AutomationNull]::Value and [NullString]::Value as $null (#10957)</span></span>
- <span data-ttu-id="b468e-307">删除 ipv6 地址中的括号以进行 SSH 远程处理 (#10968)</span><span class="sxs-lookup"><span data-stu-id="b468e-307">Remove brackets from ipv6 address for SSH remoting (#10968)</span></span>
- <span data-ttu-id="b468e-308">修复发送到 pwsh 的命令只是空白时发生的崩溃 (#10977)</span><span class="sxs-lookup"><span data-stu-id="b468e-308">Fix crash if command sent to pwsh is just whitespace (#10977)</span></span>
- <span data-ttu-id="b468e-309">添加了跨平台 Get-Clipboard 和 Set-Clipboard (#10340)</span><span class="sxs-lookup"><span data-stu-id="b468e-309">Added cross-platform Get-Clipboard and Set-Clipboard (#10340)</span></span>
- <span data-ttu-id="b468e-310">修复文件系统对象原始路径的设置，使其不包含额外的尾随反斜杠 (#10959)</span><span class="sxs-lookup"><span data-stu-id="b468e-310">Fix setting original path of filesystem object to not have extra trailing slash (#10959)</span></span>
- <span data-ttu-id="b468e-311">支持 ConvertTo-Json 为 $null (#10947)</span><span class="sxs-lookup"><span data-stu-id="b468e-311">Support $null for ConvertTo-Json (#10947)</span></span>
- <span data-ttu-id="b468e-312">在 Windows 上重新添加 Out-Printer 命令 (#10906)</span><span class="sxs-lookup"><span data-stu-id="b468e-312">Add back Out-Printer command on Windows (#10906)</span></span>
- <span data-ttu-id="b468e-313">修复包含空格的 Start-Job -WorkingDirectory (#10951)</span><span class="sxs-lookup"><span data-stu-id="b468e-313">Fix Start-Job -WorkingDirectory with whitespace (#10951)</span></span>
- <span data-ttu-id="b468e-314">为 PSConfiguration.cs 中的设置获取 null 时返回默认值 (#10963)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-314">Return default value when getting null for a setting in PSConfiguration.cs (#10963) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="b468e-315">将 IO 异常处理为非终止 (#10950)</span><span class="sxs-lookup"><span data-stu-id="b468e-315">Handle IO exception as non-terminating (#10950)</span></span>
- <span data-ttu-id="b468e-316">添加 GraphicalHost 程序集，以启用 Out-GridView、Show-Command 和 Get-Help -ShowWindow (#10899)</span><span class="sxs-lookup"><span data-stu-id="b468e-316">Add GraphicalHost assembly to enable Out-GridView, Show-Command, and Get-Help -ShowWindow (#10899)</span></span>
- <span data-ttu-id="b468e-317">在 Get-HotFix 中通过管道获取 ComputerName (#10852)（感谢 @kvprasoon！）</span><span class="sxs-lookup"><span data-stu-id="b468e-317">Take ComputerName via pipeline in Get-HotFix (#10852) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="b468e-318">修复参数的 Tab 自动补全，以便其将公共参数显示为可用 (#10850)</span><span class="sxs-lookup"><span data-stu-id="b468e-318">Fix tab completion for parameters so that it shows common parameters as available (#10850)</span></span>
- <span data-ttu-id="b468e-319">修复 GetCorrectCasedPath() 以首先检查是否在调用 First() 之前返回了任何系统文件条目 (#10930)</span><span class="sxs-lookup"><span data-stu-id="b468e-319">Fix GetCorrectCasedPath() to first check if any system file entries is returned before calling First() (#10930)</span></span>
- <span data-ttu-id="b468e-320">在 Start-Job 中将工作目录设置为当前目录 (#10920)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-320">Set working directory to current directory in Start-Job (#10920) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="b468e-321">将 TabExpansion2 更改为不需要 -CursorColumn 并将其视为 $InputScript.Length (#10849)</span><span class="sxs-lookup"><span data-stu-id="b468e-321">Change TabExpansion2 to not require -CursorColumn and treat as $InputScript.Length (#10849)</span></span>
- <span data-ttu-id="b468e-322">处理主机不返回屏幕的行或列的情况 (#10938)</span><span class="sxs-lookup"><span data-stu-id="b468e-322">Handle case where Host may not return Rows or Columns of screen (#10938)</span></span>
- <span data-ttu-id="b468e-323">修复在不支持主题色的主机上使用主题色的问题 (#10937)</span><span class="sxs-lookup"><span data-stu-id="b468e-323">Fix use of accent colors for hosts that don't support them (#10937)</span></span>
- <span data-ttu-id="b468e-324">重新添加 Update-List 命令 (#10922)</span><span class="sxs-lookup"><span data-stu-id="b468e-324">Add back Update-List command (#10922)</span></span>
- <span data-ttu-id="b468e-325">更新 Clear-RecycleBin 的 FWLink Id (#10925)</span><span class="sxs-lookup"><span data-stu-id="b468e-325">Update FWLink Id for Clear-RecycleBin (#10925)</span></span>
- <span data-ttu-id="b468e-326">在 Tab 自动补全期间，如果无法读取文件属性，则跳过文件 (#10910)</span><span class="sxs-lookup"><span data-stu-id="b468e-326">During tab completion, skip file if can't read file attributes (#10910)</span></span>
- <span data-ttu-id="b468e-327">重新添加适用于 Windows 的 Clear-RecycleBin (#10909)</span><span class="sxs-lookup"><span data-stu-id="b468e-327">Add back Clear-RecycleBin for Windows (#10909)</span></span>
- <span data-ttu-id="b468e-328">添加 `$env:__SuppressAnsiEscapeSequences` 以控制是否在输出中包含 VT 转义序列 (#10814)</span><span class="sxs-lookup"><span data-stu-id="b468e-328">Add `$env:__SuppressAnsiEscapeSequences` to control whether to have VT escape sequence in output (#10814)</span></span>
- <span data-ttu-id="b468e-329">添加 -NoEmphasize 参数来为 Select-String 输出着色 (#8963)（感谢 @derek-xia！）</span><span class="sxs-lookup"><span data-stu-id="b468e-329">Add -NoEmphasize parameter to colorize Select-String output (#8963) (Thanks @derek-xia!)</span></span>
- <span data-ttu-id="b468e-330">重新添加 Get-HotFix cmdlet (#10740)</span><span class="sxs-lookup"><span data-stu-id="b468e-330">Add back Get-HotFix cmdlet (#10740)</span></span>
- <span data-ttu-id="b468e-331">使 Add-Type 可用于托管 PowerShell 的应用程序 (#10587)</span><span class="sxs-lookup"><span data-stu-id="b468e-331">Make Add-Type usable in applications that host PowerShell (#10587)</span></span>
- <span data-ttu-id="b468e-332">在 LanguagePrimitives.IsNullLike() 中使用更有效的计算顺序 (#10781)（感谢 @vexx32！）</span><span class="sxs-lookup"><span data-stu-id="b468e-332">Use more effective evaluation order in LanguagePrimitives.IsNullLike() (#10781) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="b468e-333">在 Format-Hex 中改进对混合集合管道输入和输入管道流的处理 (#8674)（感谢 @vexx32！）</span><span class="sxs-lookup"><span data-stu-id="b468e-333">Improve handling of mixed-collection piped input and piped streams of input in Format-Hex (#8674) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="b468e-334">当值与预期类型不匹配时，在 SSHConnection 哈希表中使用类型转换 (#10720)（感谢 @SeeminglyScience！）</span><span class="sxs-lookup"><span data-stu-id="b468e-334">Use type conversion in SSHConnection hashtables when value doesn't match expected type (#10720) (Thanks @SeeminglyScience!)</span></span>
- <span data-ttu-id="b468e-335">修复在设置 -TotalCount 时的 Get-Content -ReadCount 0 行为 (#10749)（感谢 @eugenesmlv！）</span><span class="sxs-lookup"><span data-stu-id="b468e-335">Fix Get-Content -ReadCount 0 behavior when -TotalCount is set (#10749) (Thanks @eugenesmlv!)</span></span>
- <span data-ttu-id="b468e-336">在 Get-WinEvent 中改写“拒绝访问”错误消息 (#10639)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-336">Reword access denied error message in Get-WinEvent (#10639) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="b468e-337">为枚举或类型受约束的变量赋值启用 Tab 自动补全 (#10646)</span><span class="sxs-lookup"><span data-stu-id="b468e-337">Enable tab completion for variable assignment that is enum or type constrained (#10646)</span></span>
- <span data-ttu-id="b468e-338">删除导致格式设置问题的未使用的 SourceLength 远程处理属性 (#10765)</span><span class="sxs-lookup"><span data-stu-id="b468e-338">Remove unused SourceLength remoting property causing formatting issues (#10765)</span></span>
- <span data-ttu-id="b468e-339">将 -Delimiter 参数添加到 ConvertFrom-StringData (#10665)（感谢 @steviecoaster！）</span><span class="sxs-lookup"><span data-stu-id="b468e-339">Add -Delimiter parameter to ConvertFrom-StringData (#10665) (Thanks @steviecoaster!)</span></span>
- <span data-ttu-id="b468e-340">将 Invoke-Command 与 SSH 配合使用时，为 ScriptBlock 添加位置参数 (#10721)（感谢 @machgo！）</span><span class="sxs-lookup"><span data-stu-id="b468e-340">Add positional parameter for ScriptBlock when using Invoke-Command with SSH (#10721) (Thanks @machgo!)</span></span>
- <span data-ttu-id="b468e-341">如果 ConciseView 有多个行但没有脚本名称，则显示行上下文信息 (#10746)</span><span class="sxs-lookup"><span data-stu-id="b468e-341">Show line context information if multiple lines but no script name for ConciseView (#10746)</span></span>
- <span data-ttu-id="b468e-342">添加对文件系统提供程序的 \\wsl$\ 路径的支持 (#10674)</span><span class="sxs-lookup"><span data-stu-id="b468e-342">Add support for \\wsl$\ paths to file system provider (#10674)</span></span>
- <span data-ttu-id="b468e-343">在分析器中添加 TokenKind.QuestionMark 的缺失令牌文本 (#10706)</span><span class="sxs-lookup"><span data-stu-id="b468e-343">Add the missing token text for TokenKind.QuestionMark in parser (#10706)</span></span>
- <span data-ttu-id="b468e-344">将每个 ForEach-Object -Parallel 运行脚本的当前工作目录设置为调用脚本的同一位置。</span><span class="sxs-lookup"><span data-stu-id="b468e-344">Set current working directory of each ForEach-Object -Parallel running script to the same location as the calling script.</span></span> <span data-ttu-id="b468e-345">(#10672)</span><span class="sxs-lookup"><span data-stu-id="b468e-345">(#10672)</span></span>
- <span data-ttu-id="b468e-346">将 api-ms-win-core-file-l1-2-2.dll 替换为 FindFirstStreamW 和 FindNextStreamW API 的 Kernell32.dll (#10680)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-346">Replace api-ms-win-core-file-l1-2-2.dll with Kernell32.dll for FindFirstStreamW and FindNextStreamW APIs (#10680) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="b468e-347">调整帮助格式设置脚本，使其提高 StrictMode 容限 (#10563)</span><span class="sxs-lookup"><span data-stu-id="b468e-347">Tweak help formatting script to be more StrictMode tolerant (#10563)</span></span>
- <span data-ttu-id="b468e-348">将 -SecurityDescriptorSDDL 参数添加到 New-Service (#10483)（感谢 @kvprasoon！）</span><span class="sxs-lookup"><span data-stu-id="b468e-348">Add -SecurityDescriptorSDDL parameter to New-Service (#10483) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="b468e-349">删除信息性输出，合并 Test-Connection 中的 ping 使用情况 (#10478)（感谢 @vexx32！）</span><span class="sxs-lookup"><span data-stu-id="b468e-349">Remove informational output, consolidate ping usage in Test-Connection (#10478) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="b468e-350">读取特殊重新分析点，而不访问它们 (#10662)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-350">Read special reparse points without accessing them (#10662) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="b468e-351">将 Clear-Host 输出定向到终端 (#10681)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-351">Direct Clear-Host output to terminal (#10681) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="b468e-352">添加向后换行符以使用 Format-Table 和 -Property 进行分组 (#10653)</span><span class="sxs-lookup"><span data-stu-id="b468e-352">Add back newline for grouping with Format-Table and -Property (#10653)</span></span>
- <span data-ttu-id="b468e-353">从 Get-Random 上的 -InputObject 中删除 [ValidateNotNullOrEmpty] 以允许使用空字符串 (#10644)</span><span class="sxs-lookup"><span data-stu-id="b468e-353">Remove [ValidateNotNullOrEmpty] from -InputObject on Get-Random to allow empty string (#10644)</span></span>
- <span data-ttu-id="b468e-354">使建议系统字符串距离算法不区分大小写 (#10549)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-354">Make suggestion system string distance algorithm case-insensitive (#10549) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="b468e-355">修复 ForEach-Object -Parallel 输入处理中的 null 引用异常 (#10577)</span><span class="sxs-lookup"><span data-stu-id="b468e-355">Fix null reference exception in ForEach-Object -Parallel input processing (#10577)</span></span>
- <span data-ttu-id="b468e-356">添加 PowerShell Core 组策略定义 (#10468)</span><span class="sxs-lookup"><span data-stu-id="b468e-356">Add PowerShell Core group policy definitions (#10468)</span></span>
- <span data-ttu-id="b468e-357">更新控制台主机以支持用于可组合性方案的 XTPUSHSGR/XTPOPSGR VT 控件序列。</span><span class="sxs-lookup"><span data-stu-id="b468e-357">Update console host to support XTPUSHSGR/XTPOPSGR VT control sequences that are used in composability scenarios.</span></span> <span data-ttu-id="b468e-358">(#10208)</span><span class="sxs-lookup"><span data-stu-id="b468e-358">(#10208)</span></span>
- <span data-ttu-id="b468e-359">将 WorkingDirectory 参数添加到 Start-Job (#10324)（感谢 @davinci26！）</span><span class="sxs-lookup"><span data-stu-id="b468e-359">Add WorkingDirectory parameter to Start-Job (#10324) (Thanks @davinci26!)</span></span>
- <span data-ttu-id="b468e-360">删除导致断点更改被错误地复制到主机运行空间调试程序的事件处理程序 (#10503)（感谢 @KirkMunro！）</span><span class="sxs-lookup"><span data-stu-id="b468e-360">Remove the event handler that was causing breakpoint changes to be erroneously replicated to the host runspace debugger (#10503) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="b468e-361">将 api-ms-win-core-job-12-1-0.dll 替换为 Microsoft.PowerShell.Commands.NativeMethods P/Invoke API 中的 Kernell32.dll (#10417)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-361">Replace api-ms-win-core-job-12-1-0.dll with Kernell32.dll in Microsoft.PowerShell.Commands.NativeMethods P/Invoke API(#10417) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="b468e-362">修复变量赋值和 -OutVariable 中 New-Service 的错误输出 (#10444)（感谢 @kvprasoon！）</span><span class="sxs-lookup"><span data-stu-id="b468e-362">Fix wrong output for New-Service in variable assignment and -OutVariable (#10444) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="b468e-363">修复有关退出代码、命令行参数和带有空格的路径的全局工具问题 (#10461)</span><span class="sxs-lookup"><span data-stu-id="b468e-363">Fix global tool issues around exit code, command line parameters and path with spaces (#10461)</span></span>
- <span data-ttu-id="b468e-364">修复到 OneDrive 的递归 - 更改 FindFirstFileEx() 以使用 SafeFindHandle 类型 (#10405)</span><span class="sxs-lookup"><span data-stu-id="b468e-364">Fix recursion into OneDrive - change FindFirstFileEx() to use SafeFindHandle type (#10405)</span></span>
- <span data-ttu-id="b468e-365">如果 NVDA 屏幕读取器处于活动状态，则跳过在 Windows 上自动加载 PSReadLine (#10385)</span><span class="sxs-lookup"><span data-stu-id="b468e-365">Skip auto-loading PSReadLine on Windows if the NVDA screen reader is active (#10385)</span></span>
- <span data-ttu-id="b468e-366">将 built-with-PowerShell 模块版本增加到 7.0.0.0 (#10356)</span><span class="sxs-lookup"><span data-stu-id="b468e-366">Increase built-with-PowerShell module versions to 7.0.0.0 (#10356)</span></span>
- <span data-ttu-id="b468e-367">如果已存在同名类型，则添加在 Add-Type 中引发错误 (#9609)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-367">Add throwing an error in Add-Type if a type with the same name already exists (#9609) (Thanks @iSazonov!)</span></span>

### <a name="performance"></a><span data-ttu-id="b468e-368">性能</span><span class="sxs-lookup"><span data-stu-id="b468e-368">Performance</span></span>

- <span data-ttu-id="b468e-369">避免在 Parser.SaveError 中使用关闭 (#11006)</span><span class="sxs-lookup"><span data-stu-id="b468e-369">Avoid using closure in Parser.SaveError (#11006)</span></span>
- <span data-ttu-id="b468e-370">改进在创建新的正则表达式实例时的缓存 (#10657)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-370">Improve the caching when creating new Regex instances (#10657) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="b468e-371">改进对 types.ps1xml、typesV3.ps1xml 和 GetEvent.types.ps1xml 中的 PowerShell 内置类型数据的处理 (#10898)</span><span class="sxs-lookup"><span data-stu-id="b468e-371">Improve processing of the PowerShell built-in type data from types.ps1xml, typesV3.ps1xml and GetEvent.types.ps1xml (#10898)</span></span>
- <span data-ttu-id="b468e-372">更新 PSConfiguration.ReadValueFromFile，使其加快运行速度并提高内存效率 (#10839)</span><span class="sxs-lookup"><span data-stu-id="b468e-372">Update PSConfiguration.ReadValueFromFile to make it faster and more memory efficient (#10839)</span></span>
- <span data-ttu-id="b468e-373">添加较小的性能改进以进行运行空间初始化 (#10569)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-373">Add minor performance improvements for runspace initialization (#10569) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="b468e-374">使 ForEach-Object 更快地用于其常用方案 (#10454)，并使用许多运行空间修复 ForEach-Object -Parallel 性能问题 (#10455)</span><span class="sxs-lookup"><span data-stu-id="b468e-374">Make ForEach-Object faster for its commonly used scenarios (#10454) and fix ForEach-Object -Parallel performance problem with many runspaces (#10455)</span></span>

### <a name="code-cleanup"></a><span data-ttu-id="b468e-375">代码清理</span><span class="sxs-lookup"><span data-stu-id="b468e-375">Code Cleanup</span></span>

- <span data-ttu-id="b468e-376">更改注释和元素文本以符合 Microsoft 标准 (#11304)</span><span class="sxs-lookup"><span data-stu-id="b468e-376">Change comment and element text to meet Microsoft standards (#11304)</span></span>
- <span data-ttu-id="b468e-377">清理 Compiler.cs 中的样式问题 (#10368)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-377">Cleanup style issues in Compiler.cs (#10368) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="b468e-378">为 CommaDelimitedStringCollection 删除未使用的类型转换器 (#11000)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-378">Remove the unused type converter for CommaDelimitedStringCollection (#11000) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="b468e-379">清理 InitialSessionState.cs 中的样式 (#10865)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-379">Cleanup style in InitialSessionState.cs (#10865) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="b468e-380">PSSession 类的代码清理 (#11001)</span><span class="sxs-lookup"><span data-stu-id="b468e-380">Code clean up for PSSession class (#11001)</span></span>
- <span data-ttu-id="b468e-381">删除未正常运行的“在首次运行 Get-Help 时运行 Get-Help 中的 Update-Help”功能 (#10974)</span><span class="sxs-lookup"><span data-stu-id="b468e-381">Remove the not-working 'run Update-Help from Get-Help when Get-Help runs for the first time' feature (#10974)</span></span>
- <span data-ttu-id="b468e-382">修复样式问题 (#10998)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-382">Fix style issues (#10998) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="b468e-383">清除：使用内置类型别名 (#10882)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-383">Cleanup: use the built-in type alias (#10882) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="b468e-384">在查询 ExecutionPolicy 设置时删除未使用的设置密钥 ConsolePrompting 并避免创建不必要的字符串 (#10985)</span><span class="sxs-lookup"><span data-stu-id="b468e-384">Remove the unused setting key ConsolePrompting and avoid unnecessary string creation when querying ExecutionPolicy setting (#10985)</span></span>
- <span data-ttu-id="b468e-385">禁用每日生成的更新通知检查 (#10903)（感谢 @bergmeister！）</span><span class="sxs-lookup"><span data-stu-id="b468e-385">Disable update notification check for daily builds (#10903) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="b468e-386">恢复 #10338 中丢失的调试 API (#10808)</span><span class="sxs-lookup"><span data-stu-id="b468e-386">Reinstate debugging API lost in #10338 (#10808)</span></span>
- <span data-ttu-id="b468e-387">删除不再使用的 WorkflowJobSourceAdapter 引用 (#10326)（感谢 @KirkMunro！）</span><span class="sxs-lookup"><span data-stu-id="b468e-387">Remove WorkflowJobSourceAdapter reference that is no longer used (#10326) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="b468e-388">通过修复 PreserveSig 属性清除跳转列表代码中的 COM 接口 (#9899)（感谢 @weltkante！）</span><span class="sxs-lookup"><span data-stu-id="b468e-388">Cleanup COM interfaces in jump list code by fixing PreserveSig attributes (#9899) (Thanks @weltkante!)</span></span>
- <span data-ttu-id="b468e-389">添加描述为何 -ia 不是 -InformationAction 通用参数别名的注释 (#10703)（感谢 @KirkMunro！）</span><span class="sxs-lookup"><span data-stu-id="b468e-389">Add a comment describing why -ia is not the alias for -InformationAction common parameter (#10703) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="b468e-390">将 InvokeCommandCmdlet.cs 重命名为 InvokeExpressionCommand.cs (#10659)（感谢 @kilasuit！）</span><span class="sxs-lookup"><span data-stu-id="b468e-390">Rename InvokeCommandCmdlet.cs to InvokeExpressionCommand.cs (#10659) (Thanks @kilasuit!)</span></span>
- <span data-ttu-id="b468e-391">添加与更新通知相关的细微代码清理 (#10698)</span><span class="sxs-lookup"><span data-stu-id="b468e-391">Add minor code cleanups related to update notifications (#10698)</span></span>
- <span data-ttu-id="b468e-392">删除远程处理安装脚本中弃用的工作流逻辑 (#10320)（感谢 @KirkMunro！）</span><span class="sxs-lookup"><span data-stu-id="b468e-392">Remove deprecated workflow logic from the remoting setup scripts (#10320) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="b468e-393">更新帮助格式以使用正确的大小写 (#10678)（感谢 @tnieto88！）</span><span class="sxs-lookup"><span data-stu-id="b468e-393">Update help format to use proper case (#10678) (Thanks @tnieto88!)</span></span>
- <span data-ttu-id="b468e-394">清除上个月提交的 CodeFactor 样式问题 (#10591)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-394">Clean up CodeFactor style issues coming in commits for the last month (#10591) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="b468e-395">修复 PSTernaryOperator 实验性功能描述中的拼写错误 (#10586)（感谢 @bergmeister！）</span><span class="sxs-lookup"><span data-stu-id="b468e-395">Fix typo in description of PSTernaryOperator experimental feature (#10586) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="b468e-396">将 ActionPreference.Suspend 枚举值转换为不受支持的保留状态，并删除对在首选项变量中使用 ActionPreference.Ignore 的限制 (#10317)（感谢 @KirkMunro！）</span><span class="sxs-lookup"><span data-stu-id="b468e-396">Convert ActionPreference.Suspend enumeration value into a non-supported, reserved state, and remove restriction on using ActionPreference.Ignore in preference variables (#10317) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="b468e-397">将 ArrayList 替换为 List<T>，以获取更具可读性且更可靠的代码，而无需更改功能 (#10333)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-397">Replace ArrayList with List<T> to get more readable and reliable code without changing functionality (#10333) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="b468e-398">对 TestConnectionCommand 进行代码样式修复 (#10439)（感谢 @vexx32！）</span><span class="sxs-lookup"><span data-stu-id="b468e-398">Make code style fixes to TestConnectionCommand (#10439) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="b468e-399">清除 AutomationEngine 并删除额外的 SetSessionStateDrive 方法调用 (#10416)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-399">Cleanup AutomationEngine and remove extra SetSessionStateDrive method call (#10416) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="b468e-400">将默认的 ParameterSetName 重命名回 ConvertTo-Csv 和 ConvertFrom-Csv 的分隔符 (#10425)</span><span class="sxs-lookup"><span data-stu-id="b468e-400">Rename default ParameterSetName back to Delimiter for ConvertTo-Csv and ConvertFrom-Csv (#10425)</span></span>

### <a name="tools"></a><span data-ttu-id="b468e-401">工具</span><span class="sxs-lookup"><span data-stu-id="b468e-401">Tools</span></span>

- <span data-ttu-id="b468e-402">为 SDKToUse 属性添加默认设置，使其在 VS 中生成 (#11085)</span><span class="sxs-lookup"><span data-stu-id="b468e-402">Add default setting for the SDKToUse property so that it builds in VS (#11085)</span></span>
- <span data-ttu-id="b468e-403">Install-Powershell.ps1：添加参数以使用 MSI 安装 (#10921)（感谢 @MJECloud！）</span><span class="sxs-lookup"><span data-stu-id="b468e-403">Install-Powershell.ps1: Add parameter to use MSI installation (#10921) (Thanks @MJECloud!)</span></span>
- <span data-ttu-id="b468e-404">为 install-powershell.ps1 添加基本示例 (#10914)（感谢 @kilasuit！）</span><span class="sxs-lookup"><span data-stu-id="b468e-404">Add basic examples for install-powershell.ps1 (#10914) (Thanks @kilasuit!)</span></span>
- <span data-ttu-id="b468e-405">使 Install-PowerShellRemoting.ps1 处理 PowerShellHome 参数中的空字符串 (#10526)（感谢 @Orca88！）</span><span class="sxs-lookup"><span data-stu-id="b468e-405">Make Install-PowerShellRemoting.ps1 handle empty string in PowerShellHome parameter (#10526) (Thanks @Orca88!)</span></span>
- <span data-ttu-id="b468e-406">在 install-powershell.sh 中从 /etc/lsb-release 切换到 /etc/os-release (#10773)（感谢 @Himura2la！）</span><span class="sxs-lookup"><span data-stu-id="b468e-406">Switch from /etc/lsb-release to /etc/os-release in install-powershell.sh (#10773) (Thanks @Himura2la!)</span></span>
- <span data-ttu-id="b468e-407">在 Windows 上检查每日版本中的 pwsh.exe 和 pwsh (#10738)（感谢 @centreboard！）</span><span class="sxs-lookup"><span data-stu-id="b468e-407">Check pwsh.exe and pwsh in daily version on Windows (#10738) (Thanks @centreboard!)</span></span>
- <span data-ttu-id="b468e-408">删除 installpsh-osx.sh 中不必要的 tap (#10752)</span><span class="sxs-lookup"><span data-stu-id="b468e-408">Remove unneeded tap in installpsh-osx.sh (#10752)</span></span>
- <span data-ttu-id="b468e-409">更新 install-powershell.ps1 以检查是否已安装每日生成 (#10489)</span><span class="sxs-lookup"><span data-stu-id="b468e-409">Update install-powershell.ps1 to check for already installed daily build (#10489)</span></span>

### <a name="tests"></a><span data-ttu-id="b468e-410">测试</span><span class="sxs-lookup"><span data-stu-id="b468e-410">Tests</span></span>

- <span data-ttu-id="b468e-411">使不可靠的 DSC 测试挂起 (#11131)</span><span class="sxs-lookup"><span data-stu-id="b468e-411">Make unreliable DSC test pending (#11131)</span></span>
- <span data-ttu-id="b468e-412">修复字符串数据测试以正确验证哈希表的密钥 (#10810)</span><span class="sxs-lookup"><span data-stu-id="b468e-412">Fix stringdata test to correctly validate keys of hashtables (#10810)</span></span>
- <span data-ttu-id="b468e-413">卸载测试模块 (#11061)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-413">Unload test modules (#11061) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="b468e-414">增加测试 URL 重试的间隔时间 (#11015)</span><span class="sxs-lookup"><span data-stu-id="b468e-414">Increase time between retries of testing URL (#11015)</span></span>
- <span data-ttu-id="b468e-415">更新测试以准确描述测试操作。</span><span class="sxs-lookup"><span data-stu-id="b468e-415">Update tests to accurately describe test actions.</span></span> <span data-ttu-id="b468e-416">(#10928)（感谢 @romero126！）</span><span class="sxs-lookup"><span data-stu-id="b468e-416">(#10928) (Thanks @romero126!)</span></span>
- <span data-ttu-id="b468e-417">暂时跳过运行不正常的测试 TestAppDomainProcessExitEvenHandlerNotLeaking (#10827)</span><span class="sxs-lookup"><span data-stu-id="b468e-417">Temporary skip the flaky test TestAppDomainProcessExitEvenHandlerNotLeaking (#10827)</span></span>
- <span data-ttu-id="b468e-418">使事件处理程序泄漏测试稳定 (#10790)</span><span class="sxs-lookup"><span data-stu-id="b468e-418">Make the event handler leaking test stable (#10790)</span></span>
- <span data-ttu-id="b468e-419">同步 CI YAML 中的大写 (#10767)（感谢 @RDIL！）</span><span class="sxs-lookup"><span data-stu-id="b468e-419">Sync capitalization in CI YAML (#10767) (Thanks @RDIL!)</span></span>
- <span data-ttu-id="b468e-420">添加针对事件处理程序泄漏修复的测试 (#10768)</span><span class="sxs-lookup"><span data-stu-id="b468e-420">Add test for the event handler leaking fix (#10768)</span></span>
- <span data-ttu-id="b468e-421">添加 Get-ChildItem 测试 (#10507)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-421">Add Get-ChildItem test (#10507) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="b468e-422">将测试的不明确语言从开关切换到参数以确保准确性 (#10666)（感谢 @romero126！）</span><span class="sxs-lookup"><span data-stu-id="b468e-422">Replace ambiguous language for tests from switch to parameter for accuracy (#10666) (Thanks @romero126!)</span></span>
- <span data-ttu-id="b468e-423">向 ForEach-Object -Parallel 测试添加实验性检查 (#10354)（感谢 @KirkMunro！）</span><span class="sxs-lookup"><span data-stu-id="b468e-423">Add experimental check to ForEach-Object -Parallel tests (#10354) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="b468e-424">更新 Alpine 验证的测试 (#10428)</span><span class="sxs-lookup"><span data-stu-id="b468e-424">Update tests for Alpine validation (#10428)</span></span>

### <a name="build-and-package-improvements"></a><span data-ttu-id="b468e-425">生成和包改进</span><span class="sxs-lookup"><span data-stu-id="b468e-425">Build and Package Improvements</span></span>

- <span data-ttu-id="b468e-426">修复协调包生成的 Nuget 包签名 (#11316)</span><span class="sxs-lookup"><span data-stu-id="b468e-426">Fix Nuget package signing for Coordinated Package build (#11316)</span></span>
- <span data-ttu-id="b468e-427">更新 PowerShell 库和 NuGet 中的依赖项 (#11323)</span><span class="sxs-lookup"><span data-stu-id="b468e-427">Update dependencies from PowerShell Gallery and NuGet (#11323)</span></span>
- <span data-ttu-id="b468e-428">将 Microsoft.ApplicationInsights 从 2.11.0 升级到 2.12.0 (#11305)</span><span class="sxs-lookup"><span data-stu-id="b468e-428">Bump Microsoft.ApplicationInsights from 2.11.0 to 2.12.0 (#11305)</span></span>
- <span data-ttu-id="b468e-429">将 Microsoft.CodeAnalysis.CSharp 从 3.3.1 升级到 3.4.0 (#11265)</span><span class="sxs-lookup"><span data-stu-id="b468e-429">Bump Microsoft.CodeAnalysis.CSharp from 3.3.1 to 3.4.0 (#11265)</span></span>
- <span data-ttu-id="b468e-430">更新 Debian 10 和 11 的包 (#11236)</span><span class="sxs-lookup"><span data-stu-id="b468e-430">Updates packages for Debian 10 and 11 (#11236)</span></span>
- <span data-ttu-id="b468e-431">仅启用 RC 之前的实验性功能 (#11162)</span><span class="sxs-lookup"><span data-stu-id="b468e-431">Only enable experimental features prior to RC (#11162)</span></span>
- <span data-ttu-id="b468e-432">更新 macOS 最低版本 (#11163)</span><span class="sxs-lookup"><span data-stu-id="b468e-432">Update macOS minimum version (#11163)</span></span>
- <span data-ttu-id="b468e-433">将 NJsonSchema 从 10.0.27 升级到 10.0.28 (#11170)</span><span class="sxs-lookup"><span data-stu-id="b468e-433">Bump NJsonSchema from 10.0.27 to 10.0.28 (#11170)</span></span>
- <span data-ttu-id="b468e-434">更新 Preview.5 的 README.md 和 metadata.json 中的链接 (#10854)</span><span class="sxs-lookup"><span data-stu-id="b468e-434">Updating links in README.md and metadata.json for Preview.5 (#10854)</span></span>
- <span data-ttu-id="b468e-435">选择 PowerShell 拥有的符合性测试的文件 (#10837)</span><span class="sxs-lookup"><span data-stu-id="b468e-435">Select the files for compliance tests which are owned by PowerShell (#10837)</span></span>
- <span data-ttu-id="b468e-436">允许生成 win7x86 .msix 包。</span><span class="sxs-lookup"><span data-stu-id="b468e-436">Allow win7x86 msix package to build.</span></span> <span data-ttu-id="b468e-437">（内部 10515）</span><span class="sxs-lookup"><span data-stu-id="b468e-437">(Internal 10515)</span></span>
- <span data-ttu-id="b468e-438">允许将语义版本传递给 NormalizeVersion 函数 (#11087)</span><span class="sxs-lookup"><span data-stu-id="b468e-438">Allow semantic versions to be passed to NormalizeVersion function (#11087)</span></span>
- <span data-ttu-id="b468e-439">将 .NET Core 框架升级到 3.1-preview.3 (#11079)</span><span class="sxs-lookup"><span data-stu-id="b468e-439">Bump .NET core framework to 3.1-preview.3 (#11079)</span></span>
- <span data-ttu-id="b468e-440">在 /src/Modules 中将 PSReadLine 从 2.0.0-beta5 升级到 2.0.0-beta6 (#11078)</span><span class="sxs-lookup"><span data-stu-id="b468e-440">Bump PSReadLine from 2.0.0-beta5 to 2.0.0-beta6 in /src/Modules (#11078)</span></span>
- <span data-ttu-id="b468e-441">将 Newtonsoft.Json 从 12.0.2 升级到 12.0.3 (#11037) (#11038)</span><span class="sxs-lookup"><span data-stu-id="b468e-441">Bump Newtonsoft.Json from 12.0.2 to 12.0.3 (#11037) (#11038)</span></span>
- <span data-ttu-id="b468e-442">添加 Debian 10、11 和 CentOS 8 包 (#11028)</span><span class="sxs-lookup"><span data-stu-id="b468e-442">Add Debian 10, 11 and CentOS 8 packages (#11028)</span></span>
- <span data-ttu-id="b468e-443">使用 ReleaseDate 字段上传 Build-Info Json 文件 (#10986)</span><span class="sxs-lookup"><span data-stu-id="b468e-443">Upload Build-Info Json file with the ReleaseDate field (#10986)</span></span>
- <span data-ttu-id="b468e-444">将 .NET Core 框架升级到 3.1-preview.2 (#10993)</span><span class="sxs-lookup"><span data-stu-id="b468e-444">Bump .NET core framework to 3.1-preview.2 (#10993)</span></span>
- <span data-ttu-id="b468e-445">启用 x86 MSIX 包的生成 (#10934)</span><span class="sxs-lookup"><span data-stu-id="b468e-445">Enable build of x86 MSIX package (#10934)</span></span>
- <span data-ttu-id="b468e-446">更新 build.psm1 中的 dotnet SDK 安装脚本 URL (#10927)</span><span class="sxs-lookup"><span data-stu-id="b468e-446">Update the dotnet SDK install script URL in build.psm1 (#10927)</span></span>
- <span data-ttu-id="b468e-447">将 Markdig.Signed 从 0.17.1 升级到 0.18.0 (#10887)</span><span class="sxs-lookup"><span data-stu-id="b468e-447">Bump Markdig.Signed from 0.17.1 to 0.18.0 (#10887)</span></span>
- <span data-ttu-id="b468e-448">将 ThreadJob 从 2.0.1 升级到 2.0.2 (#10886)</span><span class="sxs-lookup"><span data-stu-id="b468e-448">Bump ThreadJob from 2.0.1 to 2.0.2 (#10886)</span></span>
- <span data-ttu-id="b468e-449">更新 AppX 清单和打包模块以符合 MS Store 要求 (#10878)</span><span class="sxs-lookup"><span data-stu-id="b468e-449">Update AppX Manifest and Packaging module to conform to MS Store requirements (#10878)</span></span>
- <span data-ttu-id="b468e-450">将 PowerShell SDK 的包引用更新为 preview.5（内部 10295）</span><span class="sxs-lookup"><span data-stu-id="b468e-450">Update package reference for PowerShell SDK to preview.5 (Internal 10295)</span></span>
- <span data-ttu-id="b468e-451">更新 ThirdPartyNotices.txt (#10834)</span><span class="sxs-lookup"><span data-stu-id="b468e-451">Update ThirdPartyNotices.txt (#10834)</span></span>
- <span data-ttu-id="b468e-452">将 Microsoft.PowerShell.Native 升级到 7.0.0-preview.3 (#10826)</span><span class="sxs-lookup"><span data-stu-id="b468e-452">Bump Microsoft.PowerShell.Native to 7.0.0-preview.3 (#10826)</span></span>
- <span data-ttu-id="b468e-453">将 Microsoft.ApplicationInsights 从 2.10.0 升级到 2.11.0 (#10608)</span><span class="sxs-lookup"><span data-stu-id="b468e-453">Bump Microsoft.ApplicationInsights from 2.10.0 to 2.11.0 (#10608)</span></span>
- <span data-ttu-id="b468e-454">将 NJsonSchema 从 10.0.24 升级到 10.0.27 (#10756)</span><span class="sxs-lookup"><span data-stu-id="b468e-454">Bump NJsonSchema from 10.0.24 to 10.0.27 (#10756)</span></span>
- <span data-ttu-id="b468e-455">向生成系统添加 MacPorts 支持 (#10736)（感谢 @Lucius-Q-User！）</span><span class="sxs-lookup"><span data-stu-id="b468e-455">Add MacPorts support to the build system (#10736) (Thanks @Lucius-Q-User!)</span></span>
- <span data-ttu-id="b468e-456">将 PackageManagement 从 1.4.4 升级到 1.4.5 (#10728)</span><span class="sxs-lookup"><span data-stu-id="b468e-456">Bump PackageManagement from 1.4.4 to 1.4.5 (#10728)</span></span>
- <span data-ttu-id="b468e-457">将 NJsonSchema 从 10.0.23 升级到 10.0.24 (#10635)</span><span class="sxs-lookup"><span data-stu-id="b468e-457">Bump NJsonSchema from 10.0.23 to 10.0.24 (#10635)</span></span>
- <span data-ttu-id="b468e-458">添加环境变量以区分 MSI 中的客户端/服务器遥测 (#10612)</span><span class="sxs-lookup"><span data-stu-id="b468e-458">Add environment variable to differentiate client/server telemetry in MSI (#10612)</span></span>
- <span data-ttu-id="b468e-459">将 PSDesiredStateConfiguration 从 2.0.3 升级到 2.0.4 (#10603)</span><span class="sxs-lookup"><span data-stu-id="b468e-459">Bump PSDesiredStateConfiguration from 2.0.3 to 2.0.4 (#10603)</span></span>
- <span data-ttu-id="b468e-460">将 Microsoft.CodeAnalysis.CSharp 从 3.2.1 升级到 3.3.1 (#10607)</span><span class="sxs-lookup"><span data-stu-id="b468e-460">Bump Microsoft.CodeAnalysis.CSharp from 3.2.1 to 3.3.1 (#10607)</span></span>
- <span data-ttu-id="b468e-461">更新为 Net Core 3.0 RTM (#10604)（感谢 @bergmeister！）</span><span class="sxs-lookup"><span data-stu-id="b468e-461">Update to .Net Core 3.0 RTM (#10604) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="b468e-462">更新 .MSIX 打包，使版本符合 Windows 应用商店要求 (#10588)</span><span class="sxs-lookup"><span data-stu-id="b468e-462">Update MSIX packaging so the version to Windows Store requirements (#10588)</span></span>
- <span data-ttu-id="b468e-463">将 PowerShellGet 版本从 2.2 升级到 2.2.1 (#10382)</span><span class="sxs-lookup"><span data-stu-id="b468e-463">Bump PowerShellGet version from 2.2 to 2.2.1 (#10382)</span></span>
- <span data-ttu-id="b468e-464">将 PackageManagement 版本从 1.4.3 升级到 1.4.4 (#10383)</span><span class="sxs-lookup"><span data-stu-id="b468e-464">Bump PackageManagement version from 1.4.3 to 1.4.4 (#10383)</span></span>
- <span data-ttu-id="b468e-465">更新 7.0.0-preview.4 的 README.md 和 metadata.json（内部 10011）</span><span class="sxs-lookup"><span data-stu-id="b468e-465">Update README.md and metadata.json for 7.0.0-preview.4 (Internal 10011)</span></span>
- <span data-ttu-id="b468e-466">将 .Net Core 3.0 版本从预览版 9 升级到 RC1 (#10552)（感谢 @bergmeister！）</span><span class="sxs-lookup"><span data-stu-id="b468e-466">Upgrade .Net Core 3.0 version from Preview 9 to RC1 (#10552) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="b468e-467">修复 ExperimentalFeature 列表生成（内部 9996）</span><span class="sxs-lookup"><span data-stu-id="b468e-467">Fix ExperimentalFeature list generation (Internal 9996)</span></span>
- <span data-ttu-id="b468e-468">将 PSReadLine 版本从 2.0.0-beta4 升级到 2.0.0-beta5 (#10536)</span><span class="sxs-lookup"><span data-stu-id="b468e-468">Bump PSReadLine version from 2.0.0-beta4 to 2.0.0-beta5 (#10536)</span></span>
- <span data-ttu-id="b468e-469">修复发布生成脚本以设置发布标记</span><span class="sxs-lookup"><span data-stu-id="b468e-469">Fix release build script to set release tag</span></span>
- <span data-ttu-id="b468e-470">将 Microsoft.PowerShell.Native 的版本更新为 7.0.0-preview.2 (#10519)</span><span class="sxs-lookup"><span data-stu-id="b468e-470">Update version of Microsoft.PowerShell.Native to 7.0.0-preview.2 (#10519)</span></span>
- <span data-ttu-id="b468e-471">升级到 Netcoreapp3.0 preview9 (#10484)（感谢 @bergmeister！）</span><span class="sxs-lookup"><span data-stu-id="b468e-471">Upgrade to Netcoreapp3.0 preview9 (#10484) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="b468e-472">确保每日协调生成，知道它是每日生成 (#10464)</span><span class="sxs-lookup"><span data-stu-id="b468e-472">Make sure the daily coordinated build, knows it is a daily build (#10464)</span></span>
- <span data-ttu-id="b468e-473">更新组合包生成以发布每日生成 (#10449)</span><span class="sxs-lookup"><span data-stu-id="b468e-473">Update the combined package build to release the daily builds (#10449)</span></span>
- <span data-ttu-id="b468e-474">删除 appveyor 引用 (#10445)（感谢 @RDIL！）</span><span class="sxs-lookup"><span data-stu-id="b468e-474">Remove appveyor reference (#10445) (Thanks @RDIL!)</span></span>
- <span data-ttu-id="b468e-475">将 NJsonSchema 版本从 10.0.22 升级到 10.0.23 (#10421)</span><span class="sxs-lookup"><span data-stu-id="b468e-475">Bump NJsonSchema version from 10.0.22 to 10.0.23 (#10421)</span></span>
- <span data-ttu-id="b468e-476">取消删除 linux-x64 生成文件夹，因为 Alpine 的某些依赖项需要它 (#10407)</span><span class="sxs-lookup"><span data-stu-id="b468e-476">Remove the deletion of linux-x64 build folder because some dependencies for Alpine need it (#10407)</span></span>

### <a name="documentation-and-help-content"></a><span data-ttu-id="b468e-477">文档和帮助内容</span><span class="sxs-lookup"><span data-stu-id="b468e-477">Documentation and Help Content</span></span>

- <span data-ttu-id="b468e-478">将更改日志重构到每个版本的一个日志中 (#11165)</span><span class="sxs-lookup"><span data-stu-id="b468e-478">Refactor change logs into one log per release (#11165)</span></span>
- <span data-ttu-id="b468e-479">修复 PowerShell 7 联机帮助文档的 Fwlink (#11071)</span><span class="sxs-lookup"><span data-stu-id="b468e-479">Fix FWLinks for PowerShell 7 online help documents (#11071)</span></span>
- <span data-ttu-id="b468e-480">更新 CONTRIBUTING.md (#11096)（感谢 @mklement0！）</span><span class="sxs-lookup"><span data-stu-id="b468e-480">Update CONTRIBUTING.md (#11096) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="b468e-481">修复 README.md 中的安装文档链接 (#11083)</span><span class="sxs-lookup"><span data-stu-id="b468e-481">Fix installation doc links in README.md (#11083)</span></span>
- <span data-ttu-id="b468e-482">向 install-powershell.ps1 脚本添加示例 (#11024)（感谢 @kilasuit！）</span><span class="sxs-lookup"><span data-stu-id="b468e-482">Adds examples to install-powershell.ps1 script (#11024) (Thanks @kilasuit!)</span></span>
- <span data-ttu-id="b468e-483">修复 CHANGELOG.md 中的 Select-String 强调和 Import-DscResource (#10890)</span><span class="sxs-lookup"><span data-stu-id="b468e-483">Fix to Select-String emphasis and Import-DscResource in CHANGELOG.md (#10890)</span></span>
- <span data-ttu-id="b468e-484">从 powershell-beginners-guide.md 中删除过期链接 (#10926)</span><span class="sxs-lookup"><span data-stu-id="b468e-484">Remove the stale link from powershell-beginners-guide.md (#10926)</span></span>
- <span data-ttu-id="b468e-485">合并稳定且提供服务的更改日志 (#10527)</span><span class="sxs-lookup"><span data-stu-id="b468e-485">Merge stable and servicing change logs (#10527)</span></span>
- <span data-ttu-id="b468e-486">更新生成文档中已使用的 .NET 版本 (#10775)（感谢 @Greg-Smulko！）</span><span class="sxs-lookup"><span data-stu-id="b468e-486">Update used .NET version in build docs (#10775) (Thanks @Greg-Smulko!)</span></span>
- <span data-ttu-id="b468e-487">将 MSDN 中的链接替换为 powershell-beginners-guide.md 中的 docs.microsoft.com (#10778)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="b468e-487">Replace links from MSDN to docs.microsoft.com in powershell-beginners-guide.md (#10778) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="b468e-488">修复中断的 DSC 概述链接 (#10702)</span><span class="sxs-lookup"><span data-stu-id="b468e-488">Fix broken DSC overview link (#10702)</span></span>
- <span data-ttu-id="b468e-489">更新 Support_Question.md，以链接到作为另一个社区资源的堆栈溢出 (#10638)（感谢 @mklement0！）</span><span class="sxs-lookup"><span data-stu-id="b468e-489">Update Support_Question.md to link to Stack Overflow as another community resource (#10638) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="b468e-490">将处理器体系结构添加到分发请求模板 (#10661)</span><span class="sxs-lookup"><span data-stu-id="b468e-490">Add processor architecture to distribution request template (#10661)</span></span>
- <span data-ttu-id="b468e-491">将新的 PowerShell MoL 书籍添加到学习 PowerShell Docs (#10602)</span><span class="sxs-lookup"><span data-stu-id="b468e-491">Add new PowerShell MoL book to learning PowerShell docs (#10602)</span></span>
- <span data-ttu-id="b468e-492">更新 v6.1.6 和 v6.2.3 版本的 README.md 和元数据 (#10523)</span><span class="sxs-lookup"><span data-stu-id="b468e-492">Update README.md and metadata for v6.1.6 and v6.2.3 releases (#10523)</span></span>
- <span data-ttu-id="b468e-493">修复 README.md 中的拼写错误 (#10465)（感谢 @vedhasp！）</span><span class="sxs-lookup"><span data-stu-id="b468e-493">Fix a typo in README.md (#10465) (Thanks @vedhasp!)</span></span>
- <span data-ttu-id="b468e-494">将对 PSKoans 模块的引用添加到学习资源文档 (#10369)（感谢 @vexx32！）</span><span class="sxs-lookup"><span data-stu-id="b468e-494">Add a reference to PSKoans module to Learning Resources documentation (#10369) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="b468e-495">更新 7.0.0-preview.3 的 README.md 和 metadata.json（内部 #10393）</span><span class="sxs-lookup"><span data-stu-id="b468e-495">Update README.md and metadata.json for 7.0.0-preview.3 (#10393)</span></span>
