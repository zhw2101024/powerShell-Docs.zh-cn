---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "PowerShell 50 ISE 中的新增功能"
ms.assetid: 38648d47-7c27-4b37-a40e-ad29948519c2
ms.openlocfilehash: 89dcc905ce200d06029e148c9675269e6f518fa3
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/29/2017
---
# <a name="what39s-new-in-the-windows-powershell-ise"></a><span data-ttu-id="1e5f2-103">Windows PowerShell ISE 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="1e5f2-103">What&#39;s New in the Windows PowerShell ISE</span></span>
<span data-ttu-id="1e5f2-104">本主题介绍已在 Windows PowerShell (R) 集成脚本环境 (ISE) 的各版本中引入的新增功能和更新功能。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-104">This topic explains the new and updated features that have been introduced in versions of Windows PowerShell  Integrated Scripting Environment (ISE).</span></span>

## <a name="feature-description"></a><span data-ttu-id="1e5f2-105">功能描述</span><span class="sxs-lookup"><span data-stu-id="1e5f2-105">Feature description</span></span>
<span data-ttu-id="1e5f2-106">Windows PowerShell ISE 是一款主机应用程序，让你可以在直观的图形环境中编写、运行和测试脚本与模块。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-106">The Windows PowerShell ISE is a host application that enables you to write, run, and test scripts and modules in a graphical and intuitive environment.</span></span> <span data-ttu-id="1e5f2-107">其主要功能，如语法着色、Tab 自动补全、可视调试、Unicode 遵从和上下文相关帮助，将为你带来丰富的脚本编写体验。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-107">Key features such as syntax-coloring, tab completion, visual debugging, Unicode compliance, and context-sensitive Help provide a rich scripting experience.</span></span>

