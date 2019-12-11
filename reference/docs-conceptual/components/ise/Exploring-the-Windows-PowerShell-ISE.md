---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 探究 Windows PowerShell ISE
ms.openlocfilehash: 7949b690cda73148f07922985b1fc30fe1e8b2d0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74117438"
---
# <a name="exploring-the-windows-powershell-ise"></a><span data-ttu-id="2643d-103">探究 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="2643d-103">Exploring the Windows PowerShell ISE</span></span>

<span data-ttu-id="2643d-104">可以使用 Windows PowerShell® 集成脚本环境 (ISE) 来创建、运行及调试命令和脚本。</span><span class="sxs-lookup"><span data-stu-id="2643d-104">You can use the Windows PowerShell® Integrated Scripting Environment (ISE) to create, run, and debug commands and scripts.</span></span> <span data-ttu-id="2643d-105">Windows PowerShell ISE 包含菜单栏、Windows PowerShell 选项卡、工具栏、脚本选项卡、脚本窗格、控制台窗格、状态栏、文字大小滑块和区分上下文的帮助。</span><span class="sxs-lookup"><span data-stu-id="2643d-105">The Windows PowerShell ISE consists of the menu bar, Windows PowerShell tabs, the toolbar, script tabs, a Script Pane, a Console Pane, a status bar, a text-size slider and context-sensitive Help.</span></span>

> [!NOTE]
> <span data-ttu-id="2643d-106">以 Windows PowerShell ISE 3.0 开头的命令和输出窗格已合并为单一的控制台窗格。</span><span class="sxs-lookup"><span data-stu-id="2643d-106">Beginning with Windows PowerShell ISE 3.0 the Command and Output Panes were combined into a single Console Pane.</span></span>

## <a name="menu-bar"></a><span data-ttu-id="2643d-107">菜单栏</span><span class="sxs-lookup"><span data-stu-id="2643d-107">Menu Bar</span></span>

<span data-ttu-id="2643d-108">菜单栏包含“**文件**”、“**编辑**”、“**视图**”、“**工具**”、“**调试**”、“**加载项**”和“**帮助**”菜单。</span><span class="sxs-lookup"><span data-stu-id="2643d-108">The menu bar contains the **File**, **Edit**, **View**, **Tools**, **Debug**, **Add-ons**, and **Help** menus.</span></span> <span data-ttu-id="2643d-109">菜单上的按钮允许执行与编写和运行脚本以及在 Windows PowerShell ISE 中运行命令相关的任务。</span><span class="sxs-lookup"><span data-stu-id="2643d-109">The buttons on the menus allow you to perform tasks related to writing and running scripts and running commands in the Windows PowerShell ISE.</span></span> <span data-ttu-id="2643d-110">此外，可以运行使用 [ISE 对象模型层次结构](object-model/The-ISE-Object-Model-Hierarchy.md)的脚本，将[加载项工具](object-model/The-ISEAddOnTool-Object.md)置于菜单栏中。</span><span class="sxs-lookup"><span data-stu-id="2643d-110">Additionally, an [add-on tool](object-model/The-ISEAddOnTool-Object.md) may be placed on the menu bar by running scripts that use the [The ISE Object Model Hierarchy](object-model/The-ISE-Object-Model-Hierarchy.md).</span></span>

> [!NOTE]
> <span data-ttu-id="2643d-111">在 Windows PowerShell ISE 2.0 中，不存在“**工具**”和“**加载项**”菜单。</span><span class="sxs-lookup"><span data-stu-id="2643d-111">In Windows PowerShell ISE 2.0, The **Tools** and **Add-ons** menus were not present.</span></span>

## <a name="windows-powershell-tabs"></a><span data-ttu-id="2643d-112">Windows PowerShell 选项卡</span><span class="sxs-lookup"><span data-stu-id="2643d-112">Windows PowerShell Tabs</span></span>

<span data-ttu-id="2643d-113">Windows PowerShell 选项卡是 Windows PowerShell 脚本可在其中运行的环境。</span><span class="sxs-lookup"><span data-stu-id="2643d-113">A Windows PowerShell tab is the environment in which a Windows PowerShell script runs.</span></span> <span data-ttu-id="2643d-114">可以在 Windows PowerShell ISE 中打开新的 Windows PowerShell 选项卡以在本地计算机或远程计算机上创建单独的环境。</span><span class="sxs-lookup"><span data-stu-id="2643d-114">You can open new Windows PowerShell tabs in the Windows PowerShell ISE to create separate environments on your local computer or on remote computers.</span></span> <span data-ttu-id="2643d-115">最多可同时打开八个 PowerShell 选项卡。</span><span class="sxs-lookup"><span data-stu-id="2643d-115">You may have a maximum of eight PowerShell tabs simultaneously open.</span></span>

