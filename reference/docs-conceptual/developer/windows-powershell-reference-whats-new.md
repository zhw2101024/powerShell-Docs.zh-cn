---
title: Windows PowerShell 参考-新增功能
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 364d081ddf2f87ceeaa47732266a35f4a126246f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366086"
---
# <a name="whats-new"></a>新增功能

Windows PowerShell 2.0 提供了以下新功能，可在编写 cmdlet、提供程序和主机应用程序时使用。

## <a name="modules"></a>模块

你现在可以使用模块打包和分发 Windows PowerShell 解决方案。 使用模块，可以将 Windows PowerShell 代码分区、组织和抽象到独立的可重用单元。 有关模块的详细信息，请参阅编写 Windows PowerShell 模块。

## <a name="the-powershell-class"></a>PowerShell 类

PowerShell 类提供更简单的解决方案来创建应用程序（称为宿主应用程序），以编程方式运行命令。 此类允许创建命令管道，指定用于运行命令的运行空间，并指定同步或异步调用命令。

## <a name="the-runspacepool-class"></a>RunspacePool 类

运行空间池允许使用单个调用创建多个运行空间。 CreateRunspacePool 方法提供多个重载，可用于创建具有相同功能的运行空间，例如相同的主机、初始会话状态和连接信息。

## <a name="the-initialsessionstate-class"></a>InitialSessionState 类

InitialSessionState 类允许你创建在打开运行空间时使用的会话状态配置。 你可以创建自定义配置、包含 mshshort 提供的命令的默认配置，以及基于会话功能限制其命令的配置。

## <a name="remote-runspaces"></a>远程运行空间

你现在可以创建可在远程计算机上打开的运行空间，使你能够在远程计算机上运行命令并在本地收集结果。 若要创建远程运行空间，必须在创建运行空间时指定有关远程连接的信息。 有关示例，请参阅 CreateRunspace 和 CreateRunspacePool 方法。 连接信息由 RunspaceConnectionInfo 类定义。

## <a name="private-runspace-elements"></a>专用运行空间元素

你现在可以创建其元素为公用或专用的运行空间。 这样，你便可以创建其元素可用于运行空间的运行空间，但不能供用户使用。 请参阅 ConstrainedSessionStateEntry 类，了解可以将运行空间的哪些元素设为私有。

## <a name="runspace-threading-modes-and-apartment-state"></a>运行空间线程模式和单元状态

你现在可以指定在运行空间中运行命令时如何创建和使用线程。 请参阅 ThreadOptions 和 RunspacePool。 ThreadOptions 属性（& e）：和属性。

你现在可以获取用于在运行空间中运行命令的线程的单元状态。 请参阅 System.threading.thread.apartmentstate 和 RunspacePool。 System.threading.thread.apartmentstate 属性（& e）：和属性。

## <a name="transaction-cmdlets"></a>事务 cmdlet

你现在可以创建可在事务中使用的 cmdlet。 当在事务中使用 cmdlet 时，其操作是临时的，并且可以由 Windows PowerShell 提供的事务 cmdlet 接受或拒绝。

有关事务的详细信息，请参阅如何支持事务。

## <a name="transaction-provider"></a>事务提供程序

你现在可以创建可在事务中使用的提供程序。 与 cmdlet 类似，当在事务中使用提供程序时，其操作是临时的，并且可以由 Windows PowerShell 提供的事务 cmdlet 接受或拒绝。

有关在提供程序类中指定对事务的支持的详细信息，请参阅 CmdletProviderAttribute. ProviderCapabilities 属性。

## <a name="job-cmdlets"></a>作业 cmdlet

你现在可以编写可执行其操作的 cmdlet 作为作业。 这些作业在后台运行，而不与当前会话交互。 有关 Windows PowerShell 如何支持作业的详细信息，请参阅后台作业。

## <a name="cmdlet-output-types"></a>Cmdlet 输出类型

你现在可以通过在编写 cmdlet 时声明 OutputType 属性来指定 cmdlet 返回的 .NET Framework 类型。 这将允许其他人通过查看 cmdlet 的 OutputType 属性来确定 cmdlet 返回哪种类型的对象。

## <a name="event-support"></a>事件支持

你现在可以编写添加和使用事件的 cmdlet。 请参阅 PSEvent 类。

## <a name="proxy-commands"></a>代理命令

你现在可以编写可用于运行另一个命令的代理命令。 使用代理命令可以控制源 cmdlet 的哪些功能可供用户使用。 例如，你可以创建一个代理命令，该命令删除 source 命令提供的参数。 请参阅 ProxyCommand 类。

## <a name="multiple-choice-prompts"></a>多个选择提示

你现在可以编写可提供允许用户选择多个选项的提示的应用程序。 请参阅 IHostUISupportsMultipleChoiceSelection 接口

## <a name="interactive-sessions"></a>交互式会话

你现在可以编写能够在远程计算机上启动和停止交互式会话的应用程序。
请参阅 IHostSupportsInteractiveSession 接口。

## <a name="custom-cmdlet-help-for-providers"></a>提供程序的自定义 Cmdlet 帮助

你现在可以为提供程序 cmdlet 创建自定义帮助主题。 自定义 cmdlet 帮助主题可以说明 cmdlet 在提供程序路径中的工作原理和文档特殊功能，包括提供程序添加到 cmdlet 的动态参数。
