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
ms.sourcegitcommit: f413ba6470985622e55bb4bd175d7c5d4b94c7d9
ms.openlocfilehash: e545d49381a92ef3f7cc6a27316cbfc3a036a8c9

---

#WMF 5.1 中的已知问题（预览版） #

> 注意：此信息是预发布版本，可能会进行更改。

##Pester
在本版本中，在 Nano 服务器上使用 Pester 时应注意两个问题：

* 由于 FULL CLR 和 CORE CLR 之间的差异，针对 Pester 自身运行测试可能导致一些失败。 特别是，Validate 方法不可用于 XmlDocument 类型。 众所周知，尝试验证 NUnit 输出日志的架构的六个测试都将失败。 
* 一个代码覆盖率测试失败的原因是当前 Nano 服务器中不存在 *WindowsFeature* DSC 资源。 但是，这些故障通常是无害的，可以放心地忽略。

##操作验证 

* 由于帮助 URI 不起作用，针对 Microsoft.PowerShell.Operation.Validation 模块的 Update-Help 将失败



<!--HONumber=Sep16_HO3-->


