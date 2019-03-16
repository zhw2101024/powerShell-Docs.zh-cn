---
title: Windows PowerShell 错误记录 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error category [PowerShell SDK]
- error identifier [PowerShell SDK]
- error records [PowerShell SDK]
- error category string [PowerShell SDK]
ms.assetid: bdd66fea-eb63-4bb6-9cbe-9a799e5e0db5
caps.latest.revision: 9
ms.openlocfilehash: f6f5e50c55b477cbbeeaaf4f3ea665d5dc07758c
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059756"
---
# <a name="windows-powershell-error-records"></a>Windows PowerShell 错误记录

Cmdlet 必须传递[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)标识终止和非终止性错误的错误条件的对象。

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)对象包含以下信息：

- 描述错误的异常。 通常情况下，这是该 cmdlet 捕获并转换为错误记录的异常。 每个错误记录必须包含一个异常。

如果该 cmdlet 未捕获异常，它必须创建新异常，并选择最适合描述错误条件的异常类。 但是，不需要引发异常，因为它可以通过访问[System.Management.Automation.ErrorRecord.Exception](/dotnet/api/System.Management.Automation.ErrorRecord.Exception)属性的[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)对象。

- 提供可用于诊断目的和通过 Windows PowerShell 脚本来处理具有特定的错误处理程序的特定错误条件的目标的指示符错误标识符。 每个错误记录必须包含的错误标识符 （请参阅错误标识符）。

- 错误类别，提供可用于诊断目的的常规指示符。 每个错误记录必须指定的错误类别 （请参阅错误类别）。

- 可选替换错误消息和建议的操作 （请参阅替换错误消息）。

- 可选调用引发了错误的 cmdlet 的信息。 此信息指定 Windows powershell （请参阅调用消息）。

- 发生错误时正在处理的目标对象。 这可能是输入的对象，也可能是你的 cmdlet 已处理的另一个对象。 例如，对于该命令`remove-item -recurse c:\somedirectory`，错误可能是"c:\somedirectory\lockedfile"FileInfo 对象的实例。 目标对象信息是可选的。

## <a name="error-identifier"></a>错误标识符

创建错误记录时，指定将在你的 cmdlet 中的错误条件指定的标识符。 Windows PowerShell cmdlet 来创建完全限定的错误标识符的名称与组合目标的标识符。 可以通过访问的完全限定的错误标识符[System.Management.Automation.ErrorRecord.FullyQualifiedErrorId](/dotnet/api/System.Management.Automation.ErrorRecord.FullyQualifiedErrorId)属性的[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)对象。 本身的错误标识符不可用。 该内容位于仅作为完全限定的错误标识符的一部分。

使用以下准则来创建错误记录时生成错误标识符：

- 使特定的错误条件的错误标识符。 诊断目的和处理特定错误条件使用特定的错误处理程序的脚本为目标的错误标识符。 用户应该能够使用错误标识符来标识该错误和其源。 错误标识符还为启用报表从现有异常的特定错误条件，以便新异常子类不是必需的。

- 一般情况下，将不同的错误标识符分配给不同的代码路径。 最终用户可以利用特定标识符。 通常情况下，每个调用的代码路径[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)或[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)具有其自己的标识符。 一般来说，定义一个新的标识符时定义的错误消息和进行相反转换为新的模板字符串。 不要使用错误消息作为标识符。

- 发布时使用的特定错误标识符代码，您建立的语义错误该标识符完整产品支持生命周期。 不要重复使用它在语义上不同于原始上下文的上下文中。 如果此错误的语义更改，请创建，然后使用新的标识符。

- 通常应仅为特定的 CLR 类型的异常使用的特定错误标识符。 如果异常的类型或目标对象的类型发生更改，创建，然后使用新的标识符。

- 选择你用于简明地对应于要报告的错误的错误标识符的文本。 使用标准.NET Framework 命名和大小写约定。 不要使用空格或标点。 不要本地化错误标识符。

- 不动态会生成错误标识符不可重现的方式。 例如，不包含错误的信息，例如进程 id。 错误标识符是仅在它们对应于遇到相同的错误条件的其他用户看到的错误标识符。

## <a name="error-category"></a>错误类别

