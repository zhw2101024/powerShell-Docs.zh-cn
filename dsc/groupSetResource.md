---
title: "DSC GroupSet 资源"
ms.date: 2016-05-16
keywords: powershell, DSC, built-in, resource
description: "提供了管理目标节点上的本地组的机制。"
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: bf36abde6a3bfff4c2e49868465e089cc886d031
ms.openlocfilehash: 45fe96c43a834566d398820e3d94e3be923bb385

---

# DSC GroupSet 资源

> 适用于：Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) 中的 **GroupSet** 资源提供了管理目标节点上的本地组的机制。 此资源是[复合资源](authoringResourceComposite.md)，它会针对 `GroupName` 参数中指定的每个组调用 [Group 资源](groupResource.md)。

当你要对多个组添加和/或删除相同成员列表、删除多个组或添加具有相同成员列表的多个组时，请使用此资源。

##语法##
```
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## “属性”

|  属性  |  说明   | 
|---|---| 
| GroupName| 要确保其处于特定状态的组的名称。| 
| MembersToExclude| 使用此属性从现有的组成员身份中删除成员。 此属性的值是一组形式为 *Domain*\\*UserName* 的字符串。 如果你在配置中设置此属性，请勿使用 **Members** 属性。 这样做会导致错误生成。| 
| 凭据| 访问远程资源所需的凭据。 **注意**：此帐户必须具有相应的 Active Directory 权限才能将所有非将本地帐户添加到组中；否则，将发生错误。
| Ensure| 指示组是否存在。 将此属性设置为“Absent”可确保组不存在。 将它设置为“Present”（默认值）可确保组存在。| 
| 成员| 使用此属性将当前的组成员身份替换为指定成员。 此属性的值是一组形式为 *Domain*\\*UserName* 的字符串。 如果你在配置中设置此属性，请勿使用 **MembersToExclude** 或 **MembersToInclude** 属性。 这样做会导致错误生成。| 
| MembersToInclude| 使用此属性将成员添加到组的现有成员资格中。 此属性的值是一组形式为 *Domain*\\*UserName* 的字符串。 如果你在配置中设置此属性，请勿使用 **Members** 属性。 这样做会导致错误生成。| 
| DependsOn | 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"``。| 

## 示例 1

下面的示例演示如何确保名为“myGroup”和“myOtherGroup”的两个组存在。 

```powershell
configuration GroupSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        GroupSet GroupSetTest
        {
            GroupName        = @("myGroup", "myOtherGroup")
            Ensure           = "Present"
            MembersToInclude = @("contoso\alice", "contoso\bob")
            MembersToExclude = $("contoso\john")
            Credential       = Get-Credential
        }
    }
}
$cd = @{
    AllNodes = @(
        @{
            NodeName                    = 'localhost'
            PSDscAllowPlainTextPassword = $true
            PSDscAllowDomainUser        = $true
        }
    )
}


GroupSetTest -ConfigurationData $cd
```

>**注意：**为简单起见，此示例使用纯文本凭据。 有关如何在配置 MOF 文件中加密凭据的信息，请参阅[保护 MOF 文件](secureMOF.md)。





<!--HONumber=Jul16_HO1-->


