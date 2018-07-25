---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 适用于 Linux 的 DSC nxGroup 资源
ms.openlocfilehash: c61b6ab4a8c56d085b5297dcfc7582187d54f946
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093596"
---
# <a name="dsc-for-linux-nxgroup-resource"></a>适用于 Linux 的 DSC nxGroup 资源

PowerShell Desired State Configuration (DSC) 中的 **nxGroup** 资源提供了在 Linux 节点上管理本地组的机制。

## <a name="syntax"></a>语法

```
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present } ]
    [ Members = <string[]> ]
    [ MembersToInclude = <string[]> ]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a>“属性”

|  属性 |  说明 |
|---|---|
| GroupName| 指定要确保其特定状态的组的名称。|
| Ensure| 确定是否检查组是否存在。 将此属性设置为“Present”以确保该组存在。 将其设置为“Absent”以确保该组不存在。 默认值为“Present”。|
| 成员| 指定构成该组的成员。|
| MembersToInclude| 指定要确保是该组成员的用户。|
| MembersToExclude| 指定要确保不是该组成员的用户。|
| PreferredGroupID| 尽量将组 ID 设置为提供的值。 如果组 ID 正在使用中，则使用下一个可用的组 ID。|
| DependsOn | 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 **ID** 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = '[ResourceType]ResourceName'`。|

## <a name="example"></a>示例

下面的示例确保用户“monuser”存在，且为组“DBusers”的成员。

```powershell
Import-DSCResource -Module nx

Node $node {
    nxUser UserExample {
       UserName = 'monuser'
       Description = 'Monitoring user'
       Password = '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
       Ensure = 'Present'
       HomeDirectory = '/home/monuser'
    }

    nxGroup GroupExample {
       GroupName = 'DBusers'
       Ensure = 'Present'
       MembersToInclude = 'monuser'
       DependsOn = '[nxUser]UserExample'
    }
}
```