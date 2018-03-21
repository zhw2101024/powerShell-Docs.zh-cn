---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "DSC WaitForSome 资源"
ms.openlocfilehash: 8b0ad0dbd31816cc673c7f77945927987e90e08b
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2018
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="42fa1-103">DSC WaitForSome 资源</span><span class="sxs-lookup"><span data-stu-id="42fa1-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="42fa1-104">适用于：Windows PowerShell 5.0 及更高版本</span><span class="sxs-lookup"><span data-stu-id="42fa1-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="42fa1-105">可以在 [DSC 配置](configurations.md)中的节点块内使用 WaitForAny Desired State Configuration (DSC) 资源，以指定依赖其他节点上的配置。</span><span class="sxs-lookup"><span data-stu-id="42fa1-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="42fa1-106">如果由 ResourceName 属性指定的资源在 NodeName 属性定义的最少节点数（由 NodeCount 指定）上都处于所需状态，那么此资源成功。</span><span class="sxs-lookup"><span data-stu-id="42fa1-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span> 


## <a name="syntax"></a><span data-ttu-id="42fa1-107">语法</span><span class="sxs-lookup"><span data-stu-id="42fa1-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="42fa1-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="42fa1-108">Properties</span></span>

|  <span data-ttu-id="42fa1-109">属性</span><span class="sxs-lookup"><span data-stu-id="42fa1-109">Property</span></span>  |  <span data-ttu-id="42fa1-110">说明</span><span class="sxs-lookup"><span data-stu-id="42fa1-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="42fa1-111">NodeCount</span><span class="sxs-lookup"><span data-stu-id="42fa1-111">NodeCount</span></span>| <span data-ttu-id="42fa1-112">此资源成功至少所需的处于相应状态的节点数。</span><span class="sxs-lookup"><span data-stu-id="42fa1-112">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="42fa1-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="42fa1-113">NodeName</span></span>| <span data-ttu-id="42fa1-114">要依赖的资源的目标节点。</span><span class="sxs-lookup"><span data-stu-id="42fa1-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="42fa1-115">ResourceName</span><span class="sxs-lookup"><span data-stu-id="42fa1-115">ResourceName</span></span>| <span data-ttu-id="42fa1-116">要依赖的资源名称。</span><span class="sxs-lookup"><span data-stu-id="42fa1-116">The resource name to depend on.</span></span> <span data-ttu-id="42fa1-117">如果此资源属于不同的配置，请将名称的格式设置为“[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]”</span><span class="sxs-lookup"><span data-stu-id="42fa1-117">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>| 
| <span data-ttu-id="42fa1-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="42fa1-118">RetryIntervalSec</span></span>| <span data-ttu-id="42fa1-119">重试前等待的秒数。</span><span class="sxs-lookup"><span data-stu-id="42fa1-119">The number of seconds before retrying.</span></span> <span data-ttu-id="42fa1-120">最小值为 1。</span><span class="sxs-lookup"><span data-stu-id="42fa1-120">Minimum is 1.</span></span>| 
| <span data-ttu-id="42fa1-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="42fa1-121">RetryCount</span></span>| <span data-ttu-id="42fa1-122">重试次数上限。</span><span class="sxs-lookup"><span data-stu-id="42fa1-122">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="42fa1-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="42fa1-123">ThrottleLimit</span></span>| <span data-ttu-id="42fa1-124">同时连接的计算机数量。</span><span class="sxs-lookup"><span data-stu-id="42fa1-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="42fa1-125">默认值为 new-cimsession default。</span><span class="sxs-lookup"><span data-stu-id="42fa1-125">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="42fa1-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="42fa1-126">DependsOn</span></span> | <span data-ttu-id="42fa1-127">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="42fa1-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="42fa1-128">例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="42fa1-128">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="42fa1-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="42fa1-129">PsDscRunAsCredential</span></span> | <span data-ttu-id="42fa1-130">请参阅[通过用户凭据使用 DSC](https://docs.microsoft.com/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="42fa1-130">See [Using DSC with User Credentials](https://docs.microsoft.com/powershell/dsc/runasuser)</span></span> |


## <a name="example"></a><span data-ttu-id="42fa1-131">示例</span><span class="sxs-lookup"><span data-stu-id="42fa1-131">Example</span></span>

<span data-ttu-id="42fa1-132">有关如何使用此资源的示例，请参阅[指定跨节点依赖关系](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="42fa1-132">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

