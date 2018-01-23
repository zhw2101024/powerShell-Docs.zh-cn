---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "DSC WaitForAny 资源"
ms.openlocfilehash: 795c005c67c196ef9afb08af790fe2a1695392ec
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-waitforany-resource"></a>DSC WaitForAny 资源

> 适用于：Windows PowerShell 5.1 及更高版本

可以在 [DSC 配置](configurations.md)中的节点块内使用 WaitForSome Desired State Configuration (DSC) 资源，以指定依赖其他节点上的配置。

如果由 ResourceName 属性指定的资源在 NodeName 属性定义的任意目标节点上处于相应状态，那么此资源成功。


## <a name="syntax"></a>语法

```
WaitForAny [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ] 
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>“属性”

|  属性  |  说明   | 
|---|---| 
| ResourceName| 要依赖的资源名称。| 
| NodeName| 要依赖的资源的目标节点。| 
| RetryIntervalSec| 重试前等待的秒数。 最小值为 1。| 
| RetryCount| 重试次数上限。| 
| ThrottleLimit| 同时连接的计算机数量。 默认值为 new-cimsession default。| 
| DependsOn | 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。|


## <a name="example"></a>示例

有关如何使用此资源的示例，请参阅[指定跨节点依赖关系](crossNodeDependencies.md)

