---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "jea 报告"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: d867a6462e9fa8b6e16c8c2103899c72b380116c

---

# JEA 报告
因为 JEA 允许非特权用户在特权上下文中运行，所以日志记录和审核尤为重要。
在本节中，我们将逐一运行可用于帮助进行行日志记录和报告的工具。

## 报告 JEA 操作
### 即时权限提升脚本
获取在 PowerShell 会话中所发生情况的摘要最快捷的方法之一，是通过即时权限提升查看进行键入的用户。
查看其命令、这些命令的输出是否一切正常。
或者并非一切正常，但至少你了解情况。
PowerShell 脚本旨在出现问题后，给予你类似的视图。

在会话配置中使用“TranscriptDirectory”字段时，PowerShell 将自动记录给定会话中执行的所有操作的脚本。
可在以下位置找到你执行本文档中的会话所生成的脚本：“$env:ProgramData\JEAConfiguration\Transcripts”

显而易见，该脚本记录了有关“已连接的”用户、“运行方式”用户、会话中运行的命令等的信息。
有关 PowerShell 脚本的详细信息，请参阅这篇[博客文章](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx)。

### PowerShell 事件日志
在模块日志记录处于打开状态时，所有的 PowerShell 操作也会记录在常规的 Windows 事件日志中。
与脚本相比，处理这种日志稍显复杂，但是它提供的详细信息级别可能有用。

在“PowerShell”运行日志中，如果你启用了模块日志记录，事件 ID 4104 将记录调用的每个命令。

### 其他事件日志
与 PowerShell 日志和脚本不同，其他日志记录机制将不会捕获“已连接的用户”。
你需要在其他日志和 PowerShell 日志之间进行一些关联操作，以匹配所执行的操作。

在“Windows 远程管理”运行日志中，事件 ID 193 将记录连接用户的 SID 和名称，以及运行方式虚拟帐户的 SID，来帮助进行此关联。
你可能也注意到了运行方式虚拟帐户末尾包含连接用户的域和用户名。

## 报告 JEA 配置
### Get-PSSessionConfiguration
为了准确报告你的环境状态，了解在计算机上设置的 JEA 终结点数量很重要。
`Get-PSSessionConfiguration` 请务必了解此信息。

### Get-PSSessionCapability
通过 JEA 终结点手动报告任意给定用户的功能可能相当复杂。
你可能需要检查多个角色功能。
幸运的是，“Get-PSSessionCapability”cmdlet 可完成此操作。

若要进行验证，请从管理员 PowerShell 提示符运行以下命令：
```PowerShell
Get-PSSessionCapability -Username 'CONTOSO\OperatorUser' -ConfigurationName JEADemo
```




<!--HONumber=Jul16_HO1-->


