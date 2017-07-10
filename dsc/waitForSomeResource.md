---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "DSC WaitForSome 资源"
ms.openlocfilehash: 5d67a9111f6358240590b651e627ffb96abc0896
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
<a id="dsc-waitforsome-resource" class="xliff"></a>
# DSC WaitForSome 资源

> 适用于：Windows PowerShell 5.0 及更高版本

可以在 [DSC 配置](configurations.md)中的节点块内使用 WaitForAny Desired State Configuration (DSC) 资源，以指定依赖其他节点上的配置。

如果由 ResourceName 属性指定的资源在 NodeName 属性定义的最少目标节点（由 NodeCount 指定）上都处于相应状态，那么此资源成功。 


<a id="syntax" class="xliff"></a>
## 语法

```
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    NodeCount = [Uint32]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ] 
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

<a id="properties" class="xliff"></a>
## “属性”

|  属性  |  说明   | 
|---|---| 
| ResourceName| 要依赖的资源名称。| 
| NodeName| 要依赖的资源的目标节点。| 
| NodeCount| 此资源成功至少所需的处于相应状态的节点数。|
| RetryIntervalSec| 重试前等待的秒数。 最小值为 1。| 
| RetryCount| 重试次数上限。| 
| ThrottleLimit| 同时连接的计算机数量。 默认值为 new-cimsession default。| 
| DependsOn | 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。|


<a id="example" class="xliff"></a>
## 示例

有关如何使用此资源的示例，请参阅[指定跨节点依赖关系](crossNodeDependencies.md)

