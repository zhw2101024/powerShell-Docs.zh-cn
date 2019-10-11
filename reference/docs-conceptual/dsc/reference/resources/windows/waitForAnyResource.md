---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: DSC WaitForAny 资源
ms.openlocfilehash: 61fee456d2652e08ed9bdbe64457627ff5b2e145
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952994"
---
# <a name="dsc-waitforany-resource"></a>DSC WaitForAny 资源

> 适用于：Windows PowerShell 5.1

可以在 [DSC 配置](../../../configurations/configurations.md)中的节点块内使用 WaitForAny  Desired State Configuration (DSC) 资源，以指定依赖其他节点上的配置。

如果由 ResourceName  属性指定的资源在 NodeName  属性定义的任意目标节点上处于相应状态，那么此资源成功。

> [!NOTE]
> WaitForAny 资源使用 Windows 远程管理来检查其他节点的状态  。 要详细了解 WinRM 的端口和安全性要求，请参阅 [PowerShell 远程处理安全注意事项](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6)。

## <a name="syntax"></a>语法

```Syntax
WaitForAny [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string[]]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>“属性”

|属性 |说明 |
|---|---|
|ResourceName |要依赖的资源名称。 如果此资源属于其他配置，则将名称格式设置为 `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`。 |
|NodeName |要依赖的资源的目标节点。 |
|RetryIntervalSec |重试前等待的秒数。 最小值为 1。 |
|RetryCount |重试次数上限。 |
|ThrottleLimit |同时连接的计算机数量。 默认为 `New-CimSession` 默认值。 |

## <a name="common-properties"></a>公共属性

|属性 |说明 |
|---|---|
|DependsOn |指示必须先运行其他资源的配置，再配置此资源。 例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。 |
|PsDscRunAsCredential |设置用于运行整个资源的身份的凭据。 |

> [!NOTE]
> 在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。 有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。

## <a name="example"></a>示例

有关如何使用此资源的示例，请参阅[指定跨节点依赖关系](../../../configurations/crossNodeDependencies.md)