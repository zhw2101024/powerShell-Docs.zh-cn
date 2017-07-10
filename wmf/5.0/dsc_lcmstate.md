---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,安装程序"
ms.openlocfilehash: 4fc146f84588d368ac3eb819e3acb4cb8c5d8793
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
<a id="detailed-information-about-lcm-state" class="xliff"></a>
# 关于 LCM 状态的详细信息

我们在公开有关 LCM 状态的详细信息方面进行了改进。 Get-DscLocalConfigurationManager 返回的 LCMState 现在可以包含以下值：

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

我们还添加了 LCMStateDetail 属性，它包含有关状态的详细信息。

