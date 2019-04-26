---
title: 从 Cmdlet 请求确认 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ConfirmImpact [PowerShell Programmer's Guide], described
- ShouldContinue [PowerShell Programmer's Guide], described
- user feedback [PowerShell Programmer's Guide], requesting
- ShouldProcess [PowerShell Programmer's Guide], described
- ConfirmPreference [PowerShell Programmer's Guide], described
ms.assetid: 37d6e87f-57b7-40bd-b645-392cf0b6e88e
caps.latest.revision: 13
ms.openlocfilehash: 0c0517ef7fbd5ae6434773a2dfe276f3a8c35f39
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067478"
---
# <a name="requesting-confirmation-from-cmdlets"></a>请求 Cmdlet 确认

它们是以对 Windows PowerShell 环境外部的系统进行更改时，Cmdlet 应请求确认。 例如，如果 cmdlet 是要添加的用户帐户或停止的进程，该 cmdlet 应要求来自用户的确认之前它将继续进行。 与此相反，如果某个 cmdlet 来更改 Windows PowerShell 变量，该 cmdlet 不会不需要要求进行确认。

为了使确认请求，该 cmdlet 必须指示，它支持确认请求，并且它必须调用[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) （可选） 若要显示一条确认请求消息的方法。

## <a name="supporting-confirmation-requests"></a>支持的确认请求

若要支持确认请求，该 cmdlet 必须设置`SupportsShouldProcess`Cmdlet 将属性与参数`true`。 这使得`Confirm`和`WhatIf`所提供的 Windows PowerShell cmdlet 参数。 `Confirm`参数允许用户控制是否显示确认请求。 `WhatIf`参数允许用户以确定该 cmdlet 应显示一条消息，还是执行其操作。 手动添加`Confirm`和`WhatIf`给某个 cmdlet 的参数。

下面的示例演示了一个支持确认请求的 Cmdlet 属性声明。

```csharp
[Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
        SupportsShouldProcess = true)]
```

## <a name="calling-the-confirmation-request-methods"></a>调用确认请求方法

在 cmdlet 代码中，调用[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法之前执行更改系统的操作。 设计该 cmdlet，因此，如果在调用返回的值为`false`，无法执行的操作，并处理下一步操作。

## <a name="calling-the-shouldcontinue-method"></a>调用 ShouldContinue 方法

大多数 cmdlet 请求确认仅使用[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法。 但是，某些情况下可能需要额外的确认信息。 这些情况下，对补充[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用通过调用[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法。 这允许 cmdlet 或提供程序来更精细地控制的作用域**全是**响应确认提示。

如果某个 cmdlet 调用[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，该 cmdlet 还必须提供`Force`开关参数。 如果用户指定`Force`当用户调用该 cmdlet，该 cmdlet 仍应调用[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)，但它应绕过对调用[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)。

[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)调用从非交互式环境会提示用户不能将引发异常。 添加`Force`参数可确保在非交互式环境中调用时仍可以执行该命令。

下面的示例演示如何调用[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)并[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)。

```csharp
if (ShouldProcess (...) )
{
  if (Force || ShouldContinue(...))
  {
     // Add code that performs the operation.
  }
}
```

行为[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用可以在其中调用该 cmdlet 的环境而异。 使用上一准则将有助于确保该 cmdlet 行为一致地与其他 cmdlet，而不考虑主机环境。

有关调用的示例[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法，请参阅[如何请求确认](./how-to-request-confirmations.md)。

## <a name="specify-the-impact-level"></a>指定影响级别

在创建 cmdlet 时，指定更改的影响级别 （严重性）。 若要执行此操作，设置的值`ConfirmImpact`高、 中或低将 Cmdlet 属性的参数。 可以指定的值`ConfirmImpact`仅当还指定`SupportsShouldProcess`cmdlet 参数。

对于大多数 cmdlet，你不必显式指定`ConfirmImpact`。  相反，使用默认设置的参数，这为 Medium。 如果您设置`ConfirmImpact`为高，该操作将确认默认情况下。 保留此设置为高度破坏性操作，例如重新格式化硬盘卷。

## <a name="calling-non-confirmation-methods"></a>调用非确认方法

如果 cmdlet 或提供程序必须发送一条消息，但不是请求确认，它可以调用以下三种方法。 避免使用[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法来发送这些类型的消息，因为[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)混合输出cmdlet 或提供程序的正常输出，这就可将脚本写入困难。

- 若要提醒用户，并继续执行操作，cmdlet 或提供程序可以调用[System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法。

- 若要提供用户可以检索使用的其他信息`Verbose`参数，cmdlet 或提供程序可以调用[System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法。

- 若要对其他开发人员或获取产品支持提供调试级别的详细信息，该 cmdlet 或提供程序可以调用[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法。 用户可以检索此信息使用`Debug`参数。

Cmdlet 和提供程序首先调用以下方法来尝试执行操作的更改在 Windows PowerShell 之外的系统之前请求确认：

- [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)

- [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)

在此，通过调用[System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法，它会提示用户确认操作基于用户调用该命令的方式。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
