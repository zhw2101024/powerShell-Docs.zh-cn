---
ms.date: 09/06/2019
keywords: powershell,cmdlet
title: PowerShell 5.0 ISE 中的新增功能
ms.openlocfilehash: f687c409a1a4b0e6b872863e9f132f7cf5baff20
ms.sourcegitcommit: a6e54a305fdeb6482321c77da8066d2f991c93e1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2019
ms.locfileid: "74117511"
---
# <a name="whats-new-in-the-windows-powershell-50-ise"></a><span data-ttu-id="18db9-103">Windows PowerShell 5.0 ISE 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="18db9-103">What's New in the Windows PowerShell 5.0 ISE</span></span>

<span data-ttu-id="18db9-104">本主题介绍已在 Windows PowerShell (R) 集成脚本环境 (ISE) 的各版本中引入的新增功能和更新功能。</span><span class="sxs-lookup"><span data-stu-id="18db9-104">This topic explains the new and updated features that have been introduced in versions of Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="feature-description"></a><span data-ttu-id="18db9-105">功能描述</span><span class="sxs-lookup"><span data-stu-id="18db9-105">Feature description</span></span>

<span data-ttu-id="18db9-106">Windows PowerShell ISE 是一款主机应用程序，让你可以在直观的图形环境中编写、运行和测试脚本与模块。</span><span class="sxs-lookup"><span data-stu-id="18db9-106">The Windows PowerShell ISE is a host application that enables you to write, run, and test scripts and modules in a graphical and intuitive environment.</span></span> <span data-ttu-id="18db9-107">其主要功能，如语法着色、Tab 自动补全、可视调试、Unicode 遵从和上下文相关帮助，将为你带来丰富的脚本编写体验。</span><span class="sxs-lookup"><span data-stu-id="18db9-107">Key features such as syntax-coloring, tab completion, visual debugging, Unicode compliance, and context-sensitive Help provide a rich scripting experience.</span></span>

<span data-ttu-id="18db9-108">有关详细信息，请参阅 [Windows PowerShell ISE 简介](../components/ise/Introducing-the-Windows-PowerShell-ISE.md)。</span><span class="sxs-lookup"><span data-stu-id="18db9-108">For more information, see [Introducing the Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).</span></span>

<span data-ttu-id="18db9-109">下表列出了 Windows PowerShell 中此版本的 Windows PowerShell ISE 的新增功能和更改功能。</span><span class="sxs-lookup"><span data-stu-id="18db9-109">The following table lists the new and changed features for this release of Windows PowerShell ISE in Windows PowerShell.</span></span>

## <a name="intellisense"></a><span data-ttu-id="18db9-110">Intellisense</span><span class="sxs-lookup"><span data-stu-id="18db9-110">IntelliSense</span></span>

> <span data-ttu-id="18db9-111">在 ISE 3.0 中添加</span><span class="sxs-lookup"><span data-stu-id="18db9-111">Added in ISE 3.0</span></span>

<span data-ttu-id="18db9-112">Intellisense 是一个自动完成辅助功能，是 Windows PowerShell ISE 的一部分。</span><span class="sxs-lookup"><span data-stu-id="18db9-112">IntelliSense is an automatic-completion assistance feature that is part of Windows PowerShell ISE.</span></span>
<span data-ttu-id="18db9-113">Intellisense 会在你键入时显示可单击的菜单，其中包括可能匹配的 cmdlet、参数、参数值、文件或文件夹。</span><span class="sxs-lookup"><span data-stu-id="18db9-113">IntelliSense displays clickable menus of potentially matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="18db9-114">**更改增添了什么价值？**</span><span class="sxs-lookup"><span data-stu-id="18db9-114">**What value does this change add?**</span></span>

<span data-ttu-id="18db9-115">新增 Intellisense 功能后，使用 Windows PowerShell ISE 创建脚本时，可以更容易地发现 cmdlet 和语法。</span><span class="sxs-lookup"><span data-stu-id="18db9-115">With the addition of IntelliSense, it's easier to discover cmdlets and syntax when you use Windows PowerShell ISE to create scripts.</span></span> <span data-ttu-id="18db9-116">在创建新脚本时，还可以使用 Windows PowerShell ISE 了解 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="18db9-116">You can also use Windows PowerShell ISE to learn Windows PowerShell while you create new scripts.</span></span>

<span data-ttu-id="18db9-117">**工作原理的不同之处是什么？**</span><span class="sxs-lookup"><span data-stu-id="18db9-117">**What works differently?**</span></span>

<span data-ttu-id="18db9-118">当在 Windows PowerShell ISE 中键入 cmdlet 时，会显示一个可滚动和可点击的菜单，并可在其中浏览和选择适当的命令。</span><span class="sxs-lookup"><span data-stu-id="18db9-118">When you type cmdlets in the Windows PowerShell ISE, a scrollable and clickable menu displays, allowing you to browse and select the appropriate commands.</span></span>