创建错误记录时，指定使用定义的常量之一的错误类别[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)枚举。 Windows PowerShell 使用的错误类别的用户设置时显示错误信息`$ErrorView`变量`"CategoryView"`。

避免使用[System.Management.Automation.Errorcategory.Notspecified](/dotnet/api/System.Management.Automation.ErrorCategory.NotSpecified)常量。 如果有任何有关错误或导致了错误的操作的信息，即使该类别不是完美匹配选择最适合描述错误或操作的类别。

显示 Windows powershell 的信息被称为类别查看字符串和为依据的属性[System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)类。 (此类错误可通过访问[System.Management.Automation.ErrorRecord.CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo)属性。)

```
{Category}: ({TargetName}:{TargetType}):[{Activity}], {Reason}
```

以下列表描述了显示的信息：

- 类别：Windows PowerShell 定义[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)常量。

- TargetName:默认情况下，该对象的名称 cmdlet 处理中出现错误。 或者，另一个 cmdlet，定义的字符串。

- TargetType:默认情况下，目标对象的类型。 或者，另一个 cmdlet，定义的字符串。

- 活动：默认情况下，创建错误记录 cmdlet 的名称。 或者，某些其他 cmdlet 定义的字符串。

- 原因：默认情况下，异常类型。 或者，另一个 cmdlet，定义的字符串。

## <a name="replacement-error-message"></a>替换错误消息

开发时 cmdlet 的错误记录，该错误的默认错误消息来自中的默认消息文本[System.Exception.Message](/dotnet/api/System.Exception.Message)属性。 这是其消息文本旨在仅适用于调试 （.NET Framework 指南 》 中提及） 的只读属性。 我们建议创建替换或补充默认消息文本的错误消息。 将更加友好的用户和更多特定消息给 cmdlet。

通过提供的替换消息[System.Management.Automation.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails)对象。 使用此对象的以下构造函数之一，因为它们提供可由 Windows PowerShell 的额外的本地化信息。

- [ErrorDetails.ErrorDetails (Cmdlet、 字符串、 字符串、 对象\[System.Management.Automation.ErrorDetails.%23Ctor%28System.Management.Automation.Cmdlet%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29？Displayproperty =](/dotnet/api/System.Management.Automation.ErrorDetails.%23ctor%28System.Management.Automation.Cmdlet%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29):使用此构造函数，如果您的模板字符串是在其中实现该 cmdlet 在同一程序集中的资源字符串，或如果你想要加载的模板字符串的重写通过[System.Management.Automation.Cmdlet.GetResourceString](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString)方法。

- [ErrorDetails.ErrorDetails (程序集、 字符串、 字符串、 对象\[System.Management.Automation.ErrorDetails.%23Ctor%28System.Reflection.Assembly%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29？Displayproperty =](/dotnet/api/System.Management.Automation.ErrorDetails.%23ctor%28System.Reflection.Assembly%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29):如果模板字符串为另一个程序集中并且不执行操作的重写通过加载它，请使用此构造函数[System.Management.Automation.Cmdlet.GetResourceString](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString)。

替换消息应符合编写略有不同的异常消息的.NET Framework 设计准则。 异常消息应面向开发人员指南状态。 应为 cmdlet 用户编写这些替换消息。

替换错误消息必须添加之前[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)或[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)调用方法。 若要添加置换消息，请设置[System.Management.Automation.ErrorRecord.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails)错误记录的属性。 当设置此属性时，Windows PowerShell 会显示[System.Management.Automation.ErrorDetails.Message*](/dotnet/api/System.Management.Automation.ErrorDetails.Message)属性而不是默认消息文本。

## <a name="recommended-action-information"></a>建议的操作信息

[System.Management.Automation.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails)对象还可以提供有关发生错误时，建议使用哪些操作的信息。

## <a name="invocation-information"></a>调用的信息

当使用 cmdlet [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)或[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)来报告错误记录，Windows PowerShell会自动添加描述发生错误时调用的命令的信息。 通过提供此信息[System.Management.Automation.Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo)对象，其中包含已调用的命令，命令自身中，该 cmdlet 的名称和有关管道或脚本的信息。 此属性是只读的。

## <a name="see-also"></a>另请参阅

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.Management.Automation.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails)

[System.Management.Automation.Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo)

[Windows PowerShell 错误报告](./error-reporting-concepts.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
