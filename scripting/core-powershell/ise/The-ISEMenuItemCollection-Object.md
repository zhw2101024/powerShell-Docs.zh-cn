---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: "ISEMenuItemCollection 对象"
ms.technology: powershell
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 45e9123df5f22f37d2a76e49db6df5aa98824e1c
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="the-isemenuitemcollection-object"></a>ISEMenuItemCollection 对象
  **ISEMenuItemCollection** 对象是 **ISEMenuItem** 对象的集合。 它是 Microsoft.PowerShell.Host.ISE.ISEOptions 类的实例。 一个示例是用于在 Windows PowerShell® 集成脚本环境 (ISE) 中自定义“加载项”菜单的 **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** 对象。

## <a name="method"></a>方法

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>添加\(字符串 DisplayName、System.Management.Automation.ScriptBlock Action、System.Windows.Input.KeyGesture 快捷方式\)
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。 

 将菜单项添加到集合。

 **DisplayName**
 要添加的菜单显示名称。

 **Action**
 **System.Management.Automation.ScriptBlock** 对象指定与此菜单项关联的操作。

 **Shortcut**
 此操作的键盘快捷方式。

 **Returns**
 刚添加 ISEMenuItem 对象。

```
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
```

### <a name="clear"></a>Clear\(\)
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。 

 从菜单项中删除所有子菜单。

```
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

```

## <a name="see-also"></a>另请参阅
- [ISEMenuItem 对象](The-ISEMenuItem-Object.md) 
- [Windows PowerShell ISE 脚本对象模型](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Windows PowerShell ISE 对象模型参考](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [ISE 对象模型层次结构](The-ISE-Object-Model-Hierarchy.md)

  
