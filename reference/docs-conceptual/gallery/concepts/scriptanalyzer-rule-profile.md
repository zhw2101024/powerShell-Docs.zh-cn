---
ms.date: 06/12/2017
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery
title: 库的 ScriptAnazlyer 规则配置文件
ms.openlocfilehash: 939f01dece56b283dbe6e03c888f42ff866707af
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328468"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="ee9d8-103">库的 ScriptAnazlyer 规则配置文件</span><span class="sxs-lookup"><span data-stu-id="ee9d8-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="ee9d8-104">若要确保发布到 PowerShell 库中包的质量，可运行 [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) 规则确定提交的脚本中是否存在任何冲突。</span><span class="sxs-lookup"><span data-stu-id="ee9d8-104">To ensure the quality of packages published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="ee9d8-105">可在 ScriptAnalyzer [GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1) 页面上找到正在运行的规则列表。</span><span class="sxs-lookup"><span data-stu-id="ee9d8-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="ee9d8-106">如存在任何有关所运行规则的问题，请联系 PowerShell 库管理员或打开问题进行 ScriptAnalyzer 分析。</span><span class="sxs-lookup"><span data-stu-id="ee9d8-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalyzer.</span></span>

<span data-ttu-id="ee9d8-107">在即将推出的发布版中，ScriptAnalyzer 结果将显示在库中每个单独包的页面中。</span><span class="sxs-lookup"><span data-stu-id="ee9d8-107">ScriptAnalyzer results will be displayed on each individual package page in Gallery in the coming release.</span></span> <span data-ttu-id="ee9d8-108">建议包所有者检查包，确保发布包中不存在任何严重错误。</span><span class="sxs-lookup"><span data-stu-id="ee9d8-108">We encourage package owners to check their packages to make sure there are no severe errors in published packages.</span></span>
