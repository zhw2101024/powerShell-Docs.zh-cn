---
title: Windows PowerShell 参考-新增功能
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 364d081ddf2f87ceeaa47732266a35f4a126246f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080520"
---
# <a name="whats-new"></a>新增功能

Windows PowerShell 2.0 编写 cmdlet、 提供商和主机应用程序时，用于提供了以下新功能。

## <a name="modules"></a>模块

你现在可以打包和分发 Windows PowerShell 解决方案通过使用模块。 模块可以分区、 组织和抽象化成独立的、 可重用单元的 Windows PowerShell 代码。 有关模块的详细信息，请参阅编写 Windows PowerShell 模块。

## <a name="the-powershell-class"></a>PowerShell 类

PowerShell 类提供了用于创建应用程序，称为主机应用程序，以编程方式运行命令的更简单的解决方案。 此类可以创建命令的管道，指定用于运行命令，该运行空间并指定以同步方式还是以异步方式调用命令。

## <a name="the-runspacepool-class"></a>RunspacePool 类

运行空间池，可使用一次调用创建多个运行空间。 CreateRunspacePool 方法提供了多个重载，可用于创建具有相同的功能，例如相同的主机、 初始会话状态和连接信息的运行空间。

## <a name="the-initialsessionstate-class"></a>InitialSessionState 类

InitialSessionState 类可以创建一个运行空间打开时使用的会话状态配置。 您可以创建自定义配置、 包含 mshshort，提供的命令的默认配置和配置的命令是受限制的基于会话的功能。

## <a name="remote-runspaces"></a>远程运行空间

现在可以创建运行空间可打开远程计算机上，从而可以在远程计算机上运行命令和收集本地结果。 若要创建远程运行空间，必须创建运行空间时指定的远程连接有关的信息。 请参阅有关示例的 CreateRunspace 和 CreateRunspacePool 方法。 由 RunspaceConnectionInfo 类定义的连接信息。

## <a name="private-runspace-elements"></a>专用的运行空间元素

现在可以创建其元素是公共或专用的运行空间。 这样，您可以创建它的元素可用于运行空间，但不是会向用户提供的运行空间。 请参阅 ConstrainedSessionStateEntry 类，以找出该运行空间的哪些元素可以设为专用。

## <a name="runspace-threading-modes-and-apartment-state"></a>线程处理模式和单元状态的运行空间

现在，您可以指定如何创建和运行空间中运行命令时，使用线程。 请参阅 System.Management.Automation.Runspaces.Runspace.ThreadOptions 和 System.Management.Automation.Runspaces.RunspacePool.ThreadOptions 属性。

现在可以获取用于运行命令的运行空间中的线程的单元状态。 请参阅 System.Management.Automation.Runspaces.Runspace.ApartmentState 和 System.Management.Automation.Runspaces.RunspacePool.ApartmentState 属性。

## <a name="transaction-cmdlets"></a>事务 cmdlet

现在可以创建可以在一个事务内使用的 cmdlet。 当在事务中使用的 cmdlet 时，其操作是临时的它们可以接受或拒绝通过 Windows PowerShell 提供的事务 cmdlet。

有关事务的详细信息，请参阅如何支持事务。

## <a name="transaction-provider"></a>事务提供程序

现在可以创建可以在一个事务内使用的提供程序。 类似于 cmdlet，在事务中使用一个提供程序时，其操作是临时的它们可以接受或拒绝通过 Windows PowerShell 提供的事务 cmdlet。

有关指定的提供程序类中的事务支持的详细信息，请参阅 System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities 属性。

## <a name="job-cmdlets"></a>作业 cmdlet

现在可以编写可以执行其操作作为作业的 cmdlet。 不与当前会话进行交互的情况下在后台运行这些作业。 有关 Windows PowerShell 如何支持作业的详细信息，请参阅后台作业。

## <a name="cmdlet-output-types"></a>Cmdlet 的输出类型

现在可以指定.NET Framework 类型通过时编写 cmdlet 声明 OutputType 属性返回的 cmdlet。 这将允许其他人来确定哪种类型的对象由 cmdlet 返回通过查看 cmdlet 的 OutputType 属性。

## <a name="event-support"></a>事件支持

现在可以编写添加和使用事件的 cmdlet。 请参阅 PSEvent 类。

## <a name="proxy-commands"></a>代理的命令

现在可以编写可用于运行另一个命令中的代理命令。 Proxy 命令允许你控制向用户提供了哪些功能的源 cmdlet。 例如，可以创建代理命令移除参数提供的源命令。 请参阅 ProxyCommand 类。

## <a name="multiple-choice-prompts"></a>多个选择提示

现在可以编写的应用程序可以提供允许用户选择多个选项的提示。 请参阅 IHostUISupportsMultipleChoiceSelection 接口

## <a name="interactive-sessions"></a>交互式会话

现在可以编写的应用程序可以启动和停止交互式会话的远程计算机上。
请参阅 IHostSupportsInteractiveSession 接口。

## <a name="custom-cmdlet-help-for-providers"></a>提供程序的自定义 Cmdlet 帮助

现在可以创建自定义提供程序 cmdlet 的帮助主题。 自定义 cmdlet 帮助主题可解释 cmdlet 中的提供程序路径和文档特殊功能，包括提供程序添加到 cmdlet 的动态参数的工作方式。
