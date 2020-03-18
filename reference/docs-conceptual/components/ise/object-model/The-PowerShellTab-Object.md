---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: PowerShellTab 对象
ms.openlocfilehash: 55e3678a8285f0ec7e8131d98c87478216c26f37
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "79402514"
---
# <a name="the-powershelltab-object"></a><span data-ttu-id="7795d-103">PowerShellTab 对象</span><span class="sxs-lookup"><span data-stu-id="7795d-103">The PowerShellTab Object</span></span>

<span data-ttu-id="7795d-104">**PowerShellTab** 对象代表 Windows PowerShell 运行时环境。</span><span class="sxs-lookup"><span data-stu-id="7795d-104">The **PowerShellTab** object represents a Windows PowerShell runtime environment.</span></span>

## <a name="methods"></a><span data-ttu-id="7795d-105">方法</span><span class="sxs-lookup"><span data-stu-id="7795d-105">Methods</span></span>

### <a name="invoke-script-"></a><span data-ttu-id="7795d-106">调用\(脚本\)</span><span class="sxs-lookup"><span data-stu-id="7795d-106">Invoke\( Script \)</span></span>

<span data-ttu-id="7795d-107">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="7795d-107">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7795d-108">在 PowerShell 选项卡中运行给定的脚本。</span><span class="sxs-lookup"><span data-stu-id="7795d-108">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="7795d-109">此方法仅适用于其他 PowerShell 选项卡，不适用于运行它的 PowerShell 选项卡。</span><span class="sxs-lookup"><span data-stu-id="7795d-109">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="7795d-110">它不返回任何对象或值。</span><span class="sxs-lookup"><span data-stu-id="7795d-110">It does not return any object or value.</span></span> <span data-ttu-id="7795d-111">如果代码修改任何变量，则这些更改将仍保存在根据其调用该命令的选项卡上。</span><span class="sxs-lookup"><span data-stu-id="7795d-111">If the code modifies any variable, then those changes persist on the tab against which the command was invoked.</span></span>

<span data-ttu-id="7795d-112">**Script** - 要运行的脚本块的 System.Management.Automation.ScriptBlock 或字符串。</span><span class="sxs-lookup"><span data-stu-id="7795d-112">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a><span data-ttu-id="7795d-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span><span class="sxs-lookup"><span data-stu-id="7795d-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span></span>

<span data-ttu-id="7795d-114">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="7795d-114">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="7795d-115">在 PowerShell 选项卡中运行给定的脚本。</span><span class="sxs-lookup"><span data-stu-id="7795d-115">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="7795d-116">此方法仅适用于其他 PowerShell 选项卡，不适用于运行它的 PowerShell 选项卡。</span><span class="sxs-lookup"><span data-stu-id="7795d-116">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="7795d-117">运行脚本块，并且从该脚本返回的任何值将返回到从中调用该命令的运行环境。</span><span class="sxs-lookup"><span data-stu-id="7795d-117">The script block is run and any value that is returned from the script is returned to the run environment from which you invoked the command.</span></span> <span data-ttu-id="7795d-118">如果命令运行所花费的时间大于指定的 millesecondsTimeout  值，则该命令将失败并出现异常：“操作已超时。”</span><span class="sxs-lookup"><span data-stu-id="7795d-118">If the command takes longer to run than the **millesecondsTimeout** value specifies, then the command fails with an exception: "The operation has timed out."</span></span>

<span data-ttu-id="7795d-119">**Script** - 要运行的脚本块的 System.Management.Automation.ScriptBlock 或字符串。</span><span class="sxs-lookup"><span data-stu-id="7795d-119">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

<span data-ttu-id="7795d-120">**\[useNewScope\]** -  可选的布尔值，默认值为 `$true`，如果设置为 `$true`，则会新建作用域以在其中运行命令。</span><span class="sxs-lookup"><span data-stu-id="7795d-120">**\[useNewScope\]** -  Optional Boolean that defaults to `$true` If set to `$true`, then a new scope is created within which to run the command.</span></span> <span data-ttu-id="7795d-121">它不会修改该命令指定的 PowerShell 选项卡的运行时环境。</span><span class="sxs-lookup"><span data-stu-id="7795d-121">It does not modify the runtime environment of the PowerShell tab that is specified by the command.</span></span>

<span data-ttu-id="7795d-122">**\[millisecondsTimeout\]** - 可选整数，默认值为 **500**。</span><span class="sxs-lookup"><span data-stu-id="7795d-122">**\[millisecondsTimeout\]** -  Optional integer that defaults to **500**.</span></span>
<span data-ttu-id="7795d-123">如果在指定时间内未完成命令，则该命令将生成 **TimeoutException** 并显示消息“操作已超时。”</span><span class="sxs-lookup"><span data-stu-id="7795d-123">If the command does not finish within the specified time, then the command generates a **TimeoutException** with the message "The operation has timed out."</span></span>

