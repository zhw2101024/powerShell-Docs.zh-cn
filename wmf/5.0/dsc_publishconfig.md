---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: f929ce4684bb53c3039238ecd465f1c0e432f741
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225668"
---
# <a name="deliver-a-configuration-document-without-applying"></a><span data-ttu-id="adc21-102">传递配置文档而不应用</span><span class="sxs-lookup"><span data-stu-id="adc21-102">Deliver a configuration document without applying</span></span>

<span data-ttu-id="adc21-103">[Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet 将配置 MOF 文件复制到目标节点上，但不应用该配置。</span><span class="sxs-lookup"><span data-stu-id="adc21-103">The [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet copies a configuration MOF file to a target node, but does not apply the configuration.</span></span>
<span data-ttu-id="adc21-104">将在下次一致性通过时或运行 [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet 时应用此配置。</span><span class="sxs-lookup"><span data-stu-id="adc21-104">This configuration is applied during the next consistency pass, or when you run the [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet.</span></span>
