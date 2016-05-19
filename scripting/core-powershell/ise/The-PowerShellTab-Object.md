---
title: PowerShellTab 对象
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a9b58556-951b-4f48-b3ae-b351b7564360
---
# PowerShellTab 对象
  **PowerShellTab** 对象代表 Windows PowerShell 运行时环境。

## 方法

###  <a name="invoke"></a> Invoke\( Script \)
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。 

 在 PowerShell 选项卡中运行给定的脚本。

> [!NOTE]
>  此方法仅适用于其他 PowerShell 选项卡，不适用于运行它的 PowerShell 选项卡。 它不返回任何对象或值。 如果代码修改任何变量，则这些更改将仍保存在根据其调用该命令的选项卡上。

 **脚本** \- System.Management.Automation.ScriptBlock 或字符串
 要运行的脚本块。

```
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psise.PowerShellTabs[1].Invoke({dir})
```

### InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。 

 在 PowerShell 选项卡中运行给定的脚本。

> [!NOTE]
>  此方法仅适用于其他 PowerShell 选项卡，不适用于运行它的 PowerShell 选项卡。 运行脚本块，并且从该脚本返回的任何值将返回到从中调用该命令的运行环境。 如果命令运行所花费的时间大于指定的 **millesecondsTimeout** 值，则该命令将失败并出现异常：“操作已超时。”

 **脚本** \- System.Management.Automation.ScriptBlock 或字符串
 要运行的脚本块。

 **\[useNewScope\]** \-可选布尔值，默认值为 **$true**
 如果设置为 **$true**，则将创建在其中运行命令的新作用域。 它不会修改该命令指定的 PowerShell 选项卡的运行时环境。

 **\[millisecondsTimeout\]** \-  可选整数，默认值为 **500**.
 如果在指定时间内未完成命令，则该命令将生成 **TimeoutException** 并显示消息“操作已超时。”

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

## “属性”

###  <a name="AddOnsMenu"></a> AddOnsMenu
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。 

 只读属性，可获取 PowerShell 选项卡的“加载项”菜单。

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

###  <a name="CanExecute"></a> CanInvoke
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。 

 只读布尔属性，如果可以使用 [Invoke( Script )](#invoke) 方法调用脚本，则返回 **$true** 值。

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

###  <a name="Commandpane"></a> Consolepane
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。  在 Windows PowerShell ISE 2.0 中，这命名为 **CommandPane**.

 获取“控制台”窗格 [editor](../ise/The-ISEEditor-Object.md) 对象的只读属性。

```
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane

```

###  <a name="Displayname"></a> DisplayName
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。 

 读写属性，可获取或设置 PowerShell 选项卡上显示的文本。 默认情况下，选项卡命名为“PowerShell \ #”，其中 # 表示数字。

```
$newTab = $psise.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"
```

###  <a name="ExpandedScript"></a> ExpandedScript
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。 

 读写布尔属性，可确定“脚本”窗格是展开还是隐藏的。

```
# Toggle the expanded script property to see its effect.
$PSise.CurrentPowerShellTab.ExpandedScript=!$PSise.CurrentPowerShellTab.ExpandedScript

```

###  <a name="Files"></a> 文件
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。 

 只读属性，可获取 PowerShell 选项卡中打开的[脚本文件集合](../ise/The-ISEFileCollection-Object.md)。

```
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb" 
# Gets the line count
$newFile.Editor.LineCount
```

###  <a name="Output"></a> 输出
  此功能存在于 Windows PowerShell ISE 2.0 中，但已在更高版本的 ISE 中删除或重命名。  在更高版本的 Windows PowerShell ISE 中，你可以将 **ConsolePane** 对象用于相同的目的。

 只读属性，可获取当前[编辑器](../ise/The-ISEEditor-Object.md)的“输出”窗格。.

```
# Clears the text in the Output pane.
$psise.CurrentPowerShellTab.output.clear()
```

###  <a name="Prompt"></a> 提示
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。 

 只读属性，可获取当前提示文本。 注意：**Prompt** 函数可以被用户的配置文件覆盖。 如果结果不止一个简单的字符串，则此属性不会返回任何内容。

```
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

###  <a name="ShowCommands"></a> ShowCommands
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。 

 读写属性，指示当前是否显示“命令”窗格。

```
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $True
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands=$True}
```

###  <a name="StatusText"></a> StatusText
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。 

 只读属性，可获取 **PowerShellTab** 状态文本。

```
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

###  <a name="HorizontalAddOnToolsPaneOpened"></a> HorizontalAddOnToolsPaneOpened
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。 

 只读属性，指示水平“加载项”工具窗格当前是否打开。

```
# Gets the current state of the horizontal Add-ons tool pane. 
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

###  <a name="VerticalAddOnToolsPaneOpened"></a> **VerticalAddOnToolsPaneOpened**
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。 

 只读属性，指示竖直“加载项”工具窗格当前是否打开。

```
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands=$True
# Gets the current state of the vertical Add-ons tool pane. 
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## 另请参阅
 [PowerShellTabCollection 对象](The-PowerShellTabCollection-Object.md) 
 [Windows PowerShell ISE 脚本对象模型](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Windows PowerShell ISE 对象模型参考](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [ISE 对象模型层次结构](../ise/The-ISE-Object-Model-Hierarchy.md)

  


<!--HONumber=May16_HO2-->


