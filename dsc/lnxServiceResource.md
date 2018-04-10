---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,配置,安装程序
title: 适用于 Linux 的 DSC nxService 资源
ms.openlocfilehash: b02fb1153570f628682533cb57a7d429e5cc8762
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxservice-resource"></a>适用于 Linux 的 DSC nxService 资源

PowerShell Desired State Configuration (DSC) 中的 **nxService** 资源提供了在 Linux 节点上管理服务的机制。

## <a name="syntax"></a>语法

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd }  ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>“属性”
|  属性 |  说明 |
|---|---|
| 名称| 要配置的服务/守护程序的名称。|
| 控制器| 配置服务时使用的服务控制器类型。|
| 启用| 指示服务是否开机启动。|
| State| 指示服务是否正在运行。 将此属性设置为“Stopped”以确保该服务不在运行。 将其设置为“Running”以确保该服务正在运行。|
| DependsOn | 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 **ID** 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。|


## <a name="additional-information"></a>其他信息

**nxService** 资源不会为不存在的服务创建服务定义或脚本。 你可使用 PowerShell Desired State Configuration **nxFile** 资源管理服务定义文件或脚本是否存在或管理其内容。

## <a name="example"></a>示例

以下示例显示了已注册 **SystemD** 服务控制器的“httpd”服务（适用于 Apache HTTP 服务器）的配置。

```
Import-DSCResource -Module nx

Node $node {
#Apache Service
nxService ApacheService
{
Name = "httpd"
State = "running"
Enabled = $true
Controller = "systemd"
}
}
```