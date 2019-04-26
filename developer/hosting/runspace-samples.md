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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082730"
---
# <a name="runspace-samples"></a>运行空间示例

本节包含演示如何使用不同类型的运行空间同步和异步方式运行命令的示例代码。 可以使用 Microsoft Visual Studio 创建控制台应用程序，然后将此部分中的主题从代码复制到主机应用程序。

## <a name="in-this-section"></a>本部分内容

> [!NOTE]
> 有关创建自定义主机接口的托管应用程序的示例，请参阅[自定义主机示例](./custom-host-samples.md)。

 [Runspace01 示例](./runspace01-sample.md)此示例演示如何使用[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)类来运行[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet 以同步方式和在控制台中显示其输出窗口。

 [Runspace02 示例](./runspace02-sample.md)此示例演示如何使用[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)类来运行[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)并[Sort-object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object)cmdlet 以同步方式。 使用显示的这些命令的结果[System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView)控件。

 [Runspace03 示例](./runspace03-sample.md)此示例演示如何使用[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)类来运行脚本以同步方式，以及如何处理非终止性错误。 该脚本可接收一系列进程名称，然后检索这些进程。 脚本的结果（包括运行脚本时生成的非终止错误）显示在控制台窗口中。

 [示例 Runspace04](./runspace04-sample.md)此示例演示如何使用[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)类来运行命令，以及如何捕获运行命令时引发的终止错误。 运行了两个命令，最后一个命令传递给了一个无效的参数。 因此未返回任何对象，并引发一个终止错误。

 [示例 Runspace05](./runspace05-sample.md)此示例演示如何将管理单元添加到[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象，以便当打开运行空间时，管理单元的 cmdlet 才可用。 管理单元提供 Get-proc cmdlet (由[GetProcessSample01 Sample](../cmdlet/getprocesssample01-sample.md)) 运行的是使用同步[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)对象。

 [Runspace06 示例](./runspace06-sample.md)此示例演示如何将添加到模块[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象，以便打开运行空间时加载的模块。 模块提供 Get-proc cmdlet (由[GetProcessSample02 示例](../cmdlet/getprocesssample02-sample.md)) 运行的是使用同步[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)对象。

 [Runspace07 示例](./runspace07-sample.md)此示例演示如何创建运行空间，然后使用该运行空间同步运行两个 cmdlet，通过使用[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)对象。

 [Runspace08 示例](./runspace08-sample.md)此示例演示如何将命令和参数添加到的管道[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)对象以及如何以同步方式运行命令。

 [Runspace09 示例](./runspace09-sample.md)此示例演示如何将脚本添加到的管道[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)对象以及如何以异步方式运行该脚本。 使用事件处理脚本的输出。

 [示例 Runspace10](./runspace10-sample.md)此示例演示如何创建默认初始会话状态，如何将添加到 cmdlet [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)，如何创建使用的运行空间初始会话状态，以及如何通过使用运行命令[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)对象。

 [Runspace11 示例](./runspace11-sample.md)这将显示如何使用[System.Management.Automation.Proxycommand](/dotnet/api/System.Management.Automation.ProxyCommand)类，以创建可调用现有 cmdlet 但限制可用参数集的代理命令。 然后，代理命令被添加到用来创建受限运行空间的初始会话状态。 这意味着用户只能通过该代理命令使用该 cmdlet 的功能。

## <a name="see-also"></a>另请参阅