## <a name="toolbar"></a><span data-ttu-id="2643d-116">工具栏</span><span class="sxs-lookup"><span data-stu-id="2643d-116">Toolbar</span></span>

<span data-ttu-id="2643d-117">下面的按钮位于工具栏上。</span><span class="sxs-lookup"><span data-stu-id="2643d-117">The following buttons are located on the toolbar.</span></span>

|<span data-ttu-id="2643d-118">按钮</span><span class="sxs-lookup"><span data-stu-id="2643d-118">Button</span></span>|<span data-ttu-id="2643d-119">功能</span><span class="sxs-lookup"><span data-stu-id="2643d-119">Function</span></span>|
|----------|------------|
|<span data-ttu-id="2643d-120">**新建**</span><span class="sxs-lookup"><span data-stu-id="2643d-120">**New**</span></span>|<span data-ttu-id="2643d-121">打开新脚本。</span><span class="sxs-lookup"><span data-stu-id="2643d-121">Opens a new script.</span></span>|
|<span data-ttu-id="2643d-122">**打开**</span><span class="sxs-lookup"><span data-stu-id="2643d-122">**Open**</span></span>|<span data-ttu-id="2643d-123">打开现有脚本或文件。</span><span class="sxs-lookup"><span data-stu-id="2643d-123">Opens an existing script or file.</span></span>|
|<span data-ttu-id="2643d-124">**保存**</span><span class="sxs-lookup"><span data-stu-id="2643d-124">**Save**</span></span>|<span data-ttu-id="2643d-125">保存脚本或文件。</span><span class="sxs-lookup"><span data-stu-id="2643d-125">Saves a script or file.</span></span>|
|<span data-ttu-id="2643d-126">**剪切**</span><span class="sxs-lookup"><span data-stu-id="2643d-126">**Cut**</span></span>|<span data-ttu-id="2643d-127">剪切所选文本并将其复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="2643d-127">Cuts the selected text and copies it to the clipboard.</span></span>|
|<span data-ttu-id="2643d-128">**复制**</span><span class="sxs-lookup"><span data-stu-id="2643d-128">**Copy**</span></span>|<span data-ttu-id="2643d-129">将选择的文本复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="2643d-129">Copies the selected text to the clipboard.</span></span>|
|<span data-ttu-id="2643d-130">**粘贴**</span><span class="sxs-lookup"><span data-stu-id="2643d-130">**Paste**</span></span>|<span data-ttu-id="2643d-131">将剪贴板内容粘贴到光标所在位置。</span><span class="sxs-lookup"><span data-stu-id="2643d-131">Pastes the contents of the clipboard at the cursor location.</span></span>|
|<span data-ttu-id="2643d-132">**清除输出窗格**</span><span class="sxs-lookup"><span data-stu-id="2643d-132">**Clear Output Pane**</span></span>|<span data-ttu-id="2643d-133">清除输出窗格中的所有内容。</span><span class="sxs-lookup"><span data-stu-id="2643d-133">Clears all content in the Output Pane.</span></span>|
|<span data-ttu-id="2643d-134">**撤消**</span><span class="sxs-lookup"><span data-stu-id="2643d-134">**Undo**</span></span>|<span data-ttu-id="2643d-135">撤销刚才执行的操作。</span><span class="sxs-lookup"><span data-stu-id="2643d-135">Reverses the action that was just performed.</span></span>|
|<span data-ttu-id="2643d-136">**重做**</span><span class="sxs-lookup"><span data-stu-id="2643d-136">**Redo**</span></span>|<span data-ttu-id="2643d-137">执行刚才撤销的操作。</span><span class="sxs-lookup"><span data-stu-id="2643d-137">Performs the action that was just undone.</span></span>|
|<span data-ttu-id="2643d-138">**运行脚本**</span><span class="sxs-lookup"><span data-stu-id="2643d-138">**Run Script**</span></span>|<span data-ttu-id="2643d-139">运行脚本。</span><span class="sxs-lookup"><span data-stu-id="2643d-139">Runs a script.</span></span>|
|<span data-ttu-id="2643d-140">**运行选定内容**</span><span class="sxs-lookup"><span data-stu-id="2643d-140">**Run Selection**</span></span>|<span data-ttu-id="2643d-141">运行脚本的选定部分。</span><span class="sxs-lookup"><span data-stu-id="2643d-141">Runs a selected portion of a script.</span></span>|
|<span data-ttu-id="2643d-142">**停止执行**</span><span class="sxs-lookup"><span data-stu-id="2643d-142">**Stop Execution**</span></span>|<span data-ttu-id="2643d-143">停止正在运行的脚本。</span><span class="sxs-lookup"><span data-stu-id="2643d-143">Stops a script that is running.</span></span>|
|<span data-ttu-id="2643d-144">**新建远程 PowerShell 选项卡**</span><span class="sxs-lookup"><span data-stu-id="2643d-144">**New Remote PowerShell Tab**</span></span>|<span data-ttu-id="2643d-145">创建将在远程计算机上建立会话的新 PowerShell 选项卡。</span><span class="sxs-lookup"><span data-stu-id="2643d-145">Creates a new PowerShell Tab that establishes a session on a remote computer.</span></span> <span data-ttu-id="2643d-146">将出现一个对话框，提示你输入建立远程连接所需的详细信息。</span><span class="sxs-lookup"><span data-stu-id="2643d-146">A dialog box appears and prompts you to enter details required to establish the remote connection.</span></span>|
|<span data-ttu-id="2643d-147">**启动 PowerShell.exe**</span><span class="sxs-lookup"><span data-stu-id="2643d-147">**Start PowerShell.exe**</span></span>|<span data-ttu-id="2643d-148">打开 Windows PowerShell 控制台。</span><span class="sxs-lookup"><span data-stu-id="2643d-148">Opens a PowerShell Console.</span></span>|
|<span data-ttu-id="2643d-149">**顶部显示脚本窗格**</span><span class="sxs-lookup"><span data-stu-id="2643d-149">**Show Script Pane Top**</span></span>|<span data-ttu-id="2643d-150">将脚本窗格移动到显示器顶部。</span><span class="sxs-lookup"><span data-stu-id="2643d-150">Moves the Script Pane to the top in the display.</span></span>|
|<span data-ttu-id="2643d-151">**右侧显示脚本窗格**</span><span class="sxs-lookup"><span data-stu-id="2643d-151">**Show Script Pane Right**</span></span>|<span data-ttu-id="2643d-152">将脚本窗格移动到显示器右侧。</span><span class="sxs-lookup"><span data-stu-id="2643d-152">Moves the Script Pane to the right in the display.</span></span>|
|<span data-ttu-id="2643d-153">**最大化显示脚本窗格**</span><span class="sxs-lookup"><span data-stu-id="2643d-153">**Show Script Pane Maximized**</span></span>|<span data-ttu-id="2643d-154">最大化脚本窗格。</span><span class="sxs-lookup"><span data-stu-id="2643d-154">Maximizes the Script Pane.</span></span>|

