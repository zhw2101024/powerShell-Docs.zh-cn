---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "DSC WaitForAll 资源"
ms.openlocfilehash: dcc23ad4e6905bc277ad39348350d5425fc90ad7
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="a0522-103">DSC WaitForAll 资源</span><span class="sxs-lookup"><span data-stu-id="a0522-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="a0522-104">适用于：Windows PowerShell 5.0 及更高版本</span><span class="sxs-lookup"><span data-stu-id="a0522-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="a0522-105">可以在 [DSC 配置](configurations.md)中的节点块内使用 WaitForAll Desired State Configuration (DSC) 资源，以指定依赖其他节点上的配置。</span><span class="sxs-lookup"><span data-stu-id="a0522-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="a0522-106">如果由 ResourceName 属性指定的资源在 NodeName 属性定义的所有目标节点上都处于相应状态，那么此资源成功。</span><span class="sxs-lookup"><span data-stu-id="a0522-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="a0522-107">语法</span><span class="sxs-lookup"><span data-stu-id="a0522-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="a0522-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="a0522-108">Properties</span></span>

|  <span data-ttu-id="a0522-109">属性</span><span class="sxs-lookup"><span data-stu-id="a0522-109">Property</span></span>  |  <span data-ttu-id="a0522-110">说明</span><span class="sxs-lookup"><span data-stu-id="a0522-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="a0522-111">ResourceName</span><span class="sxs-lookup"><span data-stu-id="a0522-111">ResourceName</span></span>| <span data-ttu-id="a0522-112">要依赖的资源名称。</span><span class="sxs-lookup"><span data-stu-id="a0522-112">The resource name to depend on.</span></span>| 
| <span data-ttu-id="a0522-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="a0522-113">NodeName</span></span>| <span data-ttu-id="a0522-114">要依赖的资源的目标节点。</span><span class="sxs-lookup"><span data-stu-id="a0522-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="a0522-115">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="a0522-115">RetryIntervalSec</span></span>| <span data-ttu-id="a0522-116">重试前等待的秒数。</span><span class="sxs-lookup"><span data-stu-id="a0522-116">The number of seconds before retrying.</span></span> <span data-ttu-id="a0522-117">最小值为 1。</span><span class="sxs-lookup"><span data-stu-id="a0522-117">Minimum is 1.</span></span>| 
| <span data-ttu-id="a0522-118">RetryCount</span><span class="sxs-lookup"><span data-stu-id="a0522-118">RetryCount</span></span>| <span data-ttu-id="a0522-119">重试次数上限。</span><span class="sxs-lookup"><span data-stu-id="a0522-119">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="a0522-120">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="a0522-120">ThrottleLimit</span></span>| <span data-ttu-id="a0522-121">同时连接的计算机数量。</span><span class="sxs-lookup"><span data-stu-id="a0522-121">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="a0522-122">默认值为 new-cimsession default。</span><span class="sxs-lookup"><span data-stu-id="a0522-122">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="a0522-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="a0522-123">DependsOn</span></span> | <span data-ttu-id="a0522-124">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="a0522-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a0522-125">例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="a0522-125">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="a0522-126">示例</span><span class="sxs-lookup"><span data-stu-id="a0522-126">Example</span></span>

<span data-ttu-id="a0522-127">有关如何使用此资源的示例，请参阅[指定跨节点依赖关系](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="a0522-127">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

