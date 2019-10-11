---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: DSC Service 资源
ms.openlocfilehash: 0bef6aa6d3526c9d8d92187c1e738d5c46b5665a
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953044"
---
# <a name="dsc-service-resource"></a>DSC Service 资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.x

Windows PowerShell Desired State Configuration (DSC) 中的 **Service** 资源提供了在目标节点上管理服务的机制。

## <a name="syntax"></a>语法

```Syntax
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Path = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>“属性”

|属性 |说明 |
|---|---|
|名称 |指示服务名称。 请注意，有时它与显示名称不同。 可使用 `Get-Service` cmdlet 获取服务及其当前状态的列表。 |
|BuiltInAccount |指示要用于服务的登录帐户。 允许用于此属性的值有：LocalService  、LocalSystem  和 NetworkService  。 |
|凭据 |指示服务将在其下运行的帐户的凭据。 此属性与 **BuiltinAccount** 属性不能一起使用。 |
|StartupType |设置服务的启动类型。 允许用于此属性的值有：**Automatic**、**Disabled** 和 **Manual**。 |
|State |指示你想要确保服务所处的状态。 这些值包括：**Running** 或 **Stopped**。 |
|说明 |指示目标服务的说明。 |
|DisplayName |指示目标服务的显示名称。 |
|路径 |指示新服务的二进制文件的路径。 |

## <a name="common-properties"></a>公共属性

|属性 |说明 |
|---|---|
|DependsOn |指示必须先运行其他资源的配置，再配置此资源。 例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |指示目标服务是否在系统中存在。 将此属性设置为 **Absent** 可确保目标服务不存在。 将其设置为 **Present** 可确保目标服务存在。 默认值为 **Present**。 |
|PsDscRunAsCredential |设置用于运行整个资源的身份的凭据。 |

> [!NOTE]
> 在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。 有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。

## <a name="example"></a>示例

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