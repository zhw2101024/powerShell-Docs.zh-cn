---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "角色功能的常见问题"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 0e221c840f083ce0b8ecbcbb34c184bcdbc0c73e

---

### 角色功能的常见问题
你自己完成此过程时，可能遇到一些常见问题。
以下是一个快速指南，阐释了修改或创建新的终结点时如何确定并修正这些问题：

#### 函数与Cmdlet
在 PowerShell 中编写的 PowerShell 命令即 PowerShell 函数。
作为为专用 .NET 类编写的 PowerShell 命令即 PowerShell Cmdlet。
你可以通过运行 `Get-Command` 来检查命令类型。

#### VisibleProviders
你将需要公开命令需要的任意提供程序。
最常见的是 FileSystem 提供程序，但你可能还需要公开其他提供程序，如 Registry 提供程序。
有关提供程序的简介，请参阅这篇 [Hey, Scripting Guy](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx)（你好，脚本专家）博客文章。
请谨慎公开提供程序 -- 通常，最好定义适用于基础提供程序的函数，而不是在 JEA 会话中直接公开提供程序。
这样一来，你仍可允许用户使用文件、注册表项等，但保留了对其可使用自定义验证逻辑处理**哪些**文件和注册表项的控制权。




<!--HONumber=Jul16_HO1-->


