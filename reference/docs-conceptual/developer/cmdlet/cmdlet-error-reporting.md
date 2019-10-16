---
title: Cmdlet 错误报告 |Microsoft Docs
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
ms.openlocfilehash: 5dfec318438ca139518c596011ac5e56445738ea
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365916"
---
# <a name="cmdlet-error-reporting"></a>Cmdlet 错误报告

根据错误是终止错误还是非终止错误，cmdlet 应以不同的方式报告错误。 终止错误是导致管道立即终止的错误，或在没有理由继续处理时所发生的错误。 非终止错误是报告当前错误情况的错误，但该 cmdlet 可以继续处理输入对象。 对于非终止错误，用户通常会收到有关问题的通知，但 cmdlet 会继续处理下一个输入对象。

## <a name="terminating-and-nonterminating-errors"></a>终止和非终止错误

以下准则可用于确定错误条件是终止错误还是非终止错误。

- 错误情况是否会阻止 cmdlet 成功处理任何其他输入对象？ 如果是这样，则这是一个终止错误。

- 与特定输入对象或输入对象的子集相关的错误条件？ 如果是这样，则这是一个非终止错误。

- Cmdlet 是否接受多个输入对象，以便处理可以在另一个输入对象上成功进行？ 如果是这样，则这是一个非终止错误。

- 可以接受多个输入对象的 cmdlet 应在什么是终止和非终止错误之间做出决定，即使特定情况仅适用于单个输入对象也是如此。

- 在引发终止异常之前，cmdlet 可以接收任意数量的输入对象并发送任意数量的 success 或 error 对象。 收到的输入对象数与发送的成功和错误对象数之间没有关系。

- 仅可接受0-1 输入对象并仅生成0-1 输出对象的 cmdlet 应将错误视为终止错误并生成终止异常。

## <a name="reporting-nonterminating-errors"></a>报告非终止错误

报告非终止错误的操作应始终在 cmdlet 的[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法（ [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法）的实现中完成，或为，则不应如此。[system.web. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法的方法。 这些类型的错误通过调用[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法进行报告，后者会将错误记录发送到错误流。

## <a name="reporting-terminating-errors"></a>报告终止错误

通过引发异常或通过调用[ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)方法来报告终止错误。 请注意，cmdlet 还可以捕获并重新引发异常（如**OutOfMemory**），但是，它们不需要重新引发异常，因为 PowerShell 运行时也会捕获它们。

你还可以为特定于你的情况的问题定义自己的异常，或使用其错误记录向现有异常添加其他信息。

## <a name="error-records"></a>错误记录

PowerShell 介绍了[ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)对象的非终止错误条件。 每个对象提供错误类别信息、可选的目标对象以及有关错误情况的详细信息。

### <a name="error-identifiers"></a>错误标识符

错误标识符是一个简单的字符串，用于标识 cmdlet 内的错误条件。
PowerShell 将此标识符与 cmdlet 标识符组合在一起，创建完全限定的错误标识符，稍后在筛选错误流或记录错误时、响应特定错误时或与其他用户特定活动一起使用。

指定错误标识符时，应遵循以下准则：

- 将不同的、高度特定的错误标识符分配给不同的代码路径。 调用[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)或[ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)的每个代码路径都应具有其自己的错误标识符的错误标识符。

- 错误标识符对于终止和非终止错误应是公共语言运行时（CLR）异常类型所特有的。

- 请勿更改 cmdlet 或 PowerShell 提供程序版本之间的错误标识符的语义。 建立错误标识符的语义后，它应在 cmdlet 的整个生命周期中保持不变。

- 对于终止错误，请为特定的 CLR 异常类型使用唯一的错误标识符。 如果异常类型发生更改，请使用新的错误标识符。

- 对于非终止错误，请使用特定输入对象的特定错误标识符。

- 选择 tersely 与所报告错误相对应的标识符文本。 不要使用空格或标点。

- 不要生成不可重复的错误标识符。 例如，不生成包含进程标识符的标识符。 仅当错误标识符对应于遇到相同问题的其他用户所见的标识符时，错误标识符才有用。

### <a name="error-categories"></a>错误类别

错误类别用于对用户的错误进行分组。 PowerShell 定义这些类别和 cmdlet，并且 PowerShell 提供程序在生成错误记录时必须在它们之间进行选择。

有关可用的错误类别的说明，请参阅[ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory)枚举。 通常，应尽可能避免使用**NoError**、 **UndefinedError**和**GenericError** 。

用户在将 `$ErrorView` 设置为**CategoryView**时，可以根据类别查看错误。

## <a name="see-also"></a>另请参阅

[Cmdlet 概述](./cmdlet-overview.md)

[Cmdlet 输出的类型](./types-of-cmdlet-output.md)

[Windows PowerShell 参考](../windows-powershell-reference.md)