## <a name="snippets"></a><span data-ttu-id="18db9-119">代码段</span><span class="sxs-lookup"><span data-stu-id="18db9-119">Snippets</span></span>

> <span data-ttu-id="18db9-120">在 ISE 3.0 中添加</span><span class="sxs-lookup"><span data-stu-id="18db9-120">Added in ISE 3.0</span></span>

<span data-ttu-id="18db9-121">*代码段*是 Windows PowerShell 代码的一小部分，它可以插入到你在 Windows PowerShell ISE 中创建的脚本。</span><span class="sxs-lookup"><span data-stu-id="18db9-121">*Snippets* are short sections of Windows PowerShell code that you can insert into the scripts you create in Windows PowerShell ISE.</span></span> <span data-ttu-id="18db9-122">Windows PowerShell ISE 附带一组默认的代码段。</span><span class="sxs-lookup"><span data-stu-id="18db9-122">Windows PowerShell ISE comes with a default set of snippets.</span></span> <span data-ttu-id="18db9-123">在 Windows PowerShell ISE 中工作的同时，可通过使用 `New-Snippet` cmdlet 添加代码段。</span><span class="sxs-lookup"><span data-stu-id="18db9-123">You can add snippets by using the `New-Snippet` cmdlet while working in Windows PowerShell ISE.</span></span>

<span data-ttu-id="18db9-124">**更改增添了什么价值？**</span><span class="sxs-lookup"><span data-stu-id="18db9-124">**What value does this change add?**</span></span>

<span data-ttu-id="18db9-125">通过使用代码段，可以快速组建脚本以自动运行你的环境。</span><span class="sxs-lookup"><span data-stu-id="18db9-125">By using snippets, you can quickly assemble and create scripts to automate your environment.</span></span>

<span data-ttu-id="18db9-126">**工作原理的不同之处是什么？**</span><span class="sxs-lookup"><span data-stu-id="18db9-126">**What works differently?**</span></span>

<span data-ttu-id="18db9-127">若要在 Windows PowerShell 3.0 或更高版本中使用代码段，请在“编辑  ”菜单上，单击“启动代码段  ”，或按 <kbd>Ctrl</kbd>+<kbd>J</kbd>。</span><span class="sxs-lookup"><span data-stu-id="18db9-127">To use snippets in Windows PowerShell 3.0 or later, on the **Edit** menu, click **Start Snippets**, or press <kbd>Ctrl</kbd>+<kbd>J</kbd>.</span></span>

## <a name="add-on-tools"></a><span data-ttu-id="18db9-128">附加工具</span><span class="sxs-lookup"><span data-stu-id="18db9-128">Add-on tools</span></span>

> <span data-ttu-id="18db9-129">在 PowerShell 3.0 中添加</span><span class="sxs-lookup"><span data-stu-id="18db9-129">Added in PowerShell 3.0</span></span>

<span data-ttu-id="18db9-130">Windows PowerShell ISE 现在支持使用对象模型的附加工具。</span><span class="sxs-lookup"><span data-stu-id="18db9-130">Windows PowerShell ISE now supports add-on tools using the object model.</span></span> <span data-ttu-id="18db9-131">这些附加工具是 Windows Presentation Foundation (WPF) 控件，在控制台中显示为垂直或水平窗格。</span><span class="sxs-lookup"><span data-stu-id="18db9-131">These add-ons are Windows Presentation Foundation (WPF) controls that are displayed as a vertical or horizontal pane in the console.</span></span> <span data-ttu-id="18db9-132">窗格中的多个附加工具会显示为选项卡式控件。</span><span class="sxs-lookup"><span data-stu-id="18db9-132">Multiple add-on tools in a pane are displayed as a tabbed control.</span></span> <span data-ttu-id="18db9-133">你还可以添加或删除由 Microsoft 以外的参与方创建的附加工具。</span><span class="sxs-lookup"><span data-stu-id="18db9-133">You can also add or remove add-on tools that are produced by non-Microsoft parties.</span></span> <span data-ttu-id="18db9-134">有关详细信息，请参阅 [Windows PowerShell ISE 脚本对象模型的用途](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)。</span><span class="sxs-lookup"><span data-stu-id="18db9-134">For more information, see [The Purpose of the Windows PowerShell ISE Scripting Object Model](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).</span></span>

<span data-ttu-id="18db9-135">**更改增添了什么价值？**</span><span class="sxs-lookup"><span data-stu-id="18db9-135">**What value does this change add?**</span></span>

