---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 指定跨节点依赖关系
ms.openlocfilehash: 1bdfbd9f8a94809d6bf410eff525e1c877fb6aad
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080197"
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="a29c8-103">指定跨节点依赖关系</span><span class="sxs-lookup"><span data-stu-id="a29c8-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="a29c8-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a29c8-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="a29c8-105">DSC 提供特殊的资源，**WaitForAll**、**WaitForAny** 和 **WaitForSome**，可用于在配置中指定其他节点上配置的依赖关系。</span><span class="sxs-lookup"><span data-stu-id="a29c8-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="a29c8-106">这些资源的行为如下所述：</span><span class="sxs-lookup"><span data-stu-id="a29c8-106">The behavior of these resources is as follows:</span></span>

- <span data-ttu-id="a29c8-107">**WaitForAll**：如果指定的资源在 NodeName 属性中定义的所有目标节点上处于所需状态，则该资源成功。</span><span class="sxs-lookup"><span data-stu-id="a29c8-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="a29c8-108">**WaitForAny**：如果指定的资源在 NodeName 属性中定义的至少一个目标节点上处于所需状态，则该资源成功。</span><span class="sxs-lookup"><span data-stu-id="a29c8-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="a29c8-109">**WaitForSome**：指定除 NodeName 属性之外的 NodeCount 属性。</span><span class="sxs-lookup"><span data-stu-id="a29c8-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="a29c8-110">如果资源在 **NodeName** 属性定义的节点（数量下限由 **NodeCount** 指定）上处于所需的状态，则资源成功。</span><span class="sxs-lookup"><span data-stu-id="a29c8-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="a29c8-111">语法</span><span class="sxs-lookup"><span data-stu-id="a29c8-111">Syntax</span></span>

<span data-ttu-id="a29c8-112">WaitForAll 和 WaitForAny 资源共享相同语法。</span><span class="sxs-lookup"><span data-stu-id="a29c8-112">The **WaitForAll** and **WaitForAny** resources share the same syntax.</span></span> <span data-ttu-id="a29c8-113">将以下示例中的 \<ResourceType\> 替换为 WaitForAny 或 WaitForAll。</span><span class="sxs-lookup"><span data-stu-id="a29c8-113">Replace \<ResourceType\> in the example below with either **WaitForAny** or **WaitForAll**.</span></span>
<span data-ttu-id="a29c8-114">和 DependsOn 关键字一样，需要将名称的格式设置为“[ResourceType] ResourceName”。</span><span class="sxs-lookup"><span data-stu-id="a29c8-114">Like the **DependsOn** keyword, you will need to format the name as "[ResourceType]ResourceName".</span></span> <span data-ttu-id="a29c8-115">如果资源属于一个单独的[配置](configurations.md)，则在格式化字符串“[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]”中包含 ConfigurationName。</span><span class="sxs-lookup"><span data-stu-id="a29c8-115">If the resource belongs to a separate [Configuration](configurations.md), include the **ConfigurationName** in the formatted string "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span></span> <span data-ttu-id="a29c8-116">NodeName 是计算机或节点，当前资源应在其中等待。</span><span class="sxs-lookup"><span data-stu-id="a29c8-116">The **NodeName** is the computer, or Node, on which the current resource should wait.</span></span>

```
<ResourceType> [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential]]
    [ RetryCount = [Uint32] ]
    [ RetryIntervalSec = [Uint64] ]
    [ ThrottleLimit = [Uint32]]
}
```

<span data-ttu-id="a29c8-117">WaitForSome 资源具有与上述示例类似的语法，但添加 NodeCount 项。</span><span class="sxs-lookup"><span data-stu-id="a29c8-117">The **WaitForSome** resource has a similar syntax to the example above, but adds the **NodeCount** key.</span></span> <span data-ttu-id="a29c8-118">NodeCount 指示当前资源应等待的节点数。</span><span class="sxs-lookup"><span data-stu-id="a29c8-118">The **NodeCount** indicates how many Nodes the current resource should wait on.</span></span>

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

<span data-ttu-id="a29c8-119">所有 WaitForXXXX 共享以下语法项。</span><span class="sxs-lookup"><span data-stu-id="a29c8-119">All **WaitForXXXX** share the following syntax keys.</span></span>

