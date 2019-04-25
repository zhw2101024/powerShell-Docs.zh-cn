---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 23a5c8832f7c2888880a1ee846d75feaa95ebe47
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058397"
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="3340e-102">RefreshMode 和 ConfigurationMode 的频率无需为彼此的倍数</span><span class="sxs-lookup"><span data-stu-id="3340e-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="3340e-103">在以前版本的 DSC 中，LCM 将 `RefreshFrequencyMins` 和 `ConfigurationModeFrequencyMins` 作为彼此的倍数。</span><span class="sxs-lookup"><span data-stu-id="3340e-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="3340e-104">在 WMF 5.0 RTM 中，将独立处理这些属性。</span><span class="sxs-lookup"><span data-stu-id="3340e-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span>

<span data-ttu-id="3340e-105">有关详细信息，请参阅[配置本地配置管理器](https://msdn.microsoft.com/powershell/dsc/metaconfig)。</span><span class="sxs-lookup"><span data-stu-id="3340e-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>
