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
# <a name="whats-new"></a><span data-ttu-id="77dfd-102">新增功能</span><span class="sxs-lookup"><span data-stu-id="77dfd-102">What's New</span></span>

<span data-ttu-id="77dfd-103">Windows PowerShell 2.0 提供了以下新功能，可在编写 cmdlet、提供程序和主机应用程序时使用。</span><span class="sxs-lookup"><span data-stu-id="77dfd-103">Windows PowerShell 2.0 provides the following new features for use when writing cmdlets, providers, and host applications.</span></span>

## <a name="modules"></a><span data-ttu-id="77dfd-104">模块</span><span class="sxs-lookup"><span data-stu-id="77dfd-104">Modules</span></span>

<span data-ttu-id="77dfd-105">你现在可以使用模块打包和分发 Windows PowerShell 解决方案。</span><span class="sxs-lookup"><span data-stu-id="77dfd-105">You can now package and distribute Windows PowerShell solutions by using modules.</span></span> <span data-ttu-id="77dfd-106">使用模块，可以将 Windows PowerShell 代码分区、组织和抽象到独立的可重用单元。</span><span class="sxs-lookup"><span data-stu-id="77dfd-106">Modules allow you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="77dfd-107">有关模块的详细信息，请参阅编写 Windows PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="77dfd-107">For more information about modules, see Writing a Windows PowerShell Module.</span></span>

## <a name="the-powershell-class"></a><span data-ttu-id="77dfd-108">PowerShell 类</span><span class="sxs-lookup"><span data-stu-id="77dfd-108">The PowerShell class</span></span>

<span data-ttu-id="77dfd-109">PowerShell 类提供更简单的解决方案来创建应用程序（称为宿主应用程序），以编程方式运行命令。</span><span class="sxs-lookup"><span data-stu-id="77dfd-109">The PowerShell class provides a simpler solution for creating applications, referred to as host applications, that programmatically run commands.</span></span> <span data-ttu-id="77dfd-110">此类允许创建命令管道，指定用于运行命令的运行空间，并指定同步或异步调用命令。</span><span class="sxs-lookup"><span data-stu-id="77dfd-110">This class allows you to create a pipeline of commands, specify the runspace that is used to run the commands, and specify invoking the commands synchronously or asynchronously.</span></span>

## <a name="the-runspacepool-class"></a><span data-ttu-id="77dfd-111">RunspacePool 类</span><span class="sxs-lookup"><span data-stu-id="77dfd-111">The RunspacePool class</span></span>

<span data-ttu-id="77dfd-112">运行空间池允许使用单个调用创建多个运行空间。</span><span class="sxs-lookup"><span data-stu-id="77dfd-112">Runspace pools allow you to create multiple runspaces by using a single call.</span></span> <span data-ttu-id="77dfd-113">CreateRunspacePool 方法提供多个重载，可用于创建具有相同功能的运行空间，例如相同的主机、初始会话状态和连接信息。</span><span class="sxs-lookup"><span data-stu-id="77dfd-113">The CreateRunspacePool method provides several overloads that can be used to create runspaces that have the same features, such as the same host, initial session state, and connection information.</span></span>

## <a name="the-initialsessionstate-class"></a><span data-ttu-id="77dfd-114">InitialSessionState 类</span><span class="sxs-lookup"><span data-stu-id="77dfd-114">The InitialSessionState class</span></span>

<span data-ttu-id="77dfd-115">InitialSessionState 类允许你创建在打开运行空间时使用的会话状态配置。</span><span class="sxs-lookup"><span data-stu-id="77dfd-115">The InitialSessionState class allows you to create a session state configuration that is used when a runspace is opened.</span></span> <span data-ttu-id="77dfd-116">你可以创建自定义配置、包含 mshshort 提供的命令的默认配置，以及基于会话功能限制其命令的配置。</span><span class="sxs-lookup"><span data-stu-id="77dfd-116">You can create a custom configuration, a default configuration that includes the commands provided by mshshort, and a configuration whose commands are restricted based on the capabilities of the session.</span></span>

