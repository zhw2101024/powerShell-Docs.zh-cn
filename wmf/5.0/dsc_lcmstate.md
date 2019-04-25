---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 57152e9f62c34600df63a2db8e9683928e825d93
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085790"
---
# <a name="detailed-information-about-lcm-state"></a>关于 LCM 状态的详细信息

我们在公开有关 LCM 状态的详细信息方面进行了改进。 Get-DscLocalConfigurationManager 返回的 LCMState 现在可以包含以下值：

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

我们还添加了 LCMStateDetail 属性，它包含有关状态的详细信息。
