---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "DSC WaitForSome 资源"
ms.openlocfilehash: cbe16c543f0eeb62dbe1fb439af2f9147f1bc210
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-waitforsome-resource"></a>DSC WaitForSome 资源

> 适用于：Windows PowerShell 5.0 及更高版本

可以在 [DSC 配置](configurations.md)中的节点块内使用 WaitForAny Desired State Configuration (DSC) 资源，以指定依赖其他节点上的配置。

如果由 ResourceName 属性指定的资源在 NodeName 属性定义的最少节点数（由 NodeCount 指定）上都处于所需状态，那么此资源成功。 


## <a name="syntax"></a>语法

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

## <a name="properties"></a>“属性”

|  属性  |  说明   | 
|---|---| 
| NodeCount| 此资源成功至少所需的处于相应状态的节点数。|
| NodeName| 要依赖的资源的目标节点。| 
| ResourceName| 要依赖的资源名称。| 
| RetryIntervalSec| 重试前等待的秒数。 最小值为 1。| 
| RetryCount| 重试次数上限。| 
| ThrottleLimit| 同时连接的计算机数量。 默认值为 new-cimsession default。| 
| DependsOn | 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。|
| PsDscRunAsCredential | 请参阅[通过用户凭据使用 DSC](https://docs.microsoft.com/en-us/powershell/dsc/runasuser) |


## <a name="example"></a>示例

有关如何使用此资源的示例，请参阅[指定跨节点依赖关系](crossNodeDependencies.md)

