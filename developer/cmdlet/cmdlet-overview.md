---
title: Cmdlet 概述 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK]
- cmdlets [PowerShell SDK], described
ms.assetid: 0aa32589-4447-4ead-a5dd-a3be99113140
caps.latest.revision: 21
ms.openlocfilehash: f8a8c9300d1ac811c7fbbf7050dd24f78306db8f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068464"
---
# <a name="cmdlet-overview"></a>Cmdlet 概述

Cmdlet 是 Windows PowerShell 环境中使用的轻型命令。 Windows PowerShell 运行时调用的命令行时提供的自动化脚本上下文中使用这些 cmdlet。 Windows PowerShell 运行时还将调用它们以编程方式通过 Windows PowerShell Api。

## <a name="cmdlets"></a>Cmdlet

Cmdlet 执行操作，并通常将 Microsoft.NET Framework 对象返回到管道中的下一个命令。 若要编写的 cmdlet，必须实现两个专用的 cmdlet 基类，这些类之一派生的 cmdlet 类。 在派生的类必须：

- 声明标识为 cmdlet 的派生的类的属性。

- 定义使用识别为 cmdlet 参数的公共属性的属性修饰的公共属性。

- 重写一个或多个输入处理方法来处理记录。

您可以加载的程序集的直接通过使用包含的类[导入模块](/powershell/module/microsoft.powershell.core/import-module)cmdlet，也可以创建主机应用程序加载程序集使用[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) API。 这两种方法提供对该 cmdlet 的功能的编程和命令行访问。

## <a name="cmdlet-terms"></a>Cmdlet 条款

Windows PowerShell cmdlet 文档中经常使用以下术语：

- **Cmdlet 属性**:.NET Framework 属性，用于声明 cmdlet 类作为一个 cmdlet。 尽管 Windows PowerShell 使用多个其他属性是可选的但 Cmdlet 属性是必需的。 有关此属性的详细信息，请参阅[Cmdlet 特性声明](./cmdlet-attribute-declaration.md)。

- **Cmdlet 参数**:定义可向用户或应用程序运行该 cmdlet 的参数的公共属性。 Cmdlet 可以都没有必需的命名、 位置，并*切换*参数。 开关参数可用于定义在调用中指定了参数时，才会评估的参数。 有关不同类型的参数的详细信息，请参阅[Cmdlet 参数](./cmdlet-parameters.md)。

- **参数集**:可用于相同的命令中以执行特定操作的一组参数。 一个 cmdlet 可以具有多个参数集，但每个参数集必须具有至少一个参数，它是唯一的。 好 cmdlet 设计强烈建议的唯一参数也是必需的参数。 有关参数集的详细信息，请参阅[Cmdlet 参数可设置](./cmdlet-parameter-sets.md)。

- **动态参数**:添加到该 cmdlet 在运行时参数。 通常情况下，动态参数添加到该 cmdlet 时另一个参数设置为特定值。 有关动态参数的详细信息，请参阅[Cmdlet 的动态参数](./cmdlet-dynamic-parameters.md)。

