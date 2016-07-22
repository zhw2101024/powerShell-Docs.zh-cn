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
ms.sourcegitcommit: 57049ff138604b0e13c8fd949ae14da05cb03a4b
ms.openlocfilehash: 387ebc0467b9f154444292f391af0f4b77123639

---

#WMF 5.1 中的已知问题（预览版） #

> 注意：此信息是预发布版本，可能会进行更改。

##Pester 问题
在本版本中，在 Nano 服务器上使用 Pester 时应注意两个问题：

* 由于 FULL CLR 和 CORE CLR 之间的差异，针对 Pester 自身运行测试可能导致一些失败。 特别是，Validate 方法不可用于 XmlDocument 类型。 众所周知，尝试验证 nunit 输出日志的架构的六个测试都将失败。 
* 一个代码覆盖率测试失败的原因是当前 Nano 服务器中不存在 *WindowsFeature* DSC 资源。 但是，这些故障通常是无害的，可以放心地忽略。


<!--HONumber=Jul16_HO3-->