## <a name="script-tab"></a><span data-ttu-id="2643d-155">脚本选项卡</span><span class="sxs-lookup"><span data-stu-id="2643d-155">Script Tab</span></span>

<span data-ttu-id="2643d-156">显示正在编辑的脚本的名称。</span><span class="sxs-lookup"><span data-stu-id="2643d-156">Displays the name of the script you are editing.</span></span> <span data-ttu-id="2643d-157">可以单击脚本选项卡以选择你想编辑的脚本。</span><span class="sxs-lookup"><span data-stu-id="2643d-157">You can click a script tab to select the script you want to edit.</span></span>

<span data-ttu-id="2643d-158">当指向脚本选项卡时，脚本文件的完整限定路径将显示在工具提示中。</span><span class="sxs-lookup"><span data-stu-id="2643d-158">When you point to the script tab, the fully qualified path to the script file appears in a tooltip.</span></span>

## <a name="script-pane"></a><span data-ttu-id="2643d-159">脚本窗格</span><span class="sxs-lookup"><span data-stu-id="2643d-159">Script Pane</span></span>

<span data-ttu-id="2643d-160">允许创建和运行脚本。</span><span class="sxs-lookup"><span data-stu-id="2643d-160">Allows you to create and run scripts.</span></span> <span data-ttu-id="2643d-161">可以在脚本窗格中打开、编辑和运行现有脚本。</span><span class="sxs-lookup"><span data-stu-id="2643d-161">You can open, edit and run existing scripts in the Script Pane.</span></span>

## <a name="output-pane"></a><span data-ttu-id="2643d-162">输出窗格</span><span class="sxs-lookup"><span data-stu-id="2643d-162">Output Pane</span></span>