<span data-ttu-id="a29c8-120">|  属性  |  说明   | | RetryIntervalSec| 重试之前等待的秒数。</span><span class="sxs-lookup"><span data-stu-id="a29c8-120">|  Property  |  Description   | | RetryIntervalSec| The number of seconds before retrying.</span></span> <span data-ttu-id="a29c8-121">最小值为 1。| | RetryCount| 重试的最大次数。| | ThrottleLimit| 同时连接的计算机数。</span><span class="sxs-lookup"><span data-stu-id="a29c8-121">Minimum is 1.| | RetryCount| The maximum number of times to retry.| | ThrottleLimit| Number of machines to connect simultaneously.</span></span> <span data-ttu-id="a29c8-122">默认值默认为 `New-CimSession`。| | DependsOn | 指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="a29c8-122">Default is `New-CimSession` default.| | DependsOn | Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a29c8-123">有关详细信息，请参阅 [DependsOn](resource-depends-on.md)| |PsDscRunAsCredential | 请参阅[将 DSC 与用户凭据结合使用](./runAsUser.md) |</span><span class="sxs-lookup"><span data-stu-id="a29c8-123">For more information, see [DependsOn](resource-depends-on.md)| | PsDscRunAsCredential | See [Using DSC with User Credentials](./runAsUser.md) |</span></span>


## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="a29c8-124">使用 WaitForXXXX 资源</span><span class="sxs-lookup"><span data-stu-id="a29c8-124">Using WaitForXXXX resources</span></span>

<span data-ttu-id="a29c8-125">每个 WaitForXXXX 资源都在指定节点上等待指定资源完成。</span><span class="sxs-lookup"><span data-stu-id="a29c8-125">Each **WaitForXXXX** resource waits for the specified resources to complete on the specified Node.</span></span> <span data-ttu-id="a29c8-126">然后，相同配置中的其他资源可以使用 DependsOn 项依赖于 WaitForXXXX 资源。</span><span class="sxs-lookup"><span data-stu-id="a29c8-126">Other resources in the same Configuration can then *depend on* the **WaitForXXXX** resource using the **DependsOn** key.</span></span>

<span data-ttu-id="a29c8-127">例如，在下面的配置中，目标节点正在等待 **xADDomain** 资源通过最多 30 次重试（时间间隔为 15 秒）在 **MyDC** 节点上完成，然后目标节点才能加入域。</span><span class="sxs-lookup"><span data-stu-id="a29c8-127">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

```powershell
Configuration JoinDomain
{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain NewDomain
        {
            DomainName = 'Contoso.com'
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }
    }

    Node myDomainJoinedServer
    {
        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

<span data-ttu-id="a29c8-128">在编译配置时，将生成两个“.mof”文件。</span><span class="sxs-lookup"><span data-stu-id="a29c8-128">When you compile the Configuration, two ".mof" files are generated.</span></span> <span data-ttu-id="a29c8-129">使用 [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet 将这两个“.mof”文件应用于目标节点</span><span class="sxs-lookup"><span data-stu-id="a29c8-129">Apply both ".mof" files to the target Nodes using the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span></span>

><span data-ttu-id="a29c8-130">**注意：** 默认情况下，WaitForXXX 资源尝试一次，然后就会失败。</span><span class="sxs-lookup"><span data-stu-id="a29c8-130">**Note:** By default the WaitForXXX resources try one time and then fail.</span></span> <span data-ttu-id="a29c8-131">虽然这不是必需的，但通常需要指定 RetryCount 和 RetryIntervalSec。</span><span class="sxs-lookup"><span data-stu-id="a29c8-131">Although it is not required, you will typically want to specify a **RetryCount** and **RetryIntervalSec**.</span></span>

## <a name="see-also"></a><span data-ttu-id="a29c8-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a29c8-132">See Also</span></span>

- [<span data-ttu-id="a29c8-133">DSC 配置</span><span class="sxs-lookup"><span data-stu-id="a29c8-133">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="a29c8-134">使用资源依赖项</span><span class="sxs-lookup"><span data-stu-id="a29c8-134">Use Resource Dependencies</span></span>](resource-depends-on.md)
- [<span data-ttu-id="a29c8-135">DSC 资源</span><span class="sxs-lookup"><span data-stu-id="a29c8-135">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="a29c8-136">配置本地配置管理器</span><span class="sxs-lookup"><span data-stu-id="a29c8-136">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
