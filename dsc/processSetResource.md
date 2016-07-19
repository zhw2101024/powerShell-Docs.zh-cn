---
title: "DSC ProcessSet 资源"
ms.date: 2016-05-23
keywords: powershell, DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 97714d3fa9a1c00fb3d2e79cc873280ca945a840
ms.openlocfilehash: 012a0e5c4f2a1f60ecea869d588b9c54e0567ced

---

# DSC WindowsProcess 资源

> 适用于：Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) 中的 **ProcessSet** 资源提供了用于在目标节点上配置进程的机制。 此资源是[复合资源](authoringResourceComposite.md)，它会针对 `GroupName` 参数中指定的每个组调用 [WindowsProcess 资源](windowsProcessResource.md)。

## 语法

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]   
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
}
```

## “属性”
|  属性  |  说明   | 
|---|---| 
| 参数| 包含要原样传递到进程的参数的字符串。 如果需要传递多个参数，请将它们全部放在此字符串中。| 
| 路径| 进程可执行文件的路径。 如果这些是可执行文件的名称（不是完全限定的路径），则 DSC 资源会搜索环境**路径**变量 (`$env:Path`) 以查找文件。 如果此属性的值是完全限定的路径，则 DSC 不使用**路径**环境变量查找文件，并且会在不存在任何路径时引发错误。 不允许使用相对路径。| 
| 凭据| 指示启动进程的凭据。| 
| Ensure| 指定进程是否存在。 将此属性设置为“Present”以确保进程存在。 否则，将其设置为“Absent”。 默认值为“Present”。| 
| StandardErrorPath| 进程写入标准错误的路径。 将覆盖任何现有文件。| 
| StandardInputPath| 进程从中接收标准输入的流。| 
| StandardOutputPath| 进程写入标准输出的文件的路径。 将覆盖任何现有文件。| 
| WorkingDirectory| 用作进程当前工作目录的位置。| 
| DependsOn | 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 ID 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"``。| 




<!--HONumber=Jul16_HO1-->


