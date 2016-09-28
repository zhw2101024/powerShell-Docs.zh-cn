---
title: "WMF 5.1 中的已知问题（预览版）"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: krishna
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 3dde62efa7ba595ed5160cc81b4e2b17a54e52a2
ms.openlocfilehash: d4c9e88ddd6cfaec611527d19d00cbd4db9f5d1d

---

#WMF 5.1 中的已知问题（预览版） #

> 注意：此信息是预发布版本，可能会进行更改。

##以管理员身份启动 PowerShell 快捷方式
在安装 WMF 时，如果尝试以管理员身份通过该快捷方式启动 PowerShell，可能会显示“未指定的错误”消息。
以非管理员身份重新打开快捷方式，快捷方式现在甚至可以管理员身份工作。

##Pester
在本版本中，在 Nano 服务器上使用 Pester 时应注意两个问题：

* 由于 FULL CLR 和 CORE CLR 之间的差异，针对 Pester 自身运行测试可能导致一些失败。 特别是，Validate 方法不可用于 XmlDocument 类型。 众所周知，尝试验证 NUnit 输出日志的架构的六个测试都将失败。 
* 一个代码覆盖率测试失败的原因是当前 Nano 服务器中不存在 *WindowsFeature* DSC 资源。 但是，这些故障通常是无害的，可以放心地忽略。

##操作验证 

* 由于帮助 URI 不起作用，针对 Microsoft.PowerShell.Operation.Validation 模块的 Update-Help 将失败



<!--HONumber=Sep16_HO4-->


