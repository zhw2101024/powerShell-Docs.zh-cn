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
# <a name="separation-of-node-and-configuration-ids"></a>节点和配置 ID 的分离

## <a name="overview"></a>概述

为了在请求模式下使用 DSC 时提供更加灵活和精简的体验，我们在此版本中添加了大量功能。 这些功能旨在使你能够灵活地跨多个节点轻松设置和部署配置，同时对于每个节点仍单独跟踪状态和报告信息。
这些功能如下：

* 标识计算机配置的配置名称。 此名称可由多个目标节点共享
* 唯一标识单个节点的代理 ID
* 仅在目标节点第一次连接到请求服务器时出现的注册步骤

**注意：**这些特色和功能是添加进来的，它们不取代现有的请求功能和概念。 你可以将这些新功能或将较旧的功能用于此版本中发布的新请求服务器。

有关详细信息，请参阅[使用配置名称设置请求客户端](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)