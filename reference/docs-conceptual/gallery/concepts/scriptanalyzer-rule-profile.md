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
# <a name="scriptanalyzer-rule-profile-for-gallery"></a>库的 ScriptAnazlyer 规则配置文件

若要确保发布到 PowerShell 库中包的质量，可运行 [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) 规则确定提交的脚本中是否存在任何冲突。

可在 ScriptAnalyzer [GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1) 页面上找到正在运行的规则列表。
如存在任何有关所运行规则的问题，请联系 PowerShell 库管理员或打开问题进行 ScriptAnalyzer 分析。

在即将推出的发布版中，ScriptAnalyzer 结果将显示在库中每个单独包的页面中。 建议包所有者检查包，确保发布包中不存在任何严重错误。
