---
title:   DSC Group 资源
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# DSC Group 资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) 中的 Group 资源提供了管理目标节点上的本地组的机制。

##语法##
```
Group [string] #ResourceName
{
    GroupName = [string]
    [ Credential = [PSCredential] ]
    [ Description = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Members = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn = [string[]] ]
}
```

## “属性”

|  属性  |  说明   | 
|---|---| 
| GroupName| 要确保其处于特定状态的组的名称。| 
| 凭据| 访问远程资源所需的凭据。 **注意**：此帐户必须具有相应的 Active Directory 权限才能将所有非将本地帐户添加到组中；否则，将发生错误。
| 说明| 组的说明。| 
| Ensure| 指示该组是否存在。 将其属性设置为“Absent”可确保组不存在。 将其设置为"Present"（默认值）可确保组存在。| 
| 成员| 使用此属性将当前的组成员身份替换为指定成员。 此属性的值是一组形式为 *Domain*\\*UserName* 的字符串。 如果你在配置中设置此属性，请勿使用 **MembersToExclude** 或 **MembersToInclude** 属性。 这样做会导致错误生成。| 
| MembersToExclude| 使用此属性从现有的组成员身份中删除成员。 此属性的值是一组形式为 *Domain*\\*UserName* 的字符串。 如果你在配置中设置此属性，请勿使用 **Members** 属性。 这样做会导致错误生成。| 
| MembersToInclude| 使用此属性将成员添加到组的现有成员资格中。 此属性的值是一组形式为 *Domain*\\*UserName* 的字符串。 如果你在配置中设置此属性，请勿使用 **Members** 属性。 这样做会导致错误生成。| 
| DependsOn | 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"``。| 

## 示例 1

下面的示例展示了如何确保名为“TestGroup”的组不存在。 

```powershell
Group GroupExample
{
    # This will remove TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```
## 示例 2
以下示例演示如何将 Active Directory 用户添加到属于多计算机实验室版本（已在其中对本地管理员帐户使用 PSCredential）的本地管理员组。 因为这也适用于域管理帐户（域升级后），接下来我们需要将此现有的 PSCredential 转换为域友好的凭据，以便能够在成员服务器上将域用户添加到本地管理员组。

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
     @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'   
      }    
    )
}
                  
$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup
        {
            GroupName='Administrators'   
            Ensure= 'Present'             
            MembersToInclude= "$domain\$($Node.AdminAccount)"
            Credential = $dCredential    
            PsDscRunAsCredential = $DCredential
        }
```



<!--HONumber=May16_HO3-->


