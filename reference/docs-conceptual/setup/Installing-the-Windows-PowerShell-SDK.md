---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 安装 Windows PowerShell SDK
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: fa876bac0c1afac24f93d11dd2e7ecfb1165cf5f
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893532"
---
# <a name="installing-the-windows-powershell-sdk"></a>安装 Windows PowerShell SDK

以下主题介绍了如何在不同版本的 Windows 中安装 PowerShell SDK。

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>安装用于 Windows 8 和 Windows Server 2012 的 Windows PowerShell 3.0 SDK

Windows PowerShell 3.0 随 Windows 8 和 Windows Server 2012 自动安装。
此外，可以下载并安装 Windows PowerShell 3.0 的引用程序集作为 Windows 8 SDK 的一部分。
你可以使用这些程序集为 Windows PowerShell 3.0 编写 cmdlet、提供商和主机程序。
在 Windows 8 中安装 Windows SDK 时，将在引用程序集文件夹（位于 `\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0`）中自动安装 Windows PowerShell 程序集。
有关详细信息，请参阅 [Windows 8 SDK 下载站点](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive)。
此开发中心还提供了 Windows PowerShell 的代码示例。
有关详细信息，请参阅[开发人员中心站点](https://code.msdn.microsoft.com:443/windowsdesktop/)上的桌面代码示例页。

此外，Windows PowerShell 3.0 与 Windows PowerShell 2.0 SDK 是向后兼容，后者包括大量代码示例。
有关如何下载 Windows PowerShell 2.0 SDK 的详细信息，请参阅后文。
（请注意，虽然 2.0 代码示例与 Windows 8 和 Windows PowerShell 3.0 兼容，但不能在 Windows 8 平台上安装 Windows PowerShell 2.0。）

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>安装用于 Windows 7 和 Windows Server 2008 R2 的 Windows PowerShell 3.0 SDK

Windows 7 和 Windows Server 2008 R2 将自动安装 PowerShell 2.0。
此外，你还可以在这些系统上安装 PowerShell 3.0。
（有关详细信息，请参阅[安装 Windows PowerShell](Installing-Windows-PowerShell.md)。）。
如上所述，你还可以在 Windows 7 和 Windows Server 2008 R2 中安装 Windows 8 SDK。

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>安装用于 Windows 7、Vista、XP、Server 2003 和 Server 2008 的 Windows PowerShell 2.0 SDK

Windows PowerShell 2.0 SDK 提供了用于编写 cmdlet、提供程序和托管应用程序所需的引用程序集，还提供了 C# 示例代码，开始编写代码时你可以使用此示例代码作为起点。

若要安装此 SDK，请参阅 [Windows PowerShell 2.0 SDK](http://www.microsoft.com/en-us/download/details.aspx?id=2560)。

## <a name="reference-assemblies"></a>引用程序集

默认情况下，引用程序集安装在以下位置：`c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`。

> [!NOTE] 
> 无法将针对 Windows PowerShell 2.0 程序集编译的代码加载到 Windows PowerShell 1.0 安装中。
> 但可以将针对 Windows PowerShell 1.0 程序集编译的代码加载到 Windows PowerShell 2.0 安装中。

## <a name="samples"></a>示例

默认情况下，代码示例安装在以下位置：`C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`。

以下部分提供对每个示例的作用的简要描述。

## <a name="cmdlet-samples"></a>Cmdlet 示例

### <a name="getprocesssample01"></a>GetProcessSample01

演示如何编写获取本地计算机上所有进程的简单 cmdlet。

### <a name="getprocesssample02"></a>GetProcessSample02

演示如何将参数添加到 cmdlet。
cmdlet 可接受一个或多个进程名称，并返回匹配的进程。

### <a name="getprocesssample03"></a>GetProcessSample03

演示如何添加接受来自管道的输入的参数。

### <a name="getprocesssample04"></a>GetProcessSample04

演示如何处理非终止错误。

### <a name="getprocesssample05"></a>GetProcessSample05

演示如何显示指定进程的列表。

### <a name="selectobject"></a>SelectObject

演示如何编写筛选器以仅选择特定对象。

### <a name="selectstring"></a>SelectString

演示如何搜索指定模式的文件。

### <a name="stopprocesssample01"></a>StopProcessSample01

演示如何实现 *PassThru* 参数，以及如何通过对 [ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess) 和 [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue) 方法的调用请求用户反馈。
当用户要强制 cmdlet 返回对象时，应指定 *PassThru* 参数，

### <a name="stopprocesssample02"></a>StopProcessSample02

演示如何停止特定进程。

### <a name="stopprocesssample03"></a>StopProcessSample03

演示如何声明参数的别名以及如何支持通配符。

### <a name="stopprocesssample04"></a>StopProcessSample04

演示如何声明参数集（即 cmdlet 将其作为输入的对象）以及如何指定要使用的默认参数集。

## <a name="remoting-samples"></a>远程示例

### <a name="remoterunspace01"></a>RemoteRunspace01

演示如何创建用于建立远程连接的远程运行空间。

### <a name="remoterunspacepool01"></a>RemoteRunspacePool01

演示如何构造远程运行空间池以及如何通过使用此池同时运行多个命令。

### <a name="serialization01"></a>Serialization01

演示如何查看现有 .NET 类，并确保跨序列化/反序列化保存此类的所选公共属性中的信息。

### <a name="serialization02"></a>Serialization02

演示如何查看现有.NET 类，并确保当信息在类的公共属性中不可用时，跨序列化/反序列化保存此类的实例中的信息。

### <a name="serialization03"></a>Serialization03

演示如何查看现有 .NET 类，并确保将此类和派生类的实例反序列化（解除冻结）为实时 .NET 对象。

## <a name="event-samples"></a>事件示例

### <a name="event01"></a>Event01

演示如何通过从 ObjectEventRegistrationBase 派生创建用于事件注册的 cmdlet。

### <a name="event02"></a>Event02

演示如何接收在远程计算机上生成的 Windows PowerShell 事件的通知。
它使用通过 [Runspace](/dotnet/api/system.management.automation.runspaces.runspace) 类公开的 PSEventReceived 事件。

## <a name="hosting-application-samples"></a>托管应用程序示例

### <a name="runspace01"></a>Runspace01

演示如何使用 [PowerShell](/dotnet/api/system.management.automation.powershell) 类来同步运行 [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet。
[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet 返回在本地计算机上运行的每个进程的 [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) 对象。

### <a name="runspace02"></a>Runspace02

演示如何使用 [PowerShell](/dotnet/api/system.management.automation.powershell) 类来同步运行 [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) 和 [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlet。
[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet 返回在本地计算机上运行的每个进程的 [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) 对象，而 `Sort-Object` 基于这些对象的 [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) 属性对其进行排序。
使用 [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) 控件显示这些命令的结果。

### <a name="runspace03"></a>Runspace03

演示如何使用 [PowerShell](/dotnet/api/system.management.automation.powershell) 类来同步运行脚本，以及如何处理非终止错误。
该脚本可接收一系列进程名称，然后检索这些进程。
脚本的结果（包括运行脚本时生成的非终止错误）显示在控制台窗口中。

### <a name="runspace04"></a>Runspace04

演示如何使用 [PowerShell](/dotnet/api/system.management.automation.powershell) 类来运行命令，以及如何捕获运行命令时引发的终止错误。
运行了两个命令，最后一个命令传递给了一个无效的参数。
因此，未返回对象并引发了终止错误。

### <a name="runspace05"></a>Runspace05

演示如何将管理单元添加到 [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) 对象，使该管理单元的 cmdlet 在运行空间打开时可用。
管理单元提供通过使用 [PowerShell](/dotnet/api/system.management.automation.powershell) 对象同步运行的 Get-Proc cmdlet（由 [GetProcessSample01 Sample](https://technet.microsoft.com/library/ff602028.aspx) 定义）。

### <a name="runspace06"></a>Runspace06

演示如何将模块添加到 [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) 对象，以便在打开运行空间时加载此模块。
模块提供 Get-Proc cmdlet（由 [GetProcessSample02 Sample](https://technet.microsoft.com/library/ff602027.aspx) 定义），此 cmdlet 通过使用 [PowerShell](/dotnet/api/system.management.automation.powershell) 对象同步运行。

### <a name="runspace07"></a>Runspace07

演示如何通过使用 [PowerShell](/dotnet/api/system.management.automation.powershell) 对象，创建运行空间，然后使用此运行空间同步运行两个 cmdlet。

### <a name="runspace08"></a>Runspace08

演示如何将命令和参数添加到 [PowerShell](/dotnet/api/system.management.automation.powershell) 对象的管道，以及如何同步运行命令。

### <a name="runspace09"></a>Runspace09

演示如何将脚本添加到 [PowerShell](/dotnet/api/system.management.automation.powershell) 对象的管道以及如何异步运行脚本。
使用事件处理脚本的输出。

### <a name="runspace10"></a>Runspace10

演示如何创建默认初始会话状态、如何将 cmdlet 添加到 [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate)、如何创建使用初始会话状态的运行空间以及如何使用 [PowerShell](/dotnet/api/system.management.automation.powershell) 对象运行命令。

### <a name="runspace11"></a>Runspace11

演示如何使用 [ProxyCommand](/dotnet/api/system.management.automation.proxycommand) 类创建调用现有 cmdlet 但限制可用参数集的代理命令。
然后，代理命令被添加到用来创建受限运行空间的初始会话状态。
这意味着用户只能通过该代理命令使用该 cmdlet 的功能。

### <a name="powershell01"></a>PowerShell01

演示如何使用 [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) 对象创建受约束的运行空间。

### <a name="powershell02"></a>PowerShell02

演示如何使用运行空间池同时运行多个命令。

## <a name="host-samples"></a>主机示例

### <a name="host01"></a>Host01

演示如何实现使用自定义主机的主机应用程序。
在此示例中，创建使用自定义主机的运行空间，然后 [PowerShell](/dotnet/api/system.management.automation.powershell) API 用于运行调用“exit”的脚本。
主机应用程序随后查看脚本输出并打印出结果。

### <a name="host02"></a>Host02

演示如何编写结合使用 Windows PowerShell 运行时与自定义主机实现的主机应用程序。
主机应用程序将主机区域性设置为 German，运行 [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet 并显示结果（使用 pwrsh.exe 可查看这些结果），然后打印出德语形式的当前日期和时间。

### <a name="host03"></a>Host03

演示如何生成基于控制台的交互式主机应用程序，该应用程序可从命令行读取并执行命令，然后将结果显示在控制台中。

### <a name="host04"></a>Host04

演示如何生成基于控制台的交互式主机应用程序，该应用程序可从命令行读取并执行命令，然后将结果显示在控制台中。
此主机应用程序还支持显示允许用户指定多个选项的提示。

### <a name="host05"></a>Host05

演示如何生成基于控制台的交互式主机应用程序，该应用程序可从命令行读取并执行命令，然后将结果显示在控制台中。
此主机应用程序还支持通过使用 [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) 和 [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlet 调用远程计算机。

### <a name="host06"></a>Host06

演示如何生成基于控制台的交互式主机应用程序，该应用程序可从命令行读取并执行命令，然后将结果显示在控制台中。
此外，此示例还使用了 Tokenizer API 来指定用户输入的文本颜色。

## <a name="provider-samples"></a>提供程序示例

### <a name="accessdbprovidersample01"></a>AccessDBProviderSample01

演示如何声明直接派生自 [CmdletProvider](/dotnet/api/system.management.automation.provider.cmdletprovider) 类的提供程序类。
仅出于完整性考虑而在此处包含此项。

### <a name="accessdbprovidersample02"></a>AccessDBProviderSample02

演示如何覆盖 [NewDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.newdrive) 和 [RemoveDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.removedrive) 方法，以支持对 `New-PSDrive` 和 `Remove-PSDrive` cmdlet 的调用。
此示例中的提供程序类派生自 [DriveCmdletProvider](/dotnet/api/system.management.automation.provider.drivecmdletprovider) 类。

### <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

演示如何覆盖 [GetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.getitem) 和 [SetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.setitem) 方法，以支持对 `Get-Item` 和 `Set-Item` cmdlet 的调用。
此示例中的提供程序类派生自 [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) 类。

### <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

演示如何覆盖容器方法，以支持对 `Copy-Item`、`Get-ChildItem`、`New-Item` 和 `Remove-Item` cmdlet 的调用。
当数据存储区包含属于容器的项时，应实现这些方法。
容器是包含公用父项下的子项的组。
此示例中的提供程序类派生自 [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) 类。

### <a name="accessdbprovidersample05"></a>AccessDBProviderSample05

演示如何覆盖容器方法，以支持对 `Move-Item` 和 `Join-Path` cmdlet 的调用。
当用户需要移动容器中的项时，如果数据存储区包含嵌套的容器，则应实现这些方法。
此示例中的提供程序类派生自 [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider)。

### <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

演示如何覆盖内容方法，以支持对 `Clear-Content`、`Get-Content` 和 `Set-Content` cmdlet 的调用。
当用户需要管理数据存储区中的项的内容时，应实现这些方法。
此示例中的提供程序派生自 [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) 类，并实现 [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) 接口。