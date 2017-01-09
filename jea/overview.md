---
description: 
manager: dongill
ms.topic: article
author: rpsqrd
ms.author: ryanpu
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-12-05
title: "自述文件"
ms.technology: powershell
ms.openlocfilehash: f9609f6eb7547c627bc23687c7eb242dd2f5f457
ms.sourcegitcommit: f75fc25411ce6a768596d3438e385c43c4f0bf71
translationtype: HT
---
# <a name="just-enough-administration"></a>Just Enough Administration

Just Enough Administration (JEA) 是一项安全技术，委派的管理员可通过它执行可通过 PowerShell 处理的任意操作。
使用 JEA，你可以：

- 通过利用代表普通用户执行特权操作的虚拟帐户，**减少你计算机上的管理员数量**。
- 通过指定用户可运行的 cmdlet、函数和外部命令，**限制用户可执行的操作**。
- 使用准确显示用户在会话中所执行命令的脚本和日志，**更好地了解你的用户进行的操作**。

**为什么这很重要？**

用于管理服务器的高特权帐户会造成严重的安全风险。
如果攻击者破坏这些帐户其中之一，他们可在组织中启动[横向攻击](http://aka.ms/pth)。
他们每攻击一个帐户甚至就会为它们提供访问更多帐户和资源的权限，使他们离窃取公司资源、启动拒绝服务攻击等就会更近一步。

而且，删除管理特权也并不容易。
考虑以下常见场景，即在与 Active Directory 域控制器相同的计算机上安装了 DNS 角色。
你的 DNS 管理员需要拥有本地管理员特权才能解决有关 DNS 服务器的问题，但是为了实现这一点，必须使其成为拥有高度特权的“域管理员”组的成员。
该方法将有效地给予 DNS 管理员对整个域的控制全以及对该计算机上所有资源的访问权。

JEA 可通过采用最小特权原则来帮助解决此问题。
通过 JEA，你可以为 DNS 管理员配置终结点，使其能够并且仅能够访问完成工作所需的所有 PowerShell 命令。
这意味着你可以提供适当的访问权限以修复中毒的 DNS 缓存或重启 DNS 服务器，而无需无意间授予他们对 Active Directory 的权限，或授予他们浏览文件系统、运行具有潜在危险的脚本的权限。
更棒的是，将 JEA 会话配置为使用具有临时特权的虚拟帐户时，你的 DNS 管理员可以使用非管理员凭据连接到服务器并仍可运行通常需要管理员权限的命令。
此功能使你能够从具有广泛权限的本地/域管理员角色删除用户，而不是谨慎控制他们能够在每台计算机上执行的操作。

## <a name="get-started-with-jea"></a>JEA 入门

可以立即在运行 Windows Server 2016 或 Windows 10 的任何计算机上开始使用 JEA。
还可以使用 Windows Management Framework 更新在较早的操作系统上运行 JEA。
若要深入了解使用 JEA 的要求，并了解如何创建、使用和审核 JEA 终结点，请参阅以下主题：

- [先决条件](prerequisites.md) - 说明如何设置你的环境以使用 JEA。
- [角色功能](role-capabilities.md) - 说明如何创建决定用户在 JEA 会话中允许执行的操作的角色。
- [会话配置](session-configurations.md) - 说明如何配置将用户映射到角色的 JEA 终结点并设置 JEA 标识
- [注册 JEA](register-jea.md) - 创建 JEA 终结点并使其可供用户连接。
- [使用 JEA](using-jea.md) - 了解可以使用 JEA 的各种方法。
- [安全注意事项](security-considerations.md) - 了解最佳安全方案和 JEA 配置选项的含义。
- [JEA 审核和报告](audit-and-report.md) - 了解如何审核和报告 JEA 终结点。