<span data-ttu-id="2643d-163">显示已运行的命令和脚本的结果。</span><span class="sxs-lookup"><span data-stu-id="2643d-163">Displays the results of the commands and scripts you have run.</span></span> <span data-ttu-id="2643d-164">还可以在输出窗格中复制和清除内容。</span><span class="sxs-lookup"><span data-stu-id="2643d-164">You can also copy and clear the contents in the Output Pane.</span></span>

## <a name="command-pane"></a><span data-ttu-id="2643d-165">命令窗格</span><span class="sxs-lookup"><span data-stu-id="2643d-165">Command Pane</span></span>

<span data-ttu-id="2643d-166">允许编写命令。</span><span class="sxs-lookup"><span data-stu-id="2643d-166">Allows you to write commands.</span></span> <span data-ttu-id="2643d-167">可以在命令窗格中运行单行命令或多行命令。</span><span class="sxs-lookup"><span data-stu-id="2643d-167">You can run a one line command or a multiline command in the Command Pane.</span></span> <span data-ttu-id="2643d-168">按 SHIFT+ENTER 以输入多行命令的每一行，并在输入最后一行后按 ENTER 以执行该多行命令。</span><span class="sxs-lookup"><span data-stu-id="2643d-168">Press SHIFT+ENTER to enter each line of a multiline command, and press ENTER after the last line to execute the multiline command.</span></span> <span data-ttu-id="2643d-169">命令窗格顶部显示的提示将展示当前工作目录的路径。</span><span class="sxs-lookup"><span data-stu-id="2643d-169">The prompt displayed on top of the Command Pane shows the path to the current working directory.</span></span>

## <a name="status-bar"></a><span data-ttu-id="2643d-170">状态栏</span><span class="sxs-lookup"><span data-stu-id="2643d-170">Status Bar</span></span>

<span data-ttu-id="2643d-171">允许查看你运行的命令和脚本是否完成。</span><span class="sxs-lookup"><span data-stu-id="2643d-171">Allows you to see whether the commands and scripts that you run are complete.</span></span> <span data-ttu-id="2643d-172">状态栏位于显示器最底部。</span><span class="sxs-lookup"><span data-stu-id="2643d-172">The status bar is at the very bottom of the display.</span></span> <span data-ttu-id="2643d-173">错误消息的已选部分将显示在状态栏中。</span><span class="sxs-lookup"><span data-stu-id="2643d-173">Selected portions of error messages are displayed on the status bar.</span></span>

## <a name="text-size-slider"></a><span data-ttu-id="2643d-174">文字大小滑块</span><span class="sxs-lookup"><span data-stu-id="2643d-174">Text-Size Slider</span></span>

<span data-ttu-id="2643d-175">增大或减小屏幕上的文字大小。</span><span class="sxs-lookup"><span data-stu-id="2643d-175">Increases or decreases the size of the text on the screen.</span></span>

## <a name="help"></a><span data-ttu-id="2643d-176">帮助</span><span class="sxs-lookup"><span data-stu-id="2643d-176">Help</span></span>

<span data-ttu-id="2643d-177">可在 Web 上的 TechNet 库中找到有关 Windows PowerShell ISE 的帮助。</span><span class="sxs-lookup"><span data-stu-id="2643d-177">Help for Windows PowerShell ISE is available on the Web in the TechNet Library.</span></span> <span data-ttu-id="2643d-178">可以通过单击“帮助”菜单上的“Windows PowerShell ISE 帮助”打开帮助，或通过在任意位置（光标在脚本窗格或控制台窗格中的 cmdlet 名称上时除外）按 F1 键打开帮助。  </span><span class="sxs-lookup"><span data-stu-id="2643d-178">You can open the Help by clicking **Windows PowerShell ISE Help** on the **Help** menu or by pressing the F1 key anywhere except when the cursor is on a cmdlet name in either the Script Pane or the Console Pane.</span></span> <span data-ttu-id="2643d-179">从“**帮助**”菜单还可以运行 Update-Help cmdlet 和显示命令窗口，该命令窗口可显示某个 cmdlet 的所有参数并允许你在易于使用的窗体中填写参数，从而帮助你构造命令。</span><span class="sxs-lookup"><span data-stu-id="2643d-179">From the **Help** menu you can also run the Update-Help cmdlet, and display the Command Window which assists you in constructing commands by showing you all of the parameters for a cmdlet and enabling you to fill in the parameters in an easy-to-use form.</span></span>

## <a name="see-also"></a><span data-ttu-id="2643d-180">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2643d-180">See Also</span></span>

- [<span data-ttu-id="2643d-181">Windows PowerShell ISE 简介</span><span class="sxs-lookup"><span data-stu-id="2643d-181">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
