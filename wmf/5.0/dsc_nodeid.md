---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 6d94de2d3f2c551219d8fbe5badb6e5bb913d796
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="separation-of-node-and-configuration-ids"></a><span data-ttu-id="f9a9c-102">节点和配置 ID 的分离</span><span class="sxs-lookup"><span data-stu-id="f9a9c-102">Separation of Node and Configuration IDs</span></span>

## <a name="overview"></a><span data-ttu-id="f9a9c-103">概述</span><span class="sxs-lookup"><span data-stu-id="f9a9c-103">Overview</span></span>

<span data-ttu-id="f9a9c-104">为了在请求模式下使用 DSC 时提供更加灵活和精简的体验，我们在此版本中添加了大量功能。</span><span class="sxs-lookup"><span data-stu-id="f9a9c-104">In order to provide a more flexible and streamlined experience when using DSC in Pull mode, we have added a number of features in this release.</span></span> <span data-ttu-id="f9a9c-105">这些功能旨在使你能够灵活地跨多个节点轻松设置和部署配置，同时对于每个节点仍单独跟踪状态和报告信息。</span><span class="sxs-lookup"><span data-stu-id="f9a9c-105">These features are intended to allow you to have the flexibility to easily setup and deploy configurations across multiple nodes, while still tracking status and reporting information for each node individually.</span></span>
<span data-ttu-id="f9a9c-106">这些功能如下：</span><span class="sxs-lookup"><span data-stu-id="f9a9c-106">These features are as follows:</span></span>

* <span data-ttu-id="f9a9c-107">标识计算机配置的配置名称。</span><span class="sxs-lookup"><span data-stu-id="f9a9c-107">A configuration name which identifies the configuration for a computer.</span></span> <span data-ttu-id="f9a9c-108">此名称可由多个目标节点共享</span><span class="sxs-lookup"><span data-stu-id="f9a9c-108">This name can be shared by multiple target nodes</span></span>
* <span data-ttu-id="f9a9c-109">唯一标识单个节点的代理 ID</span><span class="sxs-lookup"><span data-stu-id="f9a9c-109">An agent ID which uniquely identifies a single node</span></span>
* <span data-ttu-id="f9a9c-110">仅在目标节点第一次连接到请求服务器时出现的注册步骤</span><span class="sxs-lookup"><span data-stu-id="f9a9c-110">A registration step which only occurs the first time a target node connects to a pull server</span></span>

<span data-ttu-id="f9a9c-111">**注意：**这些特色和功能是添加进来的，它们不取代现有的请求功能和概念。</span><span class="sxs-lookup"><span data-stu-id="f9a9c-111">**Note:** These features and functionality have been added and do not replace the existing pull features and concepts.</span></span> <span data-ttu-id="f9a9c-112">你可以将这些新功能或将较旧的功能用于此版本中发布的新请求服务器。</span><span class="sxs-lookup"><span data-stu-id="f9a9c-112">You can use these new features or the older ones with the new pull server shipping in this release.</span></span>

<span data-ttu-id="f9a9c-113">有关详细信息，请参阅[使用配置名称设置请求客户端](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span><span class="sxs-lookup"><span data-stu-id="f9a9c-113">For more information, see [Setting up a pull client using configuration names](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span></span>