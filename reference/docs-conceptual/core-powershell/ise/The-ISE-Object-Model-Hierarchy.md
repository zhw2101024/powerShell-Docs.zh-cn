---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISE 对象模型层次结构"
ms.openlocfilehash: 2df6d40f39dbe14bd3f46a6400cde4a6e91052ef
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/08/2017
---
# <a name="the-ise-object-model-hierarchy"></a>ISE 对象模型层次结构
本主题介绍了属于 Windows PowerShell 集成脚本环境 (ISE) 一部分的对象的层次结构。 在 Windows PowerShell 3.0 和 Windows PowerShell 4.0 中包含 Windows PowerShell ISE。 单击一个对象，使你转到定义对象的类的参考文档。

## <a name="psise-object"></a>$psISE 对象

**$PsISE** 对象是 Windows PowerShell ISE 对象层次结构的[根对象](The-ObjectModelRoot-Object.md)。
它位于顶层，使以下对象可用于脚本编写：

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[$psISE.CurrentFile](The-ISEFile-Object.md)

$PsISE.CurrentFile 对象是 [ISEFile](The-ISEFile-Object.md) 类的一个实例。

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)

**$PsISE.CurrentPowerShellTab**对象是的一个实例[PowerShellTab](The-PowerShellTab-Object.md)类。

## <a name="psisecurrentvisiblehorizontaltool"></a>$psISE.CurrentVisibleHorizontalTool

**$PsISE.CurrentVisibleHorizontalTool** 对象是 [ISEAddOnTool](The-ISEAddOnTool-Object.md) 类的实例。
它表示已安装的外接程序工具，当前停靠在 Windows PowerShell ISE 窗口的顶部。

## <a name="psisecurrentvisibleverticaltool"></a>$psISE.CurrentVisibleVerticalTool

**$PsISE.CurrentVisibleHorizontalTool** 对象是 [ISEAddOnTool](The-ISEAddOnTool-Object.md) 类的实例。
它表示已安装的外接程序工具，当前停靠在 Windows PowerShell ISE 窗口的右侧。

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[$psISE.Options](The-ISEOptions-Object.md)

$PsISE.Options 对象是 [ISEOptions](The-ISEOptions-Object.md) 类的一个实例。
ISEOptions 对象代表 Windows PowerShell ISE 的各种设置。
它是 Microsoft.PowerShell.Host.ISE.ISEOptions 类的实例。

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)

**$PsISE.PowerShellTabs** 对象是 [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) 类的实例。
它是所有当前打开的 PowerShell 选项卡的集合，表示本地计算机上或在已连接的远程计算机上可用的 Windows PowerShell 运行环境。 集合中的每个成员均为 [PowerShellTab](The-PowerShellTab-Object.md) 类的实例。

## <a name="see-also"></a>另请参阅
- [Windows PowerShell ISE 脚本对象模型](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Windows PowerShell ISE 对象模型参考](Windows-PowerShell-ISE-Object-Model-Reference.md)
