---
title: 运行空间示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c92a6d3d-8d34-4a76-bdc3-dea923d9858e
caps.latest.revision: 17
ms.openlocfilehash: e24d40746da91f60aaf2af655ddcadc88ab6a4db
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360996"
---
# <a name="runspace-samples"></a>运行空间示例

本部分包含的示例代码演示如何使用不同类型的运行空间以同步和异步方式运行命令。 你可以使用 Microsoft Visual Studio 来创建控制台应用程序，然后将此部分中的主题中的代码复制到主机应用程序中。

## <a name="in-this-section"></a>本部分内容

> [!NOTE]
> 有关创建自定义宿主接口的主机应用程序的示例，请参阅[自定义主机示例](./custom-host-samples.md)。

 [Runspace01 示例](./runspace01-sample.md)此示例演示如何使用[system.exception 类同步](/dotnet/api/system.management.automation.powershell)运行[获取进程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)cmdlet，并在控制台窗口中显示其输出。

 [Runspace02 示例](./runspace02-sample.md)此示例演示如何使用[system.exception 类来](/dotnet/api/system.management.automation.powershell)同步运行[获取进程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)和[排序对象](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object)的 cmdlet。 这些命令的结果使用 " [system.web](/dotnet/api/System.Windows.Forms.DataGridView) " 控件显示。

 [Runspace03 示例](./runspace03-sample.md)此示例演示如何使用[system.web](/dotnet/api/system.management.automation.powershell)类来同步运行脚本，以及如何处理非终止错误的操作。 该脚本可接收一系列进程名称，然后检索这些进程。 脚本的结果（包括运行脚本时生成的非终止错误）显示在控制台窗口中。

 [Runspace04 示例](./runspace04-sample.md)此示例演示如何使用[system.web](/dotnet/api/system.management.automation.powershell)类来运行命令，以及如何捕获运行命令时引发的终止错误。 运行了两个命令，最后一个命令传递给了一个无效的参数。 因此，将不返回任何对象，并引发终止错误。

 [Runspace05 示例](./runspace05-sample.md)此示例演示如何将管理单元添加到[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象，以便打开运行空间时，管理单元的 cmdlet 可用于该管理单元。 该管理单元提供了一个通过使用[GetProcessSample01 示例](../cmdlet/getprocesssample01-sample.md)同步运行的获取处理器 cmdlet （由该示例定义[）。](/dotnet/api/system.management.automation.powershell)

 [Runspace06 示例](./runspace06-sample.md)此示例演示如何将模块添加到[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象中，以便在打开运行空间时加载该模块。 该模块提供了一个使用[GetProcessSample02](../cmdlet/getprocesssample02-sample.md)的 cmdlet，该 cmdlet 使用一个[系统管理](/dotnet/api/system.management.automation.powershell)对象进行同步运行。

 [Runspace07 示例](./runspace07-sample.md)此示例演示如何创建一个运行空间，然后使用该运行空间通过[使用一个以](/dotnet/api/system.management.automation.powershell)同步方式运行两个 cmdlet。

 [Runspace08 示例](./runspace08-sample.md)此示例演示如何将命令和参数添加到[system.web](/dotnet/api/system.management.automation.powershell)对象的管道，以及如何以同步方式运行命令。

 [Runspace09 示例](./runspace09-sample.md)此示例演示如何将脚本添加到[system.web](/dotnet/api/system.management.automation.powershell)对象的管道，以及如何以异步方式运行脚本。 使用事件处理脚本的输出。

 [Runspace10 示例](./runspace10-sample.md)此示例演示如何创建默认初始会话状态，如何将 cmdlet 添加到[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)，如何创建使用初始会话状态的运行空间，以及如何通过使用[system.exception 对象运行](/dotnet/api/system.management.automation.powershell)该命令，请执行以下操作：方法。

 [Runspace11 示例](./runspace11-sample.md)这说明了如何使用[Proxycommand](/dotnet/api/System.Management.Automation.ProxyCommand)类来创建一个代理命令，该命令将调用现有的 cmdlet，但会限制可用参数的集合。 然后，代理命令被添加到用来创建受限运行空间的初始会话状态。 这意味着用户只能通过该代理命令使用该 cmdlet 的功能。

## <a name="see-also"></a>另请参阅
