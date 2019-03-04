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
ms.openlocfilehash: a53b1ada46ad614af3522e6cc11e187afb76e7b1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855313"
---
# <a name="cmdlet-overview"></a><span data-ttu-id="849a0-102">Cmdlet 概述</span><span class="sxs-lookup"><span data-stu-id="849a0-102">Cmdlet Overview</span></span>

<span data-ttu-id="849a0-103">Cmdlet 是 Windows PowerShell 环境中使用的轻型命令。</span><span class="sxs-lookup"><span data-stu-id="849a0-103">A cmdlet is a lightweight command that is used in the Windows PowerShell environment.</span></span> <span data-ttu-id="849a0-104">Windows PowerShell 运行时调用的命令行时提供的自动化脚本上下文中使用这些 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="849a0-104">The Windows PowerShell runtime invokes these cmdlets within the context of automation scripts that are provided at the command line.</span></span> <span data-ttu-id="849a0-105">Windows PowerShell 运行时还将调用它们以编程方式通过 Windows PowerShell Api。</span><span class="sxs-lookup"><span data-stu-id="849a0-105">The Windows PowerShell runtime also invokes them programmatically through Windows PowerShell APIs.</span></span>

## <a name="cmdlets"></a><span data-ttu-id="849a0-106">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="849a0-106">Cmdlets</span></span>

<span data-ttu-id="849a0-107">Cmdlet 执行操作，并通常将 Microsoft.NET Framework 对象返回到管道中的下一个命令。</span><span class="sxs-lookup"><span data-stu-id="849a0-107">Cmdlets perform an action and typically return a Microsoft .NET Framework object to the next command in the pipeline.</span></span> <span data-ttu-id="849a0-108">若要编写的 cmdlet，必须实现两个专用的 cmdlet 基类，这些类之一派生的 cmdlet 类。</span><span class="sxs-lookup"><span data-stu-id="849a0-108">To write a cmdlet, you must implement a cmdlet class that derives from one of two specialized cmdlet base classes.</span></span> <span data-ttu-id="849a0-109">在派生的类必须：</span><span class="sxs-lookup"><span data-stu-id="849a0-109">The derived class must:</span></span>

- <span data-ttu-id="849a0-110">声明标识为 cmdlet 的派生的类的属性。</span><span class="sxs-lookup"><span data-stu-id="849a0-110">Declare an attribute that identifies the derived class as a cmdlet.</span></span>

- <span data-ttu-id="849a0-111">定义使用识别为 cmdlet 参数的公共属性的属性修饰的公共属性。</span><span class="sxs-lookup"><span data-stu-id="849a0-111">Define public properties that are decorated with attributes that identify the public properties as cmdlet parameters.</span></span>

- <span data-ttu-id="849a0-112">重写一个或多个输入处理方法来处理记录。</span><span class="sxs-lookup"><span data-stu-id="849a0-112">Override one or more of the input processing methods to process records.</span></span>

<span data-ttu-id="849a0-113">您可以加载的程序集的直接通过使用包含的类[导入模块](/powershell/module/microsoft.powershell.core/import-module)cmdlet，也可以创建主机应用程序加载程序集使用[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) API。</span><span class="sxs-lookup"><span data-stu-id="849a0-113">You can load the assembly that contains the class directly by using the [Import-Module](/powershell/module/microsoft.powershell.core/import-module) cmdlet, or you can create a host application that loads the assembly by using the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) API.</span></span> <span data-ttu-id="849a0-114">这两种方法提供对该 cmdlet 的功能的编程和命令行访问。</span><span class="sxs-lookup"><span data-stu-id="849a0-114">Both methods provide programmatic and command-line access to the functionality of the cmdlet.</span></span>

## <a name="cmdlet-terms"></a><span data-ttu-id="849a0-115">Cmdlet 条款</span><span class="sxs-lookup"><span data-stu-id="849a0-115">Cmdlet Terms</span></span>

<span data-ttu-id="849a0-116">Windows PowerShell cmdlet 文档中经常使用以下术语：</span><span class="sxs-lookup"><span data-stu-id="849a0-116">The following terms are used frequently in the Windows PowerShell cmdlet documentation:</span></span>

