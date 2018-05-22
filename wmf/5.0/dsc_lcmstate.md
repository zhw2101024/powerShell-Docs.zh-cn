---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: db9b48c188b3bfe2e20c06875606a285922f55a6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="f817b-102">关于 LCM 状态的详细信息</span><span class="sxs-lookup"><span data-stu-id="f817b-102">Detailed information about LCM state</span></span>

<span data-ttu-id="f817b-103">我们在公开有关 LCM 状态的详细信息方面进行了改进。</span><span class="sxs-lookup"><span data-stu-id="f817b-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="f817b-104">Get-DscLocalConfigurationManager 返回的 LCMState 现在可以包含以下值：</span><span class="sxs-lookup"><span data-stu-id="f817b-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="f817b-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="f817b-105">**Idle**</span></span>
* <span data-ttu-id="f817b-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="f817b-106">**Busy**</span></span>
* <span data-ttu-id="f817b-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="f817b-107">**PendingReboot**</span></span>
* <span data-ttu-id="f817b-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="f817b-108">**PendingConfiguration**</span></span>

<span data-ttu-id="f817b-109">我们还添加了 LCMStateDetail 属性，它包含有关状态的详细信息。</span><span class="sxs-lookup"><span data-stu-id="f817b-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>
