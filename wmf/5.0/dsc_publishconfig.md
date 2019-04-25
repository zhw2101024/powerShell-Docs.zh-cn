---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: db4543b788ad0a5c7aa32706246446533b901d09
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085807"
---
# <a name="deliver-a-configuration-document-without-applying"></a><span data-ttu-id="3b10d-102">传递配置文档而不应用</span><span class="sxs-lookup"><span data-stu-id="3b10d-102">Deliver a configuration document without applying</span></span>

<span data-ttu-id="3b10d-103">[Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet 将配置 MOF 文件复制到目标节点上，但不应用该配置。</span><span class="sxs-lookup"><span data-stu-id="3b10d-103">The [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet copies a configuration MOF file to a target node, but does not apply the configuration.</span></span>
<span data-ttu-id="3b10d-104">将在下次一致性通过时或运行 [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet 时应用此配置。</span><span class="sxs-lookup"><span data-stu-id="3b10d-104">This configuration is applied during the next consistency pass, or when you run the [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet.</span></span>
