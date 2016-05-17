---
title:   适用于 Linux 的 DSC nxService 资源
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# 适用于 Linux 的 DSC nxService 资源

PowerShell Desired State Configuration (DSC) 中的 **nxService** 资源提供了在 Linux 节点上管理服务的机制。

## 语法

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | system }  ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]

}
```

## “属性”
|  属性 |  说明 | 
|---|---|
| 名称| 要配置的服务/守护程序的名称。| 
| 控制器| 配置服务时使用的服务控制器类型。| 
| 启用| 指示服务是否开机启动。| 
| State| 指示服务是否正在运行。 将此属性设置为“Stopped”以确保该服务不在运行。 将其设置为“Running”以确保该服务正在运行。| 
| DependsOn | 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 **ID** 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。| 


## 其他信息

**nxService** 资源不会为不存在的服务创建服务定义或脚本。 你可使用 PowerShell Desired State Configuration **nxFile** 资源管理服务定义文件或脚本是否存在或管理其内容。

## 示例

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



<!--HONumber=May16_HO3-->


