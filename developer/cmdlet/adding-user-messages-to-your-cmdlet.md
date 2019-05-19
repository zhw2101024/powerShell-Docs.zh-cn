---
title: 将用户消息添加到你的 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WriteWarning
- notifications, writing
- progress notification
- WriteVerbose
- Stop-Proc
- WriteProgress
- WriteDebug
- notifications, debug
- ProgressRecord
- samples, Stop-Proc cmdlet
- notifications, progress
- notifications, warning
- WriteObject
- WriteError
- verbose notification
- ProcessRecord
- notifications, verbose
- debug notification
- cmdlet, writing notifications
- warning
- code sample, user notifications
- user notifications
ms.assetid: 14c13acb-f0b7-4613-bc7d-c361d14da1a2
caps.latest.revision: 8
ms.openlocfilehash: 138c6a43937e72fffaa2a09243e500e9822e6111
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854935"
---
# <a name="adding-user-messages-to-your-cmdlet"></a><span data-ttu-id="126e5-102">向 Cmdlet 添加用户消息</span><span class="sxs-lookup"><span data-stu-id="126e5-102">Adding User Messages to Your Cmdlet</span></span>

<span data-ttu-id="126e5-103">Cmdlet 可以编写多种类型的可由 Windows PowerShell 运行时向用户显示的消息。</span><span class="sxs-lookup"><span data-stu-id="126e5-103">Cmdlets can write several kinds of messages that can be displayed to the user by the Windows PowerShell runtime.</span></span> <span data-ttu-id="126e5-104">这些消息包括以下类型：</span><span class="sxs-lookup"><span data-stu-id="126e5-104">These messages include the following types:</span></span>

- <span data-ttu-id="126e5-105">包含常规用户信息的详细信息。</span><span class="sxs-lookup"><span data-stu-id="126e5-105">Verbose messages that contain general user information.</span></span>

- <span data-ttu-id="126e5-106">调试包含故障排除信息的消息。</span><span class="sxs-lookup"><span data-stu-id="126e5-106">Debug messages that contain troubleshooting information.</span></span>

- <span data-ttu-id="126e5-107">警告消息包含一条通知，该 cmdlet 即将执行的操作可以具有意外的结果。</span><span class="sxs-lookup"><span data-stu-id="126e5-107">Warning messages that contain a notification that the cmdlet is about to perform an operation that can have unexpected results.</span></span>

- <span data-ttu-id="126e5-108">包含数量相关信息的消息处理该 cmdlet 的进度报告已完成时执行时间较长的操作。</span><span class="sxs-lookup"><span data-stu-id="126e5-108">Progress report messages that contain information about how much work the cmdlet has completed when performing an operation that takes a long time.</span></span>

<span data-ttu-id="126e5-109">没有针对你的 cmdlet 可以写入的消息数或的 cmdlet 将写入的消息类型的限制。</span><span class="sxs-lookup"><span data-stu-id="126e5-109">There are no limits to the number of messages that your cmdlet can write or the type of messages that your cmdlet writes.</span></span> <span data-ttu-id="126e5-110">中的输入处理方法的 cmdlet 从特定的调用，从而写入每条消息。</span><span class="sxs-lookup"><span data-stu-id="126e5-110">Each message is written by making a specific call from within the input processing method of your cmdlet.</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="126e5-111">定义 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="126e5-111">Defining the Cmdlet</span></span>