```powershell
# Create a new PowerShell tab and then switch back to the first
$psISE.PowerShellTabs.Add()
$psISE.PowerShellTabs.SetSelectedPowerShellTab($psISE.PowerShellTabs[0])

# Invoke a simple command on the other tab, in its own scope
$psISE.PowerShellTabs[1].InvokeSynchronous('$x=1', $false)
# You can switch to the other tab and type '$x' to see that the value is saved there.

# This example sets a value in the other tab (in a different scope)
# and returns it through the pipeline to this tab to store in $a
$a = $psISE.PowerShellTabs[1].InvokeSynchronous('$z=3;$z')
$a

# This example runs a command that takes longer than the allowed timeout value
# and measures how long it runs so that you can see the impact
Measure-Command {$psISE.PowerShellTabs[1].InvokeSynchronous('sleep 10', $false, 5000)}
```

## <a name="properties"></a><span data-ttu-id="7795d-124">属性</span><span class="sxs-lookup"><span data-stu-id="7795d-124">Properties</span></span>

### <a name="addonsmenu"></a><span data-ttu-id="7795d-125">AddOnsMenu</span><span class="sxs-lookup"><span data-stu-id="7795d-125">AddOnsMenu</span></span>

<span data-ttu-id="7795d-126">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="7795d-126">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7795d-127">只读属性，可获取 PowerShell 选项卡的“加载项”菜单。</span><span class="sxs-lookup"><span data-stu-id="7795d-127">The read-only property that gets the Add-ons menu for the PowerShell tab.</span></span>

```powershell
# Clear the Add-ons menu if one exists.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
# Create an AddOns menu with an accessor.
# Note the use of "_"  as opposed to the "&" for mapping to the fast key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
# Show the Add-ons menu on the current PowerShell tab.
$psISE.CurrentPowerShellTab.AddOnsMenu
```

### <a name="caninvoke"></a><span data-ttu-id="7795d-128">CanInvoke</span><span class="sxs-lookup"><span data-stu-id="7795d-128">CanInvoke</span></span>

<span data-ttu-id="7795d-129">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="7795d-129">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7795d-130">只读布尔属性，如果可以使用 [Invoke( Script )](#invoke-script-) 方法调用脚本，则返回 `$true` 值。</span><span class="sxs-lookup"><span data-stu-id="7795d-130">The read-only Boolean property that returns a `$true` value if a script can be invoked with the [Invoke( Script )](#invoke-script-) method.</span></span>

```powershell
# CanInvoke will be false if the PowerShell
# tab is running a script that takes a while, and you
# check its properties from another PowerShell tab. It is
# always false if checked on the current PowerShell tab.
# Manually create a second PowerShell tab before running this script.
# Return to the first tab and type
$secondTab = $psISE.PowerShellTabs[1]
$secondTab.CanInvoke
$secondTab.Invoke({sleep 20})
$secondTab.CanInvoke
```

### <a name="consolepane"></a><span data-ttu-id="7795d-131">ConsolePane</span><span class="sxs-lookup"><span data-stu-id="7795d-131">ConsolePane</span></span>

<span data-ttu-id="7795d-132">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="7795d-132">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> <span data-ttu-id="7795d-133">在 Windows PowerShell ISE 2.0 中，这命名为 **CommandPane**。</span><span class="sxs-lookup"><span data-stu-id="7795d-133">In Windows PowerShell ISE 2.0 this was named **CommandPane**.</span></span>

<span data-ttu-id="7795d-134">获取“控制台”窗格 [editor](The-ISEEditor-Object.md) 对象的只读属性。</span><span class="sxs-lookup"><span data-stu-id="7795d-134">The read-only property that gets the Console pane [editor](The-ISEEditor-Object.md) object.</span></span>

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a><span data-ttu-id="7795d-135">DisplayName</span><span class="sxs-lookup"><span data-stu-id="7795d-135">DisplayName</span></span>

<span data-ttu-id="7795d-136">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="7795d-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7795d-137">读写属性，可获取或设置 PowerShell 选项卡上显示的文本。默认情况下，选项卡命名为“PowerShell #”，其中 # 表示数字。</span><span class="sxs-lookup"><span data-stu-id="7795d-137">The read-write property that gets or sets the text that is displayed on the PowerShell tab. By default, tabs are named "PowerShell #", where the # represents a number.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a><span data-ttu-id="7795d-138">ExpandedScript</span><span class="sxs-lookup"><span data-stu-id="7795d-138">ExpandedScript</span></span>

<span data-ttu-id="7795d-139">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="7795d-139">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7795d-140">读写布尔属性，可确定“脚本”窗格是展开还是隐藏的。</span><span class="sxs-lookup"><span data-stu-id="7795d-140">The read-write Boolean property that determines whether the Script pane is expanded or hidden.</span></span>

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a><span data-ttu-id="7795d-141">文件</span><span class="sxs-lookup"><span data-stu-id="7795d-141">Files</span></span>

