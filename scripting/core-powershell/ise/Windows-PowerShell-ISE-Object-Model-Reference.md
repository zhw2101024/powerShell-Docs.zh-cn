---
title: "Windows PowerShell ISE 对象模型参考"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c
ms.openlocfilehash: 44d5f142c6d2c68c1a70b3a1017a8e6e57a58abe
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="windows-powershell-ise-object-model-reference"></a>Windows PowerShell ISE 对象模型参考
  
## <a name="object-model-reference"></a>对象模型参考
 本部分对定义 Windows PowerShell® 集成脚本环境 (ISE) 中的各种对象的基础类提供了参考。 若要查看在其层次结构中组织的对象，请参阅 [ISE 对象模型层次结构](The-ISE-Object-Model-Hierarchy.md)。

 [ISEAddOnTool 对象](The-ISEAddOnTool-Object.md)
 示例：$psISE.CurrentVisibleHorizontalTool、$psISE.CurrentVisibleVerticalTool。

 [ISEAddOnTool 对象](The-ISEAddOnTool-Object.md)
  [ISEEditor 对象](The-ISEEditor-Object.md)
 示例：$psISE.CurrentFile.Editor、$psISE.CurrentPowerShellTab.Output、$psISE.CurrentPowerShellTab.CommandPane。

 [ISEFile 对象](The-ISEFile-Object.md)
 示例：$psISE.CurrentFile、$psISE.PowerShellTabs.Files\[0\]。

 [ISEFileCollection 对象](The-ISEFileCollection-Object.md)
 示例：$psISE.PowerShellTabs.Files。

 [ISEMenuItem 对象](The-ISEMenuItem-Object.md)
示例：$psISE.CurrentPowerShellTab.AddOnsMenu、$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\]。

 [ISEMenuItemCollection 对象](The-ISEMenuItemCollection-Object.md)
 示例：$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus。

 [ISEOptions 对象](The-ISEOptions-Object.md)
 示例：$psISE.Options、$psISE.Options.DefaultOptions。

 [ObjectModelRoot 对象](The-ObjectModelRoot-Object.md)
 示例：根 $psISE 对象。

 [PowerShellTab 对象](The-PowerShellTab-Object.md)
 示例：$psISE.CurrentPowerShellTab、$psISE.PowerShellTabs\[0\]。

 [PowerShellTabCollection 对象](The-PowerShellTabCollection-Object.md)
 示例：$psISE.PowerShellTabs。

## <a name="see-also"></a>另请参阅
- [Windows PowerShell ISE 脚本对象模型](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
