---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,安装程序"
ms.openlocfilehash: 4fc146f84588d368ac3eb819e3acb4cb8c5d8793
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="9bbac-102">关于 LCM 状态的详细信息</span><span class="sxs-lookup"><span data-stu-id="9bbac-102">Detailed information about LCM state</span></span>

<span data-ttu-id="9bbac-103">我们在公开有关 LCM 状态的详细信息方面进行了改进。</span><span class="sxs-lookup"><span data-stu-id="9bbac-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="9bbac-104">Get-DscLocalConfigurationManager 返回的 LCMState 现在可以包含以下值：</span><span class="sxs-lookup"><span data-stu-id="9bbac-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="9bbac-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="9bbac-105">**Idle**</span></span>
* <span data-ttu-id="9bbac-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="9bbac-106">**Busy**</span></span>
* <span data-ttu-id="9bbac-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="9bbac-107">**PendingReboot**</span></span>
* <span data-ttu-id="9bbac-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="9bbac-108">**PendingConfiguration**</span></span>

<span data-ttu-id="9bbac-109">我们还添加了 LCMStateDetail 属性，它包含有关状态的详细信息。</span><span class="sxs-lookup"><span data-stu-id="9bbac-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>

