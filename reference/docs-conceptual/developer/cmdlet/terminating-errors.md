---
title: 终止错误 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b804e738-aefa-41bb-9649-f9ed897fd96c
caps.latest.revision: 8
ms.openlocfilehash: d1967fe7996f75ec5229920f7ec49aa5ff6bdbfd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369326"
---
# <a name="terminating-errors"></a>终止错误

本主题讨论用于报告终止错误的方法。 它还讨论了如何从 cmdlet 内调用方法，并讨论了调用方法时 Windows PowerShell 运行时可能返回的异常。

当发生终止错误时，此 cmdlet 应通过调用[Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)方法报告错误消息。 此方法允许 cmdlet 发送描述引起终止错误的条件的错误记录。 有关错误记录的详细信息，请参阅[Windows PowerShell 错误记录](./windows-powershell-error-records.md)。

如果调用了 [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 方法，则 Windows PowerShell 运行时将永久停止执行管道，并引发[System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) 异常。 任何后续尝试调用 [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 或其他几个 api，都将导致这些调用引发 [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) 异常的情况下进行调用，从而引发异常。

如果管道中的另一个 cmdlet 报告终止错误（如果用户已请求停止管道），或者如果由于任何原因已暂停管道，则也会发生[Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)异常。 Cmdlet 不需要捕获[Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)异常，除非它必须清除打开的资源或其内部状态。

在报告终止错误之前，cmdlet 可以写入任意数量的输出对象或非终止错误。 但是，终止错误会永久停止管道，并且不会报告其他输出、终止错误或非终止错误。

Cmdlet 只能从名为 [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)或 [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 输入处理方法的线程调用 [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)。 不要尝试从另一个线程调用[Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)或[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)的其他线程中的其他线程。 而必须将错误发回到主线程。

Cmdlet 可在其实现[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)、 [ProcessRecord 或](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的实现中引发异常，这种情况可能会引发异常的情况下引发异常的情况下可能引发[异常。](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 从这些方法引发的任何异常（除了停止 Windows PowerShell 主机的几个严重错误情况外）均被解释为终止错误，该错误将停止管道，而不是整个 Windows PowerShell。 （这仅适用于主 cmdlet 线程。 通常，在由 cmdlet 生成的线程中未捕获到的异常通常是暂停 Windows PowerShell 主机。）建议使用[Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)而不是引发异常，因为错误记录提供了有关错误条件的其他信息，这对最终用户非常有用。 Cmdlet 应遵循托管代码准则，以避免捕获和处理所有异常（`catch (Exception e)`）。 仅将已知类型和预期类型的异常转换为错误记录。

## <a name="see-also"></a>另请参阅

["BeginProcessing"。](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.web. EndProcessing. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

["ProcessRecord"。](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.web. Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)

[Throwterminatingerror * 的 *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

["WriteError"。](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows PowerShell 错误记录](./windows-powershell-error-records.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
