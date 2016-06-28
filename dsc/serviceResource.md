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
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: ce8d6c1c9e8005c5c4792ae0fa4c5030bb9a92ed

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

## 示例

```powershell
Service ServiceExample
{
    Name = "TermService"
    StartupType = "Manual"
    State = "Running"
} 
```




<!--HONumber=Jun16_HO4-->


