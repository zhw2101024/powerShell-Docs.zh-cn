---
ms.date: 06/12/2017
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery
title: 删除包
ms.openlocfilehash: ca5e68fcad52e4c7561d2c2b3858228652f22e0b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084158"
---
# <a name="deleting-packages"></a>删除包

PowerShell 库不支持永久删除包，因为这会对依赖其仍可用的用户造成中断。

但是，PowerShell 库支持“取消列出”包的方式，可以在网站包管理页面完成此操作。
如果取消列出某个包，它将不会在搜索和任何包列表中显示（无论是在 PowerShell 库上，还是使用 PowerShellGet 命令）。
但是，仍可通过指定精确版本下载它（精确版本可允许自动脚本继续运行）。

如果遇到认为必须删除一个包的特殊情况，PowerShell 库团队可手动解决此问题。
例如，如果存在侵犯版权问题或潜在有害内容，这是删除项的正当理由。
在这种情况下，应通过 [PowerShell 库](http://www.PowerShellGallery.com)提交支持请求。
