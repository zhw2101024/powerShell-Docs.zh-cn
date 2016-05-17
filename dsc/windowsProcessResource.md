---
title:   DSC WindowsProcess 资源
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# DSC WindowsProcess 资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) 中的 **WindowsProcess** 资源提供了用于在目标节点上配置进程的机制。

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

## “属性”
|  属性  |  说明   | 
|---|---| 
| 参数| 指示要原样传递到进程的参数字符串 如果需要传递多个参数，请将它们全部放在此字符串中。| 
| 路径| 指示进程可执行文件的路径。 如果将此属性设置为可执行文件的名称，DSC 将查找 __Path__ 变量。 如果提供完全限定的域名，则进程必须存在于其中，因为在此情况下，DSC 不会检查 __Path__ 变量。| 
| 凭据| 指示启动进程的凭据。| 
| Ensure| 指示进程是否存在。 将此属性设置为“Present”以确保进程存在。 否则，将其设置为“Absent”。 默认值为“Present”。| 
| DependsOn | 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"``。| 
| StandardErrorPath| 指示写入标准错误的目录路径。 将覆盖任何现有文件。| 
| StandardInputPath| 指示标准输入位置。| 
| StandardOutputPath| 指示写入标准输出的位置。 将覆盖任何现有文件。| 
| WorkingDirectory| 指示将用作进程当前工作目录的位置。| 



<!--HONumber=May16_HO3-->