## <a name="remote-runspaces"></a><span data-ttu-id="77dfd-117">远程运行空间</span><span class="sxs-lookup"><span data-stu-id="77dfd-117">Remote runspaces</span></span>

<span data-ttu-id="77dfd-118">你现在可以创建可在远程计算机上打开的运行空间，使你能够在远程计算机上运行命令并在本地收集结果。</span><span class="sxs-lookup"><span data-stu-id="77dfd-118">You can now create runspaces that can be opened on remote computers, allowing you to run commands on the remote machine and collect the results locally.</span></span> <span data-ttu-id="77dfd-119">若要创建远程运行空间，必须在创建运行空间时指定有关远程连接的信息。</span><span class="sxs-lookup"><span data-stu-id="77dfd-119">To create a remote runspace, you must specify information about the remote connection when creating the runspace.</span></span> <span data-ttu-id="77dfd-120">有关示例，请参阅 CreateRunspace 和 CreateRunspacePool 方法。</span><span class="sxs-lookup"><span data-stu-id="77dfd-120">See the CreateRunspace and CreateRunspacePool methods for examples.</span></span> <span data-ttu-id="77dfd-121">连接信息由 RunspaceConnectionInfo 类定义。</span><span class="sxs-lookup"><span data-stu-id="77dfd-121">The connection information is defined by the RunspaceConnectionInfo class.</span></span>

## <a name="private-runspace-elements"></a><span data-ttu-id="77dfd-122">专用运行空间元素</span><span class="sxs-lookup"><span data-stu-id="77dfd-122">Private runspace elements</span></span>

<span data-ttu-id="77dfd-123">你现在可以创建其元素为公用或专用的运行空间。</span><span class="sxs-lookup"><span data-stu-id="77dfd-123">You can now create runspaces whose elements are public or private.</span></span> <span data-ttu-id="77dfd-124">这样，你便可以创建其元素可用于运行空间的运行空间，但不能供用户使用。</span><span class="sxs-lookup"><span data-stu-id="77dfd-124">This allows you to create runspaces whose elements are available to the runspace, but are not available to the user.</span></span> <span data-ttu-id="77dfd-125">请参阅 ConstrainedSessionStateEntry 类，了解可以将运行空间的哪些元素设为私有。</span><span class="sxs-lookup"><span data-stu-id="77dfd-125">See the ConstrainedSessionStateEntry class to find out which elements of the runspace can be made private.</span></span>

## <a name="runspace-threading-modes-and-apartment-state"></a><span data-ttu-id="77dfd-126">运行空间线程模式和单元状态</span><span class="sxs-lookup"><span data-stu-id="77dfd-126">Runspace threading modes and apartment state</span></span>

<span data-ttu-id="77dfd-127">你现在可以指定在运行空间中运行命令时如何创建和使用线程。</span><span class="sxs-lookup"><span data-stu-id="77dfd-127">You can now specify how threads are created and used when running commands in a runspace.</span></span> <span data-ttu-id="77dfd-128">请参阅 ThreadOptions 和 RunspacePool。 ThreadOptions 属性（& e）：和属性。</span><span class="sxs-lookup"><span data-stu-id="77dfd-128">See the System.Management.Automation.Runspaces.Runspace.ThreadOptions and System.Management.Automation.Runspaces.RunspacePool.ThreadOptions properties.</span></span>

<span data-ttu-id="77dfd-129">你现在可以获取用于在运行空间中运行命令的线程的单元状态。</span><span class="sxs-lookup"><span data-stu-id="77dfd-129">You can now get the apartment state of the threads that are used to run commands in a runspace.</span></span> <span data-ttu-id="77dfd-130">请参阅 System.threading.thread.apartmentstate 和 RunspacePool。 System.threading.thread.apartmentstate 属性（& e）：和属性。</span><span class="sxs-lookup"><span data-stu-id="77dfd-130">See the System.Management.Automation.Runspaces.Runspace.ApartmentState and System.Management.Automation.Runspaces.RunspacePool.ApartmentState properties.</span></span>

## <a name="transaction-cmdlets"></a><span data-ttu-id="77dfd-131">事务 cmdlet</span><span class="sxs-lookup"><span data-stu-id="77dfd-131">Transaction cmdlets</span></span>

