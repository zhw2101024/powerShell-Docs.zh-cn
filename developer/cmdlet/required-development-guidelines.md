---
title: 所需的开发准则 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41d2b308-a36a-496f-8542-666b6a21eedc
caps.latest.revision: 19
ms.openlocfilehash: 3f6bcd2e4ef4d9c404b3a5deeaa9f25d3fa42ec1
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056509"
---
# <a name="required-development-guidelines"></a>必需的开发指南

编写 cmdlet 时，必须遵循以下准则。 它们分为设计 cmdlet 和指引，用于编写 cmdlet 代码的准则。 如果不遵循这些指导原则，cmdlet 可能会失败，并在使用 cmdlet 时，用户可能具有不好的体验。

## <a name="in-this-topic"></a>本主题内容

### <a name="design-guidelines"></a>设计指南

- [只使用批准的谓词 (RD01)](./required-development-guidelines.md#use-only-approved-verbs-rd01)

- [Cmdlet 名称：不能使用的字符 (RD02)](./required-development-guidelines.md#cmdlet-names-characters-that-cannot-be-used-rd02)

- [不能使用的参数名称 (RD03)](./required-development-guidelines.md#parameters-names-that-cannot-be-used-rd03)

- [支持确认请求 (RD04)](./required-development-guidelines.md#support-confirmation-requests-rd04)

- [为交互式会话 (RD05) 支持 Force 参数](./required-development-guidelines.md#support-force-parameter-for-interactive-sessions-rd05)

- [文档输出对象 (RD06)](./required-development-guidelines.md#document-output-objects-rd06)

### <a name="code-guidelines"></a>代码指南

- [派生的 Cmdlet 或 PSCmdlet 类 (RC01)](./required-development-guidelines.md#derive-from-the-cmdlet-or-pscmdlet-classes-rc01)

- [指定 Cmdlet 属性 (RC02)](./required-development-guidelines.md#specify-the-cmdlet-attribute-rc02)

- [重写输入处理方法 (RC03)](./required-development-guidelines.md#override-an-input-processing-method-rc03)

- [指定 OutputType 属性 (RC04)](./required-development-guidelines.md#specify-the-outputtype-attribute-rc04)

- [不保留输出对象 (RC05) 的句柄](./required-development-guidelines.md#do-not-retain-handles-to-output-objects-rc05)

- [可靠地处理错误 (RC06)](./required-development-guidelines.md#handle-errors-robustly-rc06)

- [使用 Windows PowerShell 模块来部署 Cmdlet (RC07)](./required-development-guidelines.md#use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07)

## <a name="design-guidelines"></a>设计指南

设计用于确保使用 cmdlet 和其他 cmdlet 之间一致的用户体验的 cmdlet 时，必须遵循以下准则。 找到一个设计指导原则适用于你的情况，请务必查看类似的指导原则的代码准则。

### <a name="use-only-approved-verbs-rd01"></a>只使用批准的谓词 (RD01)

Cmdlet 属性中指定的谓词必须来自已识别组提供的 Windows PowerShell 的谓词。 它不能禁止同义词之一。 使用以下枚举来指定 cmdlet 谓词定义的常量字符串：

- [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

- [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

- [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

- [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

- [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

- [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

- [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

有关批准的动词名称的详细信息，请参阅[Cmdlet 谓词](./approved-verbs-for-windows-powershell-commands.md)。

用户需要一组可发现和预期的 cmdlet 名称。 使用相应的动词，以便用户能够进行快速评估的 cmdlet 的用途并轻松地发现系统的功能。 例如，以下命令行命令将获取名称以"start"开头的系统上的所有命令列表： `get-command start-*`。 使用中的名词 cmdlet 中将 cmdlet 与其他 cmdlet 区分开来。 （） 名词，指示将对其执行操作的资源。 谓词被表示本身的操作。

### <a name="cmdlet-names-characters-that-cannot-be-used-rd02"></a>Cmdlet 名称：不能使用的字符 (RD02)

当命名 cmdlet 时，则不使用任何以下特殊字符。

|字符|名称|
|---------------|----------|
|#|数字符号|
|、|逗号|
|()|括号|
|{}|大括号|
|[]|方括号|
|&|and 符|
|-|连字符**注意：** 可以使用连字符分隔中名词谓词，但不是能在名词或谓词中使用。|
|/|斜杠标记|
|\|反斜杠|
|$|美元符号|
|^|插入符号|
|;|以分号|
|：|冒号|
|"|双引号|
|'|单引号|
|<>|尖括号|
|&#124;|垂直条|
|?|问号|
|@|at 符号|
|| 返回时钟周期 （重音符）|
|*|星号|
|%|百分比符号|
|+|加号|
|=|等号|
|~|波形符|

### <a name="parameters-names-that-cannot-be-used-rd03"></a>不能使用的参数名称 (RD03)

Windows PowerShell 提供了一组通用的所有 cmdlet 参数加上在特定情况下添加的其他参数。 设计自己的 cmdlet 时不能使用以下名称：确认，Debug、 ErrorAction、 ErrorVariable、 OutBuffer OutVariable、 WarningAction、 WarningVariable、 WhatIf、 UseTransaction，和详细。 有关这些参数的详细信息，请参阅[通用参数名称](./common-parameter-names.md)。

### <a name="support-confirmation-requests-rd04"></a>支持确认请求 (RD04)

对于执行修改系统的操作的 cmdlet，它们应调用[System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法来请求确认，并在特殊情况下调用[System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法。 ( [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)后，才应调用方法[System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用方法。)

若要进行这些调用必须指定该 cmdlet，它支持通过设置确认请求`SupportsShouldProcess`Cmdlet 属性的关键字。 有关设置此属性的详细信息，请参阅[Cmdlet 特性声明](./cmdlet-attribute-declaration.md)。

> [!NOTE]
> 如果在 cmdlet 类 Cmdlet 属性指示该 cmdlet 支持调用[System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法，并且该 cmdlet 无法调用[System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法，用户可能意外修改系统。

使用[System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)系统进行任何修改的方法。 用户首选项和`WhatIf`参数控制[System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法。 与此相反， [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)调用具有潜在危险的修改，执行其他检查。 此方法不受任何用户首选项或`WhatIf`参数。 如果你的 cmdlet 调用[System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，它应具有`Force`参数跳过对这两种方法的调用和，继续执行该操作。 这非常重要，因为它允许您以非交互式脚本和主机中使用的 cmdlet。

如果你 cmdlet 支持这些调用，用户可以确定是否应实际执行该操作。 例如， [Stop-process](/powershell/module/microsoft.powershell.management/stop-process) cmdlet 可调用[System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法之前停止的一组关键进程，包括 Winlogon，系统和Spoolsv 进程。

支持这些方法的详细信息，请参阅[请求确认](./requesting-confirmation-from-cmdlets.md)。

### <a name="support-force-parameter-for-interactive-sessions-rd05"></a>为交互式会话 (RD05) 支持 Force 参数

如果以交互方式使用 cmdlet，则始终提供 Force 参数来重写的交互操作，如提示或读取行输入）。 这非常重要，因为它允许您以非交互式脚本和主机中使用的 cmdlet。 以下方法可以实现的交互式主机。

- [System.Management.Automation.Host.PSHostUserInterface.Prompt*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.Prompt)

- [System.Management.Automation.Host.Pshostuserinterface.PromptForChoice](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForChoice)

- [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection.PromptForChoice](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection.PromptForChoice)

- [System.Management.Automation.Host.Pshostuserinterface.PromptForCredential*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForCredential)

- [System.Management.Automation.Host.Pshostuserinterface.ReadLine*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLine)

- [System.Management.Automation.Host.Pshostuserinterface.ReadLineAsSecureString*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLineAsSecureString)

### <a name="document-output-objects-rd06"></a>文档输出对象 (RD06)

Windows PowerShell 使用写入管道的对象。 为了使用户可以利用每个 cmdlet 返回的对象，必须文档将返回的对象和必须文档使用为这些返回的对象的成员。

## <a name="code-guidelines"></a>代码指南

编写 cmdlet 代码时，必须遵循以下准则。 找到适用于您的具体情况的代码准则，请务必查看类似的指导原则的设计指南。

### <a name="derive-from-the-cmdlet-or-pscmdlet-classes-rc01"></a>派生的 Cmdlet 或 PSCmdlet 类 (RC01)

Cmdlet 必须或者派生[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)或[System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)基类。 派生的 Cmdlet [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)类不依赖于 Windows PowerShell 运行时。 它们可以直接从任何 Microsoft.NET Framework 语言调用。 派生的 Cmdlet [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)类依赖于 Windows PowerShell 运行时。 因此，它们在内执行一个运行空间。

您实现的所有 cmdlet 类必须都是公共类。 有关这些 cmdlet 类的详细信息，请参阅[Cmdlet 概述](./cmdlet-overview.md)。

### <a name="specify-the-cmdlet-attribute-rc02"></a>指定 Cmdlet 属性 (RC02)

若要识别的 Windows PowerShell cmdlet，必须使用 Cmdlet 特性修饰其.NET Framework 类。 此属性指定该 cmdlet 的以下功能。

- 标识该 cmdlet 的动词-名词对。

- 指定多个参数集时使用默认参数集。 如果 Windows PowerShell 不具有足够的信息来确定哪些参数设置为使用，则使用默认参数集。

- 指示该 cmdlet 支持调用[System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法。 该 cmdlet 对系统进行更改之前，此方法会向用户显示一条确认消息。 有关如何建立确认请求的详细信息，请参阅[请求确认](./requesting-confirmation-from-cmdlets.md)。

- 指示与确认消息关联的操作的影响级别 （或严重性）。 在大多数情况下，应使用的介质的默认值。 有关如何影响级别影响向用户显示的确认请求的详细信息，请参阅[请求确认](./requesting-confirmation-from-cmdlets.md)。

有关如何声明 cmdlet 属性的详细信息，请参阅[CmdletAttribute 声明](./cmdlet-attribute-declaration.md)。

### <a name="override-an-input-processing-method-rc03"></a>重写输入处理方法 (RC03)

若要在 Windows PowerShell 环境中参与 cmdlet，则必须重写至少一个以下*输入处理方法*。

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)调用一次，此方法，它用于提供预处理功能。

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)多次调用此方法，它用于提供按记录功能。

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)调用一次，此方法，它用于提供后续处理功能。

### <a name="specify-the-outputtype-attribute-rc04"></a>指定 OutputType 属性 (RC04)

（在 Windows PowerShell 2.0 中引入） 的 OutputType 属性指定您 cmdlet 将返回到管道的.NET Framework 类型。 通过指定 cmdlet 的输出类型可以将返回的对象在 cmdlet 更容易地发现其他 cmdlet。 修饰具有此特性在 cmdlet 类的详细信息，请参阅[OutputType 特性声明](./outputtype-attribute-declaration.md)。

### <a name="do-not-retain-handles-to-output-objects-rc05"></a>不保留输出对象 (RC05) 的句柄

你的 cmdlet 应不保留任何对象的句柄传递给[System.Management.Automation.Cmdlet.WriteObject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法。 这些对象传递给管道中下一个 cmdlet 或脚本使用它们。 如果保留对象的句柄，两个实体将拥有每个对象，这会导致错误。

### <a name="handle-errors-robustly-rc06"></a>可靠地处理错误 (RC06)

管理环境本质上是检测，并会对您管理的系统的重要更改。 因此，非常重要 cmdlet 正确地处理错误。 错误记录的详细信息，请参阅[Windows PowerShell 错误报告](./error-reporting-concepts.md)。

- 当某个错误阻止 cmdlet 继续处理任何更多记录时，它是一个终止错误。 该 cmdlet 必须调用[System.Management.Automation.Cmdlet.ThrowTerminatingError*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)引用方法[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)对象。 如果 cmdlet 不捕获异常，Windows PowerShell 运行时本身将引发一个终止错误包含较少的信息。

- 对于不会停止操作在下一个非终止错误来自管道 （例如，a 记录的其他进程生成），该 cmdlet 的记录必须调用[System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)引用方法[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)对象。 非终止错误的一个示例是如果在特定的进程无法停止，则会发生的错误。 调用[System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法允许用户以一致地执行请求的操作，并保留失败的特定操作的信息。 你的 cmdlet 应尽可能独立处理每条记录。

- [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)对象，该引用的对象[System.Management.Automation.Cmdlet.ThrowTerminatingError*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)和[System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法需要在其核心异常。 确定要使用的异常时，请遵循.NET Framework 设计准则。 如果错误是在语义上与现有异常不同，使用该异常或派生自该异常。 否则，派生的新异常或直接从异常层次结构[System.Exception](/dotnet/api/System.Exception)类型。

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)对象也需要进行分组的用户错误的错误类别。 用户可以查看基于类别的值设置的错误`$ErrorView`CategoryView 的 shell 变量。 可能的类别定义由[System.Management.Automation.ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory)枚举。

- 如果某个 cmdlet 创建一个新线程，并且在该线程中运行的代码将引发未处理的异常，Windows PowerShell 将不会捕获该错误，并将终止进程。

- 如果一个对象将代码中未经处理的异常将导致其析构函数，Windows PowerShell 将不会捕获该错误，并将终止进程。 如果对象调用 Dispose 方法会导致未经处理的异常也会发生这种情况。

### <a name="use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07"></a>使用 Windows PowerShell 模块来部署 Cmdlet (RC07)

创建一个 Windows PowerShell 模块来打包和部署 cmdlet。 在 Windows PowerShell 2.0 中引入的模块的支持。 可以使用二进制模块文件 （这是非常有用测试 cmdlet 时），作为直接包含的 cmdlet 类的程序集，或者可以创建引用 cmdlet 程序集的模块清单。 （您还可以添加现有管理单元中程序集时使用的模块。）有关模块的详细信息，请参阅[编写 Windows PowerShell 模块](../module/writing-a-windows-powershell-module.md)。

## <a name="see-also"></a>另请参阅

[强烈建议的开发指导原则](./strongly-encouraged-development-guidelines.md)

[咨询开发指导原则](./advisory-development-guidelines.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