<span data-ttu-id="18db9-136">借助附加工具，可以使用可添加功能和增强脚本编写体验的工具来扩展和自定义 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="18db9-136">Add-ons allow you to extend and customize Windows PowerShell ISE with tools that add functionality and enhance your scripting experience.</span></span>

<span data-ttu-id="18db9-137">**工作原理的不同之处是什么？**</span><span class="sxs-lookup"><span data-stu-id="18db9-137">**What works differently?**</span></span>

<span data-ttu-id="18db9-138">Windows PowerShell ISE 3.0 及更高版本附带**命令**附加工具。</span><span class="sxs-lookup"><span data-stu-id="18db9-138">Windows PowerShell ISE 3.0 and later come with the **Commands** add-on.</span></span> <span data-ttu-id="18db9-139">借助**命令**附加工具可以浏览 cmdlet，以及使用**脚本**和**控制台**窗格并行访问有关 cmdlet 的帮助。</span><span class="sxs-lookup"><span data-stu-id="18db9-139">The **Commands** add-on allows you to browse cmdlets, and access help about the cmdlets side-by-side with the **Script** and **Console** Panes.</span></span>

<span data-ttu-id="18db9-140">可通过使用  “附加工具”菜单上的  “打开附加工具网站”命令找到其他附加工具。</span><span class="sxs-lookup"><span data-stu-id="18db9-140">Additional add-ons can be found by using the **Open Add-on Tools Website** command on the **Add-ons** menu.</span></span>

## <a name="restart-manager-and-auto-save"></a><span data-ttu-id="18db9-141">重启管理器和自动保存</span><span class="sxs-lookup"><span data-stu-id="18db9-141">Restart manager and auto-save</span></span>

> <span data-ttu-id="18db9-142">在 PowerShell 3.0 中添加</span><span class="sxs-lookup"><span data-stu-id="18db9-142">Added in PowerShell 3.0</span></span>

<span data-ttu-id="18db9-143">Windows PowerShell ISE 每隔两分钟在单独的位置上自动保存你打开的脚本。</span><span class="sxs-lookup"><span data-stu-id="18db9-143">Windows PowerShell ISE now automatically saves your open scripts every two minutes, in a separate location.</span></span> <span data-ttu-id="18db9-144">当 Windows PowerShell ISE 在意外崩溃或重新启动后重新启动时，它会恢复在上一个会话中打开的脚本，即使脚本未保存也是如此。</span><span class="sxs-lookup"><span data-stu-id="18db9-144">When Windows PowerShell ISE restarts after an unexpected crash or reboot, it recovers scripts that were open in the last session, even if the scripts weren't saved.</span></span>

<span data-ttu-id="18db9-145">要更改自动保存间隔，可在控制台窗格中运行下面的命令：`$psise.Options.AutoSaveMinuteInterval`。</span><span class="sxs-lookup"><span data-stu-id="18db9-145">To change the automatic saving interval, run the following command in the Console pane: `$psise.Options.AutoSaveMinuteInterval`.</span></span>

<span data-ttu-id="18db9-146">**更改增添了什么价值？**</span><span class="sxs-lookup"><span data-stu-id="18db9-146">**What value does this change add?**</span></span>

<span data-ttu-id="18db9-147">你已经了解打开的脚本会自动保存，现在便可以在 Windows PowerShell ISE 中工作了。</span><span class="sxs-lookup"><span data-stu-id="18db9-147">You can now work within Windows PowerShell ISE knowing that your open scripts are automatically saved.</span></span>

<span data-ttu-id="18db9-148">**工作原理的不同之处是什么？**</span><span class="sxs-lookup"><span data-stu-id="18db9-148">**What works differently?**</span></span>

<span data-ttu-id="18db9-149">Windows PowerShell ISE 2.0 不会自动保存脚本。</span><span class="sxs-lookup"><span data-stu-id="18db9-149">Windows PowerShell ISE 2.0 doesn't save the scripts automatically.</span></span>

## <a name="most-recently-used-list"></a><span data-ttu-id="18db9-150">最近使用的列表</span><span class="sxs-lookup"><span data-stu-id="18db9-150">Most-recently used list</span></span>

> <span data-ttu-id="18db9-151">在 PowerShell 3.0 中添加</span><span class="sxs-lookup"><span data-stu-id="18db9-151">Added in PowerShell 3.0</span></span>

<span data-ttu-id="18db9-152">Windows PowerShell ISE 现在具有最近使用过的文件列表。</span><span class="sxs-lookup"><span data-stu-id="18db9-152">Windows PowerShell ISE now has a most-recently used list for files.</span></span> <span data-ttu-id="18db9-153">在 Windows PowerShell ISE 中打开文件时，文件会添加到“文件”  菜单上的最近使用列表中。</span><span class="sxs-lookup"><span data-stu-id="18db9-153">When you open a file in Windows PowerShell ISE, the file is added to the most-recently used list on the **File** menu.</span></span>

