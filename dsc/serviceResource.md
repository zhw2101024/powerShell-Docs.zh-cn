---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSC Service 资源
ms.openlocfilehash: 3e2db8999ab1db2964f88e1ee14c6ad6e641c5e3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222428"
---
# <a name="dsc-service-resource"></a>DSC Service 资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0


Windows PowerShell Desired State Configuration (DSC) 中的 **Service** 资源提供了在目标节点上管理服务的机制。

## <a name="syntax"></a>语法

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

## <a name="properties"></a>“属性”

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