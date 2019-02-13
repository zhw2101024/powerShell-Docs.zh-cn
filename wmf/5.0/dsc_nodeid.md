---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 7a1725e3858c59a6d31699add22b042359c48463
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676854"
---
# <a name="separation-of-node-and-configuration-ids"></a><span data-ttu-id="3d052-102">节点和配置 ID 的分离</span><span class="sxs-lookup"><span data-stu-id="3d052-102">Separation of Node and Configuration IDs</span></span>

## <a name="overview"></a><span data-ttu-id="3d052-103">概述</span><span class="sxs-lookup"><span data-stu-id="3d052-103">Overview</span></span>

<span data-ttu-id="3d052-104">为了在请求模式下使用 DSC 时提供更加灵活和精简的体验，我们在此版本中添加了大量功能。</span><span class="sxs-lookup"><span data-stu-id="3d052-104">In order to provide a more flexible and streamlined experience when using DSC in Pull mode, we have added a number of features in this release.</span></span> <span data-ttu-id="3d052-105">这些功能旨在使你能够灵活地跨多个节点轻松设置和部署配置，同时对于每个节点仍单独跟踪状态和报告信息。</span><span class="sxs-lookup"><span data-stu-id="3d052-105">These features are intended to allow you to have the flexibility to easily setup and deploy configurations across multiple nodes, while still tracking status and reporting information for each node individually.</span></span>
<span data-ttu-id="3d052-106">这些功能如下：</span><span class="sxs-lookup"><span data-stu-id="3d052-106">These features are as follows:</span></span>

* <span data-ttu-id="3d052-107">标识计算机配置的配置名称。</span><span class="sxs-lookup"><span data-stu-id="3d052-107">A configuration name which identifies the configuration for a computer.</span></span> <span data-ttu-id="3d052-108">此名称可由多个目标节点共享</span><span class="sxs-lookup"><span data-stu-id="3d052-108">This name can be shared by multiple target nodes</span></span>
* <span data-ttu-id="3d052-109">唯一标识单个节点的代理 ID</span><span class="sxs-lookup"><span data-stu-id="3d052-109">An agent ID which uniquely identifies a single node</span></span>
* <span data-ttu-id="3d052-110">仅在目标节点第一次连接到请求服务器时出现的注册步骤</span><span class="sxs-lookup"><span data-stu-id="3d052-110">A registration step which only occurs the first time a target node connects to a pull server</span></span>

<span data-ttu-id="3d052-111">**注意：** 这些特色和功能是添加进来的，它们不取代现有的请求功能和概念。</span><span class="sxs-lookup"><span data-stu-id="3d052-111">**Note:** These features and functionality have been added and do not replace the existing pull features and concepts.</span></span> <span data-ttu-id="3d052-112">你可以将这些新功能或将较旧的功能用于此版本中发布的新请求服务器。</span><span class="sxs-lookup"><span data-stu-id="3d052-112">You can use these new features or the older ones with the new pull server shipping in this release.</span></span>

<span data-ttu-id="3d052-113">有关详细信息，请参阅[使用配置名称设置请求客户端](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span><span class="sxs-lookup"><span data-stu-id="3d052-113">For more information, see [Setting up a pull client using configuration names](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span></span>
