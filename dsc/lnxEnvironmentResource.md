---
title:   适用于 Linux nxEnvironment 资源的 DSC
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# 适用于 Linux nxEnvironment 资源的 DSC

PowerShell Desired State Configuration (DSC) 中的 **nxEnvironment** 资源提供了管理 Linux 节点上系统环境变量的机制。

## 语法

```
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Path = <bool> }
    [ DependsOn = <string[]> ]

}
```

## “属性”

|  属性 |  说明 | 
|---|---|
| 名称| 指示指示你想要确保其特定状态的环境变量的名称。| 
| 值| 要分配给环境变量的值。| 
| Ensure| 确定是否要检查变量是否存在。 将此属性设置为“Present”可确保该变量存在。 将其设置为“Absent”可确保该变量不存在。 默认值为“Present”。| 
| 路径| 定义正在配置的环境变量。 如果变量是 **Path**，则将此属性设置为 **$true**；否则将其设置为 **$false**。 默认值为 **$false**。 如果正在配置的变量是 **Path**，则通过 **Value** 属性提供的值将被附加到现有值。| 
| DependsOn | 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 **ID** 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。| 

## 其他信息

* 如果 **Path** 不存在，或者设置为 **$false**，则在 `/etc/environment` 中管理环境变量。 你的程序或脚本可能需要配置以获取 `/etc/environment` 文件从而访问托管的环境变量。
* 如果 **Path** 设置为 **$true**，则在文件 `/etc/profile.d/DSCenvironment.sh` 中管理环境变量。 如果不存在，则将创建此文件。 如果 **Ensure** 设置为“Absent”，**Path** 设置为 **$true**，则将仅从 `/etc/profile.d/DSCenvironment.sh`（而非其他文件）中删除现有环境变量。

## 示例

以下示例说明如何使用 **nxEnvironment** 资源来确保 **TestEnvironmentVariable** 存在且具有值“Test-Value”。 如果不存在，则将创建 **TestEnvironmentVariable**。

```
Import-DSCResource -Module nx 


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```




<!--HONumber=May16_HO3-->


