---
title: "DSC Environment 资源"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 20a7711604033b5ff1484dbb526df2642a9a1738

---

# DSC Environment 资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) 中的 __Environment__ 资源提供了管理系统环境变量的机制。

## 语法
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## “属性”

|  属性  |  说明   | 
|---|---| 
| 名称| 指示指示你想要确保其特定状态的环境变量的名称。| 
| Ensure| 指示变量是否存在。 如果不存在此变量，将此属性设置为 __Present__ 以创建环境变量；如果已存在此变量，则确保其值与通过 __Value__ 属性提供的值相匹配。 如果存在该变量，将其设置为 __Absent__ 可将其删除。| 
| 路径| 定义正在配置的环境变量。 如果变量是 __Path__，则将此属性设置为 __$true__；否则将其设置为 __$false__。 默认值为 __$false__。 如果正在配置的变量是 __Path__，则通过 __Value__ 属性提供的值将被附加到现有值。| 
| DependsOn | 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。| 
| 值| 要分配给环境变量的值。| 

## 示例

以下示例可确保 __TestEnvironmentVariable__ 存在且具有值 __TestValue__。 如果不存在，则创建它。

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```




<!--HONumber=Jun16_HO4-->


