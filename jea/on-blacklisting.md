---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "关于列入黑名单"
ms.technology: powershell
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 8892e5e08a763fbc66d782bbc9252d1f3a7dcfcf

---

### 关于列入黑名单
在体验了一番 JEA 后，你可能会想知道是否可以将命令列入黑名单。
这一请求可以理解，但由于以下原因，目前未计划为 JEA 提供此功能：

1.  我们对 JEA 的设计是，将操作员限制为仅能执行其所需执行的操作。
黑名单则相反。

2.  PowerShell 命令的作者在设计 PowerShell 时未考虑 JEA。
在全新安装的 Windows Server 2016 上，有大约 1520 条命令立即可用。
这些命令的威胁模型未包括这种可能性，即用户将以更高权限的帐户身份运行命令。
例如，某些命令允许通过设计注入代码（例如核心 PowerShell 模块中的 Add-Type 和 Invoke-Command）。
JEA 在你公开已知特定命令时可发出警告，但是我们尚未根据新的威胁模型重新评估 Windows 中的每条命令。
请务必了解你通过 JEA 公开的命令的功能。  

3.  此外，即使 JEA 阻止了具有代码注入漏洞的所有命令，也不能保证恶意用户不能使用其他相关命令执行已列入黑名单的操作。
如果你不了解你公开的所有命令，你将无法保证某些操作是不可能的。
你肩负了解你所公开的命令的重任，无论这些命令使用白名单还是黑名单。
无法管理黑名单将公开的命令数量，因此改用白名单实现 JEA。




<!--HONumber=Jun16_HO4-->


