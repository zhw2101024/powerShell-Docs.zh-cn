---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: db9b48c188b3bfe2e20c06875606a285922f55a6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="detailed-information-about-lcm-state"></a>关于 LCM 状态的详细信息

我们在公开有关 LCM 状态的详细信息方面进行了改进。 Get-DscLocalConfigurationManager 返回的 LCMState 现在可以包含以下值：

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

我们还添加了 LCMStateDetail 属性，它包含有关状态的详细信息。
