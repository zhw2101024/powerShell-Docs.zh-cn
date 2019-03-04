---
title: 请求确认的用户 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: e4abbb14b31406b845d9b6af6b6372338fb0d926
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856233"
---
# <a name="users-requesting-confirmation"></a>请求确认的用户

指定的值时`true`有关`SupportsShouldProcess`Cmdlet 特性声明的参数，用户可以指定`Confirm`参数在命令提示符处。

在默认环境中，用户可以指定`Confirm`参数或`"-Confirm:$true`，以便请求确认时[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用方法。 这将绕过[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)确认请求，即使对于影响较大的操作。

如果`Confirm`未指定，则[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用请求确认，如果`$ConfirmPreference`首选项变量是等于或大于`ConfirmImpact`的设置cmdlet 或提供程序。 默认设置`$ConfirmPreference`是高。 因此，在默认环境中，唯一的 cmdlet 和提供程序用于指定影响较大的操作请求确认。

如果`Confirm`为 false 或者如果`"-Confirm:$false`指定，则[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用请求用户，确认和`$ConfirmPreference`shell 变量将被忽略。

## <a name="remarks"></a>备注

- 为 cmdlet 和指定的提供商`SupportsShouldProcess`，但不是`ConfirmImpact`，这些操作处理为"中等程度的影响"操作，它们将不会提示默认情况下。 其影响级别低于的默认设置`$ConfirmPreference`首选项变量。

- 如果用户指定`Verbose`参数，他们将会收到通知操作即使它们不会提示进行确认。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
