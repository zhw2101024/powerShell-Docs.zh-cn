---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: DSC WaitForAll 资源
ms.openlocfilehash: 1bdaa63812766cfe5ec0778ef07689109683b994
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953014"
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="28032-103">DSC WaitForAll 资源</span><span class="sxs-lookup"><span data-stu-id="28032-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="28032-104">适用于：Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="28032-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="28032-105">可以在 [DSC 配置](../../../configurations/configurations.md)中的节点块内使用 WaitForAll  Desired State Configuration (DSC) 资源，以指定依赖其他节点上的配置。</span><span class="sxs-lookup"><span data-stu-id="28032-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="28032-106">如果由 ResourceName  属性指定的资源在 NodeName  属性定义的所有目标节点上都处于相应状态，那么此资源成功。</span><span class="sxs-lookup"><span data-stu-id="28032-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="28032-107">WaitForAll 资源使用 Windows 远程管理来检查其他节点的状态  。</span><span class="sxs-lookup"><span data-stu-id="28032-107">**WaitForAll** resource uses Windows Remote Management to check the state of other Nodes.</span></span> <span data-ttu-id="28032-108">要详细了解 WinRM 的端口和安全性要求，请参阅 [PowerShell 远程处理安全注意事项](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6)。</span><span class="sxs-lookup"><span data-stu-id="28032-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="28032-109">语法</span><span class="sxs-lookup"><span data-stu-id="28032-109">Syntax</span></span>

```Syntax
WaitForAll [string] #ResourceName
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

## <a name="properties"></a><span data-ttu-id="28032-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="28032-110">Properties</span></span>

|<span data-ttu-id="28032-111">属性</span><span class="sxs-lookup"><span data-stu-id="28032-111">Property</span></span> |<span data-ttu-id="28032-112">说明</span><span class="sxs-lookup"><span data-stu-id="28032-112">Description</span></span> |
|---|---|
|<span data-ttu-id="28032-113">ResourceName</span><span class="sxs-lookup"><span data-stu-id="28032-113">ResourceName</span></span> |<span data-ttu-id="28032-114">要依赖的资源名称。</span><span class="sxs-lookup"><span data-stu-id="28032-114">The resource name to depend on.</span></span> <span data-ttu-id="28032-115">如果此资源属于其他配置，则将名称格式设置为 `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`。</span><span class="sxs-lookup"><span data-stu-id="28032-115">If this resource belongs to a different configuration, format the name as `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span></span> |
|<span data-ttu-id="28032-116">NodeName</span><span class="sxs-lookup"><span data-stu-id="28032-116">NodeName</span></span> |<span data-ttu-id="28032-117">要依赖的资源的目标节点。</span><span class="sxs-lookup"><span data-stu-id="28032-117">The target nodes of the resource to depend on.</span></span> |
|<span data-ttu-id="28032-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="28032-118">RetryIntervalSec</span></span> |<span data-ttu-id="28032-119">重试前等待的秒数。</span><span class="sxs-lookup"><span data-stu-id="28032-119">The number of seconds before retrying.</span></span> <span data-ttu-id="28032-120">最小值为 1。</span><span class="sxs-lookup"><span data-stu-id="28032-120">Minimum is 1.</span></span> |
|<span data-ttu-id="28032-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="28032-121">RetryCount</span></span> |<span data-ttu-id="28032-122">重试次数上限。</span><span class="sxs-lookup"><span data-stu-id="28032-122">The maximum number of times to retry.</span></span> |
|<span data-ttu-id="28032-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="28032-123">ThrottleLimit</span></span> |<span data-ttu-id="28032-124">同时连接的计算机数量。</span><span class="sxs-lookup"><span data-stu-id="28032-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="28032-125">默认为 `New-CimSession` 默认值。</span><span class="sxs-lookup"><span data-stu-id="28032-125">Default is `New-CimSession` default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="28032-126">公共属性</span><span class="sxs-lookup"><span data-stu-id="28032-126">Common properties</span></span>

|<span data-ttu-id="28032-127">属性</span><span class="sxs-lookup"><span data-stu-id="28032-127">Property</span></span> |<span data-ttu-id="28032-128">说明</span><span class="sxs-lookup"><span data-stu-id="28032-128">Description</span></span> |
|---|---|
|<span data-ttu-id="28032-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="28032-129">DependsOn</span></span> |<span data-ttu-id="28032-130">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="28032-130">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="28032-131">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="28032-131">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="28032-132">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="28032-132">PsDscRunAsCredential</span></span> |<span data-ttu-id="28032-133">设置用于运行整个资源的身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="28032-133">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="28032-134">在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="28032-134">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="28032-135">有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="28032-135">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="28032-136">示例</span><span class="sxs-lookup"><span data-stu-id="28032-136">Example</span></span>

<span data-ttu-id="28032-137">有关如何使用此资源的示例，请参阅[指定跨节点依赖关系](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="28032-137">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>