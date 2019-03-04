---
title: 解释 ErrorRecord 对象 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a65b964-5bc6-4ade-a66b-b6afa7351ce7
caps.latest.revision: 9
ms.openlocfilehash: d77e4daf25bfcd5e76c184f6dbdb619368627bfa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857223"
---
# <a name="interpreting-errorrecord-objects"></a>解释 ErrorRecord 对象

在大多数情况下， [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord)对象表示的命令或脚本生成一个非终止错误。 终止错误还可以指定其他信息中通过 ErrorRecord [System.Management.Automation.Icontainserrorrecord](/dotnet/api/System.Management.Automation.IContainsErrorRecord)接口。

如果你想要编写错误处理程序在您的脚本或主机用于处理特定错误的执行过程中发生命令或脚本，您必须解释[System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord)对象，以确定是否它表示要处理的错误的类。

当一个 cmdlet 遇到终止或非终止错误时，它应创建错误记录描述错误条件。 主机应用程序必须调查这些错误记录，并执行任何操作将会减少错误。 主机应用程序还必须调查错误记录为非终止错误，无法处理一条记录，但可以继续，并它必须调查导致停止管道的终止错误的错误记录。

> [!NOTE]
> 对于终止错误，该 cmdlet 的调用[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)方法。 对于非终止性错误，该 cmdlet 的调用[System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法。

## <a name="error-record-design"></a>错误记录设计

错误记录用于提供其他错误同时确保每个错误记录中的组合的信息唯一不可用在异常中的信息。 此唯一性允许主机应用程序检查错误记录的不同部分，以便它可以识别的错误条件，并且必须采取的操作主机。

## <a name="interpreting-error-records"></a>解释错误记录

你可以查看要识别的错误的错误记录的多个部分。 这些部分如下所示：

- 错误类别

- 错误异常

- 完全限定的错误标识符 (FQID)

- 其他信息

### <a name="the-error-category"></a>错误类别

错误记录的错误类别是由提供的预定义常量之一[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)枚举。 此信息是可通过[System.Management.Automation.Errorrecord.Categoryinfo*](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo)的属性[System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord)对象。

CloseError、 OpenError、 InvalidType、 ReadError 和 WriteError 类别和其他错误类别，可以指定该 cmdlet。 主机应用程序可以使用的错误类别捕获的错误组。

### <a name="the-exception"></a>异常

错误记录中包含的异常提供的 cmdlet，可通过访问[System.Management.Automation.Errorrecord.Exception*](/dotnet/api/System.Management.Automation.ErrorRecord.Exception)属性的[System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord)对象。

主机应用程序可以使用`is`关键字来标识异常的特定类或派生类。 最好是为 branch 异常类型，如下面的示例中所示。

`if (MyNonTerminatingError.Exception is AccessDeniedException)`

这样一来，您捕获派生的类。 但是，有问题如果异常进行反序列化。

### <a name="the-fqid"></a>FQID

FQID 是可用于标识错误的最具体信息。 它是包含 cmdlet，定义标识符、 在 cmdlet 类，并报告了错误的源的名称的字符串。 一般情况下，错误记录相当于 Windows 事件日志的事件记录。 FQID 是类似于标识的事件记录的类的以下元组: (*日志名称*，*源*，*事件 ID*)。

FQID 旨在作为单个字符串进行检查。 但是，存在情况设计错误标识符分析由主机应用程序。 下面的示例是格式正确的完全限定的错误标识符。

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand.`

在上一示例中，第一个标记是错误标识符后, 跟在 cmdlet 类的名称。 错误标识符可以是单个标记，也可以是允许在检查标识符的分支是以点号分隔的标识符。 不要在错误标识符中使用空格或标点。 它是尤为重要，不应使用逗号;Windows PowerShell 使用逗号来分隔标识符和 cmdlet 类名称。

### <a name="other-information"></a>其他信息

[System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord)对象还可能会提供描述的环境发生了错误的信息。 此信息包括错误详细信息、 调用信息和错误发生时正在处理的目标对象等项。 尽管此信息可供主机应用程序，它是通常不用于识别的错误。 此信息将可通过以下属性：

[System.Management.Automation.Errorrecord.Errordetails*](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails)

[System.Management.Automation.Errorrecord.Invocationinfo*](/dotnet/api/System.Management.Automation.ErrorRecord.InvocationInfo)

[System.Management.Automation.Errorrecord.Targetobject*](/dotnet/api/System.Management.Automation.ErrorRecord.TargetObject)

## <a name="see-also"></a>另请参阅

[System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[添加非终止错误报告到 Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows PowerShell 错误报告](./error-reporting-concepts.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
