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
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="247ea-103">DSC WaitForSome 资源</span><span class="sxs-lookup"><span data-stu-id="247ea-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="247ea-104">适用于：Windows PowerShell 5.0 及更高版本</span><span class="sxs-lookup"><span data-stu-id="247ea-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="247ea-105">可以在 [DSC 配置](configurations.md)中的节点块内使用 WaitForAny Desired State Configuration (DSC) 资源，以指定依赖其他节点上的配置。</span><span class="sxs-lookup"><span data-stu-id="247ea-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="247ea-106">如果由 ResourceName 属性指定的资源在 NodeName 属性定义的最少目标节点（由 NodeCount 指定）上都处于相应状态，那么此资源成功。</span><span class="sxs-lookup"><span data-stu-id="247ea-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span> 


## <a name="syntax"></a><span data-ttu-id="247ea-107">语法</span><span class="sxs-lookup"><span data-stu-id="247ea-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="247ea-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="247ea-108">Properties</span></span>

|  <span data-ttu-id="247ea-109">属性</span><span class="sxs-lookup"><span data-stu-id="247ea-109">Property</span></span>  |  <span data-ttu-id="247ea-110">说明</span><span class="sxs-lookup"><span data-stu-id="247ea-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="247ea-111">ResourceName</span><span class="sxs-lookup"><span data-stu-id="247ea-111">ResourceName</span></span>| <span data-ttu-id="247ea-112">要依赖的资源名称。</span><span class="sxs-lookup"><span data-stu-id="247ea-112">The resource name to depend on.</span></span>| 
| <span data-ttu-id="247ea-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="247ea-113">NodeName</span></span>| <span data-ttu-id="247ea-114">要依赖的资源的目标节点。</span><span class="sxs-lookup"><span data-stu-id="247ea-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="247ea-115">NodeCount</span><span class="sxs-lookup"><span data-stu-id="247ea-115">NodeCount</span></span>| <span data-ttu-id="247ea-116">此资源成功至少所需的处于相应状态的节点数。</span><span class="sxs-lookup"><span data-stu-id="247ea-116">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="247ea-117">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="247ea-117">RetryIntervalSec</span></span>| <span data-ttu-id="247ea-118">重试前等待的秒数。</span><span class="sxs-lookup"><span data-stu-id="247ea-118">The number of seconds before retrying.</span></span> <span data-ttu-id="247ea-119">最小值为 1。</span><span class="sxs-lookup"><span data-stu-id="247ea-119">Minimum is 1.</span></span>| 
| <span data-ttu-id="247ea-120">RetryCount</span><span class="sxs-lookup"><span data-stu-id="247ea-120">RetryCount</span></span>| <span data-ttu-id="247ea-121">重试次数上限。</span><span class="sxs-lookup"><span data-stu-id="247ea-121">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="247ea-122">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="247ea-122">ThrottleLimit</span></span>| <span data-ttu-id="247ea-123">同时连接的计算机数量。</span><span class="sxs-lookup"><span data-stu-id="247ea-123">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="247ea-124">默认值为 new-cimsession default。</span><span class="sxs-lookup"><span data-stu-id="247ea-124">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="247ea-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="247ea-125">DependsOn</span></span> | <span data-ttu-id="247ea-126">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="247ea-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="247ea-127">例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="247ea-127">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="247ea-128">示例</span><span class="sxs-lookup"><span data-stu-id="247ea-128">Example</span></span>

<span data-ttu-id="247ea-129">有关如何使用此资源的示例，请参阅[指定跨节点依赖关系](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="247ea-129">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>
