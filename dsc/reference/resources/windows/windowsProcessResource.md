---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSC WindowsProcess 资源
ms.openlocfilehash: cee93ab283ded407d6e032161125aa6d6ac98827
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047174"
---
# <a name="dsc-windowsprocess-resource"></a>DSC WindowsProcess 资源

适用于：Windows PowerShell 4.0 中，Windows PowerShell 5.0_

Windows PowerShell Desired State Configuration (DSC) 中的 **WindowsProcess** 资源提供了用于在目标节点上配置进程的机制。

## <a name="syntax"></a>语法

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

## <a name="properties"></a>“属性”

| 属性 | 说明 |
| --- | --- |
| 参数| 指示要原样传递到进程的参数字符串 如果需要传递多个参数，请将它们全部放在此字符串中。|
| 路径| 进程可执行文件的路径。 如果这是可执行文件的文件名（不是完全限定的路径），则 DSC 资源会搜索环境**路径**变量 (`$env:Path`) 以查找可执行文件。 如果此属性的值是完全限定的路径，则 DSC 不使用**路径**环境变量查找文件，并且会在不存在路径时引发错误。 不允许使用相对路径。|
| 凭据| 指示启动进程的凭据。|
| Ensure| 指示进程是否存在。 将此属性设置为“Present”以确保进程存在。 否则，将其设置为“Absent”。 默认值为“Present”。|
| DependsOn | 指示必须先运行其他资源的配置，再配置此资源。 例如，如果想要首先运行 ID 为“ResourceName”、类型为“ResourceType”的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。|
| StandardErrorPath| 指示写入标准错误的目录路径。 将覆盖任何现有文件。|
| StandardInputPath| 指示标准输入位置。|
| StandardOutputPath| 指示写入标准输出的位置。 将覆盖任何现有文件。|
| WorkingDirectory| 指示将用作进程当前工作目录的位置。|