---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSC WaitForAll 资源
ms.openlocfilehash: 1e891f1aecbdbe641973669f71f22664ad8ea16c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076916"
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="7edf0-103">DSC WaitForAll 资源</span><span class="sxs-lookup"><span data-stu-id="7edf0-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="7edf0-104">适用于：Windows PowerShell 5.0 及更高版本</span><span class="sxs-lookup"><span data-stu-id="7edf0-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="7edf0-105">可以在 [DSC 配置](../../../configurations/configurations.md)中的节点块内使用 WaitForAll Desired State Configuration (DSC) 资源，以指定依赖其他节点上的配置。</span><span class="sxs-lookup"><span data-stu-id="7edf0-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="7edf0-106">如果由 ResourceName 属性指定的资源在 NodeName 属性定义的所有目标节点上都处于相应状态，那么此资源成功。</span><span class="sxs-lookup"><span data-stu-id="7edf0-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="7edf0-107">语法</span><span class="sxs-lookup"><span data-stu-id="7edf0-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="7edf0-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="7edf0-108">Properties</span></span>

|  <span data-ttu-id="7edf0-109">属性</span><span class="sxs-lookup"><span data-stu-id="7edf0-109">Property</span></span>  |  <span data-ttu-id="7edf0-110">说明</span><span class="sxs-lookup"><span data-stu-id="7edf0-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="7edf0-111">ResourceName</span><span class="sxs-lookup"><span data-stu-id="7edf0-111">ResourceName</span></span>| <span data-ttu-id="7edf0-112">要依赖的资源名称。</span><span class="sxs-lookup"><span data-stu-id="7edf0-112">The resource name to depend on.</span></span> <span data-ttu-id="7edf0-113">如果此资源属于不同的配置，请将名称的格式设置为“[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]”</span><span class="sxs-lookup"><span data-stu-id="7edf0-113">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="7edf0-114">NodeName</span><span class="sxs-lookup"><span data-stu-id="7edf0-114">NodeName</span></span>| <span data-ttu-id="7edf0-115">要依赖的资源的目标节点。</span><span class="sxs-lookup"><span data-stu-id="7edf0-115">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="7edf0-116">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="7edf0-116">RetryIntervalSec</span></span>| <span data-ttu-id="7edf0-117">重试前等待的秒数。</span><span class="sxs-lookup"><span data-stu-id="7edf0-117">The number of seconds before retrying.</span></span> <span data-ttu-id="7edf0-118">最小值为 1。</span><span class="sxs-lookup"><span data-stu-id="7edf0-118">Minimum is 1.</span></span>|
| <span data-ttu-id="7edf0-119">RetryCount</span><span class="sxs-lookup"><span data-stu-id="7edf0-119">RetryCount</span></span>| <span data-ttu-id="7edf0-120">重试次数上限。</span><span class="sxs-lookup"><span data-stu-id="7edf0-120">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="7edf0-121">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="7edf0-121">ThrottleLimit</span></span>| <span data-ttu-id="7edf0-122">同时连接的计算机数量。</span><span class="sxs-lookup"><span data-stu-id="7edf0-122">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="7edf0-123">默认值为 new-cimsession default。</span><span class="sxs-lookup"><span data-stu-id="7edf0-123">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="7edf0-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7edf0-124">DependsOn</span></span> | <span data-ttu-id="7edf0-125">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="7edf0-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7edf0-126">例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="7edf0-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="7edf0-127">示例</span><span class="sxs-lookup"><span data-stu-id="7edf0-127">Example</span></span>

<span data-ttu-id="7edf0-128">有关如何使用此资源的示例，请参阅[指定跨节点依赖关系](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="7edf0-128">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
