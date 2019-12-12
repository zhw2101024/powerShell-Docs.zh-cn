---
title: 将用户消息添加到 Cmdlet |Microsoft Docs
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
ms.openlocfilehash: 9079f40e75dae86c22fd8b4f8a45d501c6125498
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416025"
---
# <a name="adding-user-messages-to-your-cmdlet"></a><span data-ttu-id="e340a-102">向 Cmdlet 添加用户消息</span><span class="sxs-lookup"><span data-stu-id="e340a-102">Adding User Messages to Your Cmdlet</span></span>

<span data-ttu-id="e340a-103">Cmdlet 可以编写多种消息，Windows PowerShell 运行时可向用户显示这些消息。</span><span class="sxs-lookup"><span data-stu-id="e340a-103">Cmdlets can write several kinds of messages that can be displayed to the user by the Windows PowerShell runtime.</span></span> <span data-ttu-id="e340a-104">这些消息包括以下类型：</span><span class="sxs-lookup"><span data-stu-id="e340a-104">These messages include the following types:</span></span>

- <span data-ttu-id="e340a-105">包含常规用户信息的详细消息。</span><span class="sxs-lookup"><span data-stu-id="e340a-105">Verbose messages that contain general user information.</span></span>

- <span data-ttu-id="e340a-106">调试包含故障排除信息的消息。</span><span class="sxs-lookup"><span data-stu-id="e340a-106">Debug messages that contain troubleshooting information.</span></span>

- <span data-ttu-id="e340a-107">警告消息，其中包含 cmdlet 要执行可能产生意外结果的操作的通知。</span><span class="sxs-lookup"><span data-stu-id="e340a-107">Warning messages that contain a notification that the cmdlet is about to perform an operation that can have unexpected results.</span></span>

- <span data-ttu-id="e340a-108">进度报告消息，其中包含有关在执行耗时很长的操作时 cmdlet 已完成的工作量的信息。</span><span class="sxs-lookup"><span data-stu-id="e340a-108">Progress report messages that contain information about how much work the cmdlet has completed when performing an operation that takes a long time.</span></span>

<span data-ttu-id="e340a-109">Cmdlet 可以写入的消息数或 cmdlet 写入的消息类型没有限制。</span><span class="sxs-lookup"><span data-stu-id="e340a-109">There are no limits to the number of messages that your cmdlet can write or the type of messages that your cmdlet writes.</span></span> <span data-ttu-id="e340a-110">每条消息都是通过从 cmdlet 的输入处理方法中进行特定调用来编写的。</span><span class="sxs-lookup"><span data-stu-id="e340a-110">Each message is written by making a specific call from within the input processing method of your cmdlet.</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="e340a-111">定义 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e340a-111">Defining the Cmdlet</span></span>

<span data-ttu-id="e340a-112">创建 cmdlet 的第一步是始终命名 cmdlet 并声明实现 cmdlet 的 .NET 类。</span><span class="sxs-lookup"><span data-stu-id="e340a-112">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="e340a-113">任何类型的 cmdlet 都可以从其输入处理方法写入用户通知;因此，一般情况下，可以使用指示 cmdlet 执行的系统修改的任何谓词来命名此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e340a-113">Any sort of cmdlet can write user notifications from its input processing methods; so, in general, you can name this cmdlet using any verb that indicates what system modifications the cmdlet performs.</span></span> <span data-ttu-id="e340a-114">有关批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 谓词名称](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="e340a-114">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="e340a-115">停止过程 cmdlet 用于修改系统;因此，.NET 类的[CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)声明必须包含 `SupportsShouldProcess` attribute 关键字，并将设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="e340a-115">The Stop-Proc cmdlet is designed to modify the system; therefore, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration for the .NET class must include the `SupportsShouldProcess` attribute keyword and be set to `true`.</span></span>

