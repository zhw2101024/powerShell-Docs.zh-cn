---
title: Cmdlet 概述 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK]
- cmdlets [PowerShell SDK], described
ms.assetid: 0aa32589-4447-4ead-a5dd-a3be99113140
caps.latest.revision: 21
ms.openlocfilehash: 14200aed2fb94c37c8b8af29650f602945e7ac1c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365886"
---
# <a name="cmdlet-overview"></a><span data-ttu-id="c9217-102">Cmdlet 概述</span><span class="sxs-lookup"><span data-stu-id="c9217-102">Cmdlet Overview</span></span>

<span data-ttu-id="c9217-103">Cmdlet 是在 Windows PowerShell 环境中使用的轻量命令。</span><span class="sxs-lookup"><span data-stu-id="c9217-103">A cmdlet is a lightweight command that is used in the Windows PowerShell environment.</span></span> <span data-ttu-id="c9217-104">Windows PowerShell 运行时在命令行中提供的自动化脚本的上下文中调用这些 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c9217-104">The Windows PowerShell runtime invokes these cmdlets within the context of automation scripts that are provided at the command line.</span></span> <span data-ttu-id="c9217-105">Windows PowerShell 运行时还通过 Windows PowerShell Api 以编程方式调用它们。</span><span class="sxs-lookup"><span data-stu-id="c9217-105">The Windows PowerShell runtime also invokes them programmatically through Windows PowerShell APIs.</span></span>

## <a name="cmdlets"></a><span data-ttu-id="c9217-106">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c9217-106">Cmdlets</span></span>

<span data-ttu-id="c9217-107">Cmdlet 执行操作，通常会将 Microsoft .NET 框架对象返回到管道中的下一个命令。</span><span class="sxs-lookup"><span data-stu-id="c9217-107">Cmdlets perform an action and typically return a Microsoft .NET Framework object to the next command in the pipeline.</span></span> <span data-ttu-id="c9217-108">若要编写 cmdlet，必须实现一个派生自两个专用 cmdlet 基类之一的 cmdlet 类。</span><span class="sxs-lookup"><span data-stu-id="c9217-108">To write a cmdlet, you must implement a cmdlet class that derives from one of two specialized cmdlet base classes.</span></span> <span data-ttu-id="c9217-109">派生类必须：</span><span class="sxs-lookup"><span data-stu-id="c9217-109">The derived class must:</span></span>

- <span data-ttu-id="c9217-110">声明一个将派生类标识为 cmdlet 的特性。</span><span class="sxs-lookup"><span data-stu-id="c9217-110">Declare an attribute that identifies the derived class as a cmdlet.</span></span>

- <span data-ttu-id="c9217-111">定义用特性修饰的公共属性，这些属性将公共属性标识为 cmdlet 参数。</span><span class="sxs-lookup"><span data-stu-id="c9217-111">Define public properties that are decorated with attributes that identify the public properties as cmdlet parameters.</span></span>

- <span data-ttu-id="c9217-112">重写一个或多个输入处理方法来处理记录。</span><span class="sxs-lookup"><span data-stu-id="c9217-112">Override one or more of the input processing methods to process records.</span></span>

<span data-ttu-id="c9217-113">您可以通过使用[import-module](/powershell/module/microsoft.powershell.core/import-module) cmdlet 直接加载包含该类的程序集，也可以使用[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) API 创建一个用于加载程序集的主机应用程序，。</span><span class="sxs-lookup"><span data-stu-id="c9217-113">You can load the assembly that contains the class directly by using the [Import-Module](/powershell/module/microsoft.powershell.core/import-module) cmdlet, or you can create a host application that loads the assembly by using the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) API.</span></span> <span data-ttu-id="c9217-114">这两种方法都提供对 cmdlet 功能的编程和命令行访问。</span><span class="sxs-lookup"><span data-stu-id="c9217-114">Both methods provide programmatic and command-line access to the functionality of the cmdlet.</span></span>

