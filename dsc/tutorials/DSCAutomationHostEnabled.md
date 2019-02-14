---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSCAutomationHostEnabled 注册表项
ms.openlocfilehash: 2bccd2738b9f61efd656fdf0f98cf71affdbe781
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676170"
---
>适用于：Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>DSCAutomationHostEnabled 注册表项

使用 DSC **DSCAutomationHostEnabled**注册表项下的**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System**若要启用在初始计算机的配置启动。
DSCAutomationHostEnabled 支持三种模式：

|  DSCAutomationHostEnabled 值  |  说明   |
|---|---|
0 | 禁用对启动状态计算机的配置。 |
1 | 启用对启动状态计算机的配置。 |
2 | 仅在 DSC 处于挂起或当前状态时，启用对计算机的配置。 这是默认值。 |

## <a name="see-also"></a>另请参阅

有关如何使用此功能在初始启动时运行配置的示例，请参阅[初始启动时使用 DSC 配置虚拟机](bootstrapDsc.md)。