<span data-ttu-id="18db9-154">若要更改最近使用列表中的文件默认数量，请在控制台窗格中运行以下命令：`$psise.Options.MruCount`。</span><span class="sxs-lookup"><span data-stu-id="18db9-154">To change the default number of files in the most-recently used list, run the following command in the Console Pane: `$psise.Options.MruCount`.</span></span>

<span data-ttu-id="18db9-155">**更改增添了什么价值？**</span><span class="sxs-lookup"><span data-stu-id="18db9-155">**What value does this change add?**</span></span>

<span data-ttu-id="18db9-156">现在可以使用最近使用列表轻松地访问频繁使用的文件。</span><span class="sxs-lookup"><span data-stu-id="18db9-156">You can now use the most-recently used list to easily access your frequently used files.</span></span>

<span data-ttu-id="18db9-157">**工作原理的不同之处是什么？**</span><span class="sxs-lookup"><span data-stu-id="18db9-157">**What works differently?**</span></span>

<span data-ttu-id="18db9-158">Windows PowerShell ISE 2.0 没有最近使用列表。</span><span class="sxs-lookup"><span data-stu-id="18db9-158">Windows PowerShell ISE 2.0 doesn't have a most-recently used list.</span></span>

## <a name="console-pane"></a><span data-ttu-id="18db9-159">控制台窗格</span><span class="sxs-lookup"><span data-stu-id="18db9-159">Console Pane</span></span>

> <span data-ttu-id="18db9-160">在 PowerShell 3.0 中添加</span><span class="sxs-lookup"><span data-stu-id="18db9-160">Added in PowerShell 3.0</span></span>

<span data-ttu-id="18db9-161">第一版 Windows PowerShell ISE 中可用的单独的命令窗格和输出窗格现在合并成了一个控制台窗格。</span><span class="sxs-lookup"><span data-stu-id="18db9-161">The separate Command and Output Panes that were available in the first release of Windows PowerShell ISE have been combined into a single Console Pane.</span></span> <span data-ttu-id="18db9-162">该控制台窗格的功能和外观与典型的 Windows PowerShell 控制台类似，但经过了以下改进：</span><span class="sxs-lookup"><span data-stu-id="18db9-162">The Console Pane is similar in function and appearance to a typical Windows PowerShell console, but it includes the following enhancements:</span></span>

- <span data-ttu-id="18db9-163">用于输入文本（而非输出文本）的语法着色，包括 XML 语法</span><span class="sxs-lookup"><span data-stu-id="18db9-163">Syntax coloring for input text (not output text), including XML syntax</span></span>
- <span data-ttu-id="18db9-164">Intellisense</span><span class="sxs-lookup"><span data-stu-id="18db9-164">IntelliSense</span></span>
- <span data-ttu-id="18db9-165">大括号匹配</span><span class="sxs-lookup"><span data-stu-id="18db9-165">Brace matching</span></span>
- <span data-ttu-id="18db9-166">错误指示</span><span class="sxs-lookup"><span data-stu-id="18db9-166">Error indication</span></span>
- <span data-ttu-id="18db9-167">对 Unicode 的完全支持</span><span class="sxs-lookup"><span data-stu-id="18db9-167">Full Unicode support</span></span>
- <span data-ttu-id="18db9-168"><kbd>F1</kbd> 上下文相关帮助</span><span class="sxs-lookup"><span data-stu-id="18db9-168"><kbd>F1</kbd> context-sensitive help</span></span>
- <span data-ttu-id="18db9-169"><kbd>Ctrl</kbd>+<kbd>F1</kbd> 上下文相关的 Show-Command</span><span class="sxs-lookup"><span data-stu-id="18db9-169"><kbd>Ctrl</kbd>+<kbd>F1</kbd> context-sensitive Show-Command</span></span>
- <span data-ttu-id="18db9-170">对复杂脚本和从右向左语言的支持</span><span class="sxs-lookup"><span data-stu-id="18db9-170">Complex script and right-to-left support</span></span>
- <span data-ttu-id="18db9-171">字体支持</span><span class="sxs-lookup"><span data-stu-id="18db9-171">Font support</span></span>
- <span data-ttu-id="18db9-172">缩放</span><span class="sxs-lookup"><span data-stu-id="18db9-172">Zoom</span></span>
- <span data-ttu-id="18db9-173">行选择模式和块选择模式</span><span class="sxs-lookup"><span data-stu-id="18db9-173">Line-select and block-select modes</span></span>
- <span data-ttu-id="18db9-174">当你在控制台中按“向上”<kbd></kbd>箭头查看历史记录时，命令行处会保留你所键入的内容</span><span class="sxs-lookup"><span data-stu-id="18db9-174">Preservation of typed content at the command line when you press the <kbd>UpArrow</kbd> to view history in the console</span></span>

