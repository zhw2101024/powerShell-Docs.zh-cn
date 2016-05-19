---
title: PowerShellTabCollection 对象
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
---
# PowerShellTabCollection 对象
  **PowerShellTab** 集合对象是 **PowerShellTab** 对象的集合。 每个 **PowerShellTab** 对象充当一个单独的运行时环境。 它是 Microsoft.PowerShell.Host.ISE.PowerShellTabs 类的实例。 例如 **$psISE.PowerShellTabs** 对象。

## 方法

### Add\(\)
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。 

 向集合中添加一个新的 PowerShell 选项卡。 它将返回新添加的选项卡。

```
$NewTab=$psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab"
```

### Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。 

 删除由 **psTab** 参数指定的选项卡。

 **psTab**
 要删除的 PowerShell 选项卡。

```

$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

### SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。 

 选择由 **psTab** 参数指定的 PowerShell 选项卡，以使它当前是处于活动状态的 PowerShell 选项卡。

 **psTab**
 要选择的 PowerShell 选项卡。

```
# Save the current tab in a variable and rename it
$OldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName="Old Tab"
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab" 
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab=$oldtab
```

## 另请参阅
 [PowerShellTab 对象](The-PowerShellTab-Object.md) 
 [Windows PowerShell ISE 脚本对象模型](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Windows PowerShell ISE 对象模型参考](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [ISE 对象模型层次结构](../ise/The-ISE-Object-Model-Hierarchy.md)

  


<!--HONumber=May16_HO2-->