<span data-ttu-id="77dfd-132">你现在可以创建可在事务中使用的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="77dfd-132">You can now create cmdlets that can be used within a transaction.</span></span> <span data-ttu-id="77dfd-133">当在事务中使用 cmdlet 时，其操作是临时的，并且可以由 Windows PowerShell 提供的事务 cmdlet 接受或拒绝。</span><span class="sxs-lookup"><span data-stu-id="77dfd-133">When a cmdlet is used in a transaction, its actions are temporary, and they can be accepted or rejected by the transaction cmdlets provided by Windows PowerShell.</span></span>

<span data-ttu-id="77dfd-134">有关事务的详细信息，请参阅如何支持事务。</span><span class="sxs-lookup"><span data-stu-id="77dfd-134">For more information about transactions, see How to Support Transactions.</span></span>

## <a name="transaction-provider"></a><span data-ttu-id="77dfd-135">事务提供程序</span><span class="sxs-lookup"><span data-stu-id="77dfd-135">Transaction provider</span></span>

<span data-ttu-id="77dfd-136">你现在可以创建可在事务中使用的提供程序。</span><span class="sxs-lookup"><span data-stu-id="77dfd-136">You can now create providers that can be used within a transaction.</span></span> <span data-ttu-id="77dfd-137">与 cmdlet 类似，当在事务中使用提供程序时，其操作是临时的，并且可以由 Windows PowerShell 提供的事务 cmdlet 接受或拒绝。</span><span class="sxs-lookup"><span data-stu-id="77dfd-137">Similar to cmdlets, when a provider is used in a transaction, its actions are temporary, and they can be accepted or rejected by the transaction cmdlets provided by Windows PowerShell.</span></span>

<span data-ttu-id="77dfd-138">有关在提供程序类中指定对事务的支持的详细信息，请参阅 CmdletProviderAttribute. ProviderCapabilities 属性。</span><span class="sxs-lookup"><span data-stu-id="77dfd-138">For more information about specifying support for transaction within a provider class, see the System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities property.</span></span>

## <a name="job-cmdlets"></a><span data-ttu-id="77dfd-139">作业 cmdlet</span><span class="sxs-lookup"><span data-stu-id="77dfd-139">Job cmdlets</span></span>

<span data-ttu-id="77dfd-140">你现在可以编写可执行其操作的 cmdlet 作为作业。</span><span class="sxs-lookup"><span data-stu-id="77dfd-140">You can now write cmdlets that can perform their action as a job.</span></span> <span data-ttu-id="77dfd-141">这些作业在后台运行，而不与当前会话交互。</span><span class="sxs-lookup"><span data-stu-id="77dfd-141">These jobs are run in the background without interacting with the current session.</span></span> <span data-ttu-id="77dfd-142">有关 Windows PowerShell 如何支持作业的详细信息，请参阅后台作业。</span><span class="sxs-lookup"><span data-stu-id="77dfd-142">For more information about how Windows PowerShell supports jobs, see Background Jobs.</span></span>

## <a name="cmdlet-output-types"></a><span data-ttu-id="77dfd-143">Cmdlet 输出类型</span><span class="sxs-lookup"><span data-stu-id="77dfd-143">Cmdlet output types</span></span>

<span data-ttu-id="77dfd-144">你现在可以通过在编写 cmdlet 时声明 OutputType 属性来指定 cmdlet 返回的 .NET Framework 类型。</span><span class="sxs-lookup"><span data-stu-id="77dfd-144">You can now specify the .NET Framework types that are returned by your cmdlets by declaring the OutputType attribute when writing your cmdlets.</span></span> <span data-ttu-id="77dfd-145">这将允许其他人通过查看 cmdlet 的 OutputType 属性来确定 cmdlet 返回哪种类型的对象。</span><span class="sxs-lookup"><span data-stu-id="77dfd-145">This will allow others to determine what type of objects are returned by a cmdlet by looking at the OutputType property of the cmdlet.</span></span>

