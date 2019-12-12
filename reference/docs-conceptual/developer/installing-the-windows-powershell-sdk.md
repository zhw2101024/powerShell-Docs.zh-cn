---
title: 安装 Windows PowerShell SDK
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: e7ca38377b3e6533eec1a70027f6de1a9fb3091b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "73444499"
---
# <a name="installing-the-windows-powershell-sdk"></a>安装 Windows PowerShell SDK

适用于： Windows PowerShell 2.0、Windows PowerShell 3。0

以下主题介绍了如何在不同版本的 Windows 中安装 PowerShell SDK。

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>安装用于 Windows 8 和 Windows Server 2012 的 Windows PowerShell 3.0 SDK

Windows PowerShell 3.0 随 Windows 8 和 Windows Server 2012 自动安装。 此外，可以下载并安装 Windows PowerShell 3.0 的引用程序集作为 Windows 8 SDK 的一部分。 你可以使用这些程序集为 Windows PowerShell 3.0 编写 cmdlet、提供商和主机程序。 在 Windows 8 中安装 Windows SDK 时，将在引用程序集文件夹（位于 `\Program Files
(x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0`）中自动安装 Windows PowerShell 程序集。 有关详细信息，请参阅 Windows 8 SDK 下载站点。 Windows powershell 代码示例也位于[Windows powershell 3.0 SDK 示例包](https://code.msdn.microsoft.com/Windows-PowerShell-30-SDK-9a34641d)的开发中心。

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>安装用于 Windows 7 和 Windows Server 2008 R2 的 Windows PowerShell 3.0 SDK

Windows 7 和 Windows Server 2008 R2 将自动安装 PowerShell 2.0。 此外，你还可以在这些系统上安装 PowerShell 3.0。 你还可以在 Windows 7 和 Windows Server 2008 R2 上安装 Windows 8 SDK，如上所述。

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>安装用于 Windows 7、Vista、XP、Server 2003 和 Server 2008 的 Windows PowerShell 2.0 SDK

Windows PowerShell 2.0 SDK 提供了用于编写 cmdlet、提供程序和托管应用程序所需的引用程序集，还提供了 C# 示例代码，开始编写代码时你可以使用此示例代码作为起点。 可以从[https://www.microsoft.com/download/details.aspx?id=2560](https://www.microsoft.com/download/details.aspx?id=2560)下载代码示例。

### <a name="reference-assemblies"></a>引用程序集

默认情况下，引用程序集安装在以下位置：`c:\Program Files\Reference
Assemblies\Microsoft\WindowsPowerShell\V1.0`。

> [!NOTE]
>
> 无法将针对 Windows PowerShell 2.0 程序集编译的代码加载到 Windows PowerShell 1.0 安装中。 但可以将针对 Windows PowerShell 1.0 程序集编译的代码加载到 Windows PowerShell 2.0 安装中。


### <a name="samples"></a>示例

默认情况下，代码示例安装在以下位置：`C:\Program Files\Microsoft
SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`。 以下部分提供对每个示例的作用的简要描述。

#### <a name="cmdlet-samples"></a>Cmdlet 示例

- GetProcessSample01-演示如何编写用于获取本地计算机上所有进程的简单 cmdlet。
- GetProcessSample02-演示如何将参数添加到 cmdlet。 cmdlet 可接受一个或多个进程名称，并返回匹配的进程。
- GetProcessSample03-演示如何添加接受管道输入的参数。
- GetProcessSample04-演示如何处理非终止错误。
- GetProcessSample05-演示如何显示指定进程的列表。
- SelectObject-演示如何编写筛选器以仅选择特定的对象。
- SelectString-演示如何在文件中搜索指定的模式。
- StopProcessSample01-演示如何实现 PassThru 参数，以及如何通过调用 ShouldProcess 和 ShouldContinue 方法请求用户反馈。 用户希望强制 cmdlet 返回对象时指定 PassThru 参数。
- StopProcessSample02-演示如何停止特定进程。
- StopProcessSample03-演示如何声明参数的别名以及如何支持通配符。
- StopProcessSample04-演示如何声明参数集、cmdlet 作为输入的对象，以及如何指定要使用的默认参数集。

#### <a name="remoting-samples"></a>远程示例

- RemoteRunspace01-演示如何创建用于建立远程连接的远程运行空间。
- RemoteRunspacePool01-演示如何构建远程运行空间池，以及如何使用此池并发运行多个命令。
- Serialization01-演示如何查看现有 .NET 类，并确保在序列化/反序列化时保留此类的选定公共属性中的信息。
- Serialization02-演示如何查看现有 .NET 类，并确保在类的公共属性中不提供此类的实例中的信息时，在序列化/反序列化时保留该信息。
- Serialization03-演示如何查看现有 .NET 类，并确保此类和派生类的实例反序列化（解除冻结）到实时 .NET 对象。

#### <a name="event-samples"></a>事件示例

- Event01-演示如何通过从 ObjectEventRegistrationBase 派生来创建用于事件注册的 cmdlet。
- Event02-演示如何接收在远程计算机上生成的 Windows PowerShell 事件的通知。 它使用通过运行空间类公开的 PSEventReceived 事件。

#### <a name="hosting-application-samples"></a>托管应用程序示例

- Runspace01-演示如何使用 PowerShell 类同步运行 `Get-Process` cmdlet。
`Get-Process` cmdlet 返回在本地计算机上运行的每个进程的进程对象。
- Runspace02-演示如何使用 PowerShell 类同步运行 `Get-Process` 和 `Sort-Object` cmdlet。 `Get-Process` cmdlet 返回在本地计算机上运行的每个进程的进程对象，而 `Sort-Object` 基于其 Id 属性对对象进行排序。 使用 DataGridView 控件显示这些命令的结果。
- Runspace03-演示如何使用 PowerShell 类同步运行脚本，以及如何处理非终止错误。 该脚本可接收一系列进程名称，然后检索这些进程。 脚本的结果（包括运行脚本时生成的非终止错误）显示在控制台窗口中。
- Runspace04-演示如何使用 PowerShell 类来运行命令，以及如何捕获运行命令时引发的终止错误。 运行了两个命令，最后一个命令传递给了一个无效的参数。 因此，未返回对象并引发了终止错误。
- Runspace05-演示如何将管理单元添加到 InitialSessionState 对象，以便打开运行空间时可以使用管理单元的 cmdlet。 管理单元提供了一个通过使用 PowerShell 对象同步运行的 GetProcessSample01 cmdlet （由 "" 示例定义）。
- Runspace06-演示如何将模块添加到 InitialSessionState 对象，以便在打开运行空间时加载模块。 该模块提供了一个通过使用 PowerShell 对象同步运行的 GetProcessSample02 cmdlet （由 "" 示例定义）。
- Runspace07-演示如何创建运行空间，并使用该运行空间通过 PowerShell 对象同步运行两个 cmdlet。
- Runspace08-演示如何将命令和参数添加到 PowerShell 对象的管道，以及如何同步运行命令。
- Runspace09-演示如何将脚本添加到 PowerShell 对象的管道，以及如何以异步方式运行脚本。 使用事件处理脚本的输出。
- Runspace10-演示如何创建默认初始会话状态，如何将 cmdlet 添加到 InitialSessionState，如何创建使用初始会话状态的运行空间，以及如何使用 PowerShell 对象运行命令。
- Runspace11-演示如何使用 ProxyCommand 类创建调用现有 cmdlet 但限制可用参数集的代理命令。 然后，代理命令被添加到用来创建受限运行空间的初始会话状态。 这意味着用户只能通过该代理命令使用该 cmdlet 的功能。
- PowerShell01-演示如何使用 InitialSessionState 对象创建受限的运行空间。
- PowerShell02-演示如何使用运行空间池并发运行多个命令。

#### <a name="host-samples"></a>主机示例

- Host01-演示如何实现使用自定义主机的主机应用程序。 在此示例中，创建了一个使用自定义主机的运行空间，然后使用 PowerShell API 来运行调用 "exit" 的脚本。 主机应用程序随后查看脚本输出并打印出结果。
- Host02-演示如何编写使用 Windows PowerShell 运行时以及自定义主机实现的主机应用程序。 主机应用程序将主机区域性设置为德语，运行 `Get-Process` cmdlet，并显示使用 pwrsh 时显示的结果，然后输出德语的当前数据和时间。
- Host03-演示如何生成基于控制台的交互式主机应用程序，该应用程序可从命令行读取命令，执行命令，然后将结果显示到控制台。
- Host04-演示如何生成基于控制台的交互式主机应用程序，该应用程序可从命令行读取命令，执行命令，然后将结果显示到控制台。 此主机应用程序还支持显示允许用户指定多个选项的提示。
- Host05-演示如何生成基于控制台的交互式主机应用程序，该应用程序可从命令行读取命令，执行命令，然后将结果显示到控制台。 此主机应用程序还支持通过使用 `Enter-PsSession` 和 `Exit-PsSession` cmdlet 来调用远程计算机。
- Host06-演示如何生成基于控制台的交互式主机应用程序，该应用程序可从命令行读取命令，执行命令，然后将结果显示到控制台。 此外，此示例还使用了 Tokenizer API 来指定用户输入的文本颜色。

#### <a name="provider-samples"></a>提供程序示例

- AccessDBProviderSample01-演示如何声明直接从 CmdletProvider 类派生的提供程序类。 仅出于完整性考虑而在此处包含此项。

- AccessDBProviderSample02-演示如何覆盖 NewDrive 和 RemoveDrive 方法，以支持对 `New-PSDrive` 和 `Remove-PSDrive` cmdlet 的调用。 此示例中的提供程序类派生自 DriveCmdletProvider 类。

- AccessDBProviderSample03-演示如何覆盖 GetItem 和 SetItem 方法，以支持对 `Get-Item` 和 `Set-Item` cmdlet 的调用。 此示例中的提供程序类派生自 ItemCmdletProvider 类。

- AccessDBProviderSample04-演示如何覆盖容器方法以支持对 `Copy-Item`、`Get-ChildItem`、`New-Item`和 `Remove-Item` cmdlet 的调用。 当数据存储区包含属于容器的项时，应实现这些方法。 容器是包含公用父项下的子项的组。 此示例中的提供程序类派生自 ItemCmdletProvider 类。

- AccessDBProviderSample05-演示如何覆盖容器方法以支持对 `Move-Item` 和 `Join-Path` cmdlet 的调用。 当用户需要移动容器中的项时，如果数据存储区包含嵌套的容器，则应实现这些方法。 此示例中的提供程序类派生自 NavigationCmdletProvider 类。

- AccessDBProviderSample06-演示如何覆盖内容方法以支持对 `Clear-Content`、`Get-Content`和 `Set-Content` cmdlet 的调用。 当用户需要管理数据存储区中的项的内容时，应实现这些方法。 此示例中的提供程序类派生自 NavigationCmdletProvider 类，并实现 IContentCmdletProvider 接口。
