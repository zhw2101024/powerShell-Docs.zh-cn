---
ms.date: 06/12/2017
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery
title: 库的 ScriptAnazlyer 规则配置文件
ms.openlocfilehash: 54100f7a530cbc769e4a0e2dbff18dbc5de88fa6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="1dd46-103">库的 ScriptAnazlyer 规则配置文件</span><span class="sxs-lookup"><span data-stu-id="1dd46-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="1dd46-104">若要确保发布到 PowerShell 库中的项质量，可运行 [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) 规则确定提交的脚本中是否存在任何冲突。</span><span class="sxs-lookup"><span data-stu-id="1dd46-104">To ensure the quality of items published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="1dd46-105">可在 ScriptAnalyzer [GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1) 页面上找到正在运行的规则列表。</span><span class="sxs-lookup"><span data-stu-id="1dd46-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="1dd46-106">如存在任何有关所运行规则的问题，请联系 PowerShell 库管理员或打开问题进行 ScriptAnalzyer 分析。</span><span class="sxs-lookup"><span data-stu-id="1dd46-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalzyer.</span></span>

<span data-ttu-id="1dd46-107">在即将发布的新版中，ScriptAnalyzer 结果将显示在库中每个单独项的页面中。</span><span class="sxs-lookup"><span data-stu-id="1dd46-107">ScriptAnalyzer results will be displayed on each individual item page in Gallery in the coming release.</span></span> <span data-ttu-id="1dd46-108">建议项所有者检查项，确保发布项中不存在任何严重错误。</span><span class="sxs-lookup"><span data-stu-id="1dd46-108">We encourage item owners to check their items to make sure there are no severe errors in published items.</span></span>