<span data-ttu-id="18db9-175">**更改增添了什么价值？**</span><span class="sxs-lookup"><span data-stu-id="18db9-175">**What value does this change add?**</span></span>

<span data-ttu-id="18db9-176">这些新增的控制台窗格变化提供了与控制台界面更加一致的脚本编写体验。</span><span class="sxs-lookup"><span data-stu-id="18db9-176">The addition of these Console Pane changes provides a scripting experience that is more consistent with the console interface.</span></span>

<span data-ttu-id="18db9-177">**工作原理的不同之处是什么？**</span><span class="sxs-lookup"><span data-stu-id="18db9-177">**What works differently?**</span></span>

<span data-ttu-id="18db9-178">Windows PowerShell ISE 2.0 具有单独的命令和输出窗格。</span><span class="sxs-lookup"><span data-stu-id="18db9-178">Windows PowerShell ISE 2.0 has separate Command and Output Panes.</span></span>

## <a name="command-line-switches"></a><span data-ttu-id="18db9-179">命令行开关</span><span class="sxs-lookup"><span data-stu-id="18db9-179">Command-line switches</span></span>

> <span data-ttu-id="18db9-180">在 PowerShell 3.0 中添加</span><span class="sxs-lookup"><span data-stu-id="18db9-180">Added in PowerShell 3.0</span></span>

<span data-ttu-id="18db9-181">如果从命令行（通过键入 **powershell_ise.exe**）启动 Windows PowerShell ISE，则可以添加下列新的命令行开关。</span><span class="sxs-lookup"><span data-stu-id="18db9-181">If you start Windows PowerShell ISE from the command line (by typing **powershell_ise.exe**), you can add the following new command-line switches.</span></span>

- <span data-ttu-id="18db9-182">`-NoProfile`：在不运行 `$profile` 的情况下启动 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="18db9-182">`-NoProfile`: Starts Windows PowerShell ISE without running `$profile`</span></span>
- <span data-ttu-id="18db9-183">`-Help`：显示帮助窗口</span><span class="sxs-lookup"><span data-stu-id="18db9-183">`-Help`: Displays a Help window</span></span>
- <span data-ttu-id="18db9-184">`-mta`：在多线程的单元模式下启动 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="18db9-184">`-mta`: Starts Windows PowerShell ISE in multithreaded apartment mode.</span></span> <span data-ttu-id="18db9-185">Windows PowerShell ISE 的默认操作模式是单线程的单元模式或 `-sta`。</span><span class="sxs-lookup"><span data-stu-id="18db9-185">The default operation mode for Windows PowerShell ISE is single-threaded apartment mode, or `-sta`.</span></span>

<span data-ttu-id="18db9-186">**更改增添了什么价值？**</span><span class="sxs-lookup"><span data-stu-id="18db9-186">**What value does this change add?**</span></span>

<span data-ttu-id="18db9-187">这些新增的命令行开关使你能够控制运行 Windows PowerShell ISE 的环境。</span><span class="sxs-lookup"><span data-stu-id="18db9-187">The addition of these command-line switches allows you to control the environment in which the Windows PowerShell ISE runs.</span></span>

<span data-ttu-id="18db9-188">**工作原理的不同之处是什么？**</span><span class="sxs-lookup"><span data-stu-id="18db9-188">**What works differently?**</span></span>

<span data-ttu-id="18db9-189">Windows PowerShell ISE 2.0 不识别这些命令行开关。</span><span class="sxs-lookup"><span data-stu-id="18db9-189">Windows PowerShell ISE 2.0 doesn't recognize these command-line switches.</span></span>

## <a name="new-editor-features"></a><span data-ttu-id="18db9-190">新的编辑器功能</span><span class="sxs-lookup"><span data-stu-id="18db9-190">New editor features</span></span>

> <span data-ttu-id="18db9-191">在 PowerShell 3.0 中添加</span><span class="sxs-lookup"><span data-stu-id="18db9-191">Added in PowerShell 3.0</span></span>

<span data-ttu-id="18db9-192">其他 Windows PowerShell ISE 编辑功能包括：</span><span class="sxs-lookup"><span data-stu-id="18db9-192">Other Windows PowerShell ISE editing features include:</span></span>

