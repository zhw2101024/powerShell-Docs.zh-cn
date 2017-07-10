---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "DSC WindowsProcess 资源"
ms.openlocfilehash: c34d3cb1d4d9b899b45fba7b4b148a7c977f5365
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
<a id="dsc-windowsprocess-resource" class="xliff"></a>
# DSC WindowsProcess 资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) 中的 **WindowsProcess** 资源提供了用于在目标节点上配置进程的机制。

<a id="syntax" class="xliff"></a>
## 语法

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

<a id="properties" class="xliff"></a>
## “属性”
|  属性  |  说明   | 
|---|---| 
| 参数| 指示要原样传递到进程的参数字符串 如果需要传递多个参数，请将它们全部放在此字符串中。| 
| 路径| 进程可执行文件的路径。 如果这是可执行文件的文件名（不是完全限定的路径），则 DSC 资源会搜索环境**路径**变量 (`$env:Path`) 以查找可执行文件。 如果此属性的值是完全限定的路径，则 DSC 不使用**路径**环境变量查找文件，并且会在不存在路径时引发错误。 不允许使用相对路径。| 
| 凭据| 指示启动进程的凭据。| 
| Ensure| 指示进程是否存在。 将此属性设置为“Present”以确保进程存在。 否则，将其设置为“Absent”。 默认值为“Present”。| 
| DependsOn | 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"``。| 
| StandardErrorPath| 指示写入标准错误的目录路径。 将覆盖任何现有文件。| 
| StandardInputPath| 指示标准输入位置。| 
| StandardOutputPath| 指示写入标准输出的位置。 将覆盖任何现有文件。| 
| WorkingDirectory| 指示将用作进程当前工作目录的位置。| 

