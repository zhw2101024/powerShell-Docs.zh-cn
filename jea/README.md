---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "自述文件"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: d4e46653ff31ea7cda71f1c92b12ce5f2811b8a7
ms.openlocfilehash: e24757029fd3ac9a70f710a7a755c35f440f087c

---

# Just Enough Administration
Just Enough Administration (JEA) 是一项安全技术，委派的管理员可通过它执行可通过 PowerShell 处理的任意操作。
使用 JEA，你可以：
- 通过利用代表普通用户执行特权操作的虚拟帐户，**减少你计算机上的管理员数量**。
- 通过指定用户可运行的 cmdlet、函数和外部命令，**限制用户可执行的操作**。
- 使用准确显示用户在会话中所执行命令的“即时权限提升”脚本，**更好地了解你的用户进行的操作**。

**为什么这很重要？**  
请考虑你的 DNS 服务器与 Active Directory 域控制器位于同一位置这样的常见场景。
你的 DNS 管理员需要拥有本地管理员特权才能解决有关 DNS 服务器的问题，但是为了实现这一点，必须使其成为拥有高度特权的“域管理员”组的成员。
该方法将有效地给予 DNS 管理员对整个域的控制全以及对该计算机上所有资源的访问权。

而有了 JEA，你就可以为 DNS 管理员配置角色，使其能够并且仅能够访问完成工作所需的所有命令。
这意味着你可以提供适当的访问权限以修复中毒的 DNS 缓存，而无需无意间授予他们对 Active Directory 的权限，或授予他们浏览文件系统、运行具有潜在危险的脚本的权限。
更棒的是，将 JEA 会话配置为使用具有一次性特权的虚拟帐户时，你的 DNS 管理员可以使用 *无特权* 凭据连接到服务器并仍可运行特权命令。

## 可用性
JEA 正与 Windows Server 2016 同步开发，并可通过 Windows Management Framework 更新在旧版 Windows 上使用。
当前版本的 JEA 在以下平台上可用：

**Windows Server**
- Windows Server 2016 Technical Preview 4 及更高版本
- \*安装了[ Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) 的 Windows Server 2012 R2、2012 和 2008 R2

**Windows 客户端**
- 安装了 11 月更新 (1511) 的 Windows 10
- \*安装了[ Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) 的 Windows 8.1、8 和 7

\* Windows Server 2008 R2 或 Windows 7 上目前不支持在 JEA 会话中使用虚拟帐户。


## 浏览体验指南
准备好了解如何创作、部署和使用你自己的 JEA 终结点了吗？

该指南允许你使用预构建的 JEA 终结点快速开始，让你大概了解最终用户体验；然后引导你从头重新创建终结点，以帮助解释诸如会话配置和角色功能的概念。

1.  [简介](introduction.md)   
简要了解为何应关心 JEA

2.  [必备条件](prerequisites.md)  
说明如何设置你的环境

3.  [使用 JEA](using-jea.md)  
帮助你从了解使用 JEA 的操作员体验开始

4.  [重新创建演示](remake-the-demo-endpoint.md)  
从头开始创建 JEA 会话配置

5.  [角色功能](role-capabilities.md)  
了解如何使用角色功能文件自定义 JEA 功能

6.  [端到端 - Active Directory](end-to-end---active-directory.md)  
创建用于管理 Active Directory 的全新的终结点

7.  [多计算机部署和维护](multi-machine-deployment-and-maintenance.md)  
了解部署和创作如何随缩放进行更改

8.  [JEA 报告](reporting-on-jea.md)  
了解如何审核和报告所有 JEA 操作和基础结构

9.  附录
  - [本指南中使用的主要概念](key-concepts-used-throughout-this-guide.md)  
  -  [创建域控制器](creating-a-domain-controller.md)  
  -  [关于列入黑名单](on-blacklisting.md)  
  -  [限制命令时的注意事项](considerations-when-limiting-commands.md)  
  -  [角色功能的常见问题](common-role-capability-pitfalls.md)

## 开始创作你自己的 JEA 终结点
创作 JEA 终结点很容易 -- 仅需启用了 JEA 的系统和文件编辑器（如 PowerShell ISE）。
对于开始使用很有帮助的一个提示是，使用不带任何其他参数的 `New-PSRoleCapabilityFile -Path <path>` 和 `New-PSSessionCapabilityFile -Path <Path>` 创建主干文件。
这些主干文件包含所有适用的配置字段，以及解释每个字段用途的有益注释。

若要更轻松地创作 JEA 终结点，请参阅 [JEA 工具包帮助程序](http://blogs.technet.com/b/privatecloud/archive/2015/12/20/introducing-the-updated-jea-helper-tool.aspx)，它提供可以用于创作会话配置文件和角色功能文件的 GUI。
它甚至支持生成基于 PowerShell 日志的角色功能，直接为你提供你的用户定期运行完成其工作的命令。




<!--HONumber=Jul16_HO1-->


