---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,安装程序
ms.openlocfilehash: baa35e9acd24d6f6155acf617a0d2c2210742af7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="4fe08-102">关于 LCM 状态的详细信息</span><span class="sxs-lookup"><span data-stu-id="4fe08-102">Detailed information about LCM state</span></span>

<span data-ttu-id="4fe08-103">我们在公开有关 LCM 状态的详细信息方面进行了改进。</span><span class="sxs-lookup"><span data-stu-id="4fe08-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="4fe08-104">Get-DscLocalConfigurationManager 返回的 LCMState 现在可以包含以下值：</span><span class="sxs-lookup"><span data-stu-id="4fe08-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="4fe08-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="4fe08-105">**Idle**</span></span>
* <span data-ttu-id="4fe08-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="4fe08-106">**Busy**</span></span>
* <span data-ttu-id="4fe08-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="4fe08-107">**PendingReboot**</span></span>
* <span data-ttu-id="4fe08-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="4fe08-108">**PendingConfiguration**</span></span>

<span data-ttu-id="4fe08-109">我们还添加了 LCMStateDetail 属性，它包含有关状态的详细信息。</span><span class="sxs-lookup"><span data-stu-id="4fe08-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>