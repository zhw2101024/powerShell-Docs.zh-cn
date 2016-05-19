---
title: ISEAddOnToolCollection 对象
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 634eab89-0845-4016-974b-361b09bb8f7b
---
# ISEAddOnToolCollection 对象
  **ISEAddOnToolCollection** 对象是 **ISEAddOnTool** 对象的集合。 示例是 **$psISE.CurrentPowerShellTab.VerticalAddOnTools** 对象。

## 方法

### Add\( Name, ControlType, \[IsVisible\] \)
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。 

 将新附加工具添加到集合。 它将返回新添加的附加工具。 在运行此命令之前，必须在本地计算机上安装附加工具并加载程序集。

 **Name** – String
 指定添加到 Windows PowerShell ISE 的附加工具的显示名称。

 **ControlType** –Type
 指定要添加的控件。

 **\[IsVisible\]** – 可选布尔值
 如果设置为 **$true**，附加工具立即可显示在关联的工具窗格中。

```
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)

```

### Remove\( Item \)
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。 

 从集合中删除指定的附加工具。

 **Item** – Microsoft.PowerShell.Host.ISE.ISEAddOnTool
 指定要从 Windows PowerShell ISE 中删除的对象。

```
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)

```

### SetSelectedPowerShellTab\( psTab \)
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。 

 选择 **psTab** 参数指定的 PowerShell 选项卡。

 **psTab** – Microsoft.PowerShell.Host.ISE.PowerShellTab
 要选择的 PowerShell 选项卡。

```

      $newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"

```

### Remove\( psTab \)
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。 

 删除 **psTab** 参数指定的 PowerShell 选项卡。

 **psTab** – Microsoft.PowerShell.Host.ISE.PowerShellTab
 要删除的 PowerShell 选项卡。

```

$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

## 另请参阅
 [PowerShellTab 对象](The-PowerShellTab-Object.md) 
 [Windows PowerShell ISE 脚本对象模型](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Windows PowerShell ISE 对象模型参考](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [ISE 对象模型层次结构](The-ISE-Object-Model-Hierarchy.md)

  


<!--HONumber=May16_HO2-->


