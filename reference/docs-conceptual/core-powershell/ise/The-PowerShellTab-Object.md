---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "PowerShellTab 对象"
ms.assetid: a9b58556-951b-4f48-b3ae-b351b7564360
ms.openlocfilehash: d4e9374202d352a30b3eb46bcf1e4e40dea49822
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2017
---
# <a name="the-powershelltab-object"></a><span data-ttu-id="f41de-103">PowerShellTab 对象</span><span class="sxs-lookup"><span data-stu-id="f41de-103">The PowerShellTab Object</span></span>
  <span data-ttu-id="f41de-104">**PowerShellTab** 对象代表 Windows PowerShell 运行时环境。</span><span class="sxs-lookup"><span data-stu-id="f41de-104">The **PowerShellTab** object represents a Windows PowerShell runtime environment.</span></span>

## <a name="methods"></a><span data-ttu-id="f41de-105">方法</span><span class="sxs-lookup"><span data-stu-id="f41de-105">Methods</span></span>

###  <span data-ttu-id="f41de-106"><a name="invoke"></a>调用\(脚本\)</span><span class="sxs-lookup"><span data-stu-id="f41de-106"><a name="invoke"></a> Invoke\( Script \)</span></span>
  <span data-ttu-id="f41de-107">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="f41de-107">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f41de-108">在 PowerShell 选项卡中运行给定的脚本。</span><span class="sxs-lookup"><span data-stu-id="f41de-108">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
>  <span data-ttu-id="f41de-109">此方法仅适用于其他 PowerShell 选项卡，不适用于运行它的 PowerShell 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f41de-109">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="f41de-110">它不返回任何对象或值。</span><span class="sxs-lookup"><span data-stu-id="f41de-110">It does not return any object or value.</span></span> <span data-ttu-id="f41de-111">如果代码修改任何变量，则这些更改将仍保存在根据其调用该命令的选项卡上。</span><span class="sxs-lookup"><span data-stu-id="f41de-111">If the code modifies any variable, then those changes persist on the tab against which the command was invoked.</span></span>

 <span data-ttu-id="f41de-112">**Script** - 要运行的脚本块的 System.Management.Automation.ScriptBlock 或字符串。</span><span class="sxs-lookup"><span data-stu-id="f41de-112">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

```
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psise.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a><span data-ttu-id="f41de-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span><span class="sxs-lookup"><span data-stu-id="f41de-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span></span>
  <span data-ttu-id="f41de-114">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="f41de-114">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="f41de-115">在 PowerShell 选项卡中运行给定的脚本。</span><span class="sxs-lookup"><span data-stu-id="f41de-115">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
>  <span data-ttu-id="f41de-116">此方法仅适用于其他 PowerShell 选项卡，不适用于运行它的 PowerShell 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f41de-116">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="f41de-117">运行脚本块，并且从该脚本返回的任何值将返回到从中调用该命令的运行环境。</span><span class="sxs-lookup"><span data-stu-id="f41de-117">The script block is run and any value that is returned from the script is returned to the run environment from which you invoked the command.</span></span> <span data-ttu-id="f41de-118">如果命令运行所花费的时间大于指定的 **millesecondsTimeout** 值，则该命令将失败并出现异常：“操作已超时。”</span><span class="sxs-lookup"><span data-stu-id="f41de-118">If the command takes longer to run than the **millesecondsTimeout** value specifies, then the command fails with an exception: "The operation has timed out."</span></span>

 <span data-ttu-id="f41de-119">**Script** - 要运行的脚本块的 System.Management.Automation.ScriptBlock 或字符串。</span><span class="sxs-lookup"><span data-stu-id="f41de-119">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

 <span data-ttu-id="f41de-120">**\[useNewScope\]** -  可选的布尔值，默认值为 **$true**
 如果设置为 **$true**，则会新建作用域以在其中运行命令。</span><span class="sxs-lookup"><span data-stu-id="f41de-120">**\[useNewScope\]** -  Optional Boolean that defaults to **$true**
 If set to **$true**, then a new scope is created within which to run the command.</span></span> <span data-ttu-id="f41de-121">它不会修改该命令指定的 PowerShell 选项卡的运行时环境。</span><span class="sxs-lookup"><span data-stu-id="f41de-121">It does not modify the runtime environment of the PowerShell tab that is specified by the command.</span></span>

 <span data-ttu-id="f41de-122">**\[millisecondsTimeout\]** - 可选整数，默认值为 **500**。</span><span class="sxs-lookup"><span data-stu-id="f41de-122">**\[millisecondsTimeout\]** -  Optional integer that defaults to **500**.</span></span>
<span data-ttu-id="f41de-123">如果在指定时间内未完成命令，则该命令将生成 **TimeoutException** 并显示消息“操作已超时。”</span><span class="sxs-lookup"><span data-stu-id="f41de-123">If the command does not finish within the specified time, then the command generates a **TimeoutException** with the message "The operation has timed out."</span></span>

```
# create a new PowerShell tab and then switch back to the first
$PSise.PowerShellTabs.Add()
$psISE.PowerShellTabs.SetSelectedPowerShellTab($psISE.PowerShellTabs[0]) 