<span data-ttu-id="7795d-142">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="7795d-142">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7795d-143">只读属性，可获取 PowerShell 选项卡中打开的[脚本文件集合](The-ISEFileCollection-Object.md)。</span><span class="sxs-lookup"><span data-stu-id="7795d-143">The read-only property that gets the [collection of script files](The-ISEFileCollection-Object.md) that are open in the PowerShell tab.</span></span>

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a><span data-ttu-id="7795d-144">输出</span><span class="sxs-lookup"><span data-stu-id="7795d-144">Output</span></span>

<span data-ttu-id="7795d-145">此功能存在于 Windows PowerShell ISE 2.0 中，但已在更高版本的 ISE 中删除或重命名。</span><span class="sxs-lookup"><span data-stu-id="7795d-145">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="7795d-146">在更高版本的 Windows PowerShell ISE 中，你可以将 **ConsolePane** 对象用于相同的目的。</span><span class="sxs-lookup"><span data-stu-id="7795d-146">In later versions of Windows PowerShell ISE, you can use the **ConsolePane** object for the same purposes.</span></span>

<span data-ttu-id="7795d-147">只读属性，可获取当前[编辑器](The-ISEEditor-Object.md)的“输出”窗格。</span><span class="sxs-lookup"><span data-stu-id="7795d-147">The read-only property that gets the Output pane of the current [editor](The-ISEEditor-Object.md).</span></span>

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a><span data-ttu-id="7795d-148">Prompt</span><span class="sxs-lookup"><span data-stu-id="7795d-148">Prompt</span></span>

<span data-ttu-id="7795d-149">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="7795d-149">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7795d-150">只读属性，可获取当前提示文本。</span><span class="sxs-lookup"><span data-stu-id="7795d-150">The read-only property that gets the current prompt text.</span></span> <span data-ttu-id="7795d-151">注意：Prompt 函数可以被用户的配置文件覆盖  。</span><span class="sxs-lookup"><span data-stu-id="7795d-151">Note: the **Prompt** function can be overridden by the user'™s profile.</span></span> <span data-ttu-id="7795d-152">如果结果不止一个简单的字符串，则此属性不会返回任何内容。</span><span class="sxs-lookup"><span data-stu-id="7795d-152">If the result is other than a simple string, then this property returns nothing.</span></span>

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a><span data-ttu-id="7795d-153">ShowCommands</span><span class="sxs-lookup"><span data-stu-id="7795d-153">ShowCommands</span></span>

<span data-ttu-id="7795d-154">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="7795d-154">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="7795d-155">读写属性，指示当前是否显示“命令”窗格。</span><span class="sxs-lookup"><span data-stu-id="7795d-155">The read-write property that indicates if the Commands pane is currently displayed.</span></span>

```powershell
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $true
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands = $true}
```

### <a name="statustext"></a><span data-ttu-id="7795d-156">StatusText</span><span class="sxs-lookup"><span data-stu-id="7795d-156">StatusText</span></span>

<span data-ttu-id="7795d-157">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="7795d-157">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7795d-158">只读属性，可获取 **PowerShellTab** 状态文本。</span><span class="sxs-lookup"><span data-stu-id="7795d-158">The read-only property that gets the **PowerShellTab** status text.</span></span>

```powershell
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a><span data-ttu-id="7795d-159">HorizontalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="7795d-159">HorizontalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="7795d-160">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="7795d-160">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="7795d-161">只读属性，指示水平“加载项”工具窗格当前是否打开。</span><span class="sxs-lookup"><span data-stu-id="7795d-161">The read-only property that indicates whether the horizontal Add-Ons tool pane is currently open.</span></span>

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a><span data-ttu-id="7795d-162">VerticalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="7795d-162">VerticalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="7795d-163">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="7795d-163">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="7795d-164">只读属性，指示竖直“加载项”工具窗格当前是否打开。</span><span class="sxs-lookup"><span data-stu-id="7795d-164">The read-only property that indicates whether the vertical Add-Ons tool pane is currently open.</span></span>

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a><span data-ttu-id="7795d-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7795d-165">See Also</span></span>

- [<span data-ttu-id="7795d-166">PowerShellTabCollection 对象</span><span class="sxs-lookup"><span data-stu-id="7795d-166">The PowerShellTabCollection Object</span></span>](The-PowerShellTabCollection-Object.md)
- [<span data-ttu-id="7795d-167">Windows PowerShell ISE 脚本对象模型的用途</span><span class="sxs-lookup"><span data-stu-id="7795d-167">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="7795d-168">ISE 对象模型层次结构</span><span class="sxs-lookup"><span data-stu-id="7795d-168">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