## <a name="cmdlet-terms"></a><span data-ttu-id="c9217-115">Cmdlet 术语</span><span class="sxs-lookup"><span data-stu-id="c9217-115">Cmdlet Terms</span></span>

<span data-ttu-id="c9217-116">Windows PowerShell cmdlet 文档中经常使用以下术语：</span><span class="sxs-lookup"><span data-stu-id="c9217-116">The following terms are used frequently in the Windows PowerShell cmdlet documentation:</span></span>

### <a name="cmdlet-attribute"></a><span data-ttu-id="c9217-117">Cmdlet 特性</span><span class="sxs-lookup"><span data-stu-id="c9217-117">Cmdlet attribute</span></span>

<span data-ttu-id="c9217-118">用于将 cmdlet 类声明为 cmdlet 的 .NET Framework 属性。</span><span class="sxs-lookup"><span data-stu-id="c9217-118">A .NET Framework attribute that is used to declare a cmdlet class as a cmdlet.</span></span>
<span data-ttu-id="c9217-119">尽管 PowerShell 使用几个可选的其他属性，但 Cmdlet 属性是必需的。</span><span class="sxs-lookup"><span data-stu-id="c9217-119">Although PowerShell uses several other attributes that are optional, the Cmdlet attribute is required.</span></span>
<span data-ttu-id="c9217-120">有关此属性的详细信息，请参阅[Cmdlet 特性声明](cmdlet-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="c9217-120">For more information about this attribute, see [Cmdlet Attribute Declaration](cmdlet-attribute-declaration.md).</span></span>

### <a name="cmdlet-parameter"></a><span data-ttu-id="c9217-121">Cmdlet 参数</span><span class="sxs-lookup"><span data-stu-id="c9217-121">Cmdlet parameter</span></span>

<span data-ttu-id="c9217-122">公共属性，用于定义可用于用户的参数或运行 cmdlet 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="c9217-122">The public properties that define the parameters that are available to the user or to the application that is running the cmdlet.</span></span>
<span data-ttu-id="c9217-123">Cmdlet 可以有必需的、命名的、位置参数和*开关*参数。</span><span class="sxs-lookup"><span data-stu-id="c9217-123">Cmdlets can have required, named, positional, and *switch* parameters.</span></span>
<span data-ttu-id="c9217-124">通过开关参数可以定义仅当在调用中指定了参数时才计算的参数。</span><span class="sxs-lookup"><span data-stu-id="c9217-124">Switch parameters allow you to define parameters that are evaluated only if the parameters are specified in the call.</span></span>
<span data-ttu-id="c9217-125">有关不同类型的参数的详细信息，请参阅[Cmdlet 参数](cmdlet-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="c9217-125">For more information about the different types of parameters, see [Cmdlet Parameters](cmdlet-parameters.md).</span></span>

### <a name="parameter-set"></a><span data-ttu-id="c9217-126">参数集</span><span class="sxs-lookup"><span data-stu-id="c9217-126">Parameter set</span></span>

<span data-ttu-id="c9217-127">可用于相同的命令中以执行特定操作的一组参数。</span><span class="sxs-lookup"><span data-stu-id="c9217-127">A group of parameters that can be used in the same command to perform a specific action.</span></span>
<span data-ttu-id="c9217-128">一个 cmdlet 可以具有多个参数集，但是每个参数集必须至少具有一个唯一的参数。</span><span class="sxs-lookup"><span data-stu-id="c9217-128">A cmdlet can have multiple parameter sets, but each parameter set must have at least one parameter that is unique.</span></span>
<span data-ttu-id="c9217-129">良好的 cmdlet 设计强烈意味着 unique 参数也是必需的参数。</span><span class="sxs-lookup"><span data-stu-id="c9217-129">Good cmdlet design strongly suggests that the unique parameter also be a required parameter.</span></span>
<span data-ttu-id="c9217-130">有关参数集的详细信息，请参阅[Cmdlet 参数集](cmdlet-parameter-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="c9217-130">For more information about parameter sets, see [Cmdlet Parameter Sets](cmdlet-parameter-sets.md).</span></span>

### <a name="dynamic-parameter"></a><span data-ttu-id="c9217-131">动态参数</span><span class="sxs-lookup"><span data-stu-id="c9217-131">Dynamic parameter</span></span>

<span data-ttu-id="c9217-132">在运行时添加到 cmdlet 的参数。</span><span class="sxs-lookup"><span data-stu-id="c9217-132">A parameter that is added to the cmdlet at runtime.</span></span>
<span data-ttu-id="c9217-133">通常，当另一个参数设置为特定值时，会将动态参数添加到 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c9217-133">Typically, the dynamic parameters are added to the cmdlet when another parameter is set to a specific value.</span></span>
<span data-ttu-id="c9217-134">有关动态参数的详细信息，请参阅[Cmdlet 动态参数](cmdlet-dynamic-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="c9217-134">For more information about dynamic parameters, see [Cmdlet Dynamic Parameters](cmdlet-dynamic-parameters.md).</span></span>

### <a name="input-processing-method"></a><span data-ttu-id="c9217-135">输入处理方法</span><span class="sxs-lookup"><span data-stu-id="c9217-135">Input processing method</span></span>

<span data-ttu-id="c9217-136">Cmdlet 可用于处理其以输入形式所接收的记录的一种方法。</span><span class="sxs-lookup"><span data-stu-id="c9217-136">A method that a cmdlet can use to process the records it receives as input.</span></span>
<span data-ttu-id="c9217-137">输入处理方法包括 [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 方法、[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 方法、[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 方法和 [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) 方法的输入处理方法中的一种方法，其中包括：方法和方法的方法。</span><span class="sxs-lookup"><span data-stu-id="c9217-137">The input processing methods include the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, and the [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) method.</span></span> <span data-ttu-id="c9217-138">在实现 cmdlet 时，必须重写至少一个[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)、 [ProcessRecord 和](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法中的一个方法，并且必须重写其中的一种，即[方法。](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)</span><span class="sxs-lookup"><span data-stu-id="c9217-138">When you implement a cmdlet, you must override at least one of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), and [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) methods.</span></span>
<span data-ttu-id="c9217-139">通常， [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法是重写的方法，因为它是为该 Cmdlet 处理的每条记录调用的。</span><span class="sxs-lookup"><span data-stu-id="c9217-139">Typically, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is the method that you override because it is called for every record that the cmdlet processes.</span></span>
<span data-ttu-id="c9217-140">与此相反， [BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法和[system.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法一次被调用一次来执行记录的预处理或后处理过程，而不是一次。</span><span class="sxs-lookup"><span data-stu-id="c9217-140">In contrast, the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method are called one time to perform pre-processing or post-processing of the records.</span></span>
<span data-ttu-id="c9217-141">有关这些方法的详细信息，请参阅[输入处理方法](cmdlet-input-processing-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="c9217-141">For more information about these methods, see [Input Processing Methods](cmdlet-input-processing-methods.md).</span></span>

### <a name="shouldprocess-feature"></a><span data-ttu-id="c9217-142">ShouldProcess 功能</span><span class="sxs-lookup"><span data-stu-id="c9217-142">ShouldProcess feature</span></span>

<span data-ttu-id="c9217-143">通过 PowerShell，你可以创建在 cmdlet 对系统进行更改之前提示用户提供反馈的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c9217-143">PowerShell allows you to create cmdlets that prompt the user for feedback before the cmdlet makes a change to the system.</span></span>
<span data-ttu-id="c9217-144">若要使用此功能，该 cmdlet 必须在声明 Cmdlet 特性时声明它支持 ShouldProcess 功能，并且该 cmdlet 必须从输入处理方法中调用 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 和 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 方法中的和方法。</span><span class="sxs-lookup"><span data-stu-id="c9217-144">To use this feature, the cmdlet must declare that it supports the ShouldProcess feature when you declare the Cmdlet attribute, and the cmdlet must call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods from within an input processing method.</span></span>
<span data-ttu-id="c9217-145">有关如何支持 ShouldProcess 功能的详细信息，请参阅[请求确认](requesting-confirmation-from-cmdlets.md)。</span><span class="sxs-lookup"><span data-stu-id="c9217-145">For more information about how to support the ShouldProcess functionality, see [Requesting Confirmation](requesting-confirmation-from-cmdlets.md).</span></span>

### <a name="transaction"></a><span data-ttu-id="c9217-146">Transaction</span><span class="sxs-lookup"><span data-stu-id="c9217-146">Transaction</span></span>

<span data-ttu-id="c9217-147">被视为单个任务的一组命令逻辑组。</span><span class="sxs-lookup"><span data-stu-id="c9217-147">A logical group of commands that are treated as a single task.</span></span>
<span data-ttu-id="c9217-148">如果组中的任何命令失败，并且用户可以选择接受或拒绝在事务中执行的操作，则任务将自动失败。</span><span class="sxs-lookup"><span data-stu-id="c9217-148">The task automatically fails if any command in the group fails, and the user has the choice to accept or reject the actions performed within the transaction.</span></span>
<span data-ttu-id="c9217-149">若要参与事务，cmdlet 必须在声明 Cmdlet 属性时声明它支持事务。</span><span class="sxs-lookup"><span data-stu-id="c9217-149">To participate in a transaction, the cmdlet must declare that it supports transactions when the Cmdlet attribute is declared.</span></span>
<span data-ttu-id="c9217-150">Windows PowerShell 2.0 中引入了对事务的支持。</span><span class="sxs-lookup"><span data-stu-id="c9217-150">Support for transactions was introduced in Windows PowerShell 2.0.</span></span>
<span data-ttu-id="c9217-151">有关事务的详细信息，请参阅[如何支持事务](how-to-support-transactions.md)。</span><span class="sxs-lookup"><span data-stu-id="c9217-151">For more information about transactions, see [How to Support Transactions](how-to-support-transactions.md).</span></span>

## <a name="how-cmdlets-differ-from-commands"></a><span data-ttu-id="c9217-152">Cmdlet 与命令的区别</span><span class="sxs-lookup"><span data-stu-id="c9217-152">How Cmdlets Differ from Commands</span></span>

<span data-ttu-id="c9217-153">Cmdlet 在以下方面与其他命令 shell 环境中的命令不同：</span><span class="sxs-lookup"><span data-stu-id="c9217-153">Cmdlets differ from commands in other command-shell environments in the following ways:</span></span>

- <span data-ttu-id="c9217-154">Cmdlet 是 .NET Framework 类的实例;它们不是独立的可执行文件。</span><span class="sxs-lookup"><span data-stu-id="c9217-154">Cmdlets are instances of .NET Framework classes; they are not stand-alone executables.</span></span>

- <span data-ttu-id="c9217-155">可以从多达十二行代码创建 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c9217-155">Cmdlets can be created from as few as a dozen lines of code.</span></span>

- <span data-ttu-id="c9217-156">Cmdlet 通常不会执行自己的分析、错误演示或输出格式设置。</span><span class="sxs-lookup"><span data-stu-id="c9217-156">Cmdlets do not generally do their own parsing, error presentation, or output formatting.</span></span> <span data-ttu-id="c9217-157">Windows PowerShell 运行时将处理分析、错误演示和输出格式。</span><span class="sxs-lookup"><span data-stu-id="c9217-157">Parsing, error presentation, and output formatting are handled by the Windows PowerShell runtime.</span></span>

- <span data-ttu-id="c9217-158">Cmdlet 从管道（而不是从文本流）处理输入对象，而 cmdlet 通常将对象作为输出传递到管道。</span><span class="sxs-lookup"><span data-stu-id="c9217-158">Cmdlets process input objects from the pipeline rather than from streams of text, and cmdlets typically deliver objects as output to the pipeline.</span></span>

- <span data-ttu-id="c9217-159">Cmdlet 是面向记录的，因为它们一次处理一个对象。</span><span class="sxs-lookup"><span data-stu-id="c9217-159">Cmdlets are record-oriented because they process a single object at a time.</span></span>

## <a name="cmdlet-base-classes"></a><span data-ttu-id="c9217-160">Cmdlet 基类</span><span class="sxs-lookup"><span data-stu-id="c9217-160">Cmdlet Base Classes</span></span>

<span data-ttu-id="c9217-161">Windows PowerShell 支持从以下两个基类派生的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c9217-161">Windows PowerShell supports cmdlets that are derived from the following two base classes.</span></span>

- <span data-ttu-id="c9217-162">大多数 cmdlet 都以派生自[system.exception 基类的](/dotnet/api/System.Management.Automation.Cmdlet).NET Framework 类为基础。</span><span class="sxs-lookup"><span data-stu-id="c9217-162">Most cmdlets are based on .NET Framework classes that derive from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span></span> <span data-ttu-id="c9217-163">从此类派生允许 cmdlet 使用 Windows PowerShell 运行时上的最小依赖项集。</span><span class="sxs-lookup"><span data-stu-id="c9217-163">Deriving from this class allows a cmdlet to use the minimum set of dependencies on the Windows PowerShell runtime.</span></span> <span data-ttu-id="c9217-164">这具有两方面的好处。</span><span class="sxs-lookup"><span data-stu-id="c9217-164">This has two benefits.</span></span> <span data-ttu-id="c9217-165">第一个优点是，cmdlet 对象更小，不太可能受到对 Windows PowerShell 运行时的更改的影响。</span><span class="sxs-lookup"><span data-stu-id="c9217-165">The first benefit is that the cmdlet objects are smaller, and you are less likely to be affected by changes to the Windows PowerShell runtime.</span></span> <span data-ttu-id="c9217-166">第二个优点是，如果你需要，可以直接创建 cmdlet 对象的实例，然后直接调用它，而不是通过 Windows PowerShell 运行时调用它。</span><span class="sxs-lookup"><span data-stu-id="c9217-166">The second benefit is that, if you have to, you can directly create an instance of the cmdlet object and then invoke it directly instead of invoking it through the Windows PowerShell runtime.</span></span>

- <span data-ttu-id="c9217-167">更复杂的 cmdlet 基于从[PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)基类派生的 .NET Framework 类的功能。</span><span class="sxs-lookup"><span data-stu-id="c9217-167">The more-complex cmdlets are based on .NET Framework classes that derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span> <span data-ttu-id="c9217-168">从此类派生，可以更好地访问 Windows PowerShell 运行时。</span><span class="sxs-lookup"><span data-stu-id="c9217-168">Deriving from this class gives you much more access to the Windows PowerShell runtime.</span></span> <span data-ttu-id="c9217-169">此访问权限允许 cmdlet 调用脚本、访问提供程序和访问当前会话状态。</span><span class="sxs-lookup"><span data-stu-id="c9217-169">This access allows your cmdlet to call scripts, to access providers, and to access the current session state.</span></span> <span data-ttu-id="c9217-170">（若要访问当前会话状态，可以获取和设置会话变量和首选项。）但是，从此类派生将增加 cmdlet 对象的大小，这意味着你的 cmdlet 更紧密地耦合到当前版本的 Windows PowerShell 运行时。</span><span class="sxs-lookup"><span data-stu-id="c9217-170">(To access the current session state, you get and set session variables and preferences.) However, deriving from this class increases the size of the cmdlet object, and it means that your cmdlet is more tightly coupled to the current version of the Windows PowerShell runtime.</span></span>

<span data-ttu-id="c9217-171">通常情况下，除非你需要对 Windows PowerShell 运行时的扩展访问权限，否则你应该从[system.web](/dotnet/api/System.Management.Automation.Cmdlet)类派生。</span><span class="sxs-lookup"><span data-stu-id="c9217-171">In general, unless you need the extended access to the Windows PowerShell runtime, you should derive from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="c9217-172">但是，Windows PowerShell 运行时具有广泛的日志记录功能，可以执行 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c9217-172">However, the Windows PowerShell runtime has extensive logging capabilities for the execution of cmdlets.</span></span> <span data-ttu-id="c9217-173">如果审核模型依赖于此日志记录，则可以通过从[PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)类派生来阻止从另一个 cmdlet 中执行 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c9217-173">If your auditing model depends on this logging, you can prevent the execution of your cmdlet from within another cmdlet by deriving from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

## <a name="input-processing-methods"></a><span data-ttu-id="c9217-174">输入处理方法</span><span class="sxs-lookup"><span data-stu-id="c9217-174">Input Processing Methods</span></span>

<span data-ttu-id="c9217-175">[System.web](/dotnet/api/System.Management.Automation.Cmdlet)类提供了以下用于处理记录的虚方法：。</span><span class="sxs-lookup"><span data-stu-id="c9217-175">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides the following virtual methods that are used to process records.</span></span> <span data-ttu-id="c9217-176">所有派生的 cmdlet 类必须重写前三个方法中的一个或多个：</span><span class="sxs-lookup"><span data-stu-id="c9217-176">All the derived cmdlet classes must override one or more of the first three methods:</span></span>

- <span data-ttu-id="c9217-177">[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)：用于为 Cmdlet 提供可选的一次性预处理功能（& e）。</span><span class="sxs-lookup"><span data-stu-id="c9217-177">[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing): Used to provide optional one-time, pre-processing functionality for the cmdlet.</span></span>

- <span data-ttu-id="c9217-178">[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)：用于为 Cmdlet 提供按记录处理的功能的处理功能。</span><span class="sxs-lookup"><span data-stu-id="c9217-178">[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord): Used to provide record-by-record processing functionality for the cmdlet.</span></span> <span data-ttu-id="c9217-179">根据 Cmdlet 的输入， [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法可能会被调用任意次数（或根本不会进行调用）。</span><span class="sxs-lookup"><span data-stu-id="c9217-179">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method might be called any number of times, or not at all, depending on the input of the cmdlet.</span></span>

- <span data-ttu-id="c9217-180">[System.web. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)：用于为 Cmdlet 提供可选的一次性处理后的功能，。</span><span class="sxs-lookup"><span data-stu-id="c9217-180">[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing): Used to provide optional one-time, post-processing functionality for the cmdlet.</span></span>

- <span data-ttu-id="c9217-181">[StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing)：用于在用户以异步方式停止 Cmdlet 时停止处理（例如，按 CTRL + C）。</span><span class="sxs-lookup"><span data-stu-id="c9217-181">[System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing): Used to stop processing when the user stops the cmdlet asynchronously (for example,  by pressing CTRL+C).</span></span>

<span data-ttu-id="c9217-182">有关这些方法的详细信息，请参阅[Cmdlet 输入处理方法](./cmdlet-input-processing-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="c9217-182">For more information about these methods, see [Cmdlet Input Processing Methods](./cmdlet-input-processing-methods.md).</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="c9217-183">Cmdlet 属性</span><span class="sxs-lookup"><span data-stu-id="c9217-183">Cmdlet Attributes</span></span>

<span data-ttu-id="c9217-184">Windows PowerShell 定义多个 .NET Framework 属性，这些属性用于管理 cmdlet，并用于指定 Windows PowerShell 提供的和 cmdlet 可能需要的常用功能。</span><span class="sxs-lookup"><span data-stu-id="c9217-184">Windows PowerShell defines several .NET Framework attributes that are used to manage cmdlets and to specify common functionality that is provided by Windows PowerShell and that might be required by the cmdlet.</span></span> <span data-ttu-id="c9217-185">例如，特性用于将类指定为 cmdlet、指定 cmdlet 的参数，并请求验证输入，以便 cmdlet 开发人员无需在其 cmdlet 代码中实现该功能。</span><span class="sxs-lookup"><span data-stu-id="c9217-185">For example, attributes are used to designate a class as a cmdlet, to specify the parameters of the cmdlet, and to request the validation of input so that cmdlet developers do not have to implement that functionality in their cmdlet code.</span></span> <span data-ttu-id="c9217-186">有关特性的详细信息，请参阅[Windows PowerShell 特性](./cmdlet-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="c9217-186">For more information about attributes, see [Windows PowerShell Attributes](./cmdlet-attributes.md).</span></span>

## <a name="cmdlet-names"></a><span data-ttu-id="c9217-187">Cmdlet 名称</span><span class="sxs-lookup"><span data-stu-id="c9217-187">Cmdlet Names</span></span>

<span data-ttu-id="c9217-188">Windows PowerShell 使用动词和-名词名称对来命名 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c9217-188">Windows PowerShell uses a verb-and-noun name pair to name cmdlets.</span></span> <span data-ttu-id="c9217-189">例如，Windows PowerShell 中包含的 `Get-Command` cmdlet 用于获取在命令外壳中注册的所有 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c9217-189">For example, the `Get-Command` cmdlet included in Windows PowerShell is used to get all the cmdlets that are registered in the command shell.</span></span> <span data-ttu-id="c9217-190">谓词标识 cmdlet 执行的操作，名词标识该 cmdlet 执行其操作的资源。</span><span class="sxs-lookup"><span data-stu-id="c9217-190">The verb identifies the action that the cmdlet performs, and the noun identifies the resource on which the cmdlet performs its action.</span></span>

<span data-ttu-id="c9217-191">在将 .NET Framework 类声明为 cmdlet 时指定这些名称。</span><span class="sxs-lookup"><span data-stu-id="c9217-191">These names are specified when the .NET Framework class is declared as a cmdlet.</span></span> <span data-ttu-id="c9217-192">有关如何将 .NET Framework 类声明为 cmdlet 的详细信息，请参阅[Cmdlet 特性声明](./cmdlet-class-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="c9217-192">For more information about how to declare a .NET Framework class as a cmdlet, see [Cmdlet Attribute Declaration](./cmdlet-class-declaration.md).</span></span>

## <a name="writing-cmdlet-code"></a><span data-ttu-id="c9217-193">编写 Cmdlet 代码</span><span class="sxs-lookup"><span data-stu-id="c9217-193">Writing Cmdlet Code</span></span>

<span data-ttu-id="c9217-194">本文档提供了两种方法来了解如何编写 cmdlet 代码。</span><span class="sxs-lookup"><span data-stu-id="c9217-194">This document provides two ways to discover how cmdlet code is written.</span></span> <span data-ttu-id="c9217-195">如果更喜欢查看代码而不做很多解释，请参阅[Cmdlet 代码示例](./examples-of-cmdlet-code.md)。</span><span class="sxs-lookup"><span data-stu-id="c9217-195">If you prefer to see the code without much explanation, see [Examples of Cmdlet Code](./examples-of-cmdlet-code.md).</span></span> <span data-ttu-id="c9217-196">如需更多有关代码的说明，请参阅[GetProc 教程](./getproc-tutorial.md)、 [StopProc 教程](./stopproc-tutorial.md)或[SelectStr 教程](./selectstr-tutorial.md)主题。</span><span class="sxs-lookup"><span data-stu-id="c9217-196">If you prefer more explanation about the code, see the [GetProc Tutorial](./getproc-tutorial.md),  [StopProc Tutorial](./stopproc-tutorial.md), or [SelectStr Tutorial](./selectstr-tutorial.md) topics.</span></span>

<span data-ttu-id="c9217-197">有关编写 cmdlet 的准则的详细信息，请参阅[Cmdlet 开发指南](./cmdlet-development-guidelines.md)。</span><span class="sxs-lookup"><span data-stu-id="c9217-197">For more information about the guidelines for writing cmdlets, see [Cmdlet Development Guidelines](./cmdlet-development-guidelines.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c9217-198">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c9217-198">See Also</span></span>

[<span data-ttu-id="c9217-199">Windows PowerShell Cmdlet 概念</span><span class="sxs-lookup"><span data-stu-id="c9217-199">Windows PowerShell Cmdlet Concepts</span></span>](./windows-powershell-cmdlet-concepts.md)

[<span data-ttu-id="c9217-200">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c9217-200">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="c9217-201">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c9217-201">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
