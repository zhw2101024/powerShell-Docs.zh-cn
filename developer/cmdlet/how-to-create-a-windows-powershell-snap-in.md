---
title: 如何创建一个 Windows PowerShell 管理单元 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], examples
ms.assetid: 71bd9b2c-5f2e-4aa8-b5fe-08c956540d37
caps.latest.revision: 10
ms.openlocfilehash: 73834cea1d90943cf954728d6295d8eb33e14f57
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859753"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a>如何创建 Windows PowerShell 管理单元

Windows PowerShell 管理单元提供了一种机制，用于注册的 shell，从而将扩展的 shell 功能的 cmdlet 和另一个 Windows PowerShell 提供程序集。 Windows PowerShell 管理单元可以所有 cmdlet 和提供程序中都注册一个程序集，或者它可以都注册一个特定的 cmdlet 和提供程序列表。

管理单元中的程序集应安装在受保护的目录，就像使用其他操作系统。 否则，恶意用户可以使用不安全代码替换程序集。

## <a name="windows-powershell-snap-in-classes"></a>Windows PowerShell 管理单元类

所有 Windows PowerShell 管理单元类都派生自[System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn)或[System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn)类。

## <a name="examples"></a>示例

[编写一个 Windows PowerShell 管理单元](./writing-a-windows-powershell-snap-in.md):此示例演示如何，若要创建用于注册的程序集中的所有 cmdlet 和提供程序的管理单元。

[编写自定义 Windows PowerShell 管理单元中](./writing-a-custom-windows-powershell-snap-in.md):此示例演示如何创建自定义管理单元，用于在单个程序集注册一组特定的 cmdlet 和提供程序可能会或可能不存在。

## <a name="see-also"></a>另请参阅

[System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn)

[System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[注册 Cmdlet](./registering-cmdlets.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