- <span data-ttu-id="18db9-193">**XML 语法着色** - Windows PowerShell ISE 现在以对 Windows PowerShell 语法进行着色的相同方法对 XML 语法进行着色。</span><span class="sxs-lookup"><span data-stu-id="18db9-193">**XML syntax coloring** - Windows PowerShell ISE now colors XML syntax in the same way as it colors Windows PowerShell syntax.</span></span>
- <span data-ttu-id="18db9-194">**大括号匹配** - Windows PowerShell ISE 包括大括号匹配和突出显示，并可以通过以下方式使用：（例如，如果已选择左大括号，则可使用 **Go to Match** 命令或 <kbd>Ctrl</kbd>+<kbd>]</kbd> 定位右大括号）。</span><span class="sxs-lookup"><span data-stu-id="18db9-194">**Brace matching** - Windows PowerShell ISE includes brace matching and highlighting, and can be used in the following ways: (for example, using the **Go to Match** command or <kbd>Ctrl</kbd>+<kbd>]</kbd> locates the closing brace, if you have an opening brace selected).</span></span>
- <span data-ttu-id="18db9-195">**大纲视图** 脚本窗格支持大纲显示，允许通过单击左边距中的 (+) 或 (-) 来实现代码段的折叠或展开。</span><span class="sxs-lookup"><span data-stu-id="18db9-195">**Outline view** The Script Pane supports outlining, which allows collapsing or expanding sections of code by clicking plus or minus signs in the left margin.</span></span> <span data-ttu-id="18db9-196">可以使用大括号或 `#region` 和 `#endregion` 标记来标记可折叠段的开头或末尾。</span><span class="sxs-lookup"><span data-stu-id="18db9-196">You can use braces or the `#region` and `#endregion` tags to mark the beginning or end of a collapsible section.</span></span> <span data-ttu-id="18db9-197">若要展开或折叠所有区域，请按 <kbd>Ctrl</kbd>+<kbd>M</kbd>。</span><span class="sxs-lookup"><span data-stu-id="18db9-197">To expand or collapse all regions, press <kbd>Ctrl</kbd>+<kbd>M</kbd>.</span></span>
- <span data-ttu-id="18db9-198">**拖放文本编辑** - Windows PowerShell ISE 现在支持拖放文本编辑。</span><span class="sxs-lookup"><span data-stu-id="18db9-198">**Drag and drop text editing** - Windows PowerShell ISE now supports drag and drop text editing.</span></span> <span data-ttu-id="18db9-199">可以选择任何文本块，并通过将该文本拖动到编辑器或控制台中的另一个位置来移动文本。</span><span class="sxs-lookup"><span data-stu-id="18db9-199">You can select any block of text and drag that text to another location in the editor or the console to move the text.</span></span> <span data-ttu-id="18db9-200">如果拖动所选文本时按住 <kbd>Ctrl</kbd> 键不放，则释放鼠标按钮时，文本便会复制到新位置。</span><span class="sxs-lookup"><span data-stu-id="18db9-200">If you hold down the <kbd>Ctrl</kbd> key while you drag the selected text, when you release the mouse button the text is copied to the new location.</span></span> <span data-ttu-id="18db9-201">在此版本的 Windows PowerShell ISE 中，当你将文件拖放到 Windows PowerShell ISE 中，Windows PowerShell ISE 会打开该文件。</span><span class="sxs-lookup"><span data-stu-id="18db9-201">In this version of Windows PowerShell ISE, when you drag and drop files onto Windows PowerShell ISE, Windows PowerShell ISE opens the file.</span></span>
- <span data-ttu-id="18db9-202">**分析错误显示** - 分析错误用红色下划线指示。</span><span class="sxs-lookup"><span data-stu-id="18db9-202">**Parse error display** - Parse errors are indicated with red underlines.</span></span> <span data-ttu-id="18db9-203">当你将鼠标悬停在某个指示的错误上时，工具提示文本会显示在代码中发现的问题。</span><span class="sxs-lookup"><span data-stu-id="18db9-203">When you hover over an indicated error, tooltip text displays the problem that was found in the code.</span></span>
- <span data-ttu-id="18db9-204">**缩放** - 若要设置控制台内容的缩放百分比，可以使用缩放滑块（位于 Windows PowerShell ISE 窗口右下角），也可以在控制台窗格中输入命令 `$psise.options.Zoom`。</span><span class="sxs-lookup"><span data-stu-id="18db9-204">**Zoom** - The zoom percentage of the console's content can be set by using the zoom slider (in the lower right corner of Windows PowerShell ISE window), or by entering the command `$psise.options.Zoom` in the Console Pane.</span></span>
- <span data-ttu-id="18db9-205">**富文本复制和粘贴** - 在 Windows PowerShell ISE 中将内容复制到剪贴板时，会保留原选定内容的字体、大小和颜色信息。</span><span class="sxs-lookup"><span data-stu-id="18db9-205">**Rich text copy and paste** - Copying to the clipboard in Windows PowerShell ISE preserves the font, size, and color information of the original selection.</span></span>
- <span data-ttu-id="18db9-206">**块选择** - 可以通过在用鼠标选定脚本窗格中文本的同时按住 <kbd>ALT</kbd> 键，或通过按 <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>箭头键</kbd> 来选定文本块。</span><span class="sxs-lookup"><span data-stu-id="18db9-206">**Block selection** - You can select a block of text by holding down the <kbd>ALT</kbd> key while selecting text in the Script Pane with your mouse, or by pressing <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>Arrow</kbd>.</span></span>

