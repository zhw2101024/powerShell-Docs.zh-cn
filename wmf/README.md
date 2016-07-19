---
title: Windows Management Framework (WMF)
ms.date: 2016-05-16
keywords: PowerShell, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: b32cb86b7a18fee929cc81360d81f479571a74c2
ms.openlocfilehash: a7ef0ddf4d093a89f32f3484dfbef78fb159f0c2

---

# Windows Management Framework

Windows Management Framework (WMF) 是跨各种风格的 Windows 和 Windows Server 提供一致的管理接口的传递机制。
使用 WMF 安装时，客户可无缝地在其环境中的各种操作系统之间进行交互操作。
WMF 在给定版本的 Windows 和 Windows Server 中对管理功能进行了更新，这些更新可以安装在较低版本（通常是 2 个较低版本）的 Windows 和 Windows Server 上。

WMF 安装添加和/或更新了以下功能：

- Windows PowerShell
- Windows PowerShell Desired State Configuration (DSC)
- Windows PowerShell 集成脚本环境 (ISE)
- Windows 远程管理 (WinRM)
- Windows 管理规范 (WMI)
- Windows PowerShell Web 服务（Management OData IIS 扩展）
- 软件清单日志记录 (SIL)
- 服务器管理器 CIM 提供程序

## WMF 发行说明
若要了解给定 WMF 的 PowerShell 和其他组件中的各种增强功能，请参阅以下链接以查看发行说明：


- [WMF 5.1（预览版）](5.1/release-notes.md)
- [WMF 5.0](5.0/releasenotes.md)


## 各个 Windows 操作系统间的 WMF 可用性

>TODO：在列标题上添加指向特定 WMF DLC 的链接

| 操作系统版本 | [WMF 5.1 预览版*]() | [WMF 5.0]() | [WMF 4.0]() |  [WMF 3.0]() | [WMF (2.0)]() |
| ------------------------ | ----------- | ----------- | ----------- | ------------ |  ------------- |
| Windows Server 2016 | 内置提供* | 内置提供* |  |  |  |
| Windows 10 | 内置提供* | 内置提供*  | | | |  
| Windows Server 2012 R2| ?? | 是 | 内置提供 |  |  |
| Windows 8.1 | ?? | 是 |  内置提供 |  |  |
| Windows Server 2012 | ?? | 是 | 是 |  内置提供 | |
| Windows 8 |  |  |  | 内置提供 | |
| Windows Server 2008 R2 SP1 | ?? | 是 | 是 |  是| 内置提供 |
| Windows 7 SP1  | ?? | 是 | 是 | 是 | 内置提供 |
| Windows Server 2008 SP2 | | | | 是 | 是 |
| Windows Vista | | | | | 是 |
| Windows Server 2003| | | |  | 是 |
| Windows XP | | | |  | 是 |

>TODO：解释上表中的 *



<!--HONumber=Jul16_HO1-->


