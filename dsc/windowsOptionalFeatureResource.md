---
title: "DSC WindowsOptionalFeature 资源"
ms.date: 2016-05-24
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 97714d3fa9a1c00fb3d2e79cc873280ca945a840
ms.openlocfilehash: 1254037b655a3160c90e69971c9faf061f205917

---

# DSC WindowsOptionalFeature 资源

> 适用于：Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) 中的 **WindowsOptionalFeature** 资源提供了确保在目标节点上启用可选功能的机制。

## 语法

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    
}
```

## “属性”

|  属性  |  说明   | 
|---|---| 
| 名称| 指示要确保启用或禁用的功能的名称。| 
| Ensure| 指定是否启用功能。 若要确保启用功能，请将此属性设置为“Present”。若要确保禁用功能，请将此属性设为“Absent”。|
| 源| 未实现。|
| NoWindowsUpdateCheck| 指定 DISM 在搜索源文件以启用功能时是否联系 Windows 更新 (WU)。 如果为 $true，则 DISM 不联系 WU。|
| RemoveFilesOnDisable| 设置为 **$true** 可在功能禁用时（即，**Ensure** 设置为“Absent”时）删除与之关联的所有文件。|
| 日志级别| 日志中显示的最大输出级别。 接受的值包括：“ErrorsOnly”（只记录错误）、“ErrorsAndWarning”（记录错误和警告）和“ErrorsAndWarningAndInformation”（记录错误、警告和调试信息）。|
| LogPath| 希望资源提供程序在其中记录操作的日志文件的路径。| 
| DependsOn| 指定必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。| 
 






<!--HONumber=Jul16_HO1-->


