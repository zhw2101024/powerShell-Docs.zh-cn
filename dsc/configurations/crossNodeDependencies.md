---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 指定跨节点依赖关系
ms.openlocfilehash: 62e553d894897ae1908745c2788b7b7b9cbe50ff
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734681"
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="6ef4a-103">指定跨节点依赖关系</span><span class="sxs-lookup"><span data-stu-id="6ef4a-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="6ef4a-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6ef4a-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="6ef4a-105">DSC 提供特殊的资源，**WaitForAll**、**WaitForAny** 和 **WaitForSome**，可用于在配置中指定其他节点上配置的依赖关系。</span><span class="sxs-lookup"><span data-stu-id="6ef4a-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="6ef4a-106">这些资源的行为如下所述：</span><span class="sxs-lookup"><span data-stu-id="6ef4a-106">The behavior of these resources is as follows:</span></span>

- <span data-ttu-id="6ef4a-107">**WaitForAll**：如果指定的资源在 NodeName  属性中定义的所有目标节点上处于所需状态，则该资源成功。</span><span class="sxs-lookup"><span data-stu-id="6ef4a-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="6ef4a-108">**WaitForAny**：如果指定的资源在 NodeName  属性中定义的至少一个目标节点上处于所需状态，则该资源成功。</span><span class="sxs-lookup"><span data-stu-id="6ef4a-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="6ef4a-109">**WaitForSome**：指定除 NodeName  属性之外的 NodeCount  属性。</span><span class="sxs-lookup"><span data-stu-id="6ef4a-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="6ef4a-110">如果资源在 **NodeName** 属性定义的节点（数量下限由 **NodeCount** 指定）上处于所需的状态，则资源成功。</span><span class="sxs-lookup"><span data-stu-id="6ef4a-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="6ef4a-111">语法</span><span class="sxs-lookup"><span data-stu-id="6ef4a-111">Syntax</span></span>

<span data-ttu-id="6ef4a-112">WaitForAll  和 WaitForAny  资源共享相同语法。</span><span class="sxs-lookup"><span data-stu-id="6ef4a-112">The **WaitForAll** and **WaitForAny** resources share the same syntax.</span></span> <span data-ttu-id="6ef4a-113">将以下示例中的 \<ResourceType\> 替换为 WaitForAny  或 WaitForAll  。</span><span class="sxs-lookup"><span data-stu-id="6ef4a-113">Replace \<ResourceType\> in the example below with either **WaitForAny** or **WaitForAll**.</span></span>
<span data-ttu-id="6ef4a-114">和 DependsOn  关键字一样，需要将名称的格式设置为“[ResourceType] ResourceName”。</span><span class="sxs-lookup"><span data-stu-id="6ef4a-114">Like the **DependsOn** keyword, you will need to format the name as "[ResourceType]ResourceName".</span></span> <span data-ttu-id="6ef4a-115">如果资源属于一个单独的[配置](configurations.md)，则在格式化字符串“[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]”中包含 ConfigurationName  。</span><span class="sxs-lookup"><span data-stu-id="6ef4a-115">If the resource belongs to a separate [Configuration](configurations.md), include the **ConfigurationName** in the formatted string "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span></span> <span data-ttu-id="6ef4a-116">NodeName  是计算机或节点，当前资源应在其中等待。</span><span class="sxs-lookup"><span data-stu-id="6ef4a-116">The **NodeName** is the computer, or Node, on which the current resource should wait.</span></span>

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

<span data-ttu-id="6ef4a-117">WaitForSome  资源具有与上述示例类似的语法，但添加 NodeCount  项。</span><span class="sxs-lookup"><span data-stu-id="6ef4a-117">The **WaitForSome** resource has a similar syntax to the example above, but adds the **NodeCount** key.</span></span> <span data-ttu-id="6ef4a-118">NodeCount  指示当前资源应等待的节点数。</span><span class="sxs-lookup"><span data-stu-id="6ef4a-118">The **NodeCount** indicates how many Nodes the current resource should wait on.</span></span>

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

<span data-ttu-id="6ef4a-119">所有 WaitForXXXX  共享以下语法项。</span><span class="sxs-lookup"><span data-stu-id="6ef4a-119">All **WaitForXXXX** share the following syntax keys.</span></span>

