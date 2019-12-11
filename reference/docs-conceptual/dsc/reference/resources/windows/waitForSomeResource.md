---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: DSC WaitForSome 资源
ms.openlocfilehash: 91589c84518a2bd0f4816d11aa011dec1d5305e1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71952974"
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="15810-103">DSC WaitForSome 资源</span><span class="sxs-lookup"><span data-stu-id="15810-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="15810-104">适用于：Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="15810-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="15810-105">可以在 [DSC 配置](../../../configurations/configurations.md)中的节点块内使用 WaitForSome  Desired State Configuration (DSC) 资源，以指定依赖其他节点上的配置。</span><span class="sxs-lookup"><span data-stu-id="15810-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="15810-106">如果由 ResourceName  属性指定的资源在 NodeName  属性定义的最少节点数（由 NodeCount  指定）上都处于所需状态，那么此资源成功。</span><span class="sxs-lookup"><span data-stu-id="15810-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="15810-107">WaitForSome 资源使用 Windows 远程管理来检查其他节点的状态  。</span><span class="sxs-lookup"><span data-stu-id="15810-107">**WaitForSome** resource uses Windows Remote Management to check the state of other Nodes.</span></span> <span data-ttu-id="15810-108">要详细了解 WinRM 的端口和安全性要求，请参阅 [PowerShell 远程处理安全注意事项](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6)。</span><span class="sxs-lookup"><span data-stu-id="15810-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="15810-109">语法</span><span class="sxs-lookup"><span data-stu-id="15810-109">Syntax</span></span>

```Syntax
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [ RetryCount = [UInt32] ]
    [ RetryIntervalSec = [UInt64] ]
    [ ThrottleLimit = [UInt32] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="15810-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="15810-110">Properties</span></span>

|<span data-ttu-id="15810-111">属性</span><span class="sxs-lookup"><span data-stu-id="15810-111">Property</span></span> |<span data-ttu-id="15810-112">说明</span><span class="sxs-lookup"><span data-stu-id="15810-112">Description</span></span> |
|---|---|
|<span data-ttu-id="15810-113">NodeCount</span><span class="sxs-lookup"><span data-stu-id="15810-113">NodeCount</span></span> |<span data-ttu-id="15810-114">此资源成功至少所需的处于相应状态的节点数。</span><span class="sxs-lookup"><span data-stu-id="15810-114">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span> |
|<span data-ttu-id="15810-115">NodeName</span><span class="sxs-lookup"><span data-stu-id="15810-115">NodeName</span></span> |<span data-ttu-id="15810-116">要依赖的资源的目标节点。</span><span class="sxs-lookup"><span data-stu-id="15810-116">The target nodes of the resource to depend on.</span></span> |
|<span data-ttu-id="15810-117">ResourceName</span><span class="sxs-lookup"><span data-stu-id="15810-117">ResourceName</span></span> |<span data-ttu-id="15810-118">要依赖的资源名称。</span><span class="sxs-lookup"><span data-stu-id="15810-118">The resource name to depend on.</span></span> <span data-ttu-id="15810-119">如果此资源属于其他配置，则将名称格式设置为 `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`。</span><span class="sxs-lookup"><span data-stu-id="15810-119">If this resource belongs to a different configuration, format the name as `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span></span> |
|<span data-ttu-id="15810-120">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="15810-120">RetryIntervalSec</span></span> |<span data-ttu-id="15810-121">重试前等待的秒数。</span><span class="sxs-lookup"><span data-stu-id="15810-121">The number of seconds before retrying.</span></span> <span data-ttu-id="15810-122">最小值为 1。</span><span class="sxs-lookup"><span data-stu-id="15810-122">Minimum is 1.</span></span> |
|<span data-ttu-id="15810-123">RetryCount</span><span class="sxs-lookup"><span data-stu-id="15810-123">RetryCount</span></span> |<span data-ttu-id="15810-124">重试次数上限。</span><span class="sxs-lookup"><span data-stu-id="15810-124">The maximum number of times to retry.</span></span> |
|<span data-ttu-id="15810-125">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="15810-125">ThrottleLimit</span></span> |<span data-ttu-id="15810-126">同时连接的计算机数量。</span><span class="sxs-lookup"><span data-stu-id="15810-126">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="15810-127">默认为 `New-CimSession` 默认值。</span><span class="sxs-lookup"><span data-stu-id="15810-127">Default is `New-CimSession` default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="15810-128">公共属性</span><span class="sxs-lookup"><span data-stu-id="15810-128">Common properties</span></span>

|<span data-ttu-id="15810-129">属性</span><span class="sxs-lookup"><span data-stu-id="15810-129">Property</span></span> |<span data-ttu-id="15810-130">说明</span><span class="sxs-lookup"><span data-stu-id="15810-130">Description</span></span> |
|---|---|
|<span data-ttu-id="15810-131">DependsOn</span><span class="sxs-lookup"><span data-stu-id="15810-131">DependsOn</span></span> |<span data-ttu-id="15810-132">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="15810-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="15810-133">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="15810-133">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="15810-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="15810-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="15810-135">设置用于运行整个资源的身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="15810-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="15810-136">在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="15810-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="15810-137">有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="15810-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="15810-138">示例</span><span class="sxs-lookup"><span data-stu-id="15810-138">Example</span></span>

<span data-ttu-id="15810-139">有关如何使用此资源的示例，请参阅[指定跨节点依赖关系](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="15810-139">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>