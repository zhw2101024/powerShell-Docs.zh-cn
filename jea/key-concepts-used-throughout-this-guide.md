---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "本指南中使用的主要概念"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 178fea44987b0c457b8e5d23fbe851ee12f03b31

---

# 本指南中使用的主要概念
**JEA 具体是什么？**

JEA 是 PowerShell [受约束的终结点](http://blogs.technet.com/b/heyscriptingguy/archive/2014/03/31/introduction-to-powershell-endpoints.aspx)的扩展，它添加了角色定义、虚拟帐户和多项其他改进，让你能够更轻松地锁定管理终结点。
JEA 终结点由一个 PowerShell 会话配置文件和一个或多个角色功能文件组成。

**会话配置文件和角色功能文件是什么？**

PowerShell 会话配置文件 (.pssc) 定义可连接到 PowerShell 终结点的*人员*及其配置*方式*。
在该文件中，你可以将用户和安全组映射到特定管理角色，并配置虚拟帐户和脚本策略等全局设置。
会话配置文件特定于每台计算机，让你能够根据需要按计算机控制访问权限。

PowerShell 角色功能文件 (.psrc) 定义属于某个角色的用户能够在系统上执行的*操作*。
在该文件中，你可以限制用户在其 JEA 会话中使用的 cmdlet、函数、提供程序和外部提供程序。
角色功能文件对于身为服务对象的角色（DNS 域、1 级技术支持人员、只读清单审核等）常是通用的，这些文件属于 PowerShell 模块，让你能够在你的环境中以及与他人进行共享。

**JEA 如何利用虚拟帐户？**

在 PowerShell 会话配置文件中，你可以将 JEA 会话配置为使用虚拟的“运行方式”帐户。
虚拟帐户是一次性特权帐户，在执行用户命令的上下文中，针对特定会话中的特定连接用户而生成。
默认情况下，虚拟帐户属于本地“管理员”安全组，但可以选择将其配置为仅属于你指定的安全组。

**PowerShell 远程处理**：通过 PowerShell 远程处理，你可以针对远程计算机运行 PowerShell 命令。
你可以针对一台或多台计算机进行操作，并可使用临时或永久连接。
在此演示中，你使用交互式会话远程到本地计算机。
JEA 通过 PowerShell 远程处理限制可用的功能。
有关 PowerShell 远程处理的详细信息，请运行 `Get-Help about_Remote`。

**“运行方式”用户**：使用 JEA 时，非管理员的“运行方式”有为特权的“虚拟帐户”。
虚拟帐户仅在远程会话期间存在。
也就是说，用户连接到终结点时创建此用户，用户结束会话时销毁它。
默认情况下，虚拟帐户是本地“管理员”组的成员。
在域控制器上，它是“域管理员”组的成员。
虚拟帐户对于在其上创建这些帐户的计算机来说是本地的，并且不拥有该计算机之外的权限。
这意味着它们没有在 Active Directory 中进行注册（未分配 RID）。
此外，如果允许的命令/脚本尝试访问本地计算机外部的资源，它将在计算机标识（而不是虚拟帐户标识）下访问这些资源。

**“已连接的”用户**：连接到 JEA 终结点并向其分配了角色的非管理员用户。
此用户运行的任何命令都在运行方式用户或虚拟帐户的上下文之下运行。




<!--HONumber=Jul16_HO1-->