<span data-ttu-id="1e5f2-108">有关 Windows PowerShell ISE 的概述，请参阅 [Windows PowerShell 集成脚本环境概述](https://technet.microsoft.com/en-us/library/3c1892c2-bf84-4cb6-af26-1f453be9e671)。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-108">For an overview of Windows PowerShell ISE, see [Windows PowerShell Integrated Scripting Environment overview](https://technet.microsoft.com/en-us/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).</span></span>

## <a name="new-and-changed-functionality-in-windows-powershell-ise"></a><span data-ttu-id="1e5f2-109">Windows PowerShell ISE 中的新增功能和更改功能</span><span class="sxs-lookup"><span data-stu-id="1e5f2-109">New and changed functionality in Windows PowerShell ISE</span></span>
<span data-ttu-id="1e5f2-110">下表列出了 Windows PowerShell 中此版本的 Windows PowerShell ISE 的新增功能和更改功能。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-110">The following table lists the new and changed features for this release of Windows PowerShell ISE in Windows PowerShell.</span></span>

|<span data-ttu-id="1e5f2-111">特性/功能</span><span class="sxs-lookup"><span data-stu-id="1e5f2-111">Feature/functionality</span></span>|<span data-ttu-id="1e5f2-112">Windows PowerShell ISE 4.0</span><span class="sxs-lookup"><span data-stu-id="1e5f2-112">Windows PowerShell ISE 4.0</span></span>|<span data-ttu-id="1e5f2-113">Windows PowerShell ISE 3.0</span><span class="sxs-lookup"><span data-stu-id="1e5f2-113">Windows PowerShell ISE 3.0</span></span>|<span data-ttu-id="1e5f2-114">Windows PowerShell ISE 2.0</span><span class="sxs-lookup"><span data-stu-id="1e5f2-114">Windows PowerShell ISE 2.0</span></span>|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|<span data-ttu-id="1e5f2-115">**[IntelliSense](#intellisense)**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-115">**[IntelliSense](#intellisense)**</span></span>|<span data-ttu-id="1e5f2-116">X</span><span class="sxs-lookup"><span data-stu-id="1e5f2-116">X</span></span>|<span data-ttu-id="1e5f2-117">X</span><span class="sxs-lookup"><span data-stu-id="1e5f2-117">X</span></span>||
|<span data-ttu-id="1e5f2-118">**[代码段](#snippets)**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-118">**[Snippets](#snippets)**</span></span>|<span data-ttu-id="1e5f2-119">X</span><span class="sxs-lookup"><span data-stu-id="1e5f2-119">X</span></span>|<span data-ttu-id="1e5f2-120">X</span><span class="sxs-lookup"><span data-stu-id="1e5f2-120">X</span></span>||
|<span data-ttu-id="1e5f2-121">**[外接程序工具](#add-on-tools)**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-121">**[Add-on Tools](#add-on-tools)**</span></span>|<span data-ttu-id="1e5f2-122">X</span><span class="sxs-lookup"><span data-stu-id="1e5f2-122">X</span></span>|<span data-ttu-id="1e5f2-123">X</span><span class="sxs-lookup"><span data-stu-id="1e5f2-123">X</span></span>||
|<span data-ttu-id="1e5f2-124">**[重启管理器和自动保存](#restart-manager-and-auto-save)**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-124">**[Restart Manager and Auto-save](#restart-manager-and-auto-save)**</span></span>|<span data-ttu-id="1e5f2-125">X</span><span class="sxs-lookup"><span data-stu-id="1e5f2-125">X</span></span>|<span data-ttu-id="1e5f2-126">X</span><span class="sxs-lookup"><span data-stu-id="1e5f2-126">X</span></span>||
|<span data-ttu-id="1e5f2-127">**[最近使用的列表](#most-recently-used-list)**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-127">**[Most-recently used list](#most-recently-used-list)**</span></span>|<span data-ttu-id="1e5f2-128">X</span><span class="sxs-lookup"><span data-stu-id="1e5f2-128">X</span></span>|<span data-ttu-id="1e5f2-129">X</span><span class="sxs-lookup"><span data-stu-id="1e5f2-129">X</span></span>||
|<span data-ttu-id="1e5f2-130">**[控制台窗格](#console-pane)**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-130">**[Console Pane](#console-pane)**</span></span>|<span data-ttu-id="1e5f2-131">X</span><span class="sxs-lookup"><span data-stu-id="1e5f2-131">X</span></span>|<span data-ttu-id="1e5f2-132">X</span><span class="sxs-lookup"><span data-stu-id="1e5f2-132">X</span></span>||
|<span data-ttu-id="1e5f2-133">**[命令行开关](#command-line-switches)**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-133">**[Command-line switches](#command-line-switches)**</span></span>|<span data-ttu-id="1e5f2-134">X</span><span class="sxs-lookup"><span data-stu-id="1e5f2-134">X</span></span>|<span data-ttu-id="1e5f2-135">X</span><span class="sxs-lookup"><span data-stu-id="1e5f2-135">X</span></span>||
|<span data-ttu-id="1e5f2-136">**[新的编辑器功能](#new-editor-features)**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-136">**[New editor features](#new-editor-features)**</span></span>|<span data-ttu-id="1e5f2-137">X</span><span class="sxs-lookup"><span data-stu-id="1e5f2-137">X</span></span>|<span data-ttu-id="1e5f2-138">X</span><span class="sxs-lookup"><span data-stu-id="1e5f2-138">X</span></span>||
|<span data-ttu-id="1e5f2-139">**[新的帮助查看器窗口](#new-help-viewer-window)**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-139">**[New Help viewer window](#new-help-viewer-window)**</span></span>|<span data-ttu-id="1e5f2-140">X</span><span class="sxs-lookup"><span data-stu-id="1e5f2-140">X</span></span>|<span data-ttu-id="1e5f2-141">X</span><span class="sxs-lookup"><span data-stu-id="1e5f2-141">X</span></span>||
|<span data-ttu-id="1e5f2-142">**[Show-Command cmdlet](#show-command-cmdlet)**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-142">**[Show-Command cmdlet](#show-command-cmdlet)**</span></span>|<span data-ttu-id="1e5f2-143">X</span><span class="sxs-lookup"><span data-stu-id="1e5f2-143">X</span></span>|<span data-ttu-id="1e5f2-144">X</span><span class="sxs-lookup"><span data-stu-id="1e5f2-144">X</span></span>||

### <a name="intellisense"></a><span data-ttu-id="1e5f2-145">Intellisense</span><span class="sxs-lookup"><span data-stu-id="1e5f2-145">IntelliSense</span></span>
<span data-ttu-id="1e5f2-146">**在 ISE 3.0 中添加**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-146">**Added in ISE 3.0**</span></span>

<span data-ttu-id="1e5f2-147">Intellisense 是一个自动完成辅助功能，是 Windows PowerShell ISE 的一部分。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-147">IntelliSense is an automatic-completion assistance feature that is part of Windows PowerShell ISE.</span></span> <span data-ttu-id="1e5f2-148">Intellisense 会在你键入时显示可单击的菜单，其中包括可能匹配的 cmdlet、参数、参数值、文件或文件夹。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-148">IntelliSense displays clickable menus of potentially matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="1e5f2-149">**更改增添了什么价值？**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-149">**What value does this change add?**</span></span>

<span data-ttu-id="1e5f2-150">新增 Intellisense 功能后，使用 Windows PowerShell ISE 创建脚本时，可以更容易地发现 cmdlet 和语法。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-150">With the addition of IntelliSense, it is easier to discover cmdlets and syntax when you use Windows PowerShell ISE to create scripts.</span></span> <span data-ttu-id="1e5f2-151">在创建新脚本时，还可以使用 Windows PowerShell ISE 了解 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-151">You can also use Windows PowerShell ISE to learn Windows PowerShell while you create new scripts.</span></span>

<span data-ttu-id="1e5f2-152">**工作原理的不同之处是什么？**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-152">**What works differently?**</span></span>

<span data-ttu-id="1e5f2-153">当在 Windows PowerShell ISE 3.0 或更高版本中键入 cmdlet 时，会显示一个可滚动和可点击的菜单，并可在其中浏览和选择适当的命令。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-153">When you type cmdlets in the Windows PowerShell ISE 3.0 or later, a scrollable and clickable menu displays, allowing you to browse and select the appropriate commands.</span></span>

### <a name="snippets"></a><span data-ttu-id="1e5f2-154">代码段</span><span class="sxs-lookup"><span data-stu-id="1e5f2-154">Snippets</span></span>
<span data-ttu-id="1e5f2-155">**在 ISE 3.0 中添加**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-155">**Added in ISE 3.0**</span></span>

<span data-ttu-id="1e5f2-156">*代码段*是 Windows PowerShell 代码的一小部分，它可以插入到你在 Windows PowerShell ISE 中创建的脚本。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-156">*Snippets* are short sections of Windows PowerShell code that you can insert into the scripts you create in Windows PowerShell ISE.</span></span> <span data-ttu-id="1e5f2-157">Windows PowerShell ISE 附带一组默认的代码段。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-157">Windows PowerShell ISE comes with a default set of snippets.</span></span> <span data-ttu-id="1e5f2-158">在 Windows PowerShell ISE 中工作时，可使用 **New\-Snippet** cmdlet 添加代码段。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-158">You can add snippets by using the **New-Snippet** cmdlet while working in Windows PowerShell ISE.</span></span>

<span data-ttu-id="1e5f2-159">**更改增添了什么价值？**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-159">**What value does this change add?**</span></span>

<span data-ttu-id="1e5f2-160">通过使用代码段，可以快速组建脚本以自动运行你的环境。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-160">By using snippets, you can quickly assemble and create scripts to automate your environment.</span></span>

<span data-ttu-id="1e5f2-161">**工作原理的不同之处是什么？**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-161">**What works differently?**</span></span>

<span data-ttu-id="1e5f2-162">若要在 Windows PowerShell 3.0 或更高版本中使用代码段，请在“编辑”菜单上，单击“启动代码段”，或按**Ctrl\-J**。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-162">To use snippets in Windows PowerShell 3.0 or later, on the **Edit** menu, click **Start Snippets**, or press **Ctrl-J**.</span></span>

### <a name="add-on-tools"></a><span data-ttu-id="1e5f2-163">附加工具</span><span class="sxs-lookup"><span data-stu-id="1e5f2-163">Add-on tools</span></span>
<span data-ttu-id="1e5f2-164">**在 PowerShell 3.0 中添加**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-164">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="1e5f2-165">Windows PowerShell ISE 现在支持附加工具，这些工具是通过使用对象模型添加的 Windows Presentation Foundation (WPF) 控件。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-165">Windows PowerShell ISE now supports add-on tools, which are Windows Presentation Foundation (WPF) controls that are added by using the object model.</span></span> <span data-ttu-id="1e5f2-166">附加工具可以在控制台中显示为垂直或水平窗格。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-166">Add-on tools can be displayed as a vertical or horizontal pane in the console.</span></span> <span data-ttu-id="1e5f2-167">窗格中的多个附加工具会显示为选项卡式控件。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-167">Multiple add-on tools in a pane are displayed as a tabbed control.</span></span> <span data-ttu-id="1e5f2-168">你还可以添加或删除由 Microsoft 以外的参与方创建的附加工具。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-168">You can also add or remove add-on tools that are produced by non-Microsoft parties.</span></span> <span data-ttu-id="1e5f2-169">有关如何导入或删除附加工具的详细信息，请参阅 [Windows PowerShell ISE 操作](http://technet.microsoft.com/library/cc732148.aspx)。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-169">For more information about how to import or remove add-on tools, see [Windows PowerShell ISE Operations](http://technet.microsoft.com/library/cc732148.aspx).</span></span>

<span data-ttu-id="1e5f2-170">**更改增添了什么价值？**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-170">**What value does this change add?**</span></span>

<span data-ttu-id="1e5f2-171">附加工具可以改善你的脚本编写体验，使用这些工具可以扩展和自定义 Windows PowerShell ISE，或者向 Windows PowerShell ISE 添加新的功能。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-171">Add-ons allow you to extend and customize Windows PowerShell ISE with tools that can enhance your scripting experience or add functionality to Windows PowerShell ISE.</span></span>

<span data-ttu-id="1e5f2-172">**工作原理的不同之处是什么？**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-172">**What works differently?**</span></span>

<span data-ttu-id="1e5f2-173">Windows PowerShell ISE 3.0 及更高版本附带**命令**附加工具。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-173">Windows PowerShell ISE 3.0 and later come with the **Commands** add-on.</span></span> <span data-ttu-id="1e5f2-174">借助**命令**附加工具可以浏览 cmdlet，以及使用**脚本**和**控制台**窗格并行访问有关 cmdlet 的帮助。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-174">The **Commands** add-on allows you to browse cmdlets, and access help about the cmdlets side-by-side with the **Script** and **Console** Panes.</span></span>

<span data-ttu-id="1e5f2-175">可通过使用“附加工具”菜单上的“打开附加工具网站”命令找到其他附加工具。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-175">Additional add-ons can be found by using the **Open Add-on Tools Website** command on the **Add-ons** menu.</span></span>

### <a name="restart-manager-and-auto-save"></a><span data-ttu-id="1e5f2-176">重启管理器和自动保存</span><span class="sxs-lookup"><span data-stu-id="1e5f2-176">Restart manager and auto-save</span></span>
<span data-ttu-id="1e5f2-177">**在 PowerShell 3.0 中添加**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-177">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="1e5f2-178">Windows PowerShell ISE 每隔两分钟在单独的位置上自动保存你打开的脚本。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-178">Windows PowerShell ISE now automatically saves your open scripts every two minutes, in a separate location.</span></span>  <span data-ttu-id="1e5f2-179">如果 Windows PowerShell ISE 停止工作或操作系统重新启动，则重新启动 Windows PowerShell ISE 后，它会恢复上次会话中打开的脚本（即使你未保存这些脚本）。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-179">If Windows PowerShell ISE stops working, or if the operating system is restarted, after Windows PowerShell ISE restarts, it recovers scripts that were open in the last session, even if the scripts were not saved.</span></span>

<span data-ttu-id="1e5f2-180">要更改自动保存间隔，可在控制台窗格中运行下面的命令：**$psise.Options.AutoSaveMinuteInterval**。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-180">To change the automatic saving interval, run the following command in the Console pane: **$psise.Options.AutoSaveMinuteInterval**.</span></span>

<span data-ttu-id="1e5f2-181">**更改增添了什么价值？**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-181">**What value does this change add?**</span></span>

<span data-ttu-id="1e5f2-182">你已经了解意外重启时将自动保存你打开的脚本，现在便可以在 Windows PowerShell ISE 中工作了。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-182">You can now work within Windows PowerShell ISE knowing that your open scripts are automatically saved in the event of an unexpected restart.</span></span>

<span data-ttu-id="1e5f2-183">**工作原理的不同之处是什么？**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-183">**What works differently?**</span></span>

<span data-ttu-id="1e5f2-184">Windows PowerShell ISE 2.0 在发生意外重启时不会自动保存脚本。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-184">Windows PowerShell ISE 2.0 does not save the scripts automatically in the event of a restart.</span></span>

### <a name="most-recently-used-list"></a><span data-ttu-id="1e5f2-185">最近使用的列表</span><span class="sxs-lookup"><span data-stu-id="1e5f2-185">Most-recently used list</span></span>
<span data-ttu-id="1e5f2-186">**在 PowerShell 3.0 中添加**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-186">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="1e5f2-187">Windows PowerShell ISE 现在具有最近使用过的文件列表。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-187">Windows PowerShell ISE now has a most-recently used list for files.</span></span> <span data-ttu-id="1e5f2-188">在 Windows PowerShell ISE 中打开文件时，文件会添加到“文件”菜单上的最近使用列表中。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-188">When you open a file in Windows PowerShell ISE, the file is added to the most-recently used list on the **File** menu.</span></span>

<span data-ttu-id="1e5f2-189">若要更改最近使用列表中的文件默认数量，请在控制台窗格中运行以下命令：**$psise.Options.MruCount**。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-189">To change the default number of files in the most-recently used list, run the following command in the Console Pane: **$psise.Options.MruCount**.</span></span>

<span data-ttu-id="1e5f2-190">**更改增添了什么价值？**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-190">**What value does this change add?**</span></span>

<span data-ttu-id="1e5f2-191">现在可以使用最近使用列表轻松地访问频繁使用的文件。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-191">You can now use the most-recently used list to easily access your frequently-used files.</span></span>

<span data-ttu-id="1e5f2-192">**工作原理的不同之处是什么？**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-192">**What works differently?**</span></span>

<span data-ttu-id="1e5f2-193">Windows PowerShell ISE 2.0 没有最近使用列表。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-193">Windows PowerShell ISE 2.0 does not have a most-recently used list.</span></span>

### <a name="console-pane"></a><span data-ttu-id="1e5f2-194">控制台窗格</span><span class="sxs-lookup"><span data-stu-id="1e5f2-194">Console Pane</span></span>
<span data-ttu-id="1e5f2-195">**在 PowerShell 3.0 中添加**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-195">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="1e5f2-196">第一版 Windows PowerShell ISE 中可用的单独的命令窗格和输出窗格现在合并成了一个控制台窗格。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-196">The separate Command and Output Panes that were available in the first release of Windows PowerShell ISE have been combined into a single Console Pane.</span></span> <span data-ttu-id="1e5f2-197">该控制台窗格的功能和外观与典型的 Windows PowerShell 控制台类似，但经过了以下改进（本主题对其中大多数进行了介绍）。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-197">The Console Pane is similar in function and appearance to a typical Windows PowerShell console, but it includes the following enhancements (most are described in this topic).</span></span>

- <span data-ttu-id="1e5f2-198">用于输入文本（而非输出文本）的语法着色，包括 XML 语法</span><span class="sxs-lookup"><span data-stu-id="1e5f2-198">Syntax coloring for input text (not output text), including XML syntax</span></span>

- <span data-ttu-id="1e5f2-199">Intellisense</span><span class="sxs-lookup"><span data-stu-id="1e5f2-199">IntelliSense</span></span>

- <span data-ttu-id="1e5f2-200">大括号匹配</span><span class="sxs-lookup"><span data-stu-id="1e5f2-200">Brace matching</span></span>

- <span data-ttu-id="1e5f2-201">错误指示</span><span class="sxs-lookup"><span data-stu-id="1e5f2-201">Error indication</span></span>

- <span data-ttu-id="1e5f2-202">对 Unicode 的完全支持</span><span class="sxs-lookup"><span data-stu-id="1e5f2-202">Full Unicode support</span></span>

- <span data-ttu-id="1e5f2-203">**F1** 上下文相关帮助</span><span class="sxs-lookup"><span data-stu-id="1e5f2-203">**F1** context-sensitive help</span></span>

- <span data-ttu-id="1e5f2-204">**Ctrl+F1** 上下文相关的 Show-Command</span><span class="sxs-lookup"><span data-stu-id="1e5f2-204">**Ctrl+F1** context-sensitive Show-Command</span></span>

- <span data-ttu-id="1e5f2-205">对复杂脚本和从右向左语言的支持</span><span class="sxs-lookup"><span data-stu-id="1e5f2-205">Complex script and right-to-left support</span></span>

- <span data-ttu-id="1e5f2-206">字体支持</span><span class="sxs-lookup"><span data-stu-id="1e5f2-206">Font support</span></span>

- <span data-ttu-id="1e5f2-207">缩放</span><span class="sxs-lookup"><span data-stu-id="1e5f2-207">Zoom</span></span>

- <span data-ttu-id="1e5f2-208">行选择模式和块选择模式</span><span class="sxs-lookup"><span data-stu-id="1e5f2-208">Line-select and block-select modes</span></span>

- <span data-ttu-id="1e5f2-209">当你在控制台中按“向上”箭头查看历史记录时，命令行处会保留你所键入的内容</span><span class="sxs-lookup"><span data-stu-id="1e5f2-209">Preservation of typed content at the command line when you press the **Up** arrow to view history in the console</span></span>

<span data-ttu-id="1e5f2-210">**更改增添了什么价值？**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-210">**What value does this change add?**</span></span>

<span data-ttu-id="1e5f2-211">这些新增的控制台窗格变化提供了与控制台界面更加一致的脚本编写体验。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-211">The addition of these Console Pane changes provides a scripting experience that is more consistent with the console interface.</span></span>

<span data-ttu-id="1e5f2-212">**工作原理的不同之处是什么？**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-212">**What works differently?**</span></span>

<span data-ttu-id="1e5f2-213">Windows PowerShell ISE 2.0 具有单独的命令和输出窗格。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-213">Windows PowerShell ISE 2.0 has separate Command and Output Panes.</span></span>

### <a name="command-line-switches"></a><span data-ttu-id="1e5f2-214">命令行开关</span><span class="sxs-lookup"><span data-stu-id="1e5f2-214">Command-line switches</span></span>
<span data-ttu-id="1e5f2-215">**在 PowerShell 3.0 中添加**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-215">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="1e5f2-216">如果从命令行（通过键入 **powershell_ise.exe**）启动 Windows PowerShell ISE，则可以添加下列新的命令行开关。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-216">If you start Windows PowerShell ISE from the command line (by typing **powershell_ise.exe**), you can add the following new command-line switches.</span></span>

- <span data-ttu-id="1e5f2-217">-NoProfile：在不运行 **$profile** 的情况下启动 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="1e5f2-217">*-NoProfile*: Starts Windows PowerShell ISE without running **$profile**</span></span>

- <span data-ttu-id="1e5f2-218">-Help：显示帮助窗口</span><span class="sxs-lookup"><span data-stu-id="1e5f2-218">*-Help*: Displays a Help window</span></span>

- <span data-ttu-id="1e5f2-219">-mta：在多线程的单元模式下启动 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-219">*-mta*: Starts Windows PowerShell ISE in multithreaded apartment mode.</span></span> <span data-ttu-id="1e5f2-220">Windows PowerShell ISE 的默认操作模式是单线程的单元模式，或 *-sta*。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-220">The default operation mode for Windows PowerShell ISE is single-threaded apartment mode, or *-sta*.</span></span>

<span data-ttu-id="1e5f2-221">**更改增添了什么价值？**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-221">**What value does this change add?**</span></span>

<span data-ttu-id="1e5f2-222">这些新增的命令行开关使你能够控制运行 Windows PowerShell ISE 的环境。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-222">The addition of these command-line switches allows you to control the environment in which the Windows PowerShell ISE runs.</span></span>

<span data-ttu-id="1e5f2-223">**工作原理的不同之处是什么？**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-223">**What works differently?**</span></span>

<span data-ttu-id="1e5f2-224">Windows PowerShell ISE 2.0 不识别这些命令行开关。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-224">Windows PowerShell ISE 2.0 does not recognize these command-line switches.</span></span>

### <a name="new-editor-features"></a><span data-ttu-id="1e5f2-225">新的编辑器功能</span><span class="sxs-lookup"><span data-stu-id="1e5f2-225">New editor features</span></span>
<span data-ttu-id="1e5f2-226">**在 PowerShell 3.0 中添加**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-226">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="1e5f2-227">其他 Windows PowerShell ISE 编辑功能包括：</span><span class="sxs-lookup"><span data-stu-id="1e5f2-227">Other Windows PowerShell ISE editing features include:</span></span>

- <span data-ttu-id="1e5f2-228">**XML 语法着色**Windows PowerShell ISE 现在以对 Windows PowerShell 语法进行着色的相同方法对 XML 语法进行着色。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-228">**XML syntax coloring**Windows PowerShell ISE now colors XML syntax in the same way as it colors Windows PowerShell syntax.</span></span>

- <span data-ttu-id="1e5f2-229">**大括号匹配** Windows PowerShell ISE 包括大括号匹配和突出显示，并可以通过以下方式使用：（例如，如果已选择左大括号，则可使用 **Go to Match** 命令或 **Ctrl + ]** 定位右大括号）。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-229">**Brace matching** Windows PowerShell ISE includes brace matching and highlighting, and can be used in the following ways: (for example, using the **Go to Match** command or **Ctrl + ]** locates the closing brace, if you have an opening brace selected).</span></span>

- <span data-ttu-id="1e5f2-230">**大纲视图** 脚本窗格支持大纲显示，允许通过单击左边距中的 (+) 或 (-) 来实现代码段的折叠或展开。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-230">**Outline view** The Script Pane supports outlining, which allows collapsing or expanding sections of code by clicking plus or minus signs in the left margin.</span></span> <span data-ttu-id="1e5f2-231">你可以使用大括号或 **#region** 和 **#endregion** 标记来标记可折叠段的开头或末尾。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-231">You can use braces or the **#region** and **#endregion** tags to mark the beginning or end of a collapsible section.</span></span> <span data-ttu-id="1e5f2-232">若要展开或折叠所有区域，请按 **Ctrl + M**。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-232">To expand or collapse all regions, press **Ctrl + M**.</span></span>

- <span data-ttu-id="1e5f2-233">**拖放文本编辑**Windows PowerShell ISE 现在支持拖放文本编辑。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-233">**Drag and drop text editing**Windows PowerShell ISE now supports drag and drop text editing.</span></span> <span data-ttu-id="1e5f2-234">可以选择任何文本块，并通过将该文本拖动到编辑器或控制台中的另一个位置来移动文本。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-234">You can select any block of text and drag that text to another location in the editor or the console to move the text.</span></span> <span data-ttu-id="1e5f2-235">如果拖动所选文本时按住 Ctrl 键不放，则释放鼠标按钮时，文本便会复制到新位置。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-235">If you hold down the Ctrl key while you drag the selected text, when you release the mouse button the text is copied to the new location.</span></span> <span data-ttu-id="1e5f2-236">在此版本的 Windows PowerShell ISE 以及以前版本的 Windows PowerShell ISE 中，当您将文件拖放到 Windows PowerShell ISE 中，Windows PowerShell ISE 会打开该文件。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-236">In this version of Windows PowerShell ISE, as well as the previous version of Windows PowerShell ISE, when you drag and drop files onto Windows PowerShell ISE, Windows PowerShell ISE opens the file.</span></span>

- <span data-ttu-id="1e5f2-237">**分析错误显示** 分析错误用红色下划线指示。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-237">**Parse error display** Parse errors are indicated with red underlines.</span></span> <span data-ttu-id="1e5f2-238">当你将鼠标悬停在某个指示的错误上时，工具提示文本会显示在代码中发现的问题。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-238">When you hover over an indicated error, tooltip text displays the problem that was found in the code.</span></span>

- <span data-ttu-id="1e5f2-239">缩放：可以通过使用缩放滑块（位于 Windows PowerShell ISE 窗口右下角），或在控制台窗格中输入命令 $psise.options.Zoom 来设置控制台内容的缩放百分比。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-239">**Zoom** The zoom percentage of the console'™s content can be set by using the zoom slider (in the lower right corner of Windows PowerShell ISE window), or by entering the command **$psise.options.Zoom** in the Console Pane.</span></span>

- <span data-ttu-id="1e5f2-240">**富文本复制和粘贴** 在 Windows PowerShell ISE 中将内容复制到剪贴板时，会保留原选定内容的字体、大小和颜色信息。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-240">**Rich text copy and paste** Copying to the clipboard in Windows PowerShell ISE preserves the font, size, and color information of the original selection.</span></span>

- <span data-ttu-id="1e5f2-241">**块选择** 你可以通过在用鼠标选定脚本窗格中文本的同时按住 ALT 键，或通过按 **Alt+Shift+箭头**键来选定文本块。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-241">**Block selection** You can select a block of text by holding down the ALT key while selecting text in the Script Pane with your mouse, or by pressing **Alt+Shift+Arrow**.</span></span>

<span data-ttu-id="1e5f2-242">**更改增添了什么价值？**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-242">**What value does this change add?**</span></span>

<span data-ttu-id="1e5f2-243">这些新增的编辑功能提供更一致、更强大的编辑环境。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-243">The additional editing features provide a more consistent and powerful editing environment.</span></span>

<span data-ttu-id="1e5f2-244">**工作原理的不同之处是什么？**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-244">**What works differently?**</span></span>

<span data-ttu-id="1e5f2-245">Windows PowerShell ISE 2.0 中不具有这些编辑增强功能。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-245">These editing enhancements were not present in Windows PowerShell ISE 2.0.</span></span>

### <a name="new-help-viewer-window"></a><span data-ttu-id="1e5f2-246">新的帮助查看器窗口</span><span class="sxs-lookup"><span data-stu-id="1e5f2-246">New Help viewer window</span></span>
<span data-ttu-id="1e5f2-247">**在 PowerShell 3.0 中添加**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-247">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="1e5f2-248">当你将光标置于某个 cmdlet 中，或突出显示某个 cmdlet 的一部分时，按 **F1** 会打开新的帮助查看器，其中显示了有关突出显示的 cmdlet 的上下文相关帮助。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-248">If you press **F1** when your cursor is in a cmdlet, or you have part of a cmdlet highlighted, the new Help viewer opens context-sensitive Help about the highlighted cmdlet.</span></span> <span data-ttu-id="1e5f2-249">要显示 Windows PowerShell 的“关于”帮助，可在控制台窗格中键入**operators**，然后按**F1**。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-249">To display Windows PowerShell About help, type  **operators** in the console pane, and then press **F1**.</span></span>

<span data-ttu-id="1e5f2-250">使用此功能之前，必须先从 Microsoft 网站下载最新版本的 Windows PowerShell 帮助主题。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-250">Before you use this feature, download the most current version of Windows PowerShell Help topics from the Microsoft website.</span></span> <span data-ttu-id="1e5f2-251">当你以管理员身份运行 Windows PowerShell ISE 时，下载“帮助”主题的最简单方法是在控制台窗格中运行 **Update-Help** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-251">The simplest method for downloading the Help topics is to run the **Update-Help** cmdlet in the Console Pane when running Windows PowerShell ISE as administrator.</span></span>

<span data-ttu-id="1e5f2-252">可以修改 **F1** 键寻找帮助的位置。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-252">You can alter where the **F1** key looks for Help.</span></span> <span data-ttu-id="1e5f2-253">在“工具”/“选项”菜单中“常规设置”选项卡上的“其他设置”下，可以设置或清除复选框“使用本地帮助内容而非联机内容”。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-253">In the **Tools**/**Options** menu, on the **General Settings** tab, under **Other Settings**, you can set or clear the checkbox **Use local help content instead of online content**.</span></span> <span data-ttu-id="1e5f2-254">如果勾选了此复选框，客户端便会在模块文件夹中的已下载帮助中查找 cmdlet 帮助。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-254">If checked, then the client looks for the cmdlet Help in the downloaded Help found in the modules folder.</span></span>  <span data-ttu-id="1e5f2-255">如果清除了该复选框，则客户端会在 TechNet 库中查找 cmdlet 帮助。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-255">If the checkbox is cleared, then the client looks on the TechNet library for the cmdlet help.</span></span>

<span data-ttu-id="1e5f2-256">**更改增添了什么价值？**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-256">**What value does this change add?**</span></span>

<span data-ttu-id="1e5f2-257">在无需离开当前 cmdlet 或脚本的情况下，上下文相关帮助提供了无缝的学习体验。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-257">Context-sensitive Help without leaving your current cmdlet or script provides a seamless learning experience.</span></span>

<span data-ttu-id="1e5f2-258">**工作原理的不同之处是什么？**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-258">**What works differently?**</span></span>

<span data-ttu-id="1e5f2-259">在 Windows PowerShell ISE 的早期版本中按 F1 会打开本地计算机上的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-259">Pressing F1 in previous versions of Windows PowerShell ISE opened the help file on the local computer.</span></span> <span data-ttu-id="1e5f2-260">在 Windows PowerShell ISE 3.0 及更高版本中，会打开一个窗口，其中包含该 cmdlet 的可搜索和可配置的帮助。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-260">In Windows PowerShell ISE 3.0 and later, a window opens that contains the help for the cmdlet that is searchable and configurable.</span></span> <span data-ttu-id="1e5f2-261">此帮助体验是 Windows PowerShell ISE 3.0 的新增功能，可更新帮助是 Windows PowerShell 3.0 的新增功能。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-261">This Help experience is new for Windows PowerShell ISE 3.0, and Updatable Help is new for Windows PowerShell 3.0.</span></span>

### <a name="show-command-cmdlet"></a><span data-ttu-id="1e5f2-262">Show-Command cmdlet</span><span class="sxs-lookup"><span data-stu-id="1e5f2-262">Show-Command cmdlet</span></span>
<span data-ttu-id="1e5f2-263">**在 PowerShell 3.0 中添加**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-263">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="1e5f2-264">**Show-Command** cmdlet 使你能够通过填写图形表单来编写或运行 cmdlet 或函数。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-264">The **Show-Command** cmdlet enables you to compose or run a cmdlet or function by filling in a graphical form.</span></span> <span data-ttu-id="1e5f2-265">该表单使用户可在图形环境中使用 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-265">The form lets users work with Windows PowerShell in a graphical environment.</span></span> <span data-ttu-id="1e5f2-266">**Show-Command** 还可以让高级脚本编写者快速创建基于 Windows PowerShell 的 GUI。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-266">**Show-Command** also enables advanced scripters to create a quick Windows PowerShell-based GUI.</span></span>

<span data-ttu-id="1e5f2-267">**更改增添了什么价值？**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-267">**What value does this change add?**</span></span>

<span data-ttu-id="1e5f2-268">通过在 Windows PowerShell 脚本中使用 **Show-Command**，可以为用户提供其熟悉的图形环境。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-268">By using **Show-Command** in your Windows PowerShell scripts, you can provide your users with the graphical environment with which they are familiar.</span></span> <span data-ttu-id="1e5f2-269">**Show-Command** 还有助于初级用户了解 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-269">**Show-Command** can also help introductory users learn Windows PowerShell.</span></span>

<span data-ttu-id="1e5f2-270">**工作原理的不同之处是什么？**</span><span class="sxs-lookup"><span data-stu-id="1e5f2-270">**What works differently?**</span></span>

<span data-ttu-id="1e5f2-271">Show-Command 是新的 Windows PowerShell ISE 3.0。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-271">Show-Command is new Windows PowerShell ISE 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="1e5f2-272">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1e5f2-272">See also</span></span>
<span data-ttu-id="1e5f2-273">有关在 Windows PowerShell 中使用 Windows PowerShell ISE 的详细信息，请参阅以下链接。</span><span class="sxs-lookup"><span data-stu-id="1e5f2-273">For more information about using Windows PowerShell ISE in Windows PowerShell, see the following links.</span></span>

- [<span data-ttu-id="1e5f2-274">使用 Windows PowerShell 集成脚本环境</span><span class="sxs-lookup"><span data-stu-id="1e5f2-274">Using the Windows PowerShell Integrated Scripting Environment</span></span>](../core-powershell/ise/Using-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="1e5f2-275">TechNet Wiki 上的 ISE</span><span class="sxs-lookup"><span data-stu-id="1e5f2-275">ISE on the TechNet Wiki</span></span>](http://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)
- [<span data-ttu-id="1e5f2-276">脚本中心</span><span class="sxs-lookup"><span data-stu-id="1e5f2-276">Script Center</span></span>](http://technet.microsoft.com/scriptcenter/default)

