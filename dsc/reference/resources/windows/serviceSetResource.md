---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSC ServiceSet 资源
ms.openlocfilehash: 5694c2abc5c0caf0098670b629af464b35125583
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047062"
---
# <a name="dsc-serviceset-resource"></a>DSC ServiceSet 资源

> 适用于：Windows PowerShell 4.0 中，Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) 中的 **ServiceSet** 资源提供了在目标节点上管理服务的机制。 此资源是[复合资源](../../../resources/authoringResourceComposite.md)，它会针对 `Name` 属性中指定的每个服务调用 [Service 资源](serviceResource.md)。

要将一些服务配置为相同状态时，请使用此资源。

## <a name="syntax"></a>语法

```
Service [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a>“属性”

|  属性  |  说明   |
|---|---|
| 名称| 指示服务名称。 请注意，有时它与显示名称不同。 你可以使用 [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) cmdlet 获取服务及其当前状态的列表。|
| StartupType| 设置服务的启动类型。 允许用于此属性的值包括：**自动**，**禁用**，和**手动**|
| BuiltInAccount| 指示要用于服务的登录帐户。 允许用于此属性的值包括：**LocalService**， **LocalSystem**，和**NetworkService**。|
| State| 指示你想要确保服务所处的状态。**已停止**或**运行**。|
| Ensure| 指示服务是否在系统中存在。 将此属性设置为 **Absent** 可确保服务不存在。 将它设置为 **Present**（默认值）可确保目标服务存在。|
| 凭据| 指示服务资源将在其下运行的帐户的凭据。 此属性与 **BuiltinAccount** 属性不能一起使用。|
| DependsOn| 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 ID 为 *ResourceName*、类型为 *ResourceType* 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。|



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
