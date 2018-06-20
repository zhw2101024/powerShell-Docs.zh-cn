---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 指定跨节点依赖关系
ms.openlocfilehash: c1802d6baa1f2b3449603e0374a83e213abf598e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218614"
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="494fd-103">指定跨节点依赖关系</span><span class="sxs-lookup"><span data-stu-id="494fd-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="494fd-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="494fd-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="494fd-105">DSC 提供特殊的资源，**WaitForAll**、**WaitForAny** 和 **WaitForSome**，可用于在配置中指定其他节点上配置的依赖关系。</span><span class="sxs-lookup"><span data-stu-id="494fd-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="494fd-106">这些资源的行为如下所述：</span><span class="sxs-lookup"><span data-stu-id="494fd-106">The behavior of these resources is as follows:</span></span>

* <span data-ttu-id="494fd-107">**WaitForAll**：如果指定的资源在 **NodeName** 属性中定义的所有目标节点上处于所需状态，则该资源成功。</span><span class="sxs-lookup"><span data-stu-id="494fd-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
* <span data-ttu-id="494fd-108">**WaitForAny**：如果指定的资源在**NodeName** 属性中定义的至少一个目标节点上处于所需状态，则该资源成功。</span><span class="sxs-lookup"><span data-stu-id="494fd-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
* <span data-ttu-id="494fd-109">**WaitForSome**：指定除 **NodeName** 属性之外的 **NodeCount** 属性。</span><span class="sxs-lookup"><span data-stu-id="494fd-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="494fd-110">如果资源在 **NodeName** 属性定义的节点（数量下限由 **NodeCount** 指定）上处于所需的状态，则资源成功。</span><span class="sxs-lookup"><span data-stu-id="494fd-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="494fd-111">使用 WaitForXXXX 资源</span><span class="sxs-lookup"><span data-stu-id="494fd-111">Using WaitForXXXX resources</span></span>

<span data-ttu-id="494fd-112">若要使用 **WaitForXXXX** 资源，可以创建指定要等待的 DSC 资源和节点的该资源类型的资源块。</span><span class="sxs-lookup"><span data-stu-id="494fd-112">To use the **WaitForXXXX** resources, you create a resource block of that resource type that specifies the DSC resource and node(s) to wait for.</span></span> <span data-ttu-id="494fd-113">然后，使用配置中其他任何资源块内的 **DependsOn** 属性，等待 **WaitForXXXX** 节点中指定的条件成功。</span><span class="sxs-lookup"><span data-stu-id="494fd-113">You then use the **DependsOn** property in any other resource blocks in your configuration to wait for the conditions specified in the **WaitForXXXX** node to succeed.</span></span>

<span data-ttu-id="494fd-114">例如，在下面的配置中，目标节点正在等待 **xADDomain** 资源通过最多 30 次重试（时间间隔为 15 秒）在 **MyDC** 节点上完成，然后目标节点才能加入域。</span><span class="sxs-lookup"><span data-stu-id="494fd-114">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

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

><span data-ttu-id="494fd-115">**注意：** 默认情况下，WaitForXXX 资源尝试一次，然后就会失败。</span><span class="sxs-lookup"><span data-stu-id="494fd-115">**Note:** By default the WaitForXXX resources try one time and then fail.</span></span> <span data-ttu-id="494fd-116">虽然这不是必需的，但通常需要指定重试间隔和次数。</span><span class="sxs-lookup"><span data-stu-id="494fd-116">Although it is not required, you will typically want to specify a retry interval and count.</span></span>

## <a name="see-also"></a><span data-ttu-id="494fd-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="494fd-117">See Also</span></span>
* [<span data-ttu-id="494fd-118">DSC 配置</span><span class="sxs-lookup"><span data-stu-id="494fd-118">DSC Configurations</span></span>](configurations.md)
* [<span data-ttu-id="494fd-119">DSC 资源</span><span class="sxs-lookup"><span data-stu-id="494fd-119">DSC Resources</span></span>](resources.md)
* [<span data-ttu-id="494fd-120">配置本地配置管理器</span><span class="sxs-lookup"><span data-stu-id="494fd-120">Configuring The Local Configuration Manager</span></span>](metaConfig.md)