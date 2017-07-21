---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: "库,powershell,cmdlet,psgallery"
title: psgallery_scriptanalyzer_rule_profile
ms.openlocfilehash: b178f198c9643fb39a6499d7e957cfd0d848c52d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="scriptanazlyer-rule-profile-for-gallery"></a><span data-ttu-id="714a2-103">库的 ScriptAnazlyer 规则配置文件</span><span class="sxs-lookup"><span data-stu-id="714a2-103">ScriptAnazlyer Rule Profile for Gallery</span></span>
<span data-ttu-id="714a2-104">若要确保发布到 PowerShell 库中的项质量，可运行 [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) 规则确定提交的脚本中是否存在任何冲突。</span><span class="sxs-lookup"><span data-stu-id="714a2-104">To ensure the quality of items published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="714a2-105">可在 ScriptAnalyzer [GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1) 页面上找到正在运行的规则列表。</span><span class="sxs-lookup"><span data-stu-id="714a2-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="714a2-106">如存在任何有关所运行规则的问题，请联系 PowerShell 库管理员或打开问题进行 ScriptAnalzyer 分析。</span><span class="sxs-lookup"><span data-stu-id="714a2-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalzyer.</span></span>

<span data-ttu-id="714a2-107">在即将发布的新版中，ScriptAnalyzer 结果将显示在库中每个单独项的页面中。</span><span class="sxs-lookup"><span data-stu-id="714a2-107">ScriptAnalyzer results will be displayed on each individual item page in Gallery in the coming release.</span></span> <span data-ttu-id="714a2-108">建议项所有者检查项，确保发布项中不存在任何严重错误。</span><span class="sxs-lookup"><span data-stu-id="714a2-108">We encourage item owners to check their items to make sure there are no severe errors in published items.</span></span>

