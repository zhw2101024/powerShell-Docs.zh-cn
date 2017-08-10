---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISEMenuItem 对象"
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
ms.openlocfilehash: 33de866d706ec2b0894c5bfe49e07fee142b95c0
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2017
---
# <a name="the-isemenuitem-object"></a>ISEMenuItem 对象
  **ISEMenuItem** 对象是 Microsoft.PowerShell.Host.ISE.ISEMenuItem 类的实例。 “**加载项**”菜单上的所有对象都是 **Microsoft.PowerShell.Host.ISE.ISEMenuItem** 类的实例。

## <a name="properties"></a>“属性”

###  <a name="DisplayName"></a> DisplayName
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。 

 只读属性，可获取菜单项的显示名称。

```
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName

```

###  <a name="Action"></a> 操作
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。 

 只读属性，可获取脚本块。 单击菜单项时，它将调用该操作。

```
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item 
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

###  <a name="Shortcut"></a> 快捷方式
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。 

 只读属性，可获取菜单项的 Windows 输入键盘快捷方式。

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

###  <a name="Submenus"></a> 子菜单
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。 

 只读属性，可获取菜单项的[子菜单列表](The-ISEMenuItemCollection-Object.md)。

```
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a>脚本示例
 若要更好地了解加载项菜单及其可编写脚本属性的使用，请通读下面的脚本示例。

```

# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P") 
# Add a nested menu - a parent and a child submenu item. 
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("Parent",$null,$null) 
$parentAdded.SubMenus.Add("_Dir",{dir},"Alt+D")

```

## <a name="see-also"></a>另请参阅
- [ISEMenuItemCollection 对象](The-ISEMenuItemCollection-Object.md) 
- [Windows PowerShell ISE 脚本对象模型](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Windows PowerShell ISE 对象模型参考](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [ISE 对象模型层次结构](The-ISE-Object-Model-Hierarchy.md)

  