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
ms.openlocfilehash: 32ebf2531237bfd1042310ccc4155193a58401fd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365416"
---
# <a name="interpreting-errorrecord-objects"></a>解释 ErrorRecord 对象

在大多数情况下， [ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)对象表示命令或脚本生成的非终止错误。 终止错误还可以通过[Icontainserrorrecord](/dotnet/api/System.Management.Automation.IContainsErrorRecord)接口在 ErrorRecord 中指定其他信息。

如果要在脚本或主机中编写错误处理程序来处理命令或脚本执行过程中发生的特定错误，则必须解释[ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)对象，以确定它是否表示的类要处理的错误。

当 cmdlet 遇到终止或非终止错误时，它应创建描述错误情况的错误记录。 宿主应用程序必须调查这些错误记录，并执行任何可缓解错误的操作。 主机应用程序还必须调查错误记录中是否存在无法处理记录但能够继续的非终止错误，还必须调查错误记录以终止导致管道停止的错误。

> [!NOTE]
> 对于终止错误，该 cmdlet 将调用[Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)方法。 对于非终止错误，该 cmdlet 将调用[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法。

## <a name="error-record-design"></a>错误记录设计

错误记录旨在提供不在异常中提供的其他错误信息，同时确保每个错误记录中的组合信息是唯一的。 此唯一性使宿主应用程序可以检查错误记录的不同部分，以确定错误条件和宿主必须执行的操作。

## <a name="interpreting-error-records"></a>解释错误记录

您可以查看错误记录的若干部分来确定错误。 这些部分包括：

- 错误类别

- 错误异常

- 完全限定的错误标识符（FQID）

- 其他信息

### <a name="the-error-category"></a>错误类别

错误记录的错误类别是由[Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)枚举提供的预定义常量之一。 此信息可通过[ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)对象的[ErrorRecord. CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo)属性获得。）的信息可供使用。

Cmdlet 可以指定 CloseError、OpenError、InvalidType、ReadError 和 WriteError 类别以及其他错误类别。 主机应用程序可以使用错误类别来捕获错误组。

### <a name="the-exception"></a>异常

错误记录中包含的异常由 cmdlet 提供，并可通过[ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)对象的[ErrorRecord *](/dotnet/api/System.Management.Automation.ErrorRecord.Exception)属性进行访问，可通过此方法访问。

主机应用程序可以使用 @no__t 0 关键字来确定异常是特定类还是派生类。 最好在异常类型上进行分支，如下面的示例中所示。

`if (MyNonTerminatingError.Exception is AccessDeniedException)`

这样，你将捕获派生类。 但是，如果反序列化异常，则会出现问题。

### <a name="the-fqid"></a>FQID

FQID 是可用于标识错误的最具体的信息。 它是一个字符串，其中包含 cmdlet 定义的标识符、cmdlet 类的名称以及报告错误的源。 通常，错误记录类似于 Windows 事件日志的事件记录。 FQID 类似于以下元组，该元组标识事件记录的类：（*日志名称*、*源*、*事件 ID*）。

FQID 设计为作为单个字符串被检查。 但是，在这种情况下，错误标识符旨在由主机应用程序进行分析。 下面的示例是一个格式正确的完全限定的错误标识符。

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand.`

在上面的示例中，第一个标记是错误标识符，后跟 cmdlet 类的名称。 错误标识符可以是单个标记，也可以是一个用句点分隔的标识符，该标识符允许在对标识符进行分支。 不要在错误标识符中使用空格或标点。 尤其重要的是，不要使用逗号;Windows PowerShell 使用逗号来分隔标识符和 cmdlet 类名称。

### <a name="other-information"></a>其他信息

[ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)对象还可能会提供描述发生错误的环境的信息。 此信息包括错误详细信息、调用信息以及发生错误时正在处理的目标对象等项。 尽管此信息可能对主机应用程序很有用，但它通常不用于识别错误。 此信息通过以下属性提供：

[ErrorRecord. ErrorDetails。](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails)

[ErrorRecord. InvocationInfo。](/dotnet/api/System.Management.Automation.ErrorRecord.InvocationInfo)

[ErrorRecord. TargetObject。](/dotnet/api/System.Management.Automation.ErrorRecord.TargetObject)

## <a name="see-also"></a>另请参阅

[System.web. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.web. Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System.web. Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

["WriteError"。](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Throwterminatingerror * 的 *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[向 Cmdlet 添加非终止错误报告](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows PowerShell 错误报告](./error-reporting-concepts.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