# Invoke a simple command on the other tab, in its own scope
$psISE.PowerShellTabs[1].InvokeSynchronous('$x=1',$false)
# You can switch to the other tab and type “$x” to see that the value is saved there.

# This example sets a value in the other tab (in a different scope) 
# and returns it through the pipeline to this tab to store in $a
$a=$psISE.PowerShellTabs[1].InvokeSynchronous('$z=3;$z') 
$a

# This example runs a command that takes longer than the allowed timeout value
# and measures how long it runs so that you can see the impact
measure-command {$psISE.PowerShellTabs[1].InvokeSynchronous("sleep 10",$false,5000)}

```

## <a name="properties"></a><span data-ttu-id="f41de-124">“属性”</span><span class="sxs-lookup"><span data-stu-id="f41de-124">Properties</span></span>

###  <span data-ttu-id="f41de-125"><a name="AddOnsMenu"></a> AddOnsMenu</span><span class="sxs-lookup"><span data-stu-id="f41de-125"><a name="AddOnsMenu"></a> AddOnsMenu</span></span>
  <span data-ttu-id="f41de-126">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="f41de-126">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f41de-127">只读属性，可获取 PowerShell 选项卡的“加载项”菜单。</span><span class="sxs-lookup"><span data-stu-id="f41de-127">The read-only property that gets the Add-ons menu for the PowerShell tab.</span></span>

```
# Clear the Add-ons menu if one exists.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
# Create an AddOns menu with an accessor.
# Note the use of "_"  as opposed to the "&" for mapping to the fast key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P") 
# Add a nested menu. 
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("Parent",$null,$null) 
$parentAdded.SubMenus.Add("_Dir",{dir},"Alt+D")
# Show the Add-ons menu on the current PowerShell tab.
$psISE.CurrentPowerShellTab.AddOnsMenu
```

###  <span data-ttu-id="f41de-128"><a name="CanExecute"></a> CanInvoke</span><span class="sxs-lookup"><span data-stu-id="f41de-128"><a name="CanExecute"></a> CanInvoke</span></span>
  <span data-ttu-id="f41de-129">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="f41de-129">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f41de-130">只读布尔属性，如果可以使用 [Invoke( Script )](#invoke) 方法调用脚本，则返回 **$true** 值。</span><span class="sxs-lookup"><span data-stu-id="f41de-130">The read-only Boolean property that returns a **$true** value if a script can be invoked with the [Invoke( Script )](#invoke) method.</span></span>

```
# CanInvoke will be false if the PowerShell
# tab is running a script that takes a while, and you
# check its properties from another PowerShell tab. It is
# always false if checked on the current PowerShell tab. 
# Manually create a second PowerShell tab before running this script.
# Return to the first tab and type
$secondTab = $psise.PowerShellTabs[1] 
$secondTab.CanInvoke 
$secondTab.Invoke({sleep 20})
$secondTab.CanInvoke

