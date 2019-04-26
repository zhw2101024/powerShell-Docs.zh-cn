---
title: 类型的 Cmdlet 的输出 |Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067208"
---
# <a name="types-of-cmdlet-output"></a>类型的 cmdlet 的输出

PowerShell 提供了几种方法可以调用的 cmdlet 以生成输出。 这些方法使用特定操作将其输出写入到特定的数据流，如数据流的成功或错误数据流。 本指南介绍了类型的输出和用于生成它们的方法。

## <a name="types-of-output"></a>类型的输出

### <a name="success-output"></a>成功输出

Cmdlet 返回一个对象，可以由管道中的下一个命令处理，可报告成功。 该 cmdlet 成功执行其操作后，该 cmdlet 会调用[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法。 我们建议您调用此方法，而不是[System.Console.WriteLine](/dotnet/api/System.Console.WriteLine)或[System.Management.Automation.Host.PSHostUserInterface.WriteLine](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine)方法。

你可以提供**PassThru**切换通常不会返回对象的 cmdlet 的参数。
当**PassThru**在命令行指定开关参数，则该 cmdlet 需要返回的对象。 有关具有 cmdlet 的示例**PassThru**参数，请参阅[Add-history](/powershell/module/Microsoft.PowerShell.Core/Add-History)。

### <a name="error-output"></a>错误输出

Cmdlet 会报告的错误。 发生终止错误时，该 cmdlet 将引发异常。 发生非终止错误时，该 cmdlet 将调用[System.Management.Automation.Provider.CmdletProvider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError)方法以将错误记录发送到错误数据流。 有关错误报告的详细信息，请参阅[错误报告概念](./error-reporting-concepts.md)。

### <a name="verbose-output"></a>详细输出

Cmdlet 可以提供有用信息对您在该 cmdlet 正在正确处理记录时通过调用[System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法。 此方法将生成详细消息，指示如何继续下一步操作。

默认情况下不显示详细消息。 您可以指定**Verbose**参数时运行该 cmdlet 来显示这些邮件。 **详细**是一个常见的参数，可供所有 cmdlet。

### <a name="progress-output"></a>进度输出

该 cmdlet 执行任务要花很长时间才能完成，如将目录以递归方式复制时，Cmdlet 可以向您提供进度信息。 若要显示进度信息 cmdlet 调用[System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)方法。

### <a name="debug-output"></a>调试输出

Cmdlet 可以提供故障排除的 cmdlet 代码时很有用的调试消息。 若要显示调试信息的 cmdlet 调用[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法。

默认情况下不显示调试消息。 您可以指定**调试**参数时运行该 cmdlet 来显示这些邮件。 **调试**是一个常见的参数，可供所有 cmdlet。

### <a name="warning-output"></a>警告输出

Cmdlet 可显示警告消息，通过调用[System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法。

默认情况下，会显示警告消息。 但是，可以通过配置警告消息`$WarningPreference`变量或通过使用**Verbose**并**调试**时调用该 cmdlet 的参数。

## <a name="displaying-output"></a>显示输出

对于所有写入方法调用，由特定的运行时变量确定显示内容。 例外情况是[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法。 通过使用这些变量，可以进行适当的在代码中编写正确的位置的调用，而不用担心，或者如果应显示的输出。

## <a name="accessing-the-output-functionality-of-a-host-application"></a>访问主机应用程序的输出功能

此外可以设计用于直接通过 PowerShell 运行时访问主机应用程序的输出功能的 cmdlet。 使用主机提供的 PowerShell 而不是 Api [System.Console](/dotnet/api/System.Console)或[System.Windows.Forms](/dotnet/api/System.Windows.Forms)可确保你的 cmdlet 将使用不同主机。 例如： **powershell.exe**控制台主机**powershell_ise.exe**图形主机、 PowerShell 远程处理主机和第三方主机。

## <a name="see-also"></a>另请参阅

[错误报告概念](./error-reporting-concepts.md)

[Cmdlet 概述](./cmdlet-overview.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)