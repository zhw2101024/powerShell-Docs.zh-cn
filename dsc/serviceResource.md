---
title: "DSC Service 资源"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: bda348e6597f31b8dfa2014e5c34c5d3bc7bca15
ms.openlocfilehash: 10123359213df7180388d9251e032c2bbb673143

---

# DSC Service 资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0


Windows PowerShell Desired State Configuration (DSC) 中的 **Service** 资源提供了在目标节点上管理服务的机制。

## 语法

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Path = [string] ]
}
```

## “属性”

|  属性  |  说明   | 
|---|---| 
| 名称| 指示服务名称。 请注意，有时它与显示名称不同。 你可以使用 Get-Service cmdlet 获取服务及其当前状态的列表。| 
| BuiltInAccount| 指示要用于服务的登录帐户。 允许用于此属性的值有：**LocalService**、**LocalSystem** 和 **NetworkService**。| 
| 凭据| 指示服务将在其下运行的帐户的凭据。 此属性与 __BuiltinAccount__ 属性不能一起使用。| 
| DependsOn| 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。| 
| StartupType| 设置服务的启动类型。 允许用于此属性的值有：**Automatic**、**Disabled** 和 **Manual**。| 
| State| 指示你想要确保服务所处的状态。| 
| 说明 | 指示目标服务的说明。| 
| DisplayName | 指示目标服务的显示名称。| 
| Ensure | 指示目标服务是否在系统中存在。 将此属性设置为 **Absent** 可确保目标服务不存在。 将它设置为 **Present**（默认值）可确保目标服务存在。|
| 路径 | 指示新服务的二进制文件的路径。| 

## 示例

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        } 
    }
}
```




<!--HONumber=Jul16_HO1-->


