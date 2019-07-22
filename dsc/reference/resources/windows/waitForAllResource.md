---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSC WaitForAll 资源
ms.openlocfilehash: c1125b7c5b68b9b520ed052800b6a2abf4e53b85
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726881"
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="af2e5-103">DSC WaitForAll 资源</span><span class="sxs-lookup"><span data-stu-id="af2e5-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="af2e5-104">适用于：Windows PowerShell 5.0 及更高版本</span><span class="sxs-lookup"><span data-stu-id="af2e5-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="af2e5-105">可以在 [DSC 配置](../../../configurations/configurations.md)中的节点块内使用 WaitForAll  Desired State Configuration (DSC) 资源，以指定依赖其他节点上的配置。</span><span class="sxs-lookup"><span data-stu-id="af2e5-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="af2e5-106">如果由 ResourceName  属性指定的资源在 NodeName  属性定义的所有目标节点上都处于相应状态，那么此资源成功。</span><span class="sxs-lookup"><span data-stu-id="af2e5-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="af2e5-107">WaitForAll 资源使用 Windows 远程管理来检查其他节点的状态  。</span><span class="sxs-lookup"><span data-stu-id="af2e5-107">**WaitForAll** resource uses Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="af2e5-108">要详细了解 WinRM 的端口和安全性要求，请参阅 [PowerShell 远程处理安全注意事项](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6)。</span><span class="sxs-lookup"><span data-stu-id="af2e5-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="af2e5-109">语法</span><span class="sxs-lookup"><span data-stu-id="af2e5-109">Syntax</span></span>

```
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="af2e5-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="af2e5-110">Properties</span></span>

|  <span data-ttu-id="af2e5-111">属性</span><span class="sxs-lookup"><span data-stu-id="af2e5-111">Property</span></span>  |  <span data-ttu-id="af2e5-112">说明</span><span class="sxs-lookup"><span data-stu-id="af2e5-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="af2e5-113">ResourceName</span><span class="sxs-lookup"><span data-stu-id="af2e5-113">ResourceName</span></span>| <span data-ttu-id="af2e5-114">要依赖的资源名称。</span><span class="sxs-lookup"><span data-stu-id="af2e5-114">The resource name to depend on.</span></span> <span data-ttu-id="af2e5-115">如果此资源属于不同的配置，请将名称的格式设置为“[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]”</span><span class="sxs-lookup"><span data-stu-id="af2e5-115">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="af2e5-116">NodeName</span><span class="sxs-lookup"><span data-stu-id="af2e5-116">NodeName</span></span>| <span data-ttu-id="af2e5-117">要依赖的资源的目标节点。</span><span class="sxs-lookup"><span data-stu-id="af2e5-117">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="af2e5-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="af2e5-118">RetryIntervalSec</span></span>| <span data-ttu-id="af2e5-119">重试前等待的秒数。</span><span class="sxs-lookup"><span data-stu-id="af2e5-119">The number of seconds before retrying.</span></span> <span data-ttu-id="af2e5-120">最小值为 1。</span><span class="sxs-lookup"><span data-stu-id="af2e5-120">Minimum is 1.</span></span>|
| <span data-ttu-id="af2e5-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="af2e5-121">RetryCount</span></span>| <span data-ttu-id="af2e5-122">重试次数上限。</span><span class="sxs-lookup"><span data-stu-id="af2e5-122">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="af2e5-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="af2e5-123">ThrottleLimit</span></span>| <span data-ttu-id="af2e5-124">同时连接的计算机数量。</span><span class="sxs-lookup"><span data-stu-id="af2e5-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="af2e5-125">默认值为 new-cimsession default。</span><span class="sxs-lookup"><span data-stu-id="af2e5-125">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="af2e5-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="af2e5-126">DependsOn</span></span> | <span data-ttu-id="af2e5-127">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="af2e5-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="af2e5-128">例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="af2e5-128">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="af2e5-129">示例</span><span class="sxs-lookup"><span data-stu-id="af2e5-129">Example</span></span>

<span data-ttu-id="af2e5-130">有关如何使用此资源的示例，请参阅[指定跨节点依赖关系](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="af2e5-130">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
