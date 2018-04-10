---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 16255a0f369c3df5a2131c075fc9f7006b517a63
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="remove-dsc-documents"></a>删除 DSC 文档

将配置文档传送到 DSC 时，文档将经历各个阶段（挂起、当前、上一个）。 我们在 Windows PowerShell 4.0 中向 DSC 新增了一个 cmdlet，`Remove-DscConfigurationDocument`，作为 [2014 年 11 月 Windows RT 8.1、Windows 8.1 和 Windows Server 2012 R2 更新汇总](https://support.microsoft.com/kb/3000850)的一部分。