- **输入处理方法**:Cmdlet 可用于处理其以输入形式所接收的记录的一种方法。 输入的处理方法包括[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法， [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法， [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法，并[System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing)方法。 当实现一个 cmdlet 时，您必须重写的至少一个[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)， [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)，并且[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。 通常情况下， [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法是您重写，因为调用 cmdlet 所处理的每条记录的方法。 与此相反， [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法并[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法调用一次来执行预处理或后处理的记录。 有关这些方法的详细信息，请参阅[输入处理方法](./cmdlet-input-processing-methods.md)。

- **ShouldProcess 功能**:Windows PowerShell，可创建该 cmdlet 对系统进行更改之前提示用户提供反馈的 cmdlet。 若要使用此功能，该 cmdlet 必须声明它时声明 Cmdlet 特性和必须调用该 cmdlet 支持 ShouldProcess 功能[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)从输入处理方法中的方法。 有关如何支持 ShouldProcess 功能的详细信息，请参阅[请求确认](./requesting-confirmation-from-cmdlets.md)。

- **事务**:逻辑组将被视为单个任务的命令。 如果组中的任何命令失败，并且用户可以选择接受或拒绝在事务中执行的操作，则任务自动失败。 若要参与事务，该 cmdlet 必须声明其支持事务，在声明 Cmdlet 属性。 在 Windows PowerShell 2.0 中引入了对事务的支持。 有关事务的详细信息，请参阅[Windows PowerShell 事务](http://msdn.microsoft.com/en-us/74d7bac7-bc53-49f1-a47a-272e8da84710)。

## <a name="how-cmdlets-differ-from-commands"></a>与命令 Cmdlet 有何区别

Cmdlet 不同于其他命令行界面环境中的命令通过以下方式：

- Cmdlet 是.NET Framework 类; 的实例它们不是独立的可执行文件。

- Cmdlet 可创建从一样少的代码的若干行。

- Cmdlet 通常执行其自己分析，错误演示文稿或输出格式设置。 通过 Windows PowerShell 运行时处理分析、 错误演示文稿和输出格式设置。

- Cmdlet 处理输入对象通过管道而不是从的文本，流和 cmdlet 通常将作为输出到管道的对象。

- Cmdlet 是面向记录的因为它们一次处理一个对象。

## <a name="cmdlet-base-classes"></a>Cmdlet 基类

Windows PowerShell 支持从以下两个基类派生的 cmdlet。

- 大多数 cmdlet 基于.NET Framework 类派生自[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)基类。 从此类派生允许 cmdlet 在 Windows PowerShell 运行时上使用依赖项的最小集。 这有两个好处。 第一个优点是更小，cmdlet 对象并且不太可能更改 Windows PowerShell 运行时的影响。 第二个好处是，如果有必要，您可以直接创建 cmdlet 对象的实例，然后而通过 Windows PowerShell 运行时调用它不是直接调用它。

- 更复杂 cmdlet 基于.NET Framework 类派生自[System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)基类。 从此类派生可使您更多访问 Windows PowerShell 运行时。 此访问权限允许您 cmdlet 来调用脚本，来访问提供程序，并访问当前会话状态。 （若要访问当前会话状态，获取和设置会话变量和首选项。）但是，从此类派生会增加 cmdlet 对象的大小，这意味着你的 cmdlet 更紧密地耦合到当前版本的 Windows PowerShell 运行时。

一般情况下，除非需要对 Windows PowerShell 运行时的扩展访问权限，否则您应派生自[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)类。 但是，Windows PowerShell 运行时具有 cmdlet 执行的广泛的日志记录的功能。 如果审核模型依赖于此日志记录，则可以禁止你从另一个 cmdlet 中的 cmdlet 执行通过派生自[System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)类。

## <a name="input-processing-methods"></a>输入处理方法

[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)类提供了以下用于处理记录的虚拟方法。 一个或多个的前三个方法，则必须重写所有派生的 cmdlet 类：

- [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing):用于为 cmdlet 提供可选的一次性预处理功能。

- [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord):用于为 cmdlet 提供按记录处理功能。 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)可能调用方法的次数，或根本不，具体取决于该 cmdlet 的输入的任何数字。

- [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing):用于为 cmdlet 提供可选的一次性后处理功能。

- [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing):用于用户异步停止 cmdlet （例如，通过按 CTRL + C） 时停止处理。

有关这些方法的详细信息，请参阅[Cmdlet 输入处理方法](./cmdlet-input-processing-methods.md)。

## <a name="cmdlet-attributes"></a>Cmdlet 属性

Windows PowerShell 会定义用于管理 cmdlet 并指定提供的 Windows PowerShell 和 cmdlet 可能需要的常用功能的多个.NET Framework 属性。 例如，属性用于将类指定 cmdlet，以指定的参数的 cmdlet，并请求的输入验证，以便 cmdlet 开发人员无需在其 cmdlet 代码中实现该功能。 有关属性的详细信息，请参阅[Windows PowerShell 属性](./cmdlet-attributes.md)。

## <a name="cmdlet-names"></a>Cmdlet 名称

Windows PowerShell 使用名称 cmdlet 的动词-名词名称对。 例如，`Get-Command`包含在 Windows PowerShell cmdlet 用于获取在命令行界面中注册的所有 cmdlet。 谓词标识该 cmdlet 将执行，该操作，并 （） 名词，标识该 cmdlet 将在其执行其操作的资源。

.NET Framework 类声明为一个 cmdlet 时指定这些名称。 有关如何声明为 cmdlet 的.NET Framework 类的详细信息，请参阅[Cmdlet 特性声明](./cmdlet-class-declaration.md)。

## <a name="writing-cmdlet-code"></a>编写 Cmdlet 代码

本文档提供了两种方式来了解如何编写 cmdlet 代码。 如果想要查看代码而无需多解释，请参阅[Cmdlet 的示例代码](./examples-of-cmdlet-code.md)。 如果需要有关代码的详细说明，请参阅[GetProc 教程](./getproc-tutorial.md)， [StopProc 教程](./stopproc-tutorial.md)，或[SelectStr 教程](./selectstr-tutorial.md)主题。

有关编写 cmdlet 的准则的详细信息，请参阅[Cmdlet 开发指导原则](./cmdlet-development-guidelines.md)。

## <a name="see-also"></a>另请参阅

[Windows PowerShell Cmdlet 概念](./windows-powershell-cmdlet-concepts.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
