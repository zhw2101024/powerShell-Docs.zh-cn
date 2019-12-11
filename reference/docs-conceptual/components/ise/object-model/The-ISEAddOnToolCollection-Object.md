---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: ISEAddOnToolCollection 对象
ms.openlocfilehash: 28ab9747e573b7a76ee655289b341870b1728bc2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030621"
---
# <a name="the-iseaddontoolcollection-object"></a>ISEAddOnToolCollection 对象

**ISEAddOnToolCollection** 对象是 **ISEAddOnTool** 对象的集合。 示例是 **$psISE.CurrentPowerShellTab.VerticalAddOnTools** 对象。

## <a name="methods"></a>方法

### <a name="add-name-controltype-isvisible-"></a>Add\( Name、ControlType、\[IsVisible\]\)

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

将新附加工具添加到集合。 它将返回新添加的附加工具。 在运行此命令之前，必须在本地计算机上安装附加工具并加载程序集。

**Name** - 字符串，指定添加到 Windows PowerShell ISE 的附加工具的显示名称。

**ControlType** - 类型，指定要添加的控件。

**\[IsVisible\]** - 可选布尔值，如果设置为 **$true**，可立即在关联的工具窗格中看到附加工具。

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a>Remove\( Item \)

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

从集合中删除指定的附加工具。

**Item** - Microsoft.PowerShell.Host.ISE.ISEAddOnTool，指定要从 Windows PowerShell ISE 删除的对象。

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a>SetSelectedPowerShellTab\( psTab \)

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

选择 **psTab** 参数指定的 PowerShell 选项卡。

**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab，要选择的 PowerShell 选项卡。

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a>Remove\( psTab \)

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

删除 **psTab** 参数指定的 PowerShell 选项卡。

**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab，要删除的 PowerShell 选项卡。

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a>另请参阅

- [PowerShellTab 对象](The-PowerShellTab-Object.md)
- [Windows PowerShell ISE 脚本对象模型的用途](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE 对象模型层次结构](The-ISE-Object-Model-Hierarchy.md)