## <a name="event-support"></a><span data-ttu-id="77dfd-146">事件支持</span><span class="sxs-lookup"><span data-stu-id="77dfd-146">Event support</span></span>

<span data-ttu-id="77dfd-147">你现在可以编写添加和使用事件的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="77dfd-147">You can now write cmdlets that add and consume events.</span></span> <span data-ttu-id="77dfd-148">请参阅 PSEvent 类。</span><span class="sxs-lookup"><span data-stu-id="77dfd-148">See the PSEvent class.</span></span>

## <a name="proxy-commands"></a><span data-ttu-id="77dfd-149">代理命令</span><span class="sxs-lookup"><span data-stu-id="77dfd-149">Proxy commands</span></span>

<span data-ttu-id="77dfd-150">你现在可以编写可用于运行另一个命令的代理命令。</span><span class="sxs-lookup"><span data-stu-id="77dfd-150">You can now write proxy commands that can be used to run another command.</span></span> <span data-ttu-id="77dfd-151">使用代理命令可以控制源 cmdlet 的哪些功能可供用户使用。</span><span class="sxs-lookup"><span data-stu-id="77dfd-151">A proxy command allows you to control what functionality of the source cmdlet is available to the user.</span></span> <span data-ttu-id="77dfd-152">例如，你可以创建一个代理命令，该命令删除 source 命令提供的参数。</span><span class="sxs-lookup"><span data-stu-id="77dfd-152">For example, you can create a proxy command that removes a parameter that is supplied by the source command.</span></span> <span data-ttu-id="77dfd-153">请参阅 ProxyCommand 类。</span><span class="sxs-lookup"><span data-stu-id="77dfd-153">See the ProxyCommand class.</span></span>

## <a name="multiple-choice-prompts"></a><span data-ttu-id="77dfd-154">多个选择提示</span><span class="sxs-lookup"><span data-stu-id="77dfd-154">Multiple choice prompts</span></span>

<span data-ttu-id="77dfd-155">你现在可以编写可提供允许用户选择多个选项的提示的应用程序。</span><span class="sxs-lookup"><span data-stu-id="77dfd-155">You can now write applications that can provide prompts that allow the user to select multiple choices.</span></span> <span data-ttu-id="77dfd-156">请参阅 IHostUISupportsMultipleChoiceSelection 接口</span><span class="sxs-lookup"><span data-stu-id="77dfd-156">See the IHostUISupportsMultipleChoiceSelection interface</span></span>

## <a name="interactive-sessions"></a><span data-ttu-id="77dfd-157">交互式会话</span><span class="sxs-lookup"><span data-stu-id="77dfd-157">Interactive sessions</span></span>

<span data-ttu-id="77dfd-158">你现在可以编写能够在远程计算机上启动和停止交互式会话的应用程序。</span><span class="sxs-lookup"><span data-stu-id="77dfd-158">You can now write applications that can start and stop an interactive session on a remote computer.</span></span>
<span data-ttu-id="77dfd-159">请参阅 IHostSupportsInteractiveSession 接口。</span><span class="sxs-lookup"><span data-stu-id="77dfd-159">See the IHostSupportsInteractiveSession interface.</span></span>

## <a name="custom-cmdlet-help-for-providers"></a><span data-ttu-id="77dfd-160">提供程序的自定义 Cmdlet 帮助</span><span class="sxs-lookup"><span data-stu-id="77dfd-160">Custom Cmdlet Help for Providers</span></span>

<span data-ttu-id="77dfd-161">你现在可以为提供程序 cmdlet 创建自定义帮助主题。</span><span class="sxs-lookup"><span data-stu-id="77dfd-161">You can now create customized Help topics for the provider cmdlets.</span></span> <span data-ttu-id="77dfd-162">自定义 cmdlet 帮助主题可以说明 cmdlet 在提供程序路径中的工作原理和文档特殊功能，包括提供程序添加到 cmdlet 的动态参数。</span><span class="sxs-lookup"><span data-stu-id="77dfd-162">Custom cmdlet help topics can explain how the cmdlet works in the provider path and document special features, including the dynamic parameters that the provider adds to the cmdlet.</span></span>
