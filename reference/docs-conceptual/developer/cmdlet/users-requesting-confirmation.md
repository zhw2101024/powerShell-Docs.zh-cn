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
ms.openlocfilehash: ed9ff9fc1668a89e1ac0ceac8f0800a15b349226
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369246"
---
# <a name="users-requesting-confirmation"></a>请求确认的用户

当你为 Cmdlet 特性声明的 `SupportsShouldProcess` 参数指定值 `true` 时，用户可以在命令提示符处指定 `Confirm` 参数。

在默认环境中，用户可以指定 `Confirm` 参数或 `"-Confirm:$true`，以便在调用[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法时请求确认。 这会绕过[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)确认请求，即使对于影响很大的操作也是如此。

如果未指定 `Confirm`，则在 `$ConfirmPreference` 首选项变量等于或大于 Cmdlet 或提供程序的 @no__t 设置时， [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用请求确认。 @No__t 的默认设置为 "高"。 因此，在默认环境中，只有指定了影响很大的操作请求确认的 cmdlet 和提供程序。

如果 @no__t 为 false 或指定了 `"-Confirm:$false`，则[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用请求从用户处确认，并忽略 `$ConfirmPreference` shell 变量的值。

## <a name="remarks"></a>备注

- 对于指定 `SupportsShouldProcess` 但不 `ConfirmImpact` 的 cmdlet 和提供程序，这些操作将作为 "中等影响" 操作处理，并且默认情况下不会提示。 其影响级别小于 `$ConfirmPreference` 首选项变量的默认设置。

- 如果用户指定 `Verbose` 参数，则即使不提示进行确认，他们也会收到有关该操作的通知。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