<span data-ttu-id="126e5-112">Cmdlet 创建的第一步是始终命名 cmdlet 和实现该 cmdlet 的.NET 类声明。</span><span class="sxs-lookup"><span data-stu-id="126e5-112">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="126e5-113">任何类型的 cmdlet 可以从其输入处理方法; 这些方法中编写用户通知因此，一般情况下，您可以命名使用任何谓词，指示该 cmdlet 将执行哪些系统修改此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="126e5-113">Any sort of cmdlet can write user notifications from its input processing methods; so, in general, you can name this cmdlet using any verb that indicates what system modifications the cmdlet performs.</span></span> <span data-ttu-id="126e5-114">有关已批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 的动词名称](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="126e5-114">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="126e5-115">停止进程 cmdlet 专门用于修改系统;因此， [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) .NET 类的声明必须包括`SupportsShouldProcess`属性关键字，并设置为`true`。</span><span class="sxs-lookup"><span data-stu-id="126e5-115">The Stop-Proc cmdlet is designed to modify the system; therefore, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration for the .NET class must include the `SupportsShouldProcess` attribute keyword and be set to `true`.</span></span>

<span data-ttu-id="126e5-116">以下代码是此停止进程 cmdlet 类的定义。</span><span class="sxs-lookup"><span data-stu-id="126e5-116">The following code is the definition for this Stop-Proc cmdlet class.</span></span> <span data-ttu-id="126e5-117">有关此定义的详细信息，请参阅[创建一个 Cmdlet 来修改系统](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="126e5-117">For more information about this definition, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="126e5-118">系统修改为定义参数</span><span class="sxs-lookup"><span data-stu-id="126e5-118">Defining Parameters for System Modification</span></span>

<span data-ttu-id="126e5-119">停止进程 cmdlet 定义了三个参数： `Name`， `Force`，和`PassThru`。</span><span class="sxs-lookup"><span data-stu-id="126e5-119">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span> <span data-ttu-id="126e5-120">有关定义这些参数的详细信息，请参阅[创建一个 Cmdlet 来修改系统](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="126e5-120">For more information about defining these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

<span data-ttu-id="126e5-121">下面是停止进程 cmdlet 的参数声明。</span><span class="sxs-lookup"><span data-stu-id="126e5-121">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

```csharp
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;

/// <summary>
/// Specify the Force parameter that allows the user to override
/// the ShouldContinue call to force the stop operation. This
/// parameter should always be used with caution.
/// </summary>
[Parameter]
public SwitchParameter Force
{
  get { return force; }
  set { force = value; }
}
private bool force;

/// <summary>
/// Specify the PassThru parameter that allows the user to specify
/// that the cmdlet should pass the process object down the pipeline
/// after the process has been stopped.
/// </summary>
[Parameter]
public SwitchParameter PassThru
{
  get { return passThru; }
  set { passThru = value; }
}
private bool passThru;
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="126e5-122">重写方法的处理的输入</span><span class="sxs-lookup"><span data-stu-id="126e5-122">Overriding an Input Processing Method</span></span>

<span data-ttu-id="126e5-123">你的 cmdlet 必须重写方法的处理的输入，则将其最常[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)。</span><span class="sxs-lookup"><span data-stu-id="126e5-123">Your cmdlet must override an input processing method, most often it will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="126e5-124">此停止进程 cmdlet 覆盖[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)输入处理方法。</span><span class="sxs-lookup"><span data-stu-id="126e5-124">This Stop-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) input processing method.</span></span> <span data-ttu-id="126e5-125">在停止进程 cmdlet 的此实现中，调用都要写入详细消息、 调试消息和警告消息。</span><span class="sxs-lookup"><span data-stu-id="126e5-125">In this implementation of the Stop-Proc cmdlet, calls are made to write verbose messages, debug messages, and warning messages.</span></span>

> [!NOTE]
> <span data-ttu-id="126e5-126">有关如何调用此方法的详细信息[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)并[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，请参阅[创建一个 Cmdlet 来修改系统](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="126e5-126">For more information about how this method calls the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="writing-a-verbose-message"></a><span data-ttu-id="126e5-127">写入详细消息</span><span class="sxs-lookup"><span data-stu-id="126e5-127">Writing a Verbose Message</span></span>

<span data-ttu-id="126e5-128">[System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法用于编写与特定的错误情况无关的常规用户级别信息。</span><span class="sxs-lookup"><span data-stu-id="126e5-128">The [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method is used to write general user-level information that is unrelated to specific error conditions.</span></span> <span data-ttu-id="126e5-129">然后，系统管理员可以使用该信息以继续处理其他命令。</span><span class="sxs-lookup"><span data-stu-id="126e5-129">The system administrator can then use that information to continue processing other commands.</span></span> <span data-ttu-id="126e5-130">此外，根据需要使用此方法编写的任何信息应该被本地化。</span><span class="sxs-lookup"><span data-stu-id="126e5-130">In addition, any information written using this method should be localized as needed.</span></span>

<span data-ttu-id="126e5-131">此停止进程 cmdlet 中的以下代码显示了两次调用[System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法的重写从[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。</span><span class="sxs-lookup"><span data-stu-id="126e5-131">The following code from this Stop-Proc cmdlet shows two calls to the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a><span data-ttu-id="126e5-132">写入调试消息</span><span class="sxs-lookup"><span data-stu-id="126e5-132">Writing a Debug Message</span></span>

<span data-ttu-id="126e5-133">[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法用于编写可用于排除该 cmdlet 的操作的问题的调试消息。</span><span class="sxs-lookup"><span data-stu-id="126e5-133">The [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method is used to write debug messages that can be used to troubleshoot the operation of the cmdlet.</span></span> <span data-ttu-id="126e5-134">从输入处理方法进行调用。</span><span class="sxs-lookup"><span data-stu-id="126e5-134">The call is made from an input processing method.</span></span>

> [!NOTE]
> <span data-ttu-id="126e5-135">Windows PowerShell 还定义`Debug`参数显示两者详细和调试信息。</span><span class="sxs-lookup"><span data-stu-id="126e5-135">Windows PowerShell also defines a `Debug` parameter that presents both verbose and debug information.</span></span> <span data-ttu-id="126e5-136">如果你的 cmdlet 支持此参数，它不需要调用[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)中调用的相同代码[System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span><span class="sxs-lookup"><span data-stu-id="126e5-136">If your cmdlet supports this parameter, it does not need to call [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in the same code that calls [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

<span data-ttu-id="126e5-137">以下两个部分的示例停止进程 cmdlet 中的代码显示调用[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法的重写从[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。</span><span class="sxs-lookup"><span data-stu-id="126e5-137">The following two sections of code from the sample Stop-Proc cmdlet show calls to the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="126e5-138">此调试消息写入之前[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用。</span><span class="sxs-lookup"><span data-stu-id="126e5-138">This debug message is written immediately before [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) is called.</span></span>

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

<span data-ttu-id="126e5-139">此调试消息写入之前[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)调用。</span><span class="sxs-lookup"><span data-stu-id="126e5-139">This debug message is written immediately before [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) is called.</span></span>

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

<span data-ttu-id="126e5-140">Windows PowerShell 会自动将任何路由[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)对跟踪基础结构和 cmdlet 的调用。</span><span class="sxs-lookup"><span data-stu-id="126e5-140">Windows PowerShell automatically routes any [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) calls to the tracing infrastructure and cmdlets.</span></span> <span data-ttu-id="126e5-141">这样，方法调用，而无需执行任何额外的开发工作中该 cmdlet 追溯到宿主应用程序、 文件或调试器。</span><span class="sxs-lookup"><span data-stu-id="126e5-141">This allows the method calls to be traced to the hosting application, a file, or a debugger without your having to do any extra development work within the cmdlet.</span></span> <span data-ttu-id="126e5-142">以下命令行条目实现跟踪操作。</span><span class="sxs-lookup"><span data-stu-id="126e5-142">The following command-line entry implements a tracing operation.</span></span>

<span data-ttu-id="126e5-143">**PS > 跟踪表达式停止的进程的文件 proc.log-命令停止进程记事本**</span><span class="sxs-lookup"><span data-stu-id="126e5-143">**PS> trace-expression stop-proc -file proc.log -command stop-proc notepad**</span></span>

## <a name="writing-a-warning-message"></a><span data-ttu-id="126e5-144">编写一条警告消息</span><span class="sxs-lookup"><span data-stu-id="126e5-144">Writing a Warning Message</span></span>

<span data-ttu-id="126e5-145">[System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法用于该 cmdlet 时要执行的操作可能具有意外的结果，例如，覆盖只读文件写入一条警告。</span><span class="sxs-lookup"><span data-stu-id="126e5-145">The [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method is used to write a warning when the cmdlet is about to perform an operation that might have an unexpected result, for example, overwriting a read-only file.</span></span>

<span data-ttu-id="126e5-146">示例停止进程 cmdlet 从下面的代码演示在调用[System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法的重写从[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。</span><span class="sxs-lookup"><span data-stu-id="126e5-146">The following code from the sample Stop-Proc cmdlet shows the call to the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a><span data-ttu-id="126e5-147">写入进度消息</span><span class="sxs-lookup"><span data-stu-id="126e5-147">Writing a Progress Message</span></span>

<span data-ttu-id="126e5-148">[System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)用于 cmdlet 操作需要较长的时间才能完成时写入进度消息。</span><span class="sxs-lookup"><span data-stu-id="126e5-148">The [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) is used to write progress messages when cmdlet operations take an extended amount of time to complete.</span></span> <span data-ttu-id="126e5-149">调用[System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)将传递[System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord)发送到主机应用程序向用户呈现的对象。</span><span class="sxs-lookup"><span data-stu-id="126e5-149">A call to [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passes a [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) object that is sent to the hosting application for rendering to the user.</span></span>

> [!NOTE]
> <span data-ttu-id="126e5-150">此停止进程 cmdlet 不包括调用[System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)方法。</span><span class="sxs-lookup"><span data-stu-id="126e5-150">This Stop-Proc cmdlet does not include a call to the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

<span data-ttu-id="126e5-151">以下代码是编写尝试将项复制一个 cmdlet 的进度消息的示例。</span><span class="sxs-lookup"><span data-stu-id="126e5-151">The following code is an example of a progress message written by a cmdlet that is attempting to copy an item.</span></span>

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a><span data-ttu-id="126e5-152">代码示例</span><span class="sxs-lookup"><span data-stu-id="126e5-152">Code Sample</span></span>

<span data-ttu-id="126e5-153">有关完整C#示例代码，请参阅[StopProcessSample02 示例](./stopprocesssample02-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="126e5-153">For the complete C# sample code, see [StopProcessSample02 Sample](./stopprocesssample02-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="126e5-154">定义对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="126e5-154">Define Object Types and Formatting</span></span>

<span data-ttu-id="126e5-155">Windows PowerShell cmdlet 使用.NET 对象之间传递信息。</span><span class="sxs-lookup"><span data-stu-id="126e5-155">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="126e5-156">因此，一个 cmdlet 可能需要定义其自己的类型，或者该 cmdlet 可能需要扩展现有类型提供的另一个 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="126e5-156">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="126e5-157">有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式设置](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。</span><span class="sxs-lookup"><span data-stu-id="126e5-157">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="126e5-158">生成该 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="126e5-158">Building the Cmdlet</span></span>

<span data-ttu-id="126e5-159">执行后一个 cmdlet，它必须向注册 Windows PowerShell 通过 Windows PowerShell 管理单元。</span><span class="sxs-lookup"><span data-stu-id="126e5-159">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="126e5-160">有关注册 cmdlet 的详细信息，请参阅[如何注册 Cmdlet、 提供商和主机应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="126e5-160">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="126e5-161">测试 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="126e5-161">Testing the Cmdlet</span></span>

<span data-ttu-id="126e5-162">当已使用 Windows PowerShell 注册你的 cmdlet 时，可以通过运行命令行上测试它。</span><span class="sxs-lookup"><span data-stu-id="126e5-162">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="126e5-163">让我们测试示例停止进程 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="126e5-163">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="126e5-164">有关使用命令行中的 cmdlet 的详细信息，请参阅[Windows PowerShell 入门学习](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="126e5-164">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="126e5-165">以下命令行条目使用停止的进程停止名为"NOTEPAD"的进程、 提供详细的通知，并打印调试信息。</span><span class="sxs-lookup"><span data-stu-id="126e5-165">The following command-line entry uses Stop-Proc to stop the process named "NOTEPAD", provide verbose notifications, and print debug information.</span></span>

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

<span data-ttu-id="126e5-166">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="126e5-166">The following output appears.</span></span>

    ```
    VERBOSE: Attempting to stop process " notepad ".
    DEBUG: Acquired name for pid 5584 : "notepad"

    Confirm
    Continue with this operation?
    [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): Y

    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (5584)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    VERBOSE: Stopped process "notepad", pid 5584.
    ```

## <a name="see-also"></a><span data-ttu-id="126e5-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="126e5-167">See Also</span></span>

[<span data-ttu-id="126e5-168">创建用于修改系统的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="126e5-168">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="126e5-169">如何创建 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="126e5-169">How to Create a Windows PowerShell Cmdlet</span></span>](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="126e5-170">扩展对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="126e5-170">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="126e5-171">如何注册 Cmdlet、 提供程序，和托管应用程序</span><span class="sxs-lookup"><span data-stu-id="126e5-171">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="126e5-172">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="126e5-172">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
