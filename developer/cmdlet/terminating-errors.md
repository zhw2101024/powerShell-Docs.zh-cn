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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059229"
---
# <a name="terminating-errors"></a>终止错误

本主题讨论用于终止错误的报告的方法。 它还介绍了如何调用从 cmdlet 中的方法和讨论时调用的方法可以由 Windows PowerShell 运行时返回的异常。

当终止时出现错误，该 cmdlet 应通过调用报告错误[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)方法。 此方法允许该 cmdlet 将发送错误记录描述导致终止的错误条件。 错误记录的详细信息，请参阅[Windows PowerShell 错误记录](./windows-powershell-error-records.md)。

当[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)方法调用时，Windows PowerShell 运行时永久停止管道的执行，并将引发[System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)异常。 若要调用任何后续尝试[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)， [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)，或多个其他 Api，将导致这些调用会引发[System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)异常。

[System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)如果管道中的另一个 cmdlet 报告一个终止错误，如果用户已要求停止管道，或者如果已暂停管道，也会发生异常之前出于任何原因已完成。 该 cmdlet 不需要捕获[System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)异常除非它必须清理打开资源或其内部状态。

Cmdlet 可以编写报告一个终止错误之前的任意数量的输出对象或非终止性错误。 但是，终止错误永久停止管道，并无更多输出，终止错误，或可以报告非终止错误。

Cmdlet 可以调用[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)只从调用线程[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)， [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)，或[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)输入处理方法。 请不要尝试调用[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)或[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)从另一个线程。 相反，必须返回到主线程传达错误。

很可能是 cmdlet 在其实现中引发异常[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)， [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)，或[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。 从这些方法 （除外停止 Windows PowerShell 主机的几个严重错误条件） 引发任何异常被解释为一个终止错误，它将停止管道，但不是 Windows PowerShell 作为一个整体。 （这仅适用于主要 cmdlet 线程。 Cmdlet，生成的线程中的未捕获的异常一般情况下，停止 Windows PowerShell 主机。）我们建议你使用[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)而不是引发异常，因为错误记录提供了有关错误条件的其他信息，这是适用于最终用户。 Cmdlet 应遵循针对捕获和处理所有异常的托管的代码准则 (`catch (Exception e)`)。 只有已知和预期类型的异常转换为错误记录。

## <a name="see-also"></a>另请参阅

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows PowerShell 错误记录](./windows-powershell-error-records.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
