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
# <a name="whats-new"></a><span data-ttu-id="51bb4-102">新增功能</span><span class="sxs-lookup"><span data-stu-id="51bb4-102">What's New</span></span>

<span data-ttu-id="51bb4-103">Windows PowerShell 2.0 编写 cmdlet、 提供商和主机应用程序时，用于提供了以下新功能。</span><span class="sxs-lookup"><span data-stu-id="51bb4-103">Windows PowerShell 2.0 provides the following new features for use when writing cmdlets, providers, and host applications.</span></span>

## <a name="modules"></a><span data-ttu-id="51bb4-104">模块</span><span class="sxs-lookup"><span data-stu-id="51bb4-104">Modules</span></span>

<span data-ttu-id="51bb4-105">你现在可以打包和分发 Windows PowerShell 解决方案通过使用模块。</span><span class="sxs-lookup"><span data-stu-id="51bb4-105">You can now package and distribute Windows PowerShell solutions by using modules.</span></span> <span data-ttu-id="51bb4-106">模块可以分区、 组织和抽象化成独立的、 可重用单元的 Windows PowerShell 代码。</span><span class="sxs-lookup"><span data-stu-id="51bb4-106">Modules allow you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="51bb4-107">有关模块的详细信息，请参阅编写 Windows PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="51bb4-107">For more information about modules, see Writing a Windows PowerShell Module.</span></span>

## <a name="the-powershell-class"></a><span data-ttu-id="51bb4-108">PowerShell 类</span><span class="sxs-lookup"><span data-stu-id="51bb4-108">The PowerShell class</span></span>

<span data-ttu-id="51bb4-109">PowerShell 类提供了用于创建应用程序，称为主机应用程序，以编程方式运行命令的更简单的解决方案。</span><span class="sxs-lookup"><span data-stu-id="51bb4-109">The PowerShell class provides a simpler solution for creating applications, referred to as host applications, that programmatically run commands.</span></span> <span data-ttu-id="51bb4-110">此类可以创建命令的管道，指定用于运行命令，该运行空间并指定以同步方式还是以异步方式调用命令。</span><span class="sxs-lookup"><span data-stu-id="51bb4-110">This class allows you to create a pipeline of commands, specify the runspace that is used to run the commands, and specify invoking the commands synchronously or asynchronously.</span></span>

## <a name="the-runspacepool-class"></a><span data-ttu-id="51bb4-111">RunspacePool 类</span><span class="sxs-lookup"><span data-stu-id="51bb4-111">The RunspacePool class</span></span>

<span data-ttu-id="51bb4-112">运行空间池，可使用一次调用创建多个运行空间。</span><span class="sxs-lookup"><span data-stu-id="51bb4-112">Runspace pools allow you to create multiple runspaces by using a single call.</span></span> <span data-ttu-id="51bb4-113">CreateRunspacePool 方法提供了多个重载，可用于创建具有相同的功能，例如相同的主机、 初始会话状态和连接信息的运行空间。</span><span class="sxs-lookup"><span data-stu-id="51bb4-113">The CreateRunspacePool method provides several overloads that can be used to create runspaces that have the same features, such as the same host, initial session state, and connection information.</span></span>

## <a name="the-initialsessionstate-class"></a><span data-ttu-id="51bb4-114">InitialSessionState 类</span><span class="sxs-lookup"><span data-stu-id="51bb4-114">The InitialSessionState class</span></span>

<span data-ttu-id="51bb4-115">InitialSessionState 类可以创建一个运行空间打开时使用的会话状态配置。</span><span class="sxs-lookup"><span data-stu-id="51bb4-115">The InitialSessionState class allows you to create a session state configuration that is used when a runspace is opened.</span></span> <span data-ttu-id="51bb4-116">您可以创建自定义配置、 包含 mshshort，提供的命令的默认配置和配置的命令是受限制的基于会话的功能。</span><span class="sxs-lookup"><span data-stu-id="51bb4-116">You can create a custom configuration, a default configuration that includes the commands provided by mshshort, and a configuration whose commands are restricted based on the capabilities of the session.</span></span>

