---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "如何在 Windows PowerShell ISE 中调试脚本"
ms.assetid: 6dc6d8f9-8978-46e9-a92f-169af37e2817
ms.openlocfilehash: db8847e2cc9abeec729ed8d939fc170529a93846
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2017
---
# <a name="how-to-debug-scripts-in-windows-powershell-ise"></a><span data-ttu-id="a9cab-103">如何在 Windows PowerShell ISE 中调试脚本</span><span class="sxs-lookup"><span data-stu-id="a9cab-103">How to Debug Scripts in Windows PowerShell ISE</span></span>
<span data-ttu-id="a9cab-104">本主题介绍如何通过使用 Windows PowerShell® 集成脚本环境 (ISE) 直观调试功能来调试本地计算机上的脚本。</span><span class="sxs-lookup"><span data-stu-id="a9cab-104">This topic describes how to debug scripts on a local computer by using the Windows PowerShell® Integrated Scripting Environment (ISE) visual debugging features.</span></span>

<span data-ttu-id="a9cab-105">[如何管理断点](#bkmk_1)
[如何管理调试会话](#bkmk_2)
[如何在调试过程中步越、步入和步出](#bkmk_3)
[如何在调试时显示变量的值](#bkmk_4)</span><span class="sxs-lookup"><span data-stu-id="a9cab-105">[How to manage breakpoints](#bkmk_1)
[How to manage a debugging session](#bkmk_2)
[How to step over, step into, and step out while debugging](#bkmk_3)
[How to display the values of variables while debugging](#bkmk_4)</span></span>

## <span data-ttu-id="a9cab-106"><a name="bkmk_1"></a>如何管理断点</span><span class="sxs-lookup"><span data-stu-id="a9cab-106"><a name="bkmk_1"></a>How to manage breakpoints</span></span>
<span data-ttu-id="a9cab-107">断点是脚本中你想要操作暂停的指定位置，这样你可以检查变量的当前状态和脚本运行的环境。</span><span class="sxs-lookup"><span data-stu-id="a9cab-107">A breakpoint is a designated spot in a script where you would like operation to pause so that you can examine the current state of the variables and the environment in which your script is running.</span></span> <span data-ttu-id="a9cab-108">一旦你的脚本被断点暂停，你可以在控制台窗格中运行命令来检查你的脚本状态。</span><span class="sxs-lookup"><span data-stu-id="a9cab-108">Once your script is paused by a breakpoint, you can run commands in the Console Pane to examine the state of your script.</span></span>  <span data-ttu-id="a9cab-109">你可以输出变量或运行其他命令。</span><span class="sxs-lookup"><span data-stu-id="a9cab-109">You can output variables or run other commands.</span></span> <span data-ttu-id="a9cab-110">甚至可以修改对正在运行的脚本的上下文可见的任何变量的值。</span><span class="sxs-lookup"><span data-stu-id="a9cab-110">You can even modify the value of any variables that are visible to the context of the currently running script.</span></span> <span data-ttu-id="a9cab-111">检查完你想要查看的内容后，可以恢复该脚本的运行。</span><span class="sxs-lookup"><span data-stu-id="a9cab-111">After you have examined what you want to see, you can resume operation of the script.</span></span>

<span data-ttu-id="a9cab-112">可以在 Windows PowerShell 调试环境中设置三种类型的断点：</span><span class="sxs-lookup"><span data-stu-id="a9cab-112">You can set three types of breakpoints in the Windows PowerShell debugging environment:</span></span>

1.  <span data-ttu-id="a9cab-113">行断点  </span><span class="sxs-lookup"><span data-stu-id="a9cab-113">**Line breakpoint**.</span></span> <span data-ttu-id="a9cab-114">在脚本运行期间，当达到所指定的行时，脚本暂停</span><span class="sxs-lookup"><span data-stu-id="a9cab-114">The script pauses when the designated line is reached during the operation of the script</span></span>

2.  <span data-ttu-id="a9cab-115">**变量断点。**</span><span class="sxs-lookup"><span data-stu-id="a9cab-115">**Variable breakpoint.**</span></span> <span data-ttu-id="a9cab-116">每当指定变量的值发生更改时，脚本暂停。</span><span class="sxs-lookup"><span data-stu-id="a9cab-116">The script pauses whenever the designated variable’s value changes.</span></span>

3.  <span data-ttu-id="a9cab-117">**命令断点。**</span><span class="sxs-lookup"><span data-stu-id="a9cab-117">**Command breakpoint.**</span></span> <span data-ttu-id="a9cab-118">在脚本运行期间，每当要运行指定命令时，脚本暂停。</span><span class="sxs-lookup"><span data-stu-id="a9cab-118">The script pauses whenever the designated command is about to be run during the operation of the script.</span></span> <span data-ttu-id="a9cab-119">它可以包括参数，以便仅对所需操作进一步筛选断点。</span><span class="sxs-lookup"><span data-stu-id="a9cab-119">It can include parameters to further filter the breakpoint to only the operation you want.</span></span> <span data-ttu-id="a9cab-120">该命令还可以是你创建的函数。</span><span class="sxs-lookup"><span data-stu-id="a9cab-120">The command can also be a function you created.</span></span>

<span data-ttu-id="a9cab-121">其中，在 Windows PowerShell ISE 调试环境中，只有行断点可以通过使用菜单或键盘快捷方式进行设置。</span><span class="sxs-lookup"><span data-stu-id="a9cab-121">Of these, in the Windows PowerShell ISE debugging environment, only line breakpoints can be set by using the menu or the keyboard shortcuts.</span></span> <span data-ttu-id="a9cab-122">可以设置其他两种类型的断点，但应通过使用 [Set-PSBreakpoint](https://technet.microsoft.com/library/88d2d9ad-17dc-44ae-99aa-f841125b9dc8) cmdlet 从控制台窗格中进行设置。</span><span class="sxs-lookup"><span data-stu-id="a9cab-122">The other two types of breakpoints can be set, but they are set from the Console Pane by using the [Set-PSBreakpoint](https://technet.microsoft.com/library/88d2d9ad-17dc-44ae-99aa-f841125b9dc8) cmdlet.</span></span> <span data-ttu-id="a9cab-123">本部分介绍了如何通过使用菜单（若有）在 Windows PowerShell ISE 中执行调试任务，并通过脚本从控制台窗格中执行更广泛的命令。</span><span class="sxs-lookup"><span data-stu-id="a9cab-123">This section describes how you can perform debugging tasks in Windows PowerShell ISE by using the menus where available, and perform a wider range of commands from the Console Pane by using scripting.</span></span>

### <a name="to-set-a-breakpoint"></a><span data-ttu-id="a9cab-124">设置断点</span><span class="sxs-lookup"><span data-stu-id="a9cab-124">To set a breakpoint</span></span>
<span data-ttu-id="a9cab-125">仅当保存脚本后，才可以在其中设置断点。</span><span class="sxs-lookup"><span data-stu-id="a9cab-125">A breakpoint can be set in a script only after it has been saved.</span></span> <span data-ttu-id="a9cab-126">右键单击你想要设置行断点的行，然后单击“**切换断点**”。</span><span class="sxs-lookup"><span data-stu-id="a9cab-126">Right-click the line where you want to set a line breakpoint, and then click **Toggle Breakpoint**.</span></span> <span data-ttu-id="a9cab-127">或者，单击你想要设置的行断点所在的行，然后按 **F9**，或在“调试”菜单上，单击“切换断点”。</span><span class="sxs-lookup"><span data-stu-id="a9cab-127">Or, click the line where you want to set a line breakpoint, and press **F9** or, on the **Debug** menu, click **Toggle Breakpoint**.</span></span>

<span data-ttu-id="a9cab-128">以下脚本是如何通过使用 [Set-PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420) cmdlet 从控制台窗格中设置变量断点的示例。</span><span class="sxs-lookup"><span data-stu-id="a9cab-128">The following script is an example of how you can set a variable breakpoint from the Console Pane by using the [Set-PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420) cmdlet.</span></span>

``` PowerShell
# This command sets a breakpoint on the Server variable in the Sample.ps1 script.
Set-PSBreakpoint -Script sample.ps1 -Variable Server
```

### <a name="list-all-breakpoints"></a><span data-ttu-id="a9cab-129">列出所有断点</span><span class="sxs-lookup"><span data-stu-id="a9cab-129">List all breakpoints</span></span>
<span data-ttu-id="a9cab-130">在当前 Windows PowerShell® 会话中显示所有断点。</span><span class="sxs-lookup"><span data-stu-id="a9cab-130">Displays all breakpoints in the current Windows PowerShell® session.</span></span>

<span data-ttu-id="a9cab-131">在“调试”菜单上，单击“列表断点”。</span><span class="sxs-lookup"><span data-stu-id="a9cab-131">On the **Debug** menu, click **List Breakpoints**.</span></span> <span data-ttu-id="a9cab-132">以下脚本是如何通过使用 [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) cmdlet 从控制台窗格中列出所有断点的示例。</span><span class="sxs-lookup"><span data-stu-id="a9cab-132">The following script is an example of how you can list all breakpoints from the Console Pane by using the [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) cmdlet.</span></span>

``` PowerShell
# This command lists all breakpoints in the current session. 
Get-PSBreakpoint
```

### <a name="remove-a-breakpoint"></a><span data-ttu-id="a9cab-133">移除断点</span><span class="sxs-lookup"><span data-stu-id="a9cab-133">Remove a breakpoint</span></span>
<span data-ttu-id="a9cab-134">移除断点会将其删除。</span><span class="sxs-lookup"><span data-stu-id="a9cab-134">Removing a breakpoint deletes it.</span></span>  <span data-ttu-id="a9cab-135">如果你认为稍后还可能再次使用，请考虑改为[禁用](#bkmk_disable)。</span><span class="sxs-lookup"><span data-stu-id="a9cab-135">If you think you might want to use it again later, consider [disabling](#bkmk_disable) it instead.</span></span>  <span data-ttu-id="a9cab-136">右键单击你想要移除的断点所在的行，然后单击“**切换断点**”。</span><span class="sxs-lookup"><span data-stu-id="a9cab-136">Right-click the line where you want to remove a breakpoint, and then click **Toggle Breakpoint**.</span></span> <span data-ttu-id="a9cab-137">或者，单击你想要移除的断点所在的行，然后在“调试”菜单上，单击“切换断点”。</span><span class="sxs-lookup"><span data-stu-id="a9cab-137">Or, click the line where you want to remove a breakpoint, and on the **Debug** menu, click **Toggle Breakpoint**.</span></span> <span data-ttu-id="a9cab-138">以下脚本是如何通过使用 [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet 从控制台窗格中移除具有指定 ID 的断点的示例。</span><span class="sxs-lookup"><span data-stu-id="a9cab-138">The following script is an example of how to remove a breakpoint with a specified ID from the Console Pane by using the [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet.</span></span>

``` PowerShell
# This command deletes the breakpoint with breakpoint ID 2.
Remove-PSBreakpoint -Id 2
```

### <a name="remove-all-breakpoints"></a><span data-ttu-id="a9cab-139">移除所有断点</span><span class="sxs-lookup"><span data-stu-id="a9cab-139">Remove All Breakpoints</span></span>
<span data-ttu-id="a9cab-140">若要移除在当前会话中定义的所有断点，在“调试”菜单上，单击“移除所有断点”。</span><span class="sxs-lookup"><span data-stu-id="a9cab-140">To remove all breakpoints defined in the current session, on the **Debug** menu, click **Remove All Breakpoints**.</span></span>

<span data-ttu-id="a9cab-141">以下脚本是如何通过使用 [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet 从控制台窗格中移除所有断点的示例。</span><span class="sxs-lookup"><span data-stu-id="a9cab-141">The following script is an example of how to remove all breakpoints from the Console Pane by using the [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet.</span></span>

``` PowerShell
# This command deletes all of the breakpoints in the current session.
Get-PSBreakpoint | Remove-PSBreakpoint
```

### <span data-ttu-id="a9cab-142"><a name="bkmk_disable"></a>禁用断点</span><span class="sxs-lookup"><span data-stu-id="a9cab-142"><a name="bkmk_disable"></a>Disable a Breakpoint</span></span>
<span data-ttu-id="a9cab-143">禁用断点不会将断点移除；只是会将其关闭，直至启用。</span><span class="sxs-lookup"><span data-stu-id="a9cab-143">Disabling a breakpoint does not remove it; it turns it off until it is enabled.</span></span>  <span data-ttu-id="a9cab-144">若要禁用特定行断点，右键单击你想要禁用的行断点所在的行，然后单击“**切换断点**”。</span><span class="sxs-lookup"><span data-stu-id="a9cab-144">To disable a specific line breakpoint, right-click the line where you want to disable a breakpoint, and then click **Disable Breakpoint**.</span></span> <span data-ttu-id="a9cab-145">或者，单击你想要禁用的断点所在的行，然后按 **F9**，或在“调试”菜单上，单击“禁用断点”。</span><span class="sxs-lookup"><span data-stu-id="a9cab-145">Or, click the line where you want to disable a breakpoint, and press **F9** or, on the **Debug** menu, click **Disable Breakpoint**.</span></span> <span data-ttu-id="a9cab-146">以下脚本是如何通过使用 [Disable-PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet 从控制台窗格中移除具有指定 ID 的断点的示例。</span><span class="sxs-lookup"><span data-stu-id="a9cab-146">The following script is an example of how you can remove a breakpoint with a specified ID from the Console Pane by using the [Disable-PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet.</span></span>

``` PowerShell
# This command disables the breakpoint with breakpoint ID 0.
Disable-PSBreakpoint -Id 0
```

### <a name="disable-all-breakpoints"></a><span data-ttu-id="a9cab-147">禁用所有断点</span><span class="sxs-lookup"><span data-stu-id="a9cab-147">Disable All Breakpoints</span></span>
<span data-ttu-id="a9cab-148">禁用断点不会将断点移除；只是会将其关闭，直至启用。</span><span class="sxs-lookup"><span data-stu-id="a9cab-148">Disabling a breakpoint does not remove it; it turns it off until it is enabled.</span></span>  <span data-ttu-id="a9cab-149">若要禁用在当前会话中的所有断点，在“调试”菜单上，单击“禁用所有断点”。</span><span class="sxs-lookup"><span data-stu-id="a9cab-149">To disable all breakpoints in the current session, on the **Debug** menu, click **Disable all Breakpoints**.</span></span> <span data-ttu-id="a9cab-150">以下脚本是如何通过使用 [Disable-PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet 从控制台窗格中禁用所有断点的示例。</span><span class="sxs-lookup"><span data-stu-id="a9cab-150">The following script is an example of how you can disable all breakpoints from the Console Pane by using the [Disable-PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet.</span></span>

``` PowerShell
# This command disables all breakpoints in the current session. 
# You can abbreviate this command as: "gbp | dbp".
Get-PSBreakpoint | Disable-PSBreakpoint
```

### <a name="enable-a-breakpoint"></a><span data-ttu-id="a9cab-151">启用断点</span><span class="sxs-lookup"><span data-stu-id="a9cab-151">Enable a Breakpoint</span></span>
<span data-ttu-id="a9cab-152">若要启用特定断点，右键单击你想要启用的断点所在的行，然后单击“**启用断点**”。</span><span class="sxs-lookup"><span data-stu-id="a9cab-152">To enable a specific breakpoint, right-click the line where you want to enable a breakpoint, and then click **Enable Breakpoint**.</span></span> <span data-ttu-id="a9cab-153">或者，单击你想要启用的断点所在的行，然后按 **F9**，或在“调试”菜单上，单击“启用断点”。</span><span class="sxs-lookup"><span data-stu-id="a9cab-153">Or, click the line where you want to enable a breakpoint, and then press **F9** or, on the **Debug** menu, click **Enable Breakpoint**.</span></span> <span data-ttu-id="a9cab-154">以下脚本是如何通过使用 [Enable-PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet 从控制台窗格中启用特定断点的示例。</span><span class="sxs-lookup"><span data-stu-id="a9cab-154">The following script is an example of how you can enable specific breakpoints from the Console Pane by using the [Enable-PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet.</span></span>

``` PowerShell
# This command enables breakpoints with breakpoint IDs 0, 1, and 5.
Enable-PSBreakpoint -Id 0, 1, 5
```

### <a name="enable-all-breakpoints"></a><span data-ttu-id="a9cab-155">启用所有断点</span><span class="sxs-lookup"><span data-stu-id="a9cab-155">Enable All Breakpoints</span></span>
<span data-ttu-id="a9cab-156">若要启用在当前会话中定义的所有断点，在“调试”菜单上，单击“启用所有断点”。</span><span class="sxs-lookup"><span data-stu-id="a9cab-156">To enable all breakpoints defined in the current session, on the **Debug** menu, click **Enable all Breakpoints**.</span></span> <span data-ttu-id="a9cab-157">以下脚本是如何通过使用 [Enable-PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet 从控制台窗格中启用所有断点的示例。</span><span class="sxs-lookup"><span data-stu-id="a9cab-157">The following script is an example of how you can enable all breakpoints from the Console Pane by using the [Enable-PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet.</span></span>

``` PowerShell
# This command enables all breakpoints in the current session. 
# You can abbreviate the command by using their aliases: "gbp | ebp".
Get-PSBreakpoint | Enable-PSBreakpoint
```

## <span data-ttu-id="a9cab-158"><a name="bkmk_2"></a>如何管理调试会话</span><span class="sxs-lookup"><span data-stu-id="a9cab-158"><a name="bkmk_2"></a>How to manage a debugging session</span></span>
<span data-ttu-id="a9cab-159">开始调试之前，必须设置一个或多个断点。</span><span class="sxs-lookup"><span data-stu-id="a9cab-159">Before you start debugging, you must set one or more breakpoints.</span></span> <span data-ttu-id="a9cab-160">你不能设置一个断点，除非已保存你想要调试的脚本。</span><span class="sxs-lookup"><span data-stu-id="a9cab-160">You cannot set a breakpoint unless the script that you want to debug is saved.</span></span> <span data-ttu-id="a9cab-161">有关如何设置断点的说明，请参阅[如何管理断点](#bkmk_1)或 [Set-PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420)。</span><span class="sxs-lookup"><span data-stu-id="a9cab-161">For directions on of how to set a breakpoint, see [How to manage breakpoints](#bkmk_1) or [Set-PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420).</span></span> <span data-ttu-id="a9cab-162">开始调试后，将无法编辑脚本，除非停止调试。</span><span class="sxs-lookup"><span data-stu-id="a9cab-162">After you start debugging, you cannot edit a script until you stop debugging.</span></span> <span data-ttu-id="a9cab-163">运行之前，将自动保存设置有一个或多个断点的脚本。</span><span class="sxs-lookup"><span data-stu-id="a9cab-163">A script that has one or more breakpoints set is automatically saved before it is run.</span></span>

### <a name="to-start-debugging"></a><span data-ttu-id="a9cab-164">启动调试</span><span class="sxs-lookup"><span data-stu-id="a9cab-164">To start debugging</span></span>
<span data-ttu-id="a9cab-165">按 **F5** 或在工具栏上，单击“**运行脚本**”图标，或在“**调试**”菜单上，单击“**运行/继续**”。</span><span class="sxs-lookup"><span data-stu-id="a9cab-165">Press **F5** or, on the toolbar, click the **Run Script** icon, or on the **Debug** menu click **Run/Continue**.</span></span> <span data-ttu-id="a9cab-166">脚本将一直运行，直到它遇到第一个断点。</span><span class="sxs-lookup"><span data-stu-id="a9cab-166">The script runs until it encounters the first breakpoint.</span></span> <span data-ttu-id="a9cab-167">它将在此处暂停操作，并突出显示它暂停时所在的行。</span><span class="sxs-lookup"><span data-stu-id="a9cab-167">It pauses operation there and highlights the line on which it paused.</span></span>

### <a name="to-continue-debugging"></a><span data-ttu-id="a9cab-168">继续调试</span><span class="sxs-lookup"><span data-stu-id="a9cab-168">To continue debugging</span></span>
<span data-ttu-id="a9cab-169">按 **F5** 或在工具栏上，单击“**运行脚本**”图标，或在“**调试**”菜单上，单击“**运行/继续**”或在控制台窗格中，键入 **C**，然后按 **ENTER**。</span><span class="sxs-lookup"><span data-stu-id="a9cab-169">Press **F5** or, on the toolbar, click the **Run Script** icon, or on the **Debug** menu, click **Run/Continue** or, in the Console Pane, type **C** and then press **ENTER**.</span></span> <span data-ttu-id="a9cab-170">这将导致脚本继续运行到下一个断点，或如果接下来没有遇到任何断点的话运行到脚本的末尾。</span><span class="sxs-lookup"><span data-stu-id="a9cab-170">This causes the script to continue running to the next breakpoint or to the end of the script if no further breakpoints are encountered.</span></span>

### <a name="to-view-the-call-stack"></a><span data-ttu-id="a9cab-171">查看调用堆栈</span><span class="sxs-lookup"><span data-stu-id="a9cab-171">To view the call stack</span></span>
<span data-ttu-id="a9cab-172">调用堆栈会显示脚本中的当前运行位置。</span><span class="sxs-lookup"><span data-stu-id="a9cab-172">The call stack displays the current run location in the script.</span></span> <span data-ttu-id="a9cab-173">如果脚本在由其他函数调用的函数中运行，则会由输出中的附加行在显示中表示。</span><span class="sxs-lookup"><span data-stu-id="a9cab-173">If the script is running in a function that was called by a different function, then that is represented in the display by additional rows in the output.</span></span> <span data-ttu-id="a9cab-174">最底行显示原始脚本以及脚本中调用函数所在的行。</span><span class="sxs-lookup"><span data-stu-id="a9cab-174">The bottom-most row displays the original script and the line in it in which a function was called.</span></span> <span data-ttu-id="a9cab-175">下一行显示该函数以及函数中可能调用了另一个函数所在的行。</span><span class="sxs-lookup"><span data-stu-id="a9cab-175">The next line up shows that function and the line in it in which another function might have been called.</span></span>  <span data-ttu-id="a9cab-176">最顶行显示设置了断点的当前行的当前上下文。</span><span class="sxs-lookup"><span data-stu-id="a9cab-176">The top-most row shows the current context of the current line on which the breakpoint is set.</span></span>

<span data-ttu-id="a9cab-177">在暂停时，若要查看当前调用堆栈，请按 **CTRL+SHIFT+D**，或在“**调试**”菜单上，单击“**显示调用堆栈**”，在控制台窗格中，键入 **K**，然后按 **ENTER**。</span><span class="sxs-lookup"><span data-stu-id="a9cab-177">While paused, to see the current call stack, press **CTRL+SHIFT+D** or, on the **Debug** menu, click **Display Call Stack** or, in the Console Pane, type **K** and then press **ENTER**.</span></span>

### <a name="to-stop-debugging"></a><span data-ttu-id="a9cab-178">停止调试</span><span class="sxs-lookup"><span data-stu-id="a9cab-178">To stop debugging</span></span>
<span data-ttu-id="a9cab-179">按 **SHIFT-F5**，或在“**调试**”菜单上，单击“**停止调试器**”，或者，在控制台窗格中，键入 **Q**，然后按 **ENTER**。</span><span class="sxs-lookup"><span data-stu-id="a9cab-179">Press **SHIFT-F5** or, on the **Debug** menu, click **Stop Debugger**, or, in the Console Pane, type **Q** and then press **ENTER**.</span></span>

## <span data-ttu-id="a9cab-180"><a name="bkmk_3"></a>如何在调试过程中步越、步入和步出</span><span class="sxs-lookup"><span data-stu-id="a9cab-180"><a name="bkmk_3"></a>How to step over, step into, and step out while debugging</span></span>
<span data-ttu-id="a9cab-181">单步执行是一次运行一条语句的过程。</span><span class="sxs-lookup"><span data-stu-id="a9cab-181">Stepping is the process of running one statement at a time.</span></span> <span data-ttu-id="a9cab-182">你可以在一个代码行上停止，然后检查变量的值和系统状态。</span><span class="sxs-lookup"><span data-stu-id="a9cab-182">You can stop on a line of code, and examine the values of variables and the state of the system.</span></span> <span data-ttu-id="a9cab-183">下表描述了常见的调试任务，如步越、步入和步出。</span><span class="sxs-lookup"><span data-stu-id="a9cab-183">The following table describes common debugging tasks such as stepping over, stepping into, and stepping out.</span></span>

| <span data-ttu-id="a9cab-184">调试任务</span><span class="sxs-lookup"><span data-stu-id="a9cab-184">Debugging Task</span></span> | <span data-ttu-id="a9cab-185">说明</span><span class="sxs-lookup"><span data-stu-id="a9cab-185">Description</span></span> | <span data-ttu-id="a9cab-186">如何在 PowerShell ISE 中完成它</span><span class="sxs-lookup"><span data-stu-id="a9cab-186">How to accomplish it in PowerShell ISE</span></span> |
| --- | --- | --- |
| <span data-ttu-id="a9cab-187">**步入**</span><span class="sxs-lookup"><span data-stu-id="a9cab-187">**Step Into**</span></span> | <span data-ttu-id="a9cab-188">执行当前的语句，然后在下一个语句处停止。</span><span class="sxs-lookup"><span data-stu-id="a9cab-188">Executes the current statement and then stops at the next statement.</span></span> <span data-ttu-id="a9cab-189">如果当前语句是一个函数或脚本调用，则调试器将单步调试该函数或脚本，或者停止在下一条语句上。</span><span class="sxs-lookup"><span data-stu-id="a9cab-189">If the current statement is a function or script call, then the debugger steps into that function or script, otherwise it stops at the next statement.</span></span> | <span data-ttu-id="a9cab-190">按 **F11**，或在“调试”菜单上，单击“步入”，或者，在控制台窗格中，键入 **S**，然后按 **ENTER**。</span><span class="sxs-lookup"><span data-stu-id="a9cab-190">Press **F11** or, on the **Debug** menu, click **Step Into**, or in the Console Pane, type **S** and press **ENTER**.</span></span> |
| <span data-ttu-id="a9cab-191">**步越**</span><span class="sxs-lookup"><span data-stu-id="a9cab-191">**Step Over**</span></span> | <span data-ttu-id="a9cab-192">执行当前的语句，然后在下一个语句处停止。</span><span class="sxs-lookup"><span data-stu-id="a9cab-192">Executes the current statement and then stops at the next statement.</span></span> <span data-ttu-id="a9cab-193">如果当前语句是一个函数或脚本调用，则调试器将执行整个函数或脚本，或者在函数调用后在下个语句处停止。</span><span class="sxs-lookup"><span data-stu-id="a9cab-193">If the current statement is a function or script call then the debugger executes the whole function or script, and it stops at the next statement after the function call.</span></span> | <span data-ttu-id="a9cab-194">按 **F10**，或在“调试”菜单上，单击“步越”，或者在控制台窗格中，键入 **V**，然后按 **ENTER**。</span><span class="sxs-lookup"><span data-stu-id="a9cab-194">Press **F10** or, on the **Debug** menu, click **Step Over**, or in the Console Pane, type **V** and press **ENTER**.</span></span> |
| <span data-ttu-id="a9cab-195">**步出**</span><span class="sxs-lookup"><span data-stu-id="a9cab-195">**Step Out**</span></span> | <span data-ttu-id="a9cab-196">跳出当前函数，如果函数是嵌套的则返回上一级。</span><span class="sxs-lookup"><span data-stu-id="a9cab-196">Steps out of the current function and up one level if the function is nested.</span></span> <span data-ttu-id="a9cab-197">如果在主正文中，脚本将执行到末尾，或到下一个断点。</span><span class="sxs-lookup"><span data-stu-id="a9cab-197">If in the main body, the script is executed to the end, or to the next breakpoint.</span></span> <span data-ttu-id="a9cab-198">将执行跳过的语句，但不会单步遍历。</span><span class="sxs-lookup"><span data-stu-id="a9cab-198">The skipped statements are executed, but not stepped through.</span></span> | <span data-ttu-id="a9cab-199">按 **SHIFT+F11**，或在“**调试**”菜单上，单击“**步出**”，或者，在控制台窗格中，键入 **O**，然后按 **ENTER**。</span><span class="sxs-lookup"><span data-stu-id="a9cab-199">Press **SHIFT+F11**, or on the **Debug** menu, click **Step Out**, or in the Console Pane, type **O** and press **ENTER**.</span></span> |
| <span data-ttu-id="a9cab-200">**继续**</span><span class="sxs-lookup"><span data-stu-id="a9cab-200">**Continue**</span></span> | <span data-ttu-id="a9cab-201">继续执行到结束，或到下一个断点。</span><span class="sxs-lookup"><span data-stu-id="a9cab-201">Continues execution to the end, or to the next breakpoint.</span></span> <span data-ttu-id="a9cab-202">将执行已跳过的函数和调用，但不会进行单步遍历。</span><span class="sxs-lookup"><span data-stu-id="a9cab-202">The skipped functions and invocations are executed, but not stepped through.</span></span> | <span data-ttu-id="a9cab-203">按 **F5**，或在“**调试**”菜单上，单击“**运行/继续**”，或者，在控制台窗格中，键入 **C**，然后按 **ENTER**。</span><span class="sxs-lookup"><span data-stu-id="a9cab-203">Press **F5** or, on the **Debug** menu, click **Run/Continue**, or in the Console Pane, type **C** and press **ENTER**.</span></span> |

## <span data-ttu-id="a9cab-204"><a name="bkmk_4"></a>如何在调试时显示变量的值</span><span class="sxs-lookup"><span data-stu-id="a9cab-204"><a name="bkmk_4"></a>How to display the values of variables while debugging</span></span>
<span data-ttu-id="a9cab-205">单步遍历代码时，可以在脚本中显示变量的当前值。</span><span class="sxs-lookup"><span data-stu-id="a9cab-205">You can display the current values of variables in the script as you step through the code.</span></span>

### <a name="to-display-the-values-of-standard-variables"></a><span data-ttu-id="a9cab-206">显示标准变量的值</span><span class="sxs-lookup"><span data-stu-id="a9cab-206">To display the values of standard variables</span></span>
<span data-ttu-id="a9cab-207">使用以下方法之一：</span><span class="sxs-lookup"><span data-stu-id="a9cab-207">Use one of the following methods:</span></span>

-   <span data-ttu-id="a9cab-208">在脚本窗格中，将鼠标悬停在变量上，以在工具提示中显示它的值。</span><span class="sxs-lookup"><span data-stu-id="a9cab-208">In the Script Pane, hover over the variable to display its value as a tool tip.</span></span>

-   <span data-ttu-id="a9cab-209">在控制台窗格中，键入变量的名称并按 **ENTER**。</span><span class="sxs-lookup"><span data-stu-id="a9cab-209">In the Console Pane, type the variable name and press **ENTER**.</span></span>

<span data-ttu-id="a9cab-210">ISE 中的所有窗格始终位于同一作用域中。</span><span class="sxs-lookup"><span data-stu-id="a9cab-210">All panes in ISE are always in the same scope.</span></span> <span data-ttu-id="a9cab-211">因此，调试脚本时，你在控制台窗格中键入的命令在脚本作用域中运行。</span><span class="sxs-lookup"><span data-stu-id="a9cab-211">Therefore, while you are debugging a script, the commands that you type in the Console Pane run in script scope.</span></span> <span data-ttu-id="a9cab-212">这样，你便可以使用控制台窗格查找变量的值，并调用仅在脚本中定义的函数。</span><span class="sxs-lookup"><span data-stu-id="a9cab-212">This allows you to use the Console Pane to find the values of variables and call functions that are defined only in the script.</span></span>

### <a name="to-display-the-values-of-automatic-variables"></a><span data-ttu-id="a9cab-213">显示自动变量的值</span><span class="sxs-lookup"><span data-stu-id="a9cab-213">To display the values of automatic variables</span></span>
<span data-ttu-id="a9cab-214">调试脚本时，可以使用前述方法显示几乎所有变量的值。</span><span class="sxs-lookup"><span data-stu-id="a9cab-214">You can use the preceding method to display the value of almost all variables while you are debugging a script.</span></span> <span data-ttu-id="a9cab-215">但是，这些方法不适用于以下自动变量。</span><span class="sxs-lookup"><span data-stu-id="a9cab-215">However, these methods do not work for the following automatic variables.</span></span>

-   <span data-ttu-id="a9cab-216">$_</span><span class="sxs-lookup"><span data-stu-id="a9cab-216">$_</span></span>

-   <span data-ttu-id="a9cab-217">$Input</span><span class="sxs-lookup"><span data-stu-id="a9cab-217">$Input</span></span>

-   <span data-ttu-id="a9cab-218">$MyInvocation</span><span class="sxs-lookup"><span data-stu-id="a9cab-218">$MyInvocation</span></span>

-   <span data-ttu-id="a9cab-219">$PSBoundParameters</span><span class="sxs-lookup"><span data-stu-id="a9cab-219">$PSBoundParameters</span></span>

-   <span data-ttu-id="a9cab-220">$Args</span><span class="sxs-lookup"><span data-stu-id="a9cab-220">$Args</span></span>

<span data-ttu-id="a9cab-221">如果你尝试显示这些变量中的任何一个的值，你将获取调试器使用的内部管道中变量的值，而不是脚本中变量的值。</span><span class="sxs-lookup"><span data-stu-id="a9cab-221">If you try to display the value of any of these variables, you get the value of that variable for in an internal pipeline the debugger uses, not the value of the variable in the script.</span></span> <span data-ttu-id="a9cab-222">对于一些变量（$_、$Input、$MyInvocation、$PSBoundParameters 和 $Args），可以使用以下方法解决此问题：</span><span class="sxs-lookup"><span data-stu-id="a9cab-222">You can work around this for a few variables ($_, $Input, $MyInvocation, $PSBoundParameters, and $Args) by using the following method:</span></span>

1.  <span data-ttu-id="a9cab-223">在脚本中，将自动变量的值分配给一个新变量。</span><span class="sxs-lookup"><span data-stu-id="a9cab-223">In the script, assign the value of the automatic variable to a new variable.</span></span>

2.  <span data-ttu-id="a9cab-224">通过将鼠标悬停在脚本窗格中新变量上，或通过在控制台窗格中键入新变量来显示新变量的值。</span><span class="sxs-lookup"><span data-stu-id="a9cab-224">Display the value of the new variable, either by hovering over the new variable in the Script Pane, or by typing the new variable in the Console Pane.</span></span>

<span data-ttu-id="a9cab-225">例如，若要显示 $MyInvocation 变量的值，在脚本中，将该值分配给一个新变量（如 $scriptname），然后将鼠标悬停在 $scriptname 变量上，或键入 $scriptname 变量以显示其值。</span><span class="sxs-lookup"><span data-stu-id="a9cab-225">For example, to display the value of the $MyInvocation variable, in the script, assign the value to a new variable, such as $scriptname, and then hover over or type the $scriptname variable to display its value.</span></span>

``` PowerShell
#In MyScript.ps1
$scriptname = $MyInvocation.MyCommand.Path

#In the Console Pane:
C:\ps-test> $scriptname
C:\ps-test\MyScript.ps1
```

## <a name="see-also"></a><span data-ttu-id="a9cab-226">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a9cab-226">See Also</span></span>
- [<span data-ttu-id="a9cab-227">使用 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="a9cab-227">Using the Windows PowerShell ISE</span></span>](Using-the-Windows-PowerShell-ISE.md)

