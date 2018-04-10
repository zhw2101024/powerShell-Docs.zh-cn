---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 136e16ae74e54f3bc9d0623178257df1e9104aac
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="deliver-a-configuration-document-without-applying"></a><span data-ttu-id="7252f-102">传递配置文档而不应用</span><span class="sxs-lookup"><span data-stu-id="7252f-102">Deliver a configuration document without applying</span></span>

<span data-ttu-id="7252f-103">[Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet 将配置 MOF 文件复制到目标节点上，但不应用该配置。</span><span class="sxs-lookup"><span data-stu-id="7252f-103">The [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet copies a configuration MOF file to a target node, but does not apply the configuration.</span></span>
<span data-ttu-id="7252f-104">将在下次一致性通过时或运行 [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet 时应用此配置。</span><span class="sxs-lookup"><span data-stu-id="7252f-104">This configuration is applied during the next consistency pass, or when you run the [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet.</span></span>