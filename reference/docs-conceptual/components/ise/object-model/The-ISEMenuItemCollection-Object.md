---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: ISEMenuItemCollection 对象
ms.openlocfilehash: b3795af1a6ed61ed6e371e5fc20cc4e95f643fd4
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030540"
---
# <a name="the-isemenuitemcollection-object"></a>ISEMenuItemCollection 对象

**ISEMenuItemCollection** 对象是 **ISEMenuItem** 对象的集合。 它是 Microsoft.PowerShell.Host.ISE.ISEOptions 类的实例。 一个示例是用于在 Windows PowerShell® 集成脚本环境 (ISE) 中自定义“加载项”  菜单的 **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** 对象。

## <a name="method"></a>方法

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>添加\(字符串 DisplayName、System.Management.Automation.ScriptBlock Action、System.Windows.Input.KeyGesture 快捷方式\)

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

将菜单项添加到集合。

**DisplayName** 要添加的菜单显示名称。

**Action** 用于指定与此菜单项关联的操作的 System.Management.Automation.ScriptBlock 对象  。

**Shortcut** 此操作的键盘快捷方式。

**Returns** 刚添加的 ISEMenuItem 对象。

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a>Clear\(\)

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

从菜单项中删除所有子菜单。

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a>另请参阅

- [ISEMenuItem 对象](The-ISEMenuItem-Object.md)
- [Windows PowerShell ISE 脚本对象模型的用途](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE 对象模型层次结构](The-ISE-Object-Model-Hierarchy.md)
