---
title: "适用于 Linux 的 DSC nxPackage 资源"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 31867cc7af96a3d8d527f5906d77bed5206940b4

---

# 适用于 Linux 的 DSC nxPackage 资源

PowerShell Desired State Configuration (DSC) 中的 **nxPackage** 资源提供了在 Linux 节点上管理程序包的机制。

## 语法

```
nxPackage <string> #ResourceName
{
    Name = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ LogPath = <string> ]
    [ DependsOn = <string[]> ]
    
}
```

## “属性”

|  属性 |  说明 | 
|---|---|
| 名称| 要确保其特定状态的程序包的名称。| 
| Ensure| 确定是否检查程序包是否存在。 将此属性设置为“Present”以确保该程序包存在。 将其设置为“Absent”以确保该程序包不存在。 默认值为“Present”。|  
| PackageManager| 支持的值有“yum”、“apt”和“zypper”。 指定安装程序包时要使用的程序包管理器。 如果指定了 **FilePath**，则将使用提供的路径安装程序包。 否则，将使用程序包管理器从预配置的存储库安装程序包。 如果既不提供 **PackageManager**，也不提供 **FilePath**，则将使用系统默认的程序包管理器。| 
| 文件路径| 程序包所在的文件路径| 
| PackageGroup| 如果为 **$true**，则 **Name** 应为用于 **PackageManager** 的程序包组的名称。 提供 **FilePath** 时，**PacakgeGroup** 无效。| 
| 参数| 将完全按原样传输给程序包的参数字符串。| 
| ReturnCode| 预期的返回代码。 如果实际返回代码与此处提供的预期值不匹配，则配置将返回错误。| 
| DependsOn | 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 **ID** 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。| 

## 示例

以下示例将确保使用“Yum”程序包管理器在 Linux 计算机上安装了名为“httpd”的程序包。

```
Import-DSCResource -Module nx 

Node $node {
nxPackage httpd
{
    Name = "httpd"
    Ensure = "Present"
    PackageManager = "Yum"
}
}
```




<!--HONumber=Jun16_HO4-->