<span data-ttu-id="18db9-207">**更改增添了什么价值？**</span><span class="sxs-lookup"><span data-stu-id="18db9-207">**What value does this change add?**</span></span>

<span data-ttu-id="18db9-208">这些新增的编辑功能提供更一致、更强大的编辑环境。</span><span class="sxs-lookup"><span data-stu-id="18db9-208">The additional editing features provide a more consistent and powerful editing environment.</span></span>

<span data-ttu-id="18db9-209">**工作原理的不同之处是什么？**</span><span class="sxs-lookup"><span data-stu-id="18db9-209">**What works differently?**</span></span>

<span data-ttu-id="18db9-210">Windows PowerShell ISE 2.0 中不具有这些编辑增强功能。</span><span class="sxs-lookup"><span data-stu-id="18db9-210">These editing enhancements weren't present in Windows PowerShell ISE 2.0.</span></span>

## <a name="new-help-viewer-window"></a><span data-ttu-id="18db9-211">新的帮助查看器窗口</span><span class="sxs-lookup"><span data-stu-id="18db9-211">New Help viewer window</span></span>

> <span data-ttu-id="18db9-212">在 PowerShell 3.0 中添加</span><span class="sxs-lookup"><span data-stu-id="18db9-212">Added in PowerShell 3.0</span></span>

<span data-ttu-id="18db9-213">当你将光标置于某个 cmdlet 中，或突出显示某个 cmdlet 的一部分时，按 <kbd>F1</kbd> 会打开新的帮助查看器，其中显示了有关突出显示的 cmdlet 的上下文相关帮助。</span><span class="sxs-lookup"><span data-stu-id="18db9-213">If you press <kbd>F1</kbd> when your cursor is in a cmdlet, or you have part of a cmdlet highlighted, the new Help viewer opens context-sensitive Help about the highlighted cmdlet.</span></span> <span data-ttu-id="18db9-214">要显示 Windows PowerShell 的“关于”帮助，可在控制台窗格中键入 `operators`  ，然后按 <kbd>F1</kbd>。</span><span class="sxs-lookup"><span data-stu-id="18db9-214">To display Windows PowerShell **About** help, type `operators` in the console pane, and then press <kbd>F1</kbd>.</span></span>

<span data-ttu-id="18db9-215">使用此功能之前，必须先从 Microsoft 网站下载最新版本的 Windows PowerShell 帮助主题。</span><span class="sxs-lookup"><span data-stu-id="18db9-215">Before you use this feature, download the most current version of Windows PowerShell Help topics from the Microsoft website.</span></span> <span data-ttu-id="18db9-216">当你以管理员身份运行 Windows PowerShell ISE 时，下载“帮助”主题的最简单方法是在控制台窗格中运行 `Update-Help` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="18db9-216">The simplest method for downloading the Help topics is to run the `Update-Help` cmdlet in the Console Pane when running Windows PowerShell ISE as administrator.</span></span>