<span data-ttu-id="e340a-116">下面的代码是此 Stop Proc cmdlet 类的定义。</span><span class="sxs-lookup"><span data-stu-id="e340a-116">The following code is the definition for this Stop-Proc cmdlet class.</span></span> <span data-ttu-id="e340a-117">有关此定义的详细信息，请参阅[创建修改系统的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="e340a-117">For more information about this definition, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="e340a-118">定义系统修改的参数</span><span class="sxs-lookup"><span data-stu-id="e340a-118">Defining Parameters for System Modification</span></span>

<span data-ttu-id="e340a-119">停止过程 cmdlet 定义三个参数： `Name`、`Force`和 `PassThru`。</span><span class="sxs-lookup"><span data-stu-id="e340a-119">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span> <span data-ttu-id="e340a-120">有关定义这些参数的详细信息，请参阅[创建修改系统的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="e340a-120">For more information about defining these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

<span data-ttu-id="e340a-121">下面是用于停止过程 cmdlet 的参数声明。</span><span class="sxs-lookup"><span data-stu-id="e340a-121">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="e340a-122">重写输入处理方法</span><span class="sxs-lookup"><span data-stu-id="e340a-122">Overriding an Input Processing Method</span></span>

<span data-ttu-id="e340a-123">Cmdlet 必须重写输入处理方法，最常见的方法是[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)。</span><span class="sxs-lookup"><span data-stu-id="e340a-123">Your cmdlet must override an input processing method, most often it will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="e340a-124">此 ProcessRecord cmdlet 将重写 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 输入处理方法。</span><span class="sxs-lookup"><span data-stu-id="e340a-124">This Stop-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) input processing method.</span></span> <span data-ttu-id="e340a-125">在此过程中，将调用来编写详细消息、调试消息和警告消息。</span><span class="sxs-lookup"><span data-stu-id="e340a-125">In this implementation of the Stop-Proc cmdlet, calls are made to write verbose messages, debug messages, and warning messages.</span></span>

> [!NOTE]
> <span data-ttu-id="e340a-126">有关此方法如何调用[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法的详细信息，请参阅[创建用于修改系统的 Cmdlet （& a）：创建用于修改系统的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="e340a-126">For more information about how this method calls the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="writing-a-verbose-message"></a><span data-ttu-id="e340a-127">编写详细消息</span><span class="sxs-lookup"><span data-stu-id="e340a-127">Writing a Verbose Message</span></span>

<span data-ttu-id="e340a-128">[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法用于写入与特定错误条件不相关的常规用户级别信息的情况。</span><span class="sxs-lookup"><span data-stu-id="e340a-128">The [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method is used to write general user-level information that is unrelated to specific error conditions.</span></span> <span data-ttu-id="e340a-129">然后，系统管理员可以使用该信息继续处理其他命令。</span><span class="sxs-lookup"><span data-stu-id="e340a-129">The system administrator can then use that information to continue processing other commands.</span></span> <span data-ttu-id="e340a-130">此外，使用此方法编写的任何信息都应该根据需要进行本地化。</span><span class="sxs-lookup"><span data-stu-id="e340a-130">In addition, any information written using this method should be localized as needed.</span></span>

<span data-ttu-id="e340a-131">此 Stop Proc cmdlet 中的以下代码演示了对[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法的两次调用，从[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的重写中的重写。</span><span class="sxs-lookup"><span data-stu-id="e340a-131">The following code from this Stop-Proc cmdlet shows two calls to the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a><span data-ttu-id="e340a-132">编写调试消息</span><span class="sxs-lookup"><span data-stu-id="e340a-132">Writing a Debug Message</span></span>

<span data-ttu-id="e340a-133">[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法用于编写调试消息，这些消息可用于排查 Cmdlet 的操作问题的问题。</span><span class="sxs-lookup"><span data-stu-id="e340a-133">The [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method is used to write debug messages that can be used to troubleshoot the operation of the cmdlet.</span></span> <span data-ttu-id="e340a-134">从输入处理方法进行调用。</span><span class="sxs-lookup"><span data-stu-id="e340a-134">The call is made from an input processing method.</span></span>

> [!NOTE]
> <span data-ttu-id="e340a-135">Windows PowerShell 还定义了一个 `Debug` 参数，用于提供详细信息和调试信息。</span><span class="sxs-lookup"><span data-stu-id="e340a-135">Windows PowerShell also defines a `Debug` parameter that presents both verbose and debug information.</span></span> <span data-ttu-id="e340a-136">如果你的 cmdlet 支持此参数，则它不需要在调用[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)的相同代码中调用[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) ，而不需要调用。</span><span class="sxs-lookup"><span data-stu-id="e340a-136">If your cmdlet supports this parameter, it does not need to call [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in the same code that calls [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

<span data-ttu-id="e340a-137">以下两个示例中的代码部分将从 [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 方法中调用，以从 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 方法的重写中，显示对方法的调用。</span><span class="sxs-lookup"><span data-stu-id="e340a-137">The following two sections of code from the sample Stop-Proc cmdlet show calls to the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="e340a-138">此调试消息将在调用[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)之前立即写入。</span><span class="sxs-lookup"><span data-stu-id="e340a-138">This debug message is written immediately before [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) is called.</span></span>

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

<span data-ttu-id="e340a-139">此调试消息将在调用[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)之前立即写入。</span><span class="sxs-lookup"><span data-stu-id="e340a-139">This debug message is written immediately before [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) is called.</span></span>

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

<span data-ttu-id="e340a-140">Windows PowerShell 会自动将任何[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)调用路由到跟踪基础结构和 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e340a-140">Windows PowerShell automatically routes any [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) calls to the tracing infrastructure and cmdlets.</span></span> <span data-ttu-id="e340a-141">这允许对宿主应用程序、文件或调试器跟踪方法调用，而无需在 cmdlet 中进行任何额外的开发工作。</span><span class="sxs-lookup"><span data-stu-id="e340a-141">This allows the method calls to be traced to the hosting application, a file, or a debugger without your having to do any extra development work within the cmdlet.</span></span> <span data-ttu-id="e340a-142">以下命令行项实现跟踪操作。</span><span class="sxs-lookup"><span data-stu-id="e340a-142">The following command-line entry implements a tracing operation.</span></span>

<span data-ttu-id="e340a-143">**PS > trace 表达式停止进程文件过程。日志命令停止-过程记事本**</span><span class="sxs-lookup"><span data-stu-id="e340a-143">**PS> trace-expression stop-proc -file proc.log -command stop-proc notepad**</span></span>

## <a name="writing-a-warning-message"></a><span data-ttu-id="e340a-144">写入警告消息</span><span class="sxs-lookup"><span data-stu-id="e340a-144">Writing a Warning Message</span></span>

<span data-ttu-id="e340a-145">当 Cmdlet 要执行可能产生意外结果的操作时（例如，覆盖只读文件），将使用[WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法来编写一条警告，并使用该方法。</span><span class="sxs-lookup"><span data-stu-id="e340a-145">The [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method is used to write a warning when the cmdlet is about to perform an operation that might have an unexpected result, for example, overwriting a read-only file.</span></span>

<span data-ttu-id="e340a-146">以下来自 [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) cmdlet 的代码演示了如何从 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 方法的重写调用中调用了对方法的调用的方法中。</span><span class="sxs-lookup"><span data-stu-id="e340a-146">The following code from the sample Stop-Proc cmdlet shows the call to the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a><span data-ttu-id="e340a-147">写入进度消息</span><span class="sxs-lookup"><span data-stu-id="e340a-147">Writing a Progress Message</span></span>

<span data-ttu-id="e340a-148">当 Cmdlet 操作需要很长时间才能完成时，将使用[WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)来写入进度消息。</span><span class="sxs-lookup"><span data-stu-id="e340a-148">The [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) is used to write progress messages when cmdlet operations take an extended amount of time to complete.</span></span> <span data-ttu-id="e340a-149">对[WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)的调用会传递发送到宿主应用程序的[Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord)对象，以便向用户呈现该对象的功能。</span><span class="sxs-lookup"><span data-stu-id="e340a-149">A call to [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passes a [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) object that is sent to the hosting application for rendering to the user.</span></span>

> [!NOTE]
> <span data-ttu-id="e340a-150">此 Stop Proc cmdlet 不包括对[WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)方法的调用。 "。</span><span class="sxs-lookup"><span data-stu-id="e340a-150">This Stop-Proc cmdlet does not include a call to the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

<span data-ttu-id="e340a-151">下面的代码示例是由尝试复制项的 cmdlet 编写的进度消息。</span><span class="sxs-lookup"><span data-stu-id="e340a-151">The following code is an example of a progress message written by a cmdlet that is attempting to copy an item.</span></span>

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a><span data-ttu-id="e340a-152">代码示例</span><span class="sxs-lookup"><span data-stu-id="e340a-152">Code Sample</span></span>

<span data-ttu-id="e340a-153">有关完整C#的示例代码，请参阅[StopProcessSample02 示例](./stopprocesssample02-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="e340a-153">For the complete C# sample code, see [StopProcessSample02 Sample](./stopprocesssample02-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="e340a-154">定义对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="e340a-154">Define Object Types and Formatting</span></span>

<span data-ttu-id="e340a-155">Windows PowerShell 使用 .NET 对象在 cmdlet 之间传递信息。</span><span class="sxs-lookup"><span data-stu-id="e340a-155">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="e340a-156">因此，cmdlet 可能需要定义自己的类型，或者该 cmdlet 可能需要扩展另一个 cmdlet 提供的现有类型。</span><span class="sxs-lookup"><span data-stu-id="e340a-156">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="e340a-157">有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式](/previous-versions//ms714665(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="e340a-157">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="e340a-158">构建 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e340a-158">Building the Cmdlet</span></span>

<span data-ttu-id="e340a-159">实现 cmdlet 后，必须通过 Windows PowerShell 管理单元向 Windows PowerShell 注册它。</span><span class="sxs-lookup"><span data-stu-id="e340a-159">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="e340a-160">有关注册 cmdlet 的详细信息，请参阅[如何注册 cmdlet、提供程序和主机应用程序](/previous-versions//ms714644(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="e340a-160">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="e340a-161">测试 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e340a-161">Testing the Cmdlet</span></span>

<span data-ttu-id="e340a-162">向 Windows PowerShell 注册 cmdlet 后，可以通过在命令行上运行 cmdlet 来对其进行测试。</span><span class="sxs-lookup"><span data-stu-id="e340a-162">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="e340a-163">接下来，请测试示例的停止过程 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e340a-163">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="e340a-164">有关从命令行使用 cmdlet 的详细信息，请参阅[使用 Windows PowerShell 的入门](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="e340a-164">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="e340a-165">以下命令行条目使用 Stop 进程来停止名为 "NOTEPAD" 的进程，提供详细通知并打印调试信息。</span><span class="sxs-lookup"><span data-stu-id="e340a-165">The following command-line entry uses Stop-Proc to stop the process named "NOTEPAD", provide verbose notifications, and print debug information.</span></span>

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

<span data-ttu-id="e340a-166">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="e340a-166">The following output appears.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e340a-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e340a-167">See Also</span></span>

[<span data-ttu-id="e340a-168">创建用于修改系统的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e340a-168">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="e340a-169">如何创建 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e340a-169">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="e340a-170">[扩展对象类型和格式](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="e340a-170">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="e340a-171">[如何注册 Cmdlet、提供程序和主机应用程序](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="e340a-171">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="e340a-172">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e340a-172">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