|<span data-ttu-id="6ef4a-120">属性</span><span class="sxs-lookup"><span data-stu-id="6ef4a-120">Property</span></span>|  <span data-ttu-id="6ef4a-121">说明</span><span class="sxs-lookup"><span data-stu-id="6ef4a-121">Description</span></span>   |
|---------|---------------------|
| <span data-ttu-id="6ef4a-122">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="6ef4a-122">RetryIntervalSec</span></span>| <span data-ttu-id="6ef4a-123">重试前等待的秒数。</span><span class="sxs-lookup"><span data-stu-id="6ef4a-123">The number of seconds before retrying.</span></span> <span data-ttu-id="6ef4a-124">最小值为 1。</span><span class="sxs-lookup"><span data-stu-id="6ef4a-124">Minimum is 1.</span></span>|
| <span data-ttu-id="6ef4a-125">RetryCount</span><span class="sxs-lookup"><span data-stu-id="6ef4a-125">RetryCount</span></span>| <span data-ttu-id="6ef4a-126">重试次数上限。</span><span class="sxs-lookup"><span data-stu-id="6ef4a-126">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="6ef4a-127">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="6ef4a-127">ThrottleLimit</span></span>| <span data-ttu-id="6ef4a-128">同时连接的计算机数量。</span><span class="sxs-lookup"><span data-stu-id="6ef4a-128">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="6ef4a-129">默认为 `New-CimSession` 默认值。</span><span class="sxs-lookup"><span data-stu-id="6ef4a-129">Default is `New-CimSession` default.</span></span>|
| <span data-ttu-id="6ef4a-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="6ef4a-130">DependsOn</span></span> | <span data-ttu-id="6ef4a-131">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="6ef4a-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6ef4a-132">有关详细信息，请参阅 [DependsOn](resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="6ef4a-132">For more information, see [DependsOn](resource-depends-on.md)</span></span>|
| <span data-ttu-id="6ef4a-133">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="6ef4a-133">PsDscRunAsCredential</span></span> | <span data-ttu-id="6ef4a-134">请参阅[通过用户凭据使用 DSC](./runAsUser.md)</span><span class="sxs-lookup"><span data-stu-id="6ef4a-134">See [Using DSC with User Credentials](./runAsUser.md)</span></span> |

## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="6ef4a-135">使用 WaitForXXXX 资源</span><span class="sxs-lookup"><span data-stu-id="6ef4a-135">Using WaitForXXXX resources</span></span>

<span data-ttu-id="6ef4a-136">每个 WaitForXXXX  资源都在指定节点上等待指定资源完成。</span><span class="sxs-lookup"><span data-stu-id="6ef4a-136">Each **WaitForXXXX** resource waits for the specified resources to complete on the specified Node.</span></span>
<span data-ttu-id="6ef4a-137">然后，相同配置中的其他资源可以使用 DependsOn  项依赖于  WaitForXXXX  资源。</span><span class="sxs-lookup"><span data-stu-id="6ef4a-137">Other resources in the same Configuration can then *depend on* the **WaitForXXXX** resource using the **DependsOn** key.</span></span>

<span data-ttu-id="6ef4a-138">例如，在下面的配置中，目标节点正在等待 **xADDomain** 资源通过最多 30 次重试（时间间隔为 15 秒）在 **MyDC** 节点上完成，然后目标节点才能加入域。</span><span class="sxs-lookup"><span data-stu-id="6ef4a-138">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

<span data-ttu-id="6ef4a-139">默认情况下，WaitForXXX 资源尝试一次，然后就会失败  。</span><span class="sxs-lookup"><span data-stu-id="6ef4a-139">By default the **WaitForXXX** resources try one time and then fail.</span></span> <span data-ttu-id="6ef4a-140">虽然这不是必需的，但通常需要指定 RetryCount  和 RetryIntervalSec  。</span><span class="sxs-lookup"><span data-stu-id="6ef4a-140">Although it is not required, you will typically want to specify a **RetryCount** and **RetryIntervalSec**.</span></span>

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

<span data-ttu-id="6ef4a-141">在编译配置时，将生成两个“.mof”文件。</span><span class="sxs-lookup"><span data-stu-id="6ef4a-141">When you compile the Configuration, two ".mof" files are generated.</span></span> <span data-ttu-id="6ef4a-142">使用 [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet 将这两个“.mof”文件应用于目标节点</span><span class="sxs-lookup"><span data-stu-id="6ef4a-142">Apply both ".mof" files to the target Nodes using the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span></span>

> [!NOTE]
> <span data-ttu-id="6ef4a-143">WaitForXXX 资源使用 Windows 远程管理来检查其他节点的状态  。</span><span class="sxs-lookup"><span data-stu-id="6ef4a-143">**WaitForXXX** resources use Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="6ef4a-144">要详细了解 WinRM 的端口和安全性要求，请参阅 [PowerShell 远程处理安全注意事项](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6)。</span><span class="sxs-lookup"><span data-stu-id="6ef4a-144">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="see-also"></a><span data-ttu-id="6ef4a-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6ef4a-145">See Also</span></span>

- [<span data-ttu-id="6ef4a-146">DSC 配置</span><span class="sxs-lookup"><span data-stu-id="6ef4a-146">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="6ef4a-147">使用资源依赖项</span><span class="sxs-lookup"><span data-stu-id="6ef4a-147">Use Resource Dependencies</span></span>](resource-depends-on.md)
- [<span data-ttu-id="6ef4a-148">DSC 资源</span><span class="sxs-lookup"><span data-stu-id="6ef4a-148">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="6ef4a-149">配置本地配置管理器</span><span class="sxs-lookup"><span data-stu-id="6ef4a-149">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