- <span data-ttu-id="849a0-117">**Cmdlet 属性**:.NET Framework 属性，用于声明 cmdlet 类作为一个 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="849a0-117">**Cmdlet attribute**: A .NET Framework attribute that is used to declare a cmdlet class as a cmdlet.</span></span> <span data-ttu-id="849a0-118">尽管 Windows PowerShell 使用多个其他属性是可选的但 Cmdlet 属性是必需的。</span><span class="sxs-lookup"><span data-stu-id="849a0-118">Although Windows PowerShell uses several other attributes that are optional, the Cmdlet attribute is required.</span></span> <span data-ttu-id="849a0-119">有关此属性的详细信息，请参阅[Cmdlet 特性声明](./cmdlet-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="849a0-119">For more information about this attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

- <span data-ttu-id="849a0-120">**Cmdlet 参数**:定义可向用户或应用程序运行该 cmdlet 的参数的公共属性。</span><span class="sxs-lookup"><span data-stu-id="849a0-120">**Cmdlet parameter**: The public properties that define the parameters that are available to the user or to the application that is running the cmdlet.</span></span> <span data-ttu-id="849a0-121">Cmdlet 可以都没有必需的命名、 位置，并*切换*参数。</span><span class="sxs-lookup"><span data-stu-id="849a0-121">Cmdlets can have required, named, positional, and *switch* parameters.</span></span> <span data-ttu-id="849a0-122">开关参数可用于定义在调用中指定了参数时，才会评估的参数。</span><span class="sxs-lookup"><span data-stu-id="849a0-122">Switch parameters allow you to define parameters that are evaluated only if the parameters are specified in the call.</span></span> <span data-ttu-id="849a0-123">有关不同类型的参数的详细信息，请参阅[Cmdlet 参数](./cmdlet-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="849a0-123">For more information about the different types of parameters, see [Cmdlet Parameters](./cmdlet-parameters.md).</span></span>

- <span data-ttu-id="849a0-124">**参数集**:可用于相同的命令中以执行特定操作的一组参数。</span><span class="sxs-lookup"><span data-stu-id="849a0-124">**Parameter set**: A group of parameters that can be used in the same command to perform a specific action.</span></span> <span data-ttu-id="849a0-125">一个 cmdlet 可以具有多个参数集，但每个参数集必须具有至少一个参数，它是唯一的。</span><span class="sxs-lookup"><span data-stu-id="849a0-125">A cmdlet can have multiple parameter sets, but each parameter set must have at least one parameter that is unique.</span></span> <span data-ttu-id="849a0-126">好 cmdlet 设计强烈建议的唯一参数也是必需的参数。</span><span class="sxs-lookup"><span data-stu-id="849a0-126">Good cmdlet design strongly suggests that the unique parameter also be a required parameter.</span></span> <span data-ttu-id="849a0-127">有关参数集的详细信息，请参阅[Cmdlet 参数可设置](./cmdlet-parameter-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="849a0-127">For more information about parameter sets, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

- <span data-ttu-id="849a0-128">**动态参数**:添加到该 cmdlet 在运行时参数。</span><span class="sxs-lookup"><span data-stu-id="849a0-128">**Dynamic parameter**: A parameter that is added to the cmdlet at runtime.</span></span> <span data-ttu-id="849a0-129">通常情况下，动态参数添加到该 cmdlet 时另一个参数设置为特定值。</span><span class="sxs-lookup"><span data-stu-id="849a0-129">Typically, the dynamic parameters are added to the cmdlet when another parameter is set to a specific value.</span></span> <span data-ttu-id="849a0-130">有关动态参数的详细信息，请参阅[Cmdlet 的动态参数](./cmdlet-dynamic-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="849a0-130">For more information about dynamic parameters, see [Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md).</span></span>

- <span data-ttu-id="849a0-131">**输入处理方法**:Cmdlet 可用于处理其以输入形式所接收的记录的一种方法。</span><span class="sxs-lookup"><span data-stu-id="849a0-131">**Input processing method**: A method that a cmdlet can use to process the records it receives as input.</span></span> <span data-ttu-id="849a0-132">输入的处理方法包括[System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法， [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法时， [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法，并[System.Management.Automation.Cmdlet.Stopprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing)方法。</span><span class="sxs-lookup"><span data-stu-id="849a0-132">The input processing methods include the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method, the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, the [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, and the [System.Management.Automation.Cmdlet.Stopprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) method.</span></span> <span data-ttu-id="849a0-133">当实现一个 cmdlet 时，您必须重写的至少一个[System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)， [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)，和[System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。</span><span class="sxs-lookup"><span data-stu-id="849a0-133">When you implement a cmdlet, you must override at least one of the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), and [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) methods.</span></span> <span data-ttu-id="849a0-134">通常情况下， [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法是您重写，因为调用 cmdlet 所处理的每条记录的方法。</span><span class="sxs-lookup"><span data-stu-id="849a0-134">Typically, the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is the method that you override because it is called for every record that the cmdlet processes.</span></span> <span data-ttu-id="849a0-135">与此相反， [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法并[System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法调用一次来执行预处理或后处理的记录。</span><span class="sxs-lookup"><span data-stu-id="849a0-135">In contrast, the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and the [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method are called one time to perform pre-processing or post-processing of the records.</span></span> <span data-ttu-id="849a0-136">有关这些方法的详细信息，请参阅[输入处理方法](./cmdlet-input-processing-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="849a0-136">For more information about these methods, see [Input Processing Methods](./cmdlet-input-processing-methods.md).</span></span>

- <span data-ttu-id="849a0-137">**ShouldProcess 功能**:Windows PowerShell，可创建该 cmdlet 对系统进行更改之前提示用户提供反馈的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="849a0-137">**ShouldProcess feature**: Windows PowerShell allows you to create cmdlets that prompt the user for feedback before the cmdlet makes a change to the system.</span></span> <span data-ttu-id="849a0-138">若要使用此功能，该 cmdlet 必须声明它时声明 Cmdlet 特性和必须调用该 cmdlet 支持 ShouldProcess 功能[System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)从输入处理方法中的方法。</span><span class="sxs-lookup"><span data-stu-id="849a0-138">To use this feature, the cmdlet must declare that it supports the ShouldProcess feature when you declare the Cmdlet attribute, and the cmdlet must call the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods from within an input processing method.</span></span> <span data-ttu-id="849a0-139">有关如何支持 ShouldProcess 功能的详细信息，请参阅[请求确认](./requesting-confirmation-from-cmdlets.md)。</span><span class="sxs-lookup"><span data-stu-id="849a0-139">For more information about how to support the ShouldProcess functionality, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

- <span data-ttu-id="849a0-140">**事务**:逻辑组将被视为单个任务的命令。</span><span class="sxs-lookup"><span data-stu-id="849a0-140">**Transaction**: A logical group of commands that are treated as a single task.</span></span> <span data-ttu-id="849a0-141">如果组中的任何命令失败，并且用户可以选择接受或拒绝在事务中执行的操作，则任务自动失败。</span><span class="sxs-lookup"><span data-stu-id="849a0-141">The task automatically fails if any command in the group fails, and the user has the choice to accept or reject the actions performed within the transaction.</span></span> <span data-ttu-id="849a0-142">若要参与事务，该 cmdlet 必须声明其支持事务，在声明 Cmdlet 属性。</span><span class="sxs-lookup"><span data-stu-id="849a0-142">To participate in a transaction, the cmdlet must declare that it supports transactions when the Cmdlet attribute is declared.</span></span> <span data-ttu-id="849a0-143">在 Windows PowerShell 2.0 中引入了对事务的支持。</span><span class="sxs-lookup"><span data-stu-id="849a0-143">Support for transactions was introduced in Windows PowerShell 2.0.</span></span> <span data-ttu-id="849a0-144">有关事务的详细信息，请参阅[Windows PowerShell 事务](http://msdn.microsoft.com/en-us/74d7bac7-bc53-49f1-a47a-272e8da84710)。</span><span class="sxs-lookup"><span data-stu-id="849a0-144">For more information about transactions, see [Windows PowerShell Transactions](http://msdn.microsoft.com/en-us/74d7bac7-bc53-49f1-a47a-272e8da84710).</span></span>

## <a name="how-cmdlets-differ-from-commands"></a><span data-ttu-id="849a0-145">与命令 Cmdlet 有何区别</span><span class="sxs-lookup"><span data-stu-id="849a0-145">How Cmdlets Differ from Commands</span></span>

<span data-ttu-id="849a0-146">Cmdlet 不同于其他命令行界面环境中的命令通过以下方式：</span><span class="sxs-lookup"><span data-stu-id="849a0-146">Cmdlets differ from commands in other command-shell environments in the following ways:</span></span>

- <span data-ttu-id="849a0-147">Cmdlet 是.NET Framework 类; 的实例它们不是独立的可执行文件。</span><span class="sxs-lookup"><span data-stu-id="849a0-147">Cmdlets are instances of .NET Framework classes; they are not stand-alone executables.</span></span>

- <span data-ttu-id="849a0-148">Cmdlet 可创建从一样少的代码的若干行。</span><span class="sxs-lookup"><span data-stu-id="849a0-148">Cmdlets can be created from as few as a dozen lines of code.</span></span>

- <span data-ttu-id="849a0-149">Cmdlet 通常执行其自己分析，错误演示文稿或输出格式设置。</span><span class="sxs-lookup"><span data-stu-id="849a0-149">Cmdlets do not generally do their own parsing, error presentation, or output formatting.</span></span> <span data-ttu-id="849a0-150">通过 Windows PowerShell 运行时处理分析、 错误演示文稿和输出格式设置。</span><span class="sxs-lookup"><span data-stu-id="849a0-150">Parsing, error presentation, and output formatting are handled by the Windows PowerShell runtime.</span></span>

- <span data-ttu-id="849a0-151">Cmdlet 处理输入对象通过管道而不是从的文本，流和 cmdlet 通常将作为输出到管道的对象。</span><span class="sxs-lookup"><span data-stu-id="849a0-151">Cmdlets process input objects from the pipeline rather than from streams of text, and cmdlets typically deliver objects as output to the pipeline.</span></span>

- <span data-ttu-id="849a0-152">Cmdlet 是面向记录的因为它们一次处理一个对象。</span><span class="sxs-lookup"><span data-stu-id="849a0-152">Cmdlets are record-oriented because they process a single object at a time.</span></span>

## <a name="cmdlet-base-classes"></a><span data-ttu-id="849a0-153">Cmdlet 基类</span><span class="sxs-lookup"><span data-stu-id="849a0-153">Cmdlet Base Classes</span></span>

<span data-ttu-id="849a0-154">Windows PowerShell 支持从以下两个基类派生的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="849a0-154">Windows PowerShell supports cmdlets that are derived from the following two base classes.</span></span>

- <span data-ttu-id="849a0-155">大多数 cmdlet 基于.NET Framework 类派生自[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)基类。</span><span class="sxs-lookup"><span data-stu-id="849a0-155">Most cmdlets are based on .NET Framework classes that derive from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span></span> <span data-ttu-id="849a0-156">从此类派生允许 cmdlet 在 Windows PowerShell 运行时上使用依赖项的最小集。</span><span class="sxs-lookup"><span data-stu-id="849a0-156">Deriving from this class allows a cmdlet to use the minimum set of dependencies on the Windows PowerShell runtime.</span></span> <span data-ttu-id="849a0-157">这有两个好处。</span><span class="sxs-lookup"><span data-stu-id="849a0-157">This has two benefits.</span></span> <span data-ttu-id="849a0-158">第一个优点是更小，cmdlet 对象并且不太可能更改 Windows PowerShell 运行时的影响。</span><span class="sxs-lookup"><span data-stu-id="849a0-158">The first benefit is that the cmdlet objects are smaller, and you are less likely to be affected by changes to the Windows PowerShell runtime.</span></span> <span data-ttu-id="849a0-159">第二个好处是，如果有必要，您可以直接创建 cmdlet 对象的实例，然后而通过 Windows PowerShell 运行时调用它不是直接调用它。</span><span class="sxs-lookup"><span data-stu-id="849a0-159">The second benefit is that, if you have to, you can directly create an instance of the cmdlet object and then invoke it directly instead of invoking it through the Windows PowerShell runtime.</span></span>

- <span data-ttu-id="849a0-160">更复杂 cmdlet 基于.NET Framework 类派生自[System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)基类。</span><span class="sxs-lookup"><span data-stu-id="849a0-160">The more-complex cmdlets are based on .NET Framework classes that derive from the [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span> <span data-ttu-id="849a0-161">从此类派生可使您更多访问 Windows PowerShell 运行时。</span><span class="sxs-lookup"><span data-stu-id="849a0-161">Deriving from this class gives you much more access to the Windows PowerShell runtime.</span></span> <span data-ttu-id="849a0-162">此访问权限允许您 cmdlet 来调用脚本，来访问提供程序，并访问当前会话状态。</span><span class="sxs-lookup"><span data-stu-id="849a0-162">This access allows your cmdlet to call scripts, to access providers, and to access the current session state.</span></span> <span data-ttu-id="849a0-163">（若要访问当前会话状态，获取和设置会话变量和首选项。）但是，从此类派生会增加 cmdlet 对象的大小，这意味着你的 cmdlet 更紧密地耦合到当前版本的 Windows PowerShell 运行时。</span><span class="sxs-lookup"><span data-stu-id="849a0-163">(To access the current session state, you get and set session variables and preferences.) However, deriving from this class increases the size of the cmdlet object, and it means that your cmdlet is more tightly coupled to the current version of the Windows PowerShell runtime.</span></span>

<span data-ttu-id="849a0-164">一般情况下，除非需要对 Windows PowerShell 运行时的扩展访问权限，否则您应派生自[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)类。</span><span class="sxs-lookup"><span data-stu-id="849a0-164">In general, unless you need the extended access to the Windows PowerShell runtime, you should derive from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="849a0-165">但是，Windows PowerShell 运行时具有 cmdlet 执行的广泛的日志记录的功能。</span><span class="sxs-lookup"><span data-stu-id="849a0-165">However, the Windows PowerShell runtime has extensive logging capabilities for the execution of cmdlets.</span></span> <span data-ttu-id="849a0-166">如果审核模型依赖于此日志记录，则可以禁止你从另一个 cmdlet 中的 cmdlet 执行通过派生自[System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)类。</span><span class="sxs-lookup"><span data-stu-id="849a0-166">If your auditing model depends on this logging, you can prevent the execution of your cmdlet from within another cmdlet by deriving from the [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

## <a name="input-processing-methods"></a><span data-ttu-id="849a0-167">输入处理方法</span><span class="sxs-lookup"><span data-stu-id="849a0-167">Input Processing Methods</span></span>

<span data-ttu-id="849a0-168">[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)类提供了以下用于处理记录的虚拟方法。</span><span class="sxs-lookup"><span data-stu-id="849a0-168">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides the following virtual methods that are used to process records.</span></span> <span data-ttu-id="849a0-169">一个或多个的前三个方法，则必须重写所有派生的 cmdlet 类：</span><span class="sxs-lookup"><span data-stu-id="849a0-169">All the derived cmdlet classes must override one or more of the first three methods:</span></span>

- <span data-ttu-id="849a0-170">[System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing):用于为 cmdlet 提供可选的一次性预处理功能。</span><span class="sxs-lookup"><span data-stu-id="849a0-170">[System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing): Used to provide optional one-time, pre-processing functionality for the cmdlet.</span></span>

- <span data-ttu-id="849a0-171">[System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord):用于为 cmdlet 提供按记录处理功能。</span><span class="sxs-lookup"><span data-stu-id="849a0-171">[System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord): Used to provide record-by-record processing functionality for the cmdlet.</span></span> <span data-ttu-id="849a0-172">[System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)可能调用方法的次数，或根本不，具体取决于该 cmdlet 的输入的任何数字。</span><span class="sxs-lookup"><span data-stu-id="849a0-172">The [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method might be called any number of times, or not at all, depending on the input of the cmdlet.</span></span>

- <span data-ttu-id="849a0-173">[System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing):用于为 cmdlet 提供可选的一次性后处理功能。</span><span class="sxs-lookup"><span data-stu-id="849a0-173">[System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing): Used to provide optional one-time, post-processing functionality for the cmdlet.</span></span>

- <span data-ttu-id="849a0-174">[System.Management.Automation.Cmdlet.Stopprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing):用于用户异步停止 cmdlet （例如，通过按 CTRL + C） 时停止处理。</span><span class="sxs-lookup"><span data-stu-id="849a0-174">[System.Management.Automation.Cmdlet.Stopprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing): Used to stop processing when the user stops the cmdlet asynchronously (for example,  by pressing CTRL+C).</span></span>

<span data-ttu-id="849a0-175">有关这些方法的详细信息，请参阅[Cmdlet 输入处理方法](./cmdlet-input-processing-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="849a0-175">For more information about these methods, see [Cmdlet Input Processing Methods](./cmdlet-input-processing-methods.md).</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="849a0-176">Cmdlet 属性</span><span class="sxs-lookup"><span data-stu-id="849a0-176">Cmdlet Attributes</span></span>

<span data-ttu-id="849a0-177">Windows PowerShell 会定义用于管理 cmdlet 并指定提供的 Windows PowerShell 和 cmdlet 可能需要的常用功能的多个.NET Framework 属性。</span><span class="sxs-lookup"><span data-stu-id="849a0-177">Windows PowerShell defines several .NET Framework attributes that are used to manage cmdlets and to specify common functionality that is provided by Windows PowerShell and that might be required by the cmdlet.</span></span> <span data-ttu-id="849a0-178">例如，属性用于将类指定 cmdlet，以指定的参数的 cmdlet，并请求的输入验证，以便 cmdlet 开发人员无需在其 cmdlet 代码中实现该功能。</span><span class="sxs-lookup"><span data-stu-id="849a0-178">For example, attributes are used to designate a class as a cmdlet, to specify the parameters of the cmdlet, and to request the validation of input so that cmdlet developers do not have to implement that functionality in their cmdlet code.</span></span> <span data-ttu-id="849a0-179">有关属性的详细信息，请参阅[Windows PowerShell 属性](./cmdlet-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="849a0-179">For more information about attributes, see [Windows PowerShell Attributes](./cmdlet-attributes.md).</span></span>

## <a name="cmdlet-names"></a><span data-ttu-id="849a0-180">Cmdlet 名称</span><span class="sxs-lookup"><span data-stu-id="849a0-180">Cmdlet Names</span></span>

<span data-ttu-id="849a0-181">Windows PowerShell 使用名称 cmdlet 的动词-名词名称对。</span><span class="sxs-lookup"><span data-stu-id="849a0-181">Windows PowerShell uses a verb-and-noun name pair to name cmdlets.</span></span> <span data-ttu-id="849a0-182">例如，`Get-Command`包含在 Windows PowerShell cmdlet 用于获取在命令行界面中注册的所有 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="849a0-182">For example, the `Get-Command` cmdlet included in Windows PowerShell is used to get all the cmdlets that are registered in the command shell.</span></span> <span data-ttu-id="849a0-183">谓词标识该 cmdlet 将执行，该操作，并 （） 名词，标识该 cmdlet 将在其执行其操作的资源。</span><span class="sxs-lookup"><span data-stu-id="849a0-183">The verb identifies the action that the cmdlet performs, and the noun identifies the resource on which the cmdlet performs its action.</span></span>

<span data-ttu-id="849a0-184">.NET Framework 类声明为一个 cmdlet 时指定这些名称。</span><span class="sxs-lookup"><span data-stu-id="849a0-184">These names are specified when the .NET Framework class is declared as a cmdlet.</span></span> <span data-ttu-id="849a0-185">有关如何声明为 cmdlet 的.NET Framework 类的详细信息，请参阅[Cmdlet 特性声明](./cmdlet-class-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="849a0-185">For more information about how to declare a .NET Framework class as a cmdlet, see [Cmdlet Attribute Declaration](./cmdlet-class-declaration.md).</span></span>

## <a name="writing-cmdlet-code"></a><span data-ttu-id="849a0-186">编写 Cmdlet 代码</span><span class="sxs-lookup"><span data-stu-id="849a0-186">Writing Cmdlet Code</span></span>

<span data-ttu-id="849a0-187">本文档提供了两种方式来了解如何编写 cmdlet 代码。</span><span class="sxs-lookup"><span data-stu-id="849a0-187">This document provides two ways to discover how cmdlet code is written.</span></span> <span data-ttu-id="849a0-188">如果想要查看代码而无需多解释，请参阅[Cmdlet 的示例代码](./examples-of-cmdlet-code.md)。</span><span class="sxs-lookup"><span data-stu-id="849a0-188">If you prefer to see the code without much explanation, see [Examples of Cmdlet Code](./examples-of-cmdlet-code.md).</span></span> <span data-ttu-id="849a0-189">如果需要有关代码的详细说明，请参阅[GetProc 教程](./getproc-tutorial.md)， [StopProc 教程](./stopproc-tutorial.md)，或[SelectStr 教程](./selectstr-tutorial.md)主题。</span><span class="sxs-lookup"><span data-stu-id="849a0-189">If you prefer more explanation about the code, see the [GetProc Tutorial](./getproc-tutorial.md),  [StopProc Tutorial](./stopproc-tutorial.md), or [SelectStr Tutorial](./selectstr-tutorial.md) topics.</span></span>

<span data-ttu-id="849a0-190">有关编写 cmdlet 的准则的详细信息，请参阅[Cmdlet 开发指导原则](./cmdlet-development-guidelines.md)。</span><span class="sxs-lookup"><span data-stu-id="849a0-190">For more information about the guidelines for writing cmdlets, see [Cmdlet Development Guidelines](./cmdlet-development-guidelines.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="849a0-191">另请参阅</span><span class="sxs-lookup"><span data-stu-id="849a0-191">See Also</span></span>

[<span data-ttu-id="849a0-192">Windows PowerShell Cmdlet 概念</span><span class="sxs-lookup"><span data-stu-id="849a0-192">Windows PowerShell Cmdlet Concepts</span></span>](./windows-powershell-cmdlet-concepts.md)

[<span data-ttu-id="849a0-193">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="849a0-193">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="849a0-194">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="849a0-194">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)