```

###  <span data-ttu-id="f41de-131"><a name="Commandpane"></a> Consolepane</span><span class="sxs-lookup"><span data-stu-id="f41de-131"><a name="Commandpane"></a> Consolepane</span></span>
  <span data-ttu-id="f41de-132">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="f41de-132">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>  <span data-ttu-id="f41de-133">在 Windows PowerShell ISE 2.0 中，这命名为 **CommandPane**。</span><span class="sxs-lookup"><span data-stu-id="f41de-133">In Windows PowerShell ISE 2.0 this was named **CommandPane**.</span></span>

 <span data-ttu-id="f41de-134">获取“控制台”窗格 [editor](../ise/The-ISEEditor-Object.md) 对象的只读属性。</span><span class="sxs-lookup"><span data-stu-id="f41de-134">The read-only property that gets the Console pane [editor](../ise/The-ISEEditor-Object.md) object.</span></span>

```
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane

```

###  <span data-ttu-id="f41de-135"><a name="Displayname"></a> DisplayName</span><span class="sxs-lookup"><span data-stu-id="f41de-135"><a name="Displayname"></a> DisplayName</span></span>
  <span data-ttu-id="f41de-136">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="f41de-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f41de-137">读写属性，可获取或设置 PowerShell 选项卡上显示的文本。</span><span class="sxs-lookup"><span data-stu-id="f41de-137">The read-write property that gets or sets the text that is displayed on the PowerShell tab.</span></span> <span data-ttu-id="f41de-138">默认情况下，选项卡命名为“PowerShell #”，其中 # 表示数字。</span><span class="sxs-lookup"><span data-stu-id="f41de-138">By default, tabs are named "PowerShell #", where the # represents a number.</span></span>

```
$newTab = $psise.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"
```

###  <span data-ttu-id="f41de-139"><a name="ExpandedScript"></a> ExpandedScript</span><span class="sxs-lookup"><span data-stu-id="f41de-139"><a name="ExpandedScript"></a> ExpandedScript</span></span>
  <span data-ttu-id="f41de-140">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="f41de-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f41de-141">读写布尔属性，可确定“脚本”窗格是展开还是隐藏的。</span><span class="sxs-lookup"><span data-stu-id="f41de-141">The read-write Boolean property that determines whether the Script pane is expanded or hidden.</span></span>

```
# Toggle the expanded script property to see its effect.
$PSise.CurrentPowerShellTab.ExpandedScript=!$PSise.CurrentPowerShellTab.ExpandedScript

```

###  <span data-ttu-id="f41de-142"><a name="Files"></a>文件</span><span class="sxs-lookup"><span data-stu-id="f41de-142"><a name="Files"></a> Files</span></span>
  <span data-ttu-id="f41de-143">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="f41de-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f41de-144">只读属性，可获取 PowerShell 选项卡中打开的[脚本文件集合](../ise/The-ISEFileCollection-Object.md)。</span><span class="sxs-lookup"><span data-stu-id="f41de-144">The read-only property that gets the [collection of script files](../ise/The-ISEFileCollection-Object.md) that are open in the PowerShell tab.</span></span>

```
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb" 
# Gets the line count
$newFile.Editor.LineCount
```

###  <span data-ttu-id="f41de-145"><a name="Output"></a>输出</span><span class="sxs-lookup"><span data-stu-id="f41de-145"><a name="Output"></a> Output</span></span>
  <span data-ttu-id="f41de-146">此功能存在于 Windows PowerShell ISE 2.0 中，但已在更高版本的 ISE 中删除或重命名。</span><span class="sxs-lookup"><span data-stu-id="f41de-146">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="f41de-147">在更高版本的 Windows PowerShell ISE 中，你可以将 **ConsolePane** 对象用于相同的目的。</span><span class="sxs-lookup"><span data-stu-id="f41de-147">In later versions of Windows PowerShell ISE, you can use the **ConsolePane** object for the same purposes.</span></span>

 <span data-ttu-id="f41de-148">只读属性，可获取当前[编辑器](../ise/The-ISEEditor-Object.md)的“输出”窗格。</span><span class="sxs-lookup"><span data-stu-id="f41de-148">The read-only property that gets the Output pane of the current [editor](../ise/The-ISEEditor-Object.md).</span></span>

```
# Clears the text in the Output pane.
$psise.CurrentPowerShellTab.output.clear()
```

###  <span data-ttu-id="f41de-149"><a name="Prompt"></a>提示</span><span class="sxs-lookup"><span data-stu-id="f41de-149"><a name="Prompt"></a> Prompt</span></span>
  <span data-ttu-id="f41de-150">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="f41de-150">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f41de-151">只读属性，可获取当前提示文本。</span><span class="sxs-lookup"><span data-stu-id="f41de-151">The read-only property that gets the current prompt text.</span></span> <span data-ttu-id="f41de-152">注意：**Prompt** 函数可以被用户的配置文件覆盖。</span><span class="sxs-lookup"><span data-stu-id="f41de-152">Note: the **Prompt** function can be overridden by the user’s profile.</span></span> <span data-ttu-id="f41de-153">如果结果不止一个简单的字符串，则此属性不会返回任何内容。</span><span class="sxs-lookup"><span data-stu-id="f41de-153">If the result is other than a simple string, then this property returns nothing.</span></span>

```
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

