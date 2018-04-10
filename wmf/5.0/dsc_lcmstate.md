---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,安装程序
ms.openlocfilehash: baa35e9acd24d6f6155acf617a0d2c2210742af7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="detailed-information-about-lcm-state"></a>关于 LCM 状态的详细信息

我们在公开有关 LCM 状态的详细信息方面进行了改进。 Get-DscLocalConfigurationManager 返回的 LCMState 现在可以包含以下值：

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

我们还添加了 LCMStateDetail 属性，它包含有关状态的详细信息。