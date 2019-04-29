---
title: 错误报告概念 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.assetid: 0dce97c0-bd9a-4691-8ca3-e8d5dea902c5
caps.latest.revision: 11
ms.openlocfilehash: 2f185e415e3effc2cf09a282ca1167e3bcfb7d6a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068175"
---
# <a name="error-reporting-concepts"></a>错误报告概念

Windows PowerShell 提供了两种机制用于报告错误： 一种机制*终止错误*和另一种可*非终止性错误*。 务必为你的 cmdlet 报告错误正确，以便运行 cmdlet 的主机应用程序可以以适当的方式作出反应。

你的 cmdlet 应调用[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)方法在出错时却没有或不应允许该 cmdlet 可以继续处理其输入的对象。 你的 cmdlet 应调用[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法来报告非终止性错误，该 cmdlet 可以继续处理输入的对象时。 这两种方法提供主机应用程序可用于调查该错误的原因的错误记录。

使用以下准则来确定错误是否终止或非终止错误。

- 如果从继续处理当前对象或已成功处理任何进一步输入的对象，而不考虑其内容，它使你的 cmdlet，错误将是一个终止错误。

- 如果您不希望你的 cmdlet 以继续处理当前对象或任何进一步输入的对象，而不考虑其内容，错误将是一个终止错误。

- 错误是一个终止错误时不会接受或返回的对象的 cmdlet 或 cmdlet 接受或返回一个对象中发生。

- 如果你的 cmdlet 要继续处理当前对象和任何进一步输入的对象，错误将是一个非终止错误。

- 如果它与特定输入的对象或输入对象的子集，错误将是一个非终止错误。

## <a name="see-also"></a>另请参阅

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows PowerShell 错误记录](./windows-powershell-error-records.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
