---
title: 创建修改系统的 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- should process [PowerShell Programmer's Guide]
- should continue [PowerShell Programmer's Guide]
- user feedback [PowerShell Programmer's Guide]
- confirm impact [PowerShell Programmer's Guide]
ms.assetid: 59be4120-1700-4d92-a308-ef4a32ccf11a
caps.latest.revision: 8
ms.openlocfilehash: 8a65915b88a04e36e773853b903528a65fe11e99
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365756"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a><span data-ttu-id="6740d-102">创建用于修改系统的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6740d-102">Creating a Cmdlet that Modifies the System</span></span>

<span data-ttu-id="6740d-103">有时，cmdlet 必须修改系统的运行状态，而不只是 Windows PowerShell 运行时的状态。</span><span class="sxs-lookup"><span data-stu-id="6740d-103">Sometimes a cmdlet must modify the running state of the system, not just the state of the Windows PowerShell runtime.</span></span> <span data-ttu-id="6740d-104">在这些情况下，cmdlet 应该允许用户有机会确认是否要进行更改。</span><span class="sxs-lookup"><span data-stu-id="6740d-104">In these cases, the cmdlet should allow the user a chance to confirm whether or not to make the change.</span></span>

<span data-ttu-id="6740d-105">若要支持确认，cmdlet 必须执行两项操作。</span><span class="sxs-lookup"><span data-stu-id="6740d-105">To support confirmation a cmdlet must do two things.</span></span>

- <span data-ttu-id="6740d-106">声明通过将 SupportsShouldProcess 关键字设置为 `true`来指定[CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)属性时，cmdlet 支持确认。</span><span class="sxs-lookup"><span data-stu-id="6740d-106">Declare that the cmdlet supports confirmation when you specify the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute by setting the SupportsShouldProcess keyword to `true`.</span></span>

- <span data-ttu-id="6740d-107">在执行 Cmdlet 的过程中，请调用[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) （如以下示例中所示）。</span><span class="sxs-lookup"><span data-stu-id="6740d-107">Call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) during the execution of the cmdlet (as shown in the following example).</span></span>

<span data-ttu-id="6740d-108">通过支持确认，cmdlet 将公开 Windows PowerShell 提供的 `Confirm` 和 `WhatIf` 参数，同时满足 cmdlet 的开发准则（有关 cmdlet 开发指南的详细信息，请参阅[Cmdlet 开发指南](./cmdlet-development-guidelines.md)）。</span><span class="sxs-lookup"><span data-stu-id="6740d-108">By supporting confirmation, a cmdlet exposes the `Confirm` and `WhatIf` parameters that are provided by Windows PowerShell, and also meets the development guidelines for cmdlets (For more information about cmdlet development guidelines, see [Cmdlet Development Guidelines](./cmdlet-development-guidelines.md).).</span></span>

## <a name="changing-the-system"></a><span data-ttu-id="6740d-109">更改系统</span><span class="sxs-lookup"><span data-stu-id="6740d-109">Changing the System</span></span>

<span data-ttu-id="6740d-110">"更改系统" 的作用是指任何可能更改 Windows PowerShell 外部系统状态的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6740d-110">The act of "changing the system" refers to any cmdlet that potentially changes the state of the system outside Windows PowerShell.</span></span> <span data-ttu-id="6740d-111">例如，停止进程、启用或禁用用户帐户，或者向数据库表添加行都是对系统进行的所有更改。</span><span class="sxs-lookup"><span data-stu-id="6740d-111">For example, stopping a process, enabling or disabling a user account, or adding a row to a database table are all changes to the system that should be confirmed.</span></span> <span data-ttu-id="6740d-112">与此相反，读取数据或建立暂时性连接的操作不会更改系统，通常不需要确认。</span><span class="sxs-lookup"><span data-stu-id="6740d-112">In contrast, operations that read data or establish transient connections do not change the system and generally do not require confirmation.</span></span> <span data-ttu-id="6740d-113">对于其效果限制在 Windows PowerShell 运行时内的操作（如 `set-variable`），也不需要确认。</span><span class="sxs-lookup"><span data-stu-id="6740d-113">Confirmation is also not needed for actions whose effect is limited to inside the Windows PowerShell runtime, such as `set-variable`.</span></span> <span data-ttu-id="6740d-114">可能或可能不会进行永久更改的 cmdlet 应该仅在要进行持久更改时才声明 `SupportsShouldProcess` 和[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 。</span><span class="sxs-lookup"><span data-stu-id="6740d-114">Cmdlets that might or might not make a persistent change should declare `SupportsShouldProcess` and call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) only if they are about to make a persistent change.</span></span>

> [!NOTE]
> <span data-ttu-id="6740d-115">ShouldProcess 确认仅适用于 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6740d-115">ShouldProcess confirmation applies only to cmdlets.</span></span> <span data-ttu-id="6740d-116">如果命令或脚本通过直接调用 .NET 方法或属性，或在 Windows PowerShell 外部调用应用程序来修改系统的运行状态，则这种形式的确认将不可用。</span><span class="sxs-lookup"><span data-stu-id="6740d-116">If a command or script modifies the running state of a system by directly calling .NET methods or properties, or by calling applications outside of Windows PowerShell, this form of confirmation will not be available.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="6740d-117">StopProc Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6740d-117">The StopProc Cmdlet</span></span>

<span data-ttu-id="6740d-118">本主题介绍了一种停止过程 cmdlet，该 cmdlet 尝试使用 Get-help cmdlet （在[创建第一个 cmdlet](./creating-a-cmdlet-without-parameters.md)时介绍）来停止检索的进程。</span><span class="sxs-lookup"><span data-stu-id="6740d-118">This topic describes a Stop-Proc cmdlet that attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="6740d-119">定义 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6740d-119">Defining the Cmdlet</span></span>

<span data-ttu-id="6740d-120">创建 cmdlet 的第一步是始终命名 cmdlet 并声明实现 cmdlet 的 .NET 类。</span><span class="sxs-lookup"><span data-stu-id="6740d-120">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="6740d-121">因为你要编写一个 cmdlet 来更改系统，所以应该相应地对其进行命名。</span><span class="sxs-lookup"><span data-stu-id="6740d-121">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="6740d-122">此 cmdlet 将停止系统进程，因此在此处选择的谓词名称为 "Stop"，由[Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)类定义，名词 "Proc" 指示该 cmdlet 停止进程。</span><span class="sxs-lookup"><span data-stu-id="6740d-122">This cmdlet stops system processes, so the verb name chosen here is "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate that the cmdlet stops processes.</span></span> <span data-ttu-id="6740d-123">有关批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 谓词名称](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="6740d-123">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="6740d-124">下面是此 Stop Proc cmdlet 的类定义。</span><span class="sxs-lookup"><span data-stu-id="6740d-124">The following is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

<span data-ttu-id="6740d-125">请注意，在 [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) 声明中，`SupportsShouldProcess` attribute 关键字设置为 `true`，以使 cmdlet 能够对 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 和 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 进行调用，从而实现对和的调用的调用。</span><span class="sxs-lookup"><span data-stu-id="6740d-125">Be aware that in the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration, the `SupportsShouldProcess` attribute keyword is set to `true` to enable the cmdlet to make calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="6740d-126">如果未设置此关键字，则用户将无法使用 `Confirm` 和 `WhatIf` 参数。</span><span class="sxs-lookup"><span data-stu-id="6740d-126">Without this keyword set, the `Confirm` and `WhatIf` parameters will not be available to the user.</span></span>

### <a name="extremely-destructive-actions"></a><span data-ttu-id="6740d-127">极其破坏性操作</span><span class="sxs-lookup"><span data-stu-id="6740d-127">Extremely Destructive Actions</span></span>

<span data-ttu-id="6740d-128">有些操作非常有破坏性，如重新格式化活动硬盘分区。</span><span class="sxs-lookup"><span data-stu-id="6740d-128">Some operations are extremely destructive, such as reformatting an active hard disk partition.</span></span> <span data-ttu-id="6740d-129">在这些情况下，cmdlet 应在声明[CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)属性时设置 `ConfirmImpact` = `ConfirmImpact.High`。</span><span class="sxs-lookup"><span data-stu-id="6740d-129">In these cases, the cmdlet should set `ConfirmImpact` = `ConfirmImpact.High` when declaring the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute.</span></span> <span data-ttu-id="6740d-130">此设置强制 cmdlet 即使在用户未指定 `Confirm` 参数时也请求用户确认。</span><span class="sxs-lookup"><span data-stu-id="6740d-130">This setting forces the cmdlet to request user confirmation even when the user has not specified the `Confirm` parameter.</span></span> <span data-ttu-id="6740d-131">但是，cmdlet 开发人员应避免过度使用 `ConfirmImpact` 的操作，这些操作可能具有破坏性，如删除用户帐户。</span><span class="sxs-lookup"><span data-stu-id="6740d-131">However, cmdlet developers should avoid overusing `ConfirmImpact` for operations that are just potentially destructive, such as deleting a user account.</span></span> <span data-ttu-id="6740d-132">请记住，如果 `ConfirmImpact` 设置为[ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) **High**。</span><span class="sxs-lookup"><span data-stu-id="6740d-132">Remember that if `ConfirmImpact` is set to [System.Management.Automation.ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) **High**.</span></span>

<span data-ttu-id="6740d-133">同样，某些操作不太可能是破坏性的，尽管它们在理论上是在 Windows PowerShell 之外修改系统的运行状态。</span><span class="sxs-lookup"><span data-stu-id="6740d-133">Similarly, some operations are unlikely to be destructive, although they do in theory modify the running state of a system outside Windows PowerShell.</span></span> <span data-ttu-id="6740d-134">此类 cmdlet 可将 `ConfirmImpact` 设置为[Confirmimpact](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0)。</span><span class="sxs-lookup"><span data-stu-id="6740d-134">Such cmdlets can set `ConfirmImpact` to [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span></span> <span data-ttu-id="6740d-135">这会绕过确认请求，用户只要求确认影响和影响最大的操作。</span><span class="sxs-lookup"><span data-stu-id="6740d-135">This will bypass confirmation requests where the user has asked to confirm only medium-impact and high-impact operations.</span></span>

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="6740d-136">定义系统修改的参数</span><span class="sxs-lookup"><span data-stu-id="6740d-136">Defining Parameters for System Modification</span></span>

<span data-ttu-id="6740d-137">本部分介绍如何定义 cmdlet 参数，包括支持系统修改所需的参数。</span><span class="sxs-lookup"><span data-stu-id="6740d-137">This section describes how to define the cmdlet parameters, including those that are needed to support system modification.</span></span> <span data-ttu-id="6740d-138">如果需要有关定义参数的常规信息，请参阅[添加处理命令行输入的参数](./adding-parameters-that-process-command-line-input.md)。</span><span class="sxs-lookup"><span data-stu-id="6740d-138">See [Adding Parameters that Process CommandLine Input](./adding-parameters-that-process-command-line-input.md) if you need general information about defining parameters.</span></span>

<span data-ttu-id="6740d-139">停止过程 cmdlet 定义三个参数： `Name`、`Force`和 `PassThru`。</span><span class="sxs-lookup"><span data-stu-id="6740d-139">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span>

<span data-ttu-id="6740d-140">`Name` 参数对应于进程输入对象的 `Name` 属性。</span><span class="sxs-lookup"><span data-stu-id="6740d-140">The `Name` parameter corresponds to the `Name` property of the process input object.</span></span> <span data-ttu-id="6740d-141">请注意，此示例中的 `Name` 参数是必需的，因为如果没有要停止的命名进程，cmdlet 将失败。</span><span class="sxs-lookup"><span data-stu-id="6740d-141">Be aware that the `Name` parameter in this sample is mandatory, as the cmdlet will fail if it does not have a named process to stop.</span></span>

<span data-ttu-id="6740d-142">`Force` 参数允许用户重写对[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)的调用。）</span><span class="sxs-lookup"><span data-stu-id="6740d-142">The `Force` parameter allows the user to override calls to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="6740d-143">事实上，调用 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 的任何 cmdlet 都应具有一个 `Force` 参数，以便在指定 `Force` 时，该 cmdlet 将跳过对 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 的调用。 继续执行该操作。</span><span class="sxs-lookup"><span data-stu-id="6740d-143">In fact, any cmdlet that calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) should have a `Force` parameter so that when `Force` is specified, the cmdlet skips the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) and proceeds with the operation.</span></span> <span data-ttu-id="6740d-144">请注意，这不会影响对[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)的调用。</span><span class="sxs-lookup"><span data-stu-id="6740d-144">Be aware that this does not affect calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span></span>

<span data-ttu-id="6740d-145">`PassThru` 参数允许用户指示 cmdlet 是否通过管道传递输出对象，在这种情况下，进程停止后。</span><span class="sxs-lookup"><span data-stu-id="6740d-145">The `PassThru` parameter allows the user to indicate whether the cmdlet passes an output object through the pipeline, in this case, after a process is stopped.</span></span> <span data-ttu-id="6740d-146">请注意，此参数绑定到 cmdlet 本身，而不是绑定到输入对象的属性。</span><span class="sxs-lookup"><span data-stu-id="6740d-146">Be aware that this parameter is tied to the cmdlet itself instead of to a property of the input object.</span></span>

<span data-ttu-id="6740d-147">下面是用于停止过程 cmdlet 的参数声明。</span><span class="sxs-lookup"><span data-stu-id="6740d-147">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="6740d-148">重写输入处理方法</span><span class="sxs-lookup"><span data-stu-id="6740d-148">Overriding an Input Processing Method</span></span>

<span data-ttu-id="6740d-149">该 cmdlet 必须重写输入处理方法。</span><span class="sxs-lookup"><span data-stu-id="6740d-149">The cmdlet must override an input processing method.</span></span> <span data-ttu-id="6740d-150">下面的代码演示了示例 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Cmdlet 中使用的重写。</span><span class="sxs-lookup"><span data-stu-id="6740d-150">The following code illustrates the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override used in the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="6740d-151">对于每个请求的进程名称，此方法可确保该进程不是一个特殊的进程，尝试停止该进程，然后发送一个输出对象（如果指定了 `PassThru` 参数）。</span><span class="sxs-lookup"><span data-stu-id="6740d-151">For each requested process name, this method ensures that the process is not a special process, tries to stop the process, and then sends an output object if the `PassThru` parameter is specified.</span></span>

```csharp
protected override void ProcessRecord()
{
  foreach (string name in processNames)
  {
    // For every process name passed to the cmdlet, get the associated
    // process(es). For failures, write a non-terminating error
    Process[] processes;

    try
    {
      processes = Process.GetProcessesByName(name);
    }
    catch (InvalidOperationException ioe)
    {
      WriteError(new ErrorRecord(ioe,"Unable to access the target process by name",
                 ErrorCategory.InvalidOperation, name));
      continue;
    }

    // Try to stop the process(es) that have been retrieved for a name
    foreach (Process process in processes)
    {
      string processName;

      try
      {
        processName = process.ProcessName;
      }

      catch (Win32Exception e)
        {
          WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                     ErrorCategory.ReadError, process));
          continue;
        }

        // Call Should Process to confirm the operation first.
        // This is always false if WhatIf is set.
        if (!ShouldProcess(string.Format("{0} ({1})", processName,
                           process.Id)))
        {
          continue;
        }
        // Call ShouldContinue to make sure the user really does want
        // to stop a critical process that could possibly stop the computer.
        bool criticalProcess =
             criticalProcessNames.Contains(processName.ToLower());

        if (criticalProcess &&!force)
        {
          string message = String.Format
                ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                processName);

          // It is possible that ProcessRecord is called multiple times
          // when the Name parameter receives objects as input from the
          // pipeline. So to retain YesToAll and NoToAll input that the
          // user may enter across multiple calls to ProcessRecord, this
          // information is stored as private members of the cmdlet.
          if (!ShouldContinue(message, "Warning!",
                              ref yesToAll,
                              ref noToAll))
          {
            continue;
          }
        } // if (criticalProcess...
        // Stop the named process.
        try
        {
          process.Kill();
        }
        catch (Exception e)
        {
          if ((e is Win32Exception) || (e is SystemException) ||
              (e is InvalidOperationException))
          {
            // This process could not be stopped so write
            // a non-terminating error.
            string message = String.Format("{0} {1} {2}",
                             "Could not stop process \"", processName,
                             "\".");
            WriteError(new ErrorRecord(e, message,
                       ErrorCategory.CloseError, process));
                       continue;
          } // if ((e is...
          else throw;
        } // catch

        // If the PassThru parameter argument is
        // True, pass the terminated process on.
        if (passThru)
        {
          WriteObject(process);
        }
    } // foreach (Process...
  } // foreach (string...
} // ProcessRecord
```

## <a name="calling-the-shouldprocess-method"></a><span data-ttu-id="6740d-152">调用 ShouldProcess 方法</span><span class="sxs-lookup"><span data-stu-id="6740d-152">Calling the ShouldProcess Method</span></span>

<span data-ttu-id="6740d-153">Cmdlet 的输入处理方法应调用[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法，以确认在更改之前（例如，删除文件）对系统运行状态进行的操作的执行操作是否正常。</span><span class="sxs-lookup"><span data-stu-id="6740d-153">The input processing method of your cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to confirm execution of an operation before a change (for example, deleting files) is made to the running state of the system.</span></span> <span data-ttu-id="6740d-154">这允许 Windows PowerShell 运行时在 shell 内提供正确的 "WhatIf" 和 "Confirm" 行为。</span><span class="sxs-lookup"><span data-stu-id="6740d-154">This allows the Windows PowerShell runtime to supply the correct "WhatIf" and "Confirm" behavior within the shell.</span></span>

> [!NOTE]
> <span data-ttu-id="6740d-155">如果某个 cmdlet 指出它支持的操作应该处理并无法进行[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用，则用户可能会意外地修改系统。</span><span class="sxs-lookup"><span data-stu-id="6740d-155">If a cmdlet states that it supports should process and fails to make the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, the user might modify the system unexpectedly.</span></span>

<span data-ttu-id="6740d-156">对[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)的调用会发送要更改为用户的资源的名称，并且 Windows PowerShell 运行时在确定应该向用户显示的内容时考虑了任何命令行设置或首选项变量。</span><span class="sxs-lookup"><span data-stu-id="6740d-156">The call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command-line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="6740d-157">下面的示例演示了如何调用[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ，以便从示例停止过程 Cmdlet 中的[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的重写中调用该方法的调用。</span><span class="sxs-lookup"><span data-stu-id="6740d-157">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="6740d-158">调用 ShouldContinue 方法</span><span class="sxs-lookup"><span data-stu-id="6740d-158">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="6740d-159">对[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法的调用会向用户发送一条辅助消息。</span><span class="sxs-lookup"><span data-stu-id="6740d-159">The call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method sends a secondary message to the user.</span></span> <span data-ttu-id="6740d-160">如果 `Force` 参数未设置为 `true`，则在对 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 的调用 `true` 返回后，就会调用 。</span><span class="sxs-lookup"><span data-stu-id="6740d-160">This call is made after the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returns `true` and if the `Force` parameter was not set to `true`.</span></span> <span data-ttu-id="6740d-161">然后，用户可以提供反馈来指出是否应继续操作。</span><span class="sxs-lookup"><span data-stu-id="6740d-161">The user can then provide feedback to say whether the operation should be continued.</span></span> <span data-ttu-id="6740d-162">你的 cmdlet 会调用[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)作为额外的检查，以查看是否存在潜在的危险系统修改，或者你希望为用户提供 "全部" 和 "无" 选项。</span><span class="sxs-lookup"><span data-stu-id="6740d-162">Your cmdlet calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) as an additional check for potentially dangerous system modifications or when you want to provide yes-to-all and no-to-all options to the user.</span></span>

<span data-ttu-id="6740d-163">下面的示例演示了如何调用[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) ，以便从示例停止过程 Cmdlet 中的[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的重写中调用该方法的调用。</span><span class="sxs-lookup"><span data-stu-id="6740d-163">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (criticalProcess &&!force)
{
  string message = String.Format
        ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
        processName);

  // It is possible that ProcessRecord is called multiple times
  // when the Name parameter receives objects as input from the
  // pipeline. So to retain YesToAll and NoToAll input that the
  // user may enter across multiple calls to ProcessRecord, this
  // information is stored as private members of the cmdlet.
  if (!ShouldContinue(message, "Warning!",
                      ref yesToAll,
                      ref noToAll))
  {
    continue;
  }
} // if (criticalProcess...
```

## <a name="stopping-input-processing"></a><span data-ttu-id="6740d-164">正在停止输入处理</span><span class="sxs-lookup"><span data-stu-id="6740d-164">Stopping Input Processing</span></span>

<span data-ttu-id="6740d-165">进行系统修改的 cmdlet 的输入处理方法必须提供一种方法来停止处理输入。</span><span class="sxs-lookup"><span data-stu-id="6740d-165">The input processing method of a cmdlet that makes system modifications must provide a way of stopping the processing of input.</span></span> <span data-ttu-id="6740d-166">对于这种停止过程 cmdlet，将从[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法发出到 system.exception [\*](/dotnet/api/System.Diagnostics.Process.Kill)方法的调用。 "..." 的方法是。</span><span class="sxs-lookup"><span data-stu-id="6740d-166">In the case of this Stop-Proc cmdlet, a call is made from the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to the [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) method.</span></span> <span data-ttu-id="6740d-167">由于将 `PassThru` 参数设置为 `true`，因此 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 还会调用 [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)，以将进程对象发送到管道中的对象。</span><span class="sxs-lookup"><span data-stu-id="6740d-167">Because the `PassThru` parameter is set to `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) also calls [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) to send the process object to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="6740d-168">代码示例</span><span class="sxs-lookup"><span data-stu-id="6740d-168">Code Sample</span></span>

<span data-ttu-id="6740d-169">有关完整C#的示例代码，请参阅[StopProcessSample01 示例](./stopprocesssample01-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="6740d-169">For the complete C# sample code, see [StopProcessSample01 Sample](./stopprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="6740d-170">定义对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="6740d-170">Defining Object Types and Formatting</span></span>

<span data-ttu-id="6740d-171">Windows PowerShell 使用 .Net 对象在 cmdlet 之间传递信息。</span><span class="sxs-lookup"><span data-stu-id="6740d-171">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="6740d-172">因此，cmdlet 可能需要定义自己的类型，或者该 cmdlet 可能需要扩展另一个 cmdlet 提供的现有类型。</span><span class="sxs-lookup"><span data-stu-id="6740d-172">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="6740d-173">有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式](/previous-versions//ms714665(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="6740d-173">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="6740d-174">构建 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6740d-174">Building the Cmdlet</span></span>

<span data-ttu-id="6740d-175">实现 cmdlet 后，必须通过 Windows PowerShell 管理单元向 Windows PowerShell 注册它。</span><span class="sxs-lookup"><span data-stu-id="6740d-175">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="6740d-176">有关注册 cmdlet 的详细信息，请参阅[如何注册 cmdlet、提供程序和主机应用程序](/previous-versions//ms714644(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="6740d-176">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="6740d-177">测试 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6740d-177">Testing the Cmdlet</span></span>

<span data-ttu-id="6740d-178">向 Windows PowerShell 注册 cmdlet 后，可以通过在命令行上运行 cmdlet 来对其进行测试。</span><span class="sxs-lookup"><span data-stu-id="6740d-178">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="6740d-179">下面是测试停止过程 cmdlet 的几个测试。</span><span class="sxs-lookup"><span data-stu-id="6740d-179">Here are several tests that test the Stop-Proc cmdlet.</span></span> <span data-ttu-id="6740d-180">有关从命令行使用 cmdlet 的详细信息，请参阅[使用 Windows PowerShell 的入门](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="6740d-180">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="6740d-181">启动 Windows PowerShell 并使用 Stop Proc cmdlet 停止处理，如下所示。</span><span class="sxs-lookup"><span data-stu-id="6740d-181">Start Windows PowerShell and use the Stop-Proc cmdlet to stop processing as shown below.</span></span> <span data-ttu-id="6740d-182">由于该 cmdlet 将 `Name` 参数指定为必需，因此该 cmdlet 会查询参数。</span><span class="sxs-lookup"><span data-stu-id="6740d-182">Because the cmdlet specifies the `Name` parameter as mandatory, the cmdlet queries for the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="6740d-183">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="6740d-183">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- <span data-ttu-id="6740d-184">现在，让我们使用 cmdlet 来停止名为 "NOTEPAD" 的进程。</span><span class="sxs-lookup"><span data-stu-id="6740d-184">Now let's use the cmdlet to stop the process named "NOTEPAD".</span></span> <span data-ttu-id="6740d-185">Cmdlet 会要求你确认操作。</span><span class="sxs-lookup"><span data-stu-id="6740d-185">The cmdlet asks you to confirm the action.</span></span>

    ```powershell
    PS> stop-proc -Name notepad
    ```

<span data-ttu-id="6740d-186">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="6740d-186">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="6740d-187">使用所示的停止进程来停止名为 "WINLOGON" 的关键进程。</span><span class="sxs-lookup"><span data-stu-id="6740d-187">Use Stop-Proc as shown to stop the critical process named "WINLOGON".</span></span> <span data-ttu-id="6740d-188">系统将提示您执行此操作，并向您发出警告，因为这会导致操作系统重启。</span><span class="sxs-lookup"><span data-stu-id="6740d-188">You are prompted and warned about performing this action because it will cause the operating system to reboot.</span></span>

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

<span data-ttu-id="6740d-189">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="6740d-189">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- <span data-ttu-id="6740d-190">现在，让我们尝试停止 WINLOGON 进程，而不会收到警告。</span><span class="sxs-lookup"><span data-stu-id="6740d-190">Let's now try to stop the WINLOGON process without receiving a warning.</span></span> <span data-ttu-id="6740d-191">请注意，此命令项使用 `Force` 参数来覆盖该警告。</span><span class="sxs-lookup"><span data-stu-id="6740d-191">Be aware that this command entry uses the `Force` parameter to override the warning.</span></span>

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

<span data-ttu-id="6740d-192">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="6740d-192">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="6740d-193">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6740d-193">See Also</span></span>

[<span data-ttu-id="6740d-194">添加用于处理命令行输入的参数</span><span class="sxs-lookup"><span data-stu-id="6740d-194">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

<span data-ttu-id="6740d-195">[扩展对象类型和格式](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="6740d-195">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="6740d-196">[如何注册 Cmdlet、提供程序和主机应用程序](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="6740d-196">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="6740d-197">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="6740d-197">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="6740d-198">Cmdlet 示例</span><span class="sxs-lookup"><span data-stu-id="6740d-198">Cmdlet Samples</span></span>](./cmdlet-samples.md)