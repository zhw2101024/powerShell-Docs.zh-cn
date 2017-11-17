---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,安装程序"
ms.openlocfilehash: 30055cff87159df98029e25409782e0fe2f0bae4
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="45a76-102">RefreshMode 和 ConfigurationMode 的频率无需为彼此的倍数</span><span class="sxs-lookup"><span data-stu-id="45a76-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="45a76-103">在以前版本的 DSC 中，LCM 将 `RefreshFrequencyMins` 和 `ConfigurationModeFrequencyMins` 作为彼此的倍数。</span><span class="sxs-lookup"><span data-stu-id="45a76-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="45a76-104">在 WMF 5.0 RTM 中，将独立处理这些属性。</span><span class="sxs-lookup"><span data-stu-id="45a76-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span> 

<span data-ttu-id="45a76-105">有关详细信息，请参阅[配置本地配置管理器](https://msdn.microsoft.com/powershell/dsc/metaconfig)。</span><span class="sxs-lookup"><span data-stu-id="45a76-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>

