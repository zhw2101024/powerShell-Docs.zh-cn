---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: DSC ServiceSet 资源
ms.openlocfilehash: 97c25f46940d69ed6c696e2692e29131e9a997b0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953024"
---
# <a name="dsc-serviceset-resource"></a>DSC ServiceSet 资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.x

Windows PowerShell Desired State Configuration (DSC) 中的 **ServiceSet** 资源提供了在目标节点上管理服务的机制。 此资源是[复合资源](../../../resources/authoringResourceComposite.md)，它会针对 **Name** 属性中指定的每个服务调用 [Service 资源](serviceResource.md)。

要将一些服务配置为相同状态时，请使用此资源。

## <a name="syntax"></a>语法

```Syntax
ServiceSet [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>“属性”

|属性 |说明 |
|---|---|
|名称 |指示服务名称。 请注意，有时它与显示名称不同。 可使用 `Get-Service` cmdlet 获取服务及其当前状态的列表。 |
|StartupType |指示服务的启动类型。 允许用于此属性的值有：**Automatic**、**Disabled** 和 **Manual**。 |
|BuiltInAccount |指示要用于服务的登录帐户。 允许用于此属性的值有：LocalService  、LocalSystem  和 NetworkService  。 |
|State |指示你想要确保服务所处的状态：Stopped  或 Running  。 |
|凭据 |指示服务资源将在其下运行的帐户的凭据。 此属性与 **BuiltinAccount** 属性不能一起使用。 |

## <a name="common-properties"></a>公共属性

|属性 |说明 |
|---|---|
|DependsOn |指示必须先运行其他资源的配置，再配置此资源。 例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |指示服务是否在系统中存在。 将此属性设置为 **Absent** 可确保服务不存在。 将它设置为 **Present** 可确保目标服务存在。 默认值为 **Present**。 |
|PsDscRunAsCredential |设置用于运行整个资源的身份的凭据。 |

> [!NOTE]
> 在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。 有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。

## <a name="example"></a>示例

以下配置启动“Windows 音频”和“远程桌面服务”服务。

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```