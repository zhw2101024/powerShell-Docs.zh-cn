---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: a3ac215396206fba62bce303733429d60722ee6b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="79e75-102">RefreshMode 和 ConfigurationMode 的频率无需为彼此的倍数</span><span class="sxs-lookup"><span data-stu-id="79e75-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="79e75-103">在以前版本的 DSC 中，LCM 将 `RefreshFrequencyMins` 和 `ConfigurationModeFrequencyMins` 作为彼此的倍数。</span><span class="sxs-lookup"><span data-stu-id="79e75-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="79e75-104">在 WMF 5.0 RTM 中，将独立处理这些属性。</span><span class="sxs-lookup"><span data-stu-id="79e75-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span>

<span data-ttu-id="79e75-105">有关详细信息，请参阅[配置本地配置管理器](https://msdn.microsoft.com/powershell/dsc/metaconfig)。</span><span class="sxs-lookup"><span data-stu-id="79e75-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>
