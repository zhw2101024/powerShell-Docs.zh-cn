---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,安装程序
ms.openlocfilehash: e1faf71436c8ba0ae02a166ce06d03de9f66f094
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="3d93b-102">RefreshMode 和 ConfigurationMode 的频率无需为彼此的倍数</span><span class="sxs-lookup"><span data-stu-id="3d93b-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="3d93b-103">在以前版本的 DSC 中，LCM 将 `RefreshFrequencyMins` 和 `ConfigurationModeFrequencyMins` 作为彼此的倍数。</span><span class="sxs-lookup"><span data-stu-id="3d93b-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="3d93b-104">在 WMF 5.0 RTM 中，将独立处理这些属性。</span><span class="sxs-lookup"><span data-stu-id="3d93b-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span>

<span data-ttu-id="3d93b-105">有关详细信息，请参阅[配置本地配置管理器](https://msdn.microsoft.com/powershell/dsc/metaconfig)。</span><span class="sxs-lookup"><span data-stu-id="3d93b-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>