###  <span data-ttu-id="f41de-154"><a name="ShowCommands"></a> ShowCommands</span><span class="sxs-lookup"><span data-stu-id="f41de-154"><a name="ShowCommands"></a> ShowCommands</span></span>
  <span data-ttu-id="f41de-155">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="f41de-155">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="f41de-156">读写属性，指示当前是否显示“命令”窗格。</span><span class="sxs-lookup"><span data-stu-id="f41de-156">The read-write property that indicates if the Commands pane is currently displayed.</span></span>

```
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $True
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands=$True}
```

###  <span data-ttu-id="f41de-157"><a name="StatusText"></a> StatusText</span><span class="sxs-lookup"><span data-stu-id="f41de-157"><a name="StatusText"></a> StatusText</span></span>
  <span data-ttu-id="f41de-158">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="f41de-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f41de-159">只读属性，可获取 **PowerShellTab** 状态文本。</span><span class="sxs-lookup"><span data-stu-id="f41de-159">The read-only property that gets the **PowerShellTab** status text.</span></span>

```
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

###  <span data-ttu-id="f41de-160"><a name="HorizontalAddOnToolsPaneOpened"></a> HorizontalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="f41de-160"><a name="HorizontalAddOnToolsPaneOpened"></a> HorizontalAddOnToolsPaneOpened</span></span>
  <span data-ttu-id="f41de-161">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="f41de-161">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="f41de-162">只读属性，指示水平“加载项”工具窗格当前是否打开。</span><span class="sxs-lookup"><span data-stu-id="f41de-162">The read-only property that indicates whether the horizontal Add-Ons tool pane is currently open.</span></span>

```
# Gets the current state of the horizontal Add-ons tool pane. 
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

###  <span data-ttu-id="f41de-163"><a name="VerticalAddOnToolsPaneOpened"></a> **VerticalAddOnToolsPaneOpened**</span><span class="sxs-lookup"><span data-stu-id="f41de-163"><a name="VerticalAddOnToolsPaneOpened"></a> **VerticalAddOnToolsPaneOpened**</span></span>
  <span data-ttu-id="f41de-164">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="f41de-164">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="f41de-165">只读属性，指示竖直“加载项”工具窗格当前是否打开。</span><span class="sxs-lookup"><span data-stu-id="f41de-165">The read-only property that indicates whether the vertical Add-Ons tool pane is currently open.</span></span>

```
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands=$True
# Gets the current state of the vertical Add-ons tool pane. 
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a><span data-ttu-id="f41de-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f41de-166">See Also</span></span>
- [<span data-ttu-id="f41de-167">PowerShellTabCollection 对象</span><span class="sxs-lookup"><span data-stu-id="f41de-167">The PowerShellTabCollection Object</span></span>](The-PowerShellTabCollection-Object.md) 
- [<span data-ttu-id="f41de-168">Windows PowerShell ISE 脚本对象模型</span><span class="sxs-lookup"><span data-stu-id="f41de-168">The Windows PowerShell ISE Scripting Object Model</span></span>](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="f41de-169">Windows PowerShell ISE 对象模型参考</span><span class="sxs-lookup"><span data-stu-id="f41de-169">Windows PowerShell ISE Object Model Reference</span></span>](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="f41de-170">ISE 对象模型层次结构</span><span class="sxs-lookup"><span data-stu-id="f41de-170">The ISE Object Model Hierarchy</span></span>](../ise/The-ISE-Object-Model-Hierarchy.md)

  
