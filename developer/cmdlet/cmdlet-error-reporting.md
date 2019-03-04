---
title: Cmdlet 的错误报告 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error records [PowerShell], terminating
- non-terminating errors [PowerShell]
- error records [PowerShell]
- terminating errors [PowerShell]
- error records [PowerShell], non-terminating
ms.assetid: 0b014035-52ea-44cb-ab38-bbe463c5465a
caps.latest.revision: 8
ms.openlocfilehash: 7b54fc220a66a47c25b3e8cba644882d31713cb7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857683"
---
# <a name="cmdlet-error-reporting"></a>Cmdlet 错误报告

Cmdlet 应报告以不同的方式根据错误是否终止错误的错误或非终止错误。 终止错误会导致立即终止，将管道的错误或无需继续进行处理时，可能发生的错误。 非终止错误，报告当前的错误条件，这些错误，但该 cmdlet 可以继续处理输入的对象。 与非终止错误的问题，通常会通知用户，但该 cmdlet 将继续处理下一步的输入的对象。

## <a name="terminating-and-nonterminating-errors"></a>终止性和非终止错误

可以使用以下准则，以确定错误条件是否终止错误或非终止错误。

- 错误条件是否已成功处理任何进一步输入的对象阻止 cmdlet？ 如果是这样，这是一个终止错误。

- 与特定的输入的对象或输入对象的一个子集相关的错误条件？ 如果是这样，这是一个非终止错误。

- 该 cmdlet 是否接受多个输入的对象，此类处理可能会在另一个输入对象上成功？ 如果是这样，这是一个非终止错误。

- 即使在特定情况下适用于单个输入对象时，可以接受多个输入的对象的 Cmdlet 应确定什么终止和非终止错误之间。

- Cmdlet 可以接收任意数量的输入对象，并引发了终止异常之前发送任意数量的成功或错误的对象。 收到的输入对象的数量和发送的 success 和 error 对象数之间没有关系。

- Cmdlet 可接受 0 到 1 输入对象，并生成 0 到 1 的输出对象应将错误视为终止错误并生成终止的异常。

## <a name="reporting-nonterminating-errors"></a>报告非终止错误

非终止错误的报告应始终进行中的 cmdlet 的实现[System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法， [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，或[System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。 这些类型的错误报告通过调用[System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)反过来将错误记录发送到错误流的方法。

## <a name="reporting-terminating-errors"></a>报告的终止错误

通过引发异常或通过调用报告的终止错误[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)方法。 请注意，cmdlet 还可以捕获并重新引发如 OutOfMemory 异常，但是，它们不需要重新引发异常，如 Windows PowerShell 运行时将同时捕获它们。

此外可以定义自己的特定问题的异常情况，或将其他信息添加到现有异常使用其错误记录。

## <a name="error-records"></a>错误记录

Windows PowerShell 描述使用非终止错误条件[System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord)对象。 每个[System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord)对象提供错误类别信息、 可选目标对象，以及有关错误条件的详细信息。

### <a name="error-identifiers"></a>错误标识符

错误标识符是一个简单字符串，标识 cmdlet 中的错误情况。 Windows PowerShell 将合并此标识符与创建时，可以使用更高版本筛选错误流或日志记录错误，具体的错误，在响应时的完全限定的错误标识符的 cmdlet 标识符或其他特定于用户的活动。

指定错误标识符时，应遵循以下准则。

- 不同且非常具体的错误标识符分配到不同的代码路径。 调用每个代码路径[System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)或[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)应具有其自己的错误标识符。

- 错误标识符应是唯一的 CLR 异常类型的终止性和非终止错误。

- 不要更改 cmdlet 或 Windows PowerShell 提供程序的不同版本之间的错误标识符的语义。 错误标识符的语义建立后，它应保留常量整个生命周期的 cmdlet。

- 对于终止错误，为特定的 CLR 异常类型使用唯一的错误标识符。 如果异常类型发生更改，使用新的错误标识符。

- 对于非终止错误，使用一个特定的输入对象特定的错误标识符。

- 选择文本 tersely 与所报告的错误相对应的标识符。 不要使用空格或标点。

- 不会生成不是可重现的错误标识符。 例如，不生成标识符，其中包括进程标识符。 仅当它们对应于遇到相同问题的其他用户看到的标识符时，错误标识符是非常有用。

### <a name="error-categories"></a>错误类别

错误类别用于为最终用户的错误进行分组。 Windows PowerShell 定义了这些类别和 cmdlet 和 Windows PowerShell 提供程序必须选择时生成的错误记录在它们之间。

可将错误类别的说明，请参阅[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)枚举。 一般情况下，应避免使用 NoError、 UndefinedError 和 GenericError 只要有可能。

用户可以查看基于类别，这些设置时的错误"`$ErrorView`"到"CategoryView"。

## <a name="see-also"></a>另请参阅

[Windows PowerShell Cmdlets](./cmdlet-overview.md)

[Cmdlet Output](./types-of-cmdlet-output.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
