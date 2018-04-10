---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: 库,powershell,cmdlet,psgallery
title: psgallery_scriptanalyzer_rule_profile
ms.openlocfilehash: ff575ab56f07312658d111bccd7793b64ac071ea
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="scriptanazlyer-rule-profile-for-gallery"></a>库的 ScriptAnazlyer 规则配置文件
若要确保发布到 PowerShell 库中的项质量，可运行 [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) 规则确定提交的脚本中是否存在任何冲突。

可在 ScriptAnalyzer [GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1) 页面上找到正在运行的规则列表。
如存在任何有关所运行规则的问题，请联系 PowerShell 库管理员或打开问题进行 ScriptAnalzyer 分析。

在即将发布的新版中，ScriptAnalyzer 结果将显示在库中每个单独项的页面中。 建议项所有者检查项，确保发布项中不存在任何严重错误。