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
ms.openlocfilehash: 5412d88b690a1f5f1ef387416e3bf9da3a32c95d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369106"
---
# <a name="windows-powershell-error-records"></a>Windows PowerShell 错误记录

Cmdlet 必须传递一个[ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)对象，该对象标识用于终止和非终止错误的错误条件。

[ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)对象包含下面的信息：

- 描述错误的异常。 通常，这是 cmdlet 捕获并转换为错误记录的异常。 每个错误记录都必须包含一个异常。

如果 cmdlet 未捕获异常，则它必须创建新的异常，并选择最能描述错误情况的异常类。 但是，您不需要引发异常，因为它可以通过[ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)对象的[ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord.Exception)属性进行访问，这是因为它是可访问的。

- 错误标识符，提供可用于诊断目的的目标标识符，以及用于处理特定错误处理程序的特定错误条件的 Windows PowerShell 脚本。 每个错误记录都必须包含错误标识符（请参阅错误标识符）。

- 一个错误类别，提供可用于诊断目的的常规指示符。 每个错误记录必须指定错误类别（请参阅错误类别）。

- 可选的替换错误消息和建议的操作（请参阅替换错误消息）。

- 有关引发错误的 cmdlet 的可选调用信息。 此信息由 Windows PowerShell 指定（请参阅调用消息）。

- 发生错误时正在处理的目标对象。 这可能是输入对象，也可能是 cmdlet 正在处理的另一个对象。 例如，对于命令 `remove-item -recurse c:\somedirectory`，该错误可能是 "c:\somedirectory\lockedfile" 的 FileInfo 对象的实例。 目标对象信息是可选的。

## <a name="error-identifier"></a>错误标识符

创建错误记录时，请指定在 cmdlet 中指定错误条件的标识符。 Windows PowerShell 将目标标识符与 cmdlet 的名称相结合，以创建完全限定的错误标识符。 完全限定的错误标识符可以通过 [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 对象的 [System.Management.Automation.ErrorRecord.FullyQualifiedErrorId](/dotnet/api/System.Management.Automation.ErrorRecord.FullyQualifiedErrorId) 属性进行访问。 错误标识符本身不可用。 它仅可用作完全限定的错误标识符的一部分。

创建错误记录时，使用以下准则生成错误标识符：

- 使错误标识符特定于错误条件。 针对诊断目的指定错误标识符，并针对处理特定错误处理程序的特定错误条件的脚本进行定位。 用户应能够使用错误标识符来标识错误及其源。 错误标识符还启用了从现有异常中报告特定错误条件，以便不需要新的异常子类。

- 通常，将不同的错误标识符分配给不同的代码路径。 最终用户将受益于特定标识符。 通常情况下，调用[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)或[Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)的每个代码路径都有其自己的标识符）。 通常，在为错误消息定义新的模板字符串时定义新的标识符，反之亦然。 不要将错误消息用作标识符。

- 当你使用特定的错误标识符发布代码时，将使用该标识符为完整的产品支持生命周期建立错误的语义。 不要在语义不同于原始上下文的上下文中重用它。 如果此错误的语义发生更改，请创建并使用新的标识符。

- 通常应仅对特定 CLR 类型的异常使用特定的错误标识符。 如果异常的类型或目标对象的类型发生更改，请创建并使用新的标识符。

- 选择您的错误标识符文本，该文本将简明扼要地对应于要报告的错误。 使用标准 .NET Framework 命名和大小写约定。 不要使用空格或标点。 不要本地化错误标识符。

- 不要以无法重现的方式动态生成错误标识符。 例如，不要合并错误信息，如进程 ID。 仅当错误标识符对应于遇到相同错误情况的其他用户所见到的错误标识符时，错误标识符才有用。

## <a name="error-category"></a>错误类别

当你创建错误记录时，使用[ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0)枚举定义的其中一个常量指定错误的类别。 当用户将 `$ErrorView` 变量设置为 `"CategoryView"` 时，Windows PowerShell 使用错误类别显示错误信息。

避免使用[ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0) **NotSpecified**常数。 如果有关于错误的任何信息或有关导致错误的操作的信息，请选择最能描述错误或操作的类别，即使该类别不是完全匹配。

Windows PowerShell 显示的信息称为类别视图字符串，是从[Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)类的属性中生成的，它是从 （此类通过错误[ErrorRecord. CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo)属性访问。）

```
{Category}: ({TargetName}:{TargetType}):[{Activity}], {Reason}
```

以下列表描述了显示的信息：

- 类别：Windows PowerShell 定义的[ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0)常量。

- TargetName默认情况下，该 cmdlet 在发生错误时正在处理的对象的名称。 或其他 cmdlet 定义的字符串。

- TargetType默认情况下，目标对象的类型。 或其他 cmdlet 定义的字符串。

- 活动默认情况下，创建错误记录的 cmdlet 的名称。 或其他 cmdlet 定义的字符串。

- 原因：默认情况下，异常类型。 或其他 cmdlet 定义的字符串。

## <a name="replacement-error-message"></a>替换错误消息

当你为某个 cmdlet 开发错误记录时，该错误的默认错误消息将来自[system.exception 属性中](/dotnet/api/System.Exception.Message)的默认消息文本。 这是一个只读属性，其消息文本仅用于调试目的（根据 .NET Framework 准则）。 建议创建一个错误消息来替换或扩充默认消息文本。 使消息更易于用户理解，更具针对性于 cmdlet。

替换消息是由[ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails)对象提供的。 使用此对象的以下构造函数之一，因为它们提供了可供 Windows PowerShell 使用的其他本地化信息。

- [ErrorDetails （Cmdlet，string，string，Object []）](/dotnet/api/system.management.automation.errordetails.-ctor?view=pscore-6.2.0#System_Management_Automation_ErrorDetails__ctor_System_Management_Automation_Cmdlet_System_String_System_String_System_Object___)：如果模板字符串是在其中实现了 cmdlet 的同一程序集中的资源字符串，或者如果要通过[GetResourceString](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString)方法的重写加载模板字符串，请使用此构造函数.

- [ErrorDetails （Assembly，string，string，Object []）](/dotnet/api/system.management.automation.errordetails.-ctor?view=pscore-6.2.0#System_Management_Automation_ErrorDetails__ctor_System_Reflection_Assembly_System_String_System_String_System_Object___)：如果模板字符串在另一个程序集中，并且不通过重写[GetResourceString](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString)来加载它，请使用此构造函数。

替换消息应该符合 .NET Framework 的设计准则，用于编写少量的异常消息。 准则表明应为开发人员编写异常消息。 应为 cmdlet 用户编写这些替换消息。

在调用[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)或[Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)方法之前，必须先添加替换错误消息，然后再将其添加。 若要添加替代消息，请设置错误记录的[ErrorRecord. ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails)属性。 设置此属性后，Windows PowerShell 会显示[ErrorDetails *](/dotnet/api/System.Management.Automation.ErrorDetails.Message)属性，而不是默认消息文本。

## <a name="recommended-action-information"></a>建议的操作信息

[ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails)对象还可以提供有关在发生错误时建议的操作的信息。

## <a name="invocation-information"></a>调用信息

当某个 cmdlet 使用[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)或[Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)来报告错误记录时，Windows PowerShell 会自动添加描述该内容的信息，这些发生错误时调用的命令。 此信息由[Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo)对象提供，该对象包含命令调用的 cmdlet 的名称、命令本身，以及有关管道或脚本的信息。 此属性是只读的。

## <a name="see-also"></a>另请参阅

["WriteError"。](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Throwterminatingerror * 的 *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.web. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0)

[System.web. Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System.web. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.web. ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails)

[System.web. Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo)

[Windows PowerShell 错误报告](./error-reporting-concepts.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