<span data-ttu-id="18db9-217">可以修改 <kbd>F1</kbd> 键寻找帮助的位置。</span><span class="sxs-lookup"><span data-stu-id="18db9-217">You can alter where the <kbd>F1</kbd> key looks for Help.</span></span> <span data-ttu-id="18db9-218">在“工具”  /“选项”  菜单中“常规设置”  选项卡上的“其他设置”  下，可以设置或清除复选框“使用本地帮助内容而非联机内容”  。</span><span class="sxs-lookup"><span data-stu-id="18db9-218">In the **Tools**/**Options** menu, on the **General Settings** tab, under **Other Settings**, you can set or clear the checkbox **Use local help content instead of online content**.</span></span> <span data-ttu-id="18db9-219">勾选此复选框后，客户端便会在模块文件夹中的已下载帮助中查找 cmdlet 帮助。</span><span class="sxs-lookup"><span data-stu-id="18db9-219">When checked, the client looks for the cmdlet Help in the downloaded Help found in the modules folder.</span></span> <span data-ttu-id="18db9-220">如果清除该复选框，客户端将查找联机帮助。</span><span class="sxs-lookup"><span data-stu-id="18db9-220">If the checkbox is cleared, the client looks for help online.</span></span>

<span data-ttu-id="18db9-221">**更改增添了什么价值？**</span><span class="sxs-lookup"><span data-stu-id="18db9-221">**What value does this change add?**</span></span>

<span data-ttu-id="18db9-222">在无需离开当前 cmdlet 或脚本的情况下，上下文相关帮助提供了完整的学习体验。</span><span class="sxs-lookup"><span data-stu-id="18db9-222">Context-sensitive Help without leaving your current cmdlet or script provides an integrated learning experience.</span></span>

<span data-ttu-id="18db9-223">**工作原理的不同之处是什么？**</span><span class="sxs-lookup"><span data-stu-id="18db9-223">**What works differently?**</span></span>

<span data-ttu-id="18db9-224">在 Windows PowerShell ISE 的早期版本中按 <kbd>F1</kbd> 会打开本地计算机上的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="18db9-224">Pressing <kbd>F1</kbd> in previous versions of Windows PowerShell ISE opened the help file on the local computer.</span></span> <span data-ttu-id="18db9-225">在 Windows PowerShell ISE 3.0 及更高版本中，会打开一个窗口，其中包含该 cmdlet 的可搜索和可配置的帮助。</span><span class="sxs-lookup"><span data-stu-id="18db9-225">In Windows PowerShell ISE 3.0 and later, a window opens that contains the help for the cmdlet that is searchable and configurable.</span></span> <span data-ttu-id="18db9-226">此帮助体验是 Windows PowerShell ISE 3.0 的新增功能，可更新帮助是 Windows PowerShell 3.0 的新增功能。</span><span class="sxs-lookup"><span data-stu-id="18db9-226">This Help experience is new for Windows PowerShell ISE 3.0, and Updatable Help is new for Windows PowerShell 3.0.</span></span>

## <a name="show-command-cmdlet"></a><span data-ttu-id="18db9-227">Show-Command cmdlet</span><span class="sxs-lookup"><span data-stu-id="18db9-227">Show-Command cmdlet</span></span>

> <span data-ttu-id="18db9-228">在 PowerShell 3.0 中添加</span><span class="sxs-lookup"><span data-stu-id="18db9-228">Added in PowerShell 3.0</span></span>

<span data-ttu-id="18db9-229">`Show-Command` cmdlet 使你能够通过填写图形表单来编写或运行 cmdlet 或函数。</span><span class="sxs-lookup"><span data-stu-id="18db9-229">The `Show-Command` cmdlet enables you to compose or run a cmdlet or function by filling in a graphical form.</span></span> <span data-ttu-id="18db9-230">该表单使用户可在图形环境中使用 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="18db9-230">The form lets users work with Windows PowerShell in a graphical environment.</span></span>
<span data-ttu-id="18db9-231">`Show-Command` 还可以让高级脚本编写者快速创建基于 Windows PowerShell 的 GUI。</span><span class="sxs-lookup"><span data-stu-id="18db9-231">`Show-Command` also enables advanced scripters to create a quick Windows PowerShell-based GUI.</span></span>

<span data-ttu-id="18db9-232">**更改增添了什么价值？**</span><span class="sxs-lookup"><span data-stu-id="18db9-232">**What value does this change add?**</span></span>

<span data-ttu-id="18db9-233">通过在 Windows PowerShell 脚本中使用 `Show-Command`，可以为用户提供其熟悉的图形环境。</span><span class="sxs-lookup"><span data-stu-id="18db9-233">By using `Show-Command` in your Windows PowerShell scripts, you can provide your users with the graphical environment with which they're familiar.</span></span> <span data-ttu-id="18db9-234">`Show-Command` 还有助于引导用户了解 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="18db9-234">`Show-Command` can also help introductory users learn Windows PowerShell.</span></span>

<span data-ttu-id="18db9-235">**工作原理的不同之处是什么？**</span><span class="sxs-lookup"><span data-stu-id="18db9-235">**What works differently?**</span></span>

<span data-ttu-id="18db9-236">`Show-Command` 是新的 Windows PowerShell ISE 3.0。</span><span class="sxs-lookup"><span data-stu-id="18db9-236">`Show-Command` is new Windows PowerShell ISE 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="18db9-237">另请参阅</span><span class="sxs-lookup"><span data-stu-id="18db9-237">See also</span></span>

<span data-ttu-id="18db9-238">若要详细了解如何使用 Windows PowerShell ISE，请参阅[了解 Windows PowerShell 集成脚本环境](../components/ise/exploring-the-windows-powershell-ise.md)。</span><span class="sxs-lookup"><span data-stu-id="18db9-238">For more information about using Windows PowerShell ISE, see [Exploring the Windows PowerShell Integrated Scripting Environment](../components/ise/exploring-the-windows-powershell-ise.md).</span></span>
