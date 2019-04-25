---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 57152e9f62c34600df63a2db8e9683928e825d93
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085790"
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="a4219-102">关于 LCM 状态的详细信息</span><span class="sxs-lookup"><span data-stu-id="a4219-102">Detailed information about LCM state</span></span>

<span data-ttu-id="a4219-103">我们在公开有关 LCM 状态的详细信息方面进行了改进。</span><span class="sxs-lookup"><span data-stu-id="a4219-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="a4219-104">Get-DscLocalConfigurationManager 返回的 LCMState 现在可以包含以下值：</span><span class="sxs-lookup"><span data-stu-id="a4219-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="a4219-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="a4219-105">**Idle**</span></span>
* <span data-ttu-id="a4219-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="a4219-106">**Busy**</span></span>
* <span data-ttu-id="a4219-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="a4219-107">**PendingReboot**</span></span>
* <span data-ttu-id="a4219-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="a4219-108">**PendingConfiguration**</span></span>

<span data-ttu-id="a4219-109">我们还添加了 LCMStateDetail 属性，它包含有关状态的详细信息。</span><span class="sxs-lookup"><span data-stu-id="a4219-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>
