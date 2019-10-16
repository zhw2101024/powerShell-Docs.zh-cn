---
title: Cmdlet 输出的类型 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], output
ms.assetid: 547e6695-e936-4cac-a90b-417d0dab393d
caps.latest.revision: 12
ms.openlocfilehash: 3efa98c7aa22fdaee8042bae99282aea0618ef5f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369286"
---
# <a name="types-of-cmdlet-output"></a>Cmdlet 输出的类型

PowerShell 提供多种方法，这些方法可由 cmdlet 调用以生成输出。 这些方法使用特定操作将其输出写入特定数据流，如成功数据流或错误数据流。 本文介绍输出类型以及用于生成它们的方法。

## <a name="types-of-output"></a>输出类型

### <a name="success-output"></a>成功输出

Cmdlet 可以通过返回可由管道中的下一个命令处理的对象来报告成功。 Cmdlet 成功执行了其操作后，该 cmdlet 将调用[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法。 我们建议你调用此方法，而不是调用[PSHostUserInterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine)方法或[方法的方法](/dotnet/api/System.Console.WriteLine)。

你可以为不返回对象的 cmdlet 提供**PassThru**交换机参数。
当在命令行中指定**PassThru**交换机参数时，系统将要求 cmdlet 返回对象。 有关具有**PassThru**参数的 cmdlet 的示例，请参阅[添加-历史记录](/powershell/module/Microsoft.PowerShell.Core/Add-History)。

### <a name="error-output"></a>错误输出

Cmdlet 可以报告错误。 当发生终止错误时，cmdlet 会引发异常。 当发生非终止错误时，该 cmdlet 将调用[CmdletProvider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError)方法，将错误记录发送到错误数据流。 有关错误报告的详细信息，请参阅[错误报告概念](./error-reporting-concepts.md)。

### <a name="verbose-output"></a>详细输出

Cmdlet 可以通过调用[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法正确地处理记录，为你提供有用的信息。 方法会生成详细消息，指示操作的执行方式。

默认情况下，不显示详细消息。 可以在运行 cmdlet 时指定**详细**参数，以显示这些消息。 **详细**是适用于所有 cmdlet 的通用参数。

### <a name="progress-output"></a>进度输出

当 cmdlet 执行需要很长时间才能完成的任务（例如，递归复制目录）时，cmdlet 可为你提供进度信息。 若要显示进度信息，cmdlet 将调用[WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)方法。

### <a name="debug-output"></a>调试输出

Cmdlet 可以提供调试消息，这些消息对 cmdlet 代码进行疑难解答时非常有用。 若要显示调试信息，该 cmdlet 将调用[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法。

默认情况下，不显示调试消息。 可以在运行 cmdlet 时指定**Debug**参数以显示这些消息。 **Debug**是适用于所有 cmdlet 的通用参数。

### <a name="warning-output"></a>警告输出

Cmdlet 可以通过调用[WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法来显示警告消息。

默认情况下，会显示警告消息。 但是，你可以通过使用 `$WarningPreference` 变量或在调用 cmdlet 时使用**Verbose**和**Debug**参数来配置警告消息。

## <a name="displaying-output"></a>显示输出

对于所有写方法调用，内容显示由特定的运行时变量确定。 [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法是异常的例外情况。 通过使用这些变量，你可以在代码中的正确位置进行适当的写入调用，而无需担心是否应显示输出。

## <a name="accessing-the-output-functionality-of-a-host-application"></a>访问主机应用程序的输出功能

你还可以设计 cmdlet，以通过 PowerShell 运行时直接访问主机应用程序的输出功能。 使用 PowerShell 提供的宿主 Api，而不是使用[system. 控制台](/dotnet/api/System.Console)或[System.web。窗体](/dotnet/api/System.Windows.Forms)可确保你的 cmdlet 可与各种主机一起使用。 例如： **ngen.exe**控制台主机、 **powershell_ise**图形主机、powershell 远程处理主机和第三方主机。

## <a name="see-also"></a>另请参阅

[错误报告概念](./error-reporting-concepts.md)

[Cmdlet 概述](./cmdlet-overview.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)