## <a name="remote-runspaces"></a><span data-ttu-id="51bb4-117">远程运行空间</span><span class="sxs-lookup"><span data-stu-id="51bb4-117">Remote runspaces</span></span>

<span data-ttu-id="51bb4-118">现在可以创建运行空间可打开远程计算机上，从而可以在远程计算机上运行命令和收集本地结果。</span><span class="sxs-lookup"><span data-stu-id="51bb4-118">You can now create runspaces that can be opened on remote computers, allowing you to run commands on the remote machine and collect the results locally.</span></span> <span data-ttu-id="51bb4-119">若要创建远程运行空间，必须创建运行空间时指定的远程连接有关的信息。</span><span class="sxs-lookup"><span data-stu-id="51bb4-119">To create a remote runspace, you must specify information about the remote connection when creating the runspace.</span></span> <span data-ttu-id="51bb4-120">请参阅有关示例的 CreateRunspace 和 CreateRunspacePool 方法。</span><span class="sxs-lookup"><span data-stu-id="51bb4-120">See the CreateRunspace and CreateRunspacePool methods for examples.</span></span> <span data-ttu-id="51bb4-121">由 RunspaceConnectionInfo 类定义的连接信息。</span><span class="sxs-lookup"><span data-stu-id="51bb4-121">The connection information is defined by the RunspaceConnectionInfo class.</span></span>

## <a name="private-runspace-elements"></a><span data-ttu-id="51bb4-122">专用的运行空间元素</span><span class="sxs-lookup"><span data-stu-id="51bb4-122">Private runspace elements</span></span>

<span data-ttu-id="51bb4-123">现在可以创建其元素是公共或专用的运行空间。</span><span class="sxs-lookup"><span data-stu-id="51bb4-123">You can now create runspaces whose elements are public or private.</span></span> <span data-ttu-id="51bb4-124">这样，您可以创建它的元素可用于运行空间，但不是会向用户提供的运行空间。</span><span class="sxs-lookup"><span data-stu-id="51bb4-124">This allows you to create runspaces whose elements are available to the runspace, but are not available to the user.</span></span> <span data-ttu-id="51bb4-125">请参阅 ConstrainedSessionStateEntry 类，以找出该运行空间的哪些元素可以设为专用。</span><span class="sxs-lookup"><span data-stu-id="51bb4-125">See the ConstrainedSessionStateEntry class to find out which elements of the runspace can be made private.</span></span>

## <a name="runspace-threading-modes-and-apartment-state"></a><span data-ttu-id="51bb4-126">线程处理模式和单元状态的运行空间</span><span class="sxs-lookup"><span data-stu-id="51bb4-126">Runspace threading modes and apartment state</span></span>

<span data-ttu-id="51bb4-127">现在，您可以指定如何创建和运行空间中运行命令时，使用线程。</span><span class="sxs-lookup"><span data-stu-id="51bb4-127">You can now specify how threads are created and used when running commands in a runspace.</span></span> <span data-ttu-id="51bb4-128">请参阅 System.Management.Automation.Runspaces.Runspace.ThreadOptions 和 System.Management.Automation.Runspaces.RunspacePool.ThreadOptions 属性。</span><span class="sxs-lookup"><span data-stu-id="51bb4-128">See the System.Management.Automation.Runspaces.Runspace.ThreadOptions and System.Management.Automation.Runspaces.RunspacePool.ThreadOptions properties.</span></span>

<span data-ttu-id="51bb4-129">现在可以获取用于运行命令的运行空间中的线程的单元状态。</span><span class="sxs-lookup"><span data-stu-id="51bb4-129">You can now get the apartment state of the threads that are used to run commands in a runspace.</span></span> <span data-ttu-id="51bb4-130">请参阅 System.Management.Automation.Runspaces.Runspace.ApartmentState 和 System.Management.Automation.Runspaces.RunspacePool.ApartmentState 属性。</span><span class="sxs-lookup"><span data-stu-id="51bb4-130">See the System.Management.Automation.Runspaces.Runspace.ApartmentState and System.Management.Automation.Runspaces.RunspacePool.ApartmentState properties.</span></span>

## <a name="transaction-cmdlets"></a><span data-ttu-id="51bb4-131">事务 cmdlet</span><span class="sxs-lookup"><span data-stu-id="51bb4-131">Transaction cmdlets</span></span>

<span data-ttu-id="51bb4-132">现在可以创建可以在一个事务内使用的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="51bb4-132">You can now create cmdlets that can be used within a transaction.</span></span> <span data-ttu-id="51bb4-133">当在事务中使用的 cmdlet 时，其操作是临时的它们可以接受或拒绝通过 Windows PowerShell 提供的事务 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="51bb4-133">When a cmdlet is used in a transaction, its actions are temporary, and they can be accepted or rejected by the transaction cmdlets provided by Windows PowerShell.</span></span>

<span data-ttu-id="51bb4-134">有关事务的详细信息，请参阅如何支持事务。</span><span class="sxs-lookup"><span data-stu-id="51bb4-134">For more information about transactions, see How to Support Transactions.</span></span>

## <a name="transaction-provider"></a><span data-ttu-id="51bb4-135">事务提供程序</span><span class="sxs-lookup"><span data-stu-id="51bb4-135">Transaction provider</span></span>

<span data-ttu-id="51bb4-136">现在可以创建可以在一个事务内使用的提供程序。</span><span class="sxs-lookup"><span data-stu-id="51bb4-136">You can now create providers that can be used within a transaction.</span></span> <span data-ttu-id="51bb4-137">类似于 cmdlet，在事务中使用一个提供程序时，其操作是临时的它们可以接受或拒绝通过 Windows PowerShell 提供的事务 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="51bb4-137">Similar to cmdlets, when a provider is used in a transaction, its actions are temporary, and they can be accepted or rejected by the transaction cmdlets provided by Windows PowerShell.</span></span>

<span data-ttu-id="51bb4-138">有关指定的提供程序类中的事务支持的详细信息，请参阅 System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities 属性。</span><span class="sxs-lookup"><span data-stu-id="51bb4-138">For more information about specifying support for transaction within a provider class, see the System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities property.</span></span>

## <a name="job-cmdlets"></a><span data-ttu-id="51bb4-139">作业 cmdlet</span><span class="sxs-lookup"><span data-stu-id="51bb4-139">Job cmdlets</span></span>

<span data-ttu-id="51bb4-140">现在可以编写可以执行其操作作为作业的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="51bb4-140">You can now write cmdlets that can perform their action as a job.</span></span> <span data-ttu-id="51bb4-141">不与当前会话进行交互的情况下在后台运行这些作业。</span><span class="sxs-lookup"><span data-stu-id="51bb4-141">These jobs are run in the background without interacting with the current session.</span></span> <span data-ttu-id="51bb4-142">有关 Windows PowerShell 如何支持作业的详细信息，请参阅后台作业。</span><span class="sxs-lookup"><span data-stu-id="51bb4-142">For more information about how Windows PowerShell supports jobs, see Background Jobs.</span></span>

## <a name="cmdlet-output-types"></a><span data-ttu-id="51bb4-143">Cmdlet 的输出类型</span><span class="sxs-lookup"><span data-stu-id="51bb4-143">Cmdlet output types</span></span>

<span data-ttu-id="51bb4-144">现在可以指定.NET Framework 类型通过时编写 cmdlet 声明 OutputType 属性返回的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="51bb4-144">You can now specify the .NET Framework types that are returned by your cmdlets by declaring the OutputType attribute when writing your cmdlets.</span></span> <span data-ttu-id="51bb4-145">这将允许其他人来确定哪种类型的对象由 cmdlet 返回通过查看 cmdlet 的 OutputType 属性。</span><span class="sxs-lookup"><span data-stu-id="51bb4-145">This will allow others to determine what type of objects are returned by a cmdlet by looking at the OutputType property of the cmdlet.</span></span>

## <a name="event-support"></a><span data-ttu-id="51bb4-146">事件支持</span><span class="sxs-lookup"><span data-stu-id="51bb4-146">Event support</span></span>

<span data-ttu-id="51bb4-147">现在可以编写添加和使用事件的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="51bb4-147">You can now write cmdlets that add and consume events.</span></span> <span data-ttu-id="51bb4-148">请参阅 PSEvent 类。</span><span class="sxs-lookup"><span data-stu-id="51bb4-148">See the PSEvent class.</span></span>

## <a name="proxy-commands"></a><span data-ttu-id="51bb4-149">代理的命令</span><span class="sxs-lookup"><span data-stu-id="51bb4-149">Proxy commands</span></span>

<span data-ttu-id="51bb4-150">现在可以编写可用于运行另一个命令中的代理命令。</span><span class="sxs-lookup"><span data-stu-id="51bb4-150">You can now write proxy commands that can be used to run another command.</span></span> <span data-ttu-id="51bb4-151">Proxy 命令允许你控制向用户提供了哪些功能的源 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="51bb4-151">A proxy command allows you to control what functionality of the source cmdlet is available to the user.</span></span> <span data-ttu-id="51bb4-152">例如，可以创建代理命令移除参数提供的源命令。</span><span class="sxs-lookup"><span data-stu-id="51bb4-152">For example, you can create a proxy command that removes a parameter that is supplied by the source command.</span></span> <span data-ttu-id="51bb4-153">请参阅 ProxyCommand 类。</span><span class="sxs-lookup"><span data-stu-id="51bb4-153">See the ProxyCommand class.</span></span>

## <a name="multiple-choice-prompts"></a><span data-ttu-id="51bb4-154">多个选择提示</span><span class="sxs-lookup"><span data-stu-id="51bb4-154">Multiple choice prompts</span></span>

<span data-ttu-id="51bb4-155">现在可以编写的应用程序可以提供允许用户选择多个选项的提示。</span><span class="sxs-lookup"><span data-stu-id="51bb4-155">You can now write applications that can provide prompts that allow the user to select multiple choices.</span></span> <span data-ttu-id="51bb4-156">请参阅 IHostUISupportsMultipleChoiceSelection 接口</span><span class="sxs-lookup"><span data-stu-id="51bb4-156">See the IHostUISupportsMultipleChoiceSelection interface</span></span>

## <a name="interactive-sessions"></a><span data-ttu-id="51bb4-157">交互式会话</span><span class="sxs-lookup"><span data-stu-id="51bb4-157">Interactive sessions</span></span>

<span data-ttu-id="51bb4-158">现在可以编写的应用程序可以启动和停止交互式会话的远程计算机上。</span><span class="sxs-lookup"><span data-stu-id="51bb4-158">You can now write applications that can start and stop an interactive session on a remote computer.</span></span>
<span data-ttu-id="51bb4-159">请参阅 IHostSupportsInteractiveSession 接口。</span><span class="sxs-lookup"><span data-stu-id="51bb4-159">See the IHostSupportsInteractiveSession interface.</span></span>

## <a name="custom-cmdlet-help-for-providers"></a><span data-ttu-id="51bb4-160">提供程序的自定义 Cmdlet 帮助</span><span class="sxs-lookup"><span data-stu-id="51bb4-160">Custom Cmdlet Help for Providers</span></span>

<span data-ttu-id="51bb4-161">现在可以创建自定义提供程序 cmdlet 的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="51bb4-161">You can now create customized Help topics for the provider cmdlets.</span></span> <span data-ttu-id="51bb4-162">自定义 cmdlet 帮助主题可解释 cmdlet 中的提供程序路径和文档特殊功能，包括提供程序添加到 cmdlet 的动态参数的工作方式。</span><span class="sxs-lookup"><span data-stu-id="51bb4-162">Custom cmdlet help topics can explain how the cmdlet works in the provider path and document special features, including the dynamic parameters that the provider adds to the cmdlet.</span></span>
