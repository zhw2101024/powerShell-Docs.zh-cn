---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 适用于 Linux 的 DSC nxService 资源
ms.openlocfilehash: fe8043995205649378725f2ab0a78e19313739c9
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/26/2018
ms.locfileid: "39267773"
---
# <a name="dsc-for-linux-nxservice-resource"></a>适用于 Linux 的 DSC nxService 资源

PowerShell Desired State Configuration (DSC) 中的 **nxService** 资源提供了在 Linux 节点上管理服务的机制。

## <a name="syntax"></a>语法

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd } ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a>“属性”

| 属性 | 说明 |
|---|---|
| 名称| 要配置的服务/守护程序的名称。|
| 控制器| 配置服务时使用的服务控制器类型。|
| 启用| 指示服务是否开机启动。|
| State| 指示服务是否正在运行。 将此属性设置为“Stopped”以确保该服务不在运行。 将其设置为“Running”以确保该服务正在运行。|
| DependsOn | 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 **ID** 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。|

## <a name="additional-information"></a>其他信息

**nxService** 资源不会为不存在的服务创建服务定义或脚本。 你可使用 PowerShell Desired State Configuration **nxFile** 资源管理服务定义文件或脚本是否存在或管理其内容。

## <a name="example"></a>示例

下面的示例展示了已向 SystemD 服务控制器注册的“httpd”服务（适用于 Apache HTTP 服务器）的配置。

```powershell
Import-DSCResource -Module nx

Node $node {
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```