---
ms.date: 06/12/2017
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery
title: 删除项
ms.openlocfilehash: 454cd404437bf1c31b9a1b81cd9dd0ac81e6b0f6
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893087"
---
# <a name="deleting-items"></a>删除项

PowerShell 库不支持永久删除项，因为这会对依赖其仍可用的人造成中断。

但是，PowerShell 库支持“取消列出”项的方式，可以在网站项管理页面完成完成此操作。
如果取消列出某个项，它将不会在搜索和任何项列表中出现（无论是在 PowerShell 库上，还是使用 PowerShellGet 命令）。
但是，仍可通过指定精确版本下载它（精确版本可允许自动脚本继续运行）。

如果你遇到你认为必须删除一个项的特殊情况，PowerShell 库团队可手动解决此问题。
例如，如果存在侵犯版权问题或潜在有害内容，这是删除项的正当理由。
在这种情况下，应通过 [PowerShell 库](http://www.PowerShellGallery.com)提交支持请求。