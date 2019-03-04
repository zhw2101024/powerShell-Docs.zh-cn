---
title: 创建一个 Cmdlet 来修改系统 |Microsoft Docs
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
ms.openlocfilehash: d93cc4a05a6625d073791c067d1e9b6662c3a565
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856333"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a><span data-ttu-id="c9016-102">创建用于修改系统的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c9016-102">Creating a Cmdlet that Modifies the System</span></span>

<span data-ttu-id="c9016-103">有时 cmdlet 必须修改系统，而不仅仅是 Windows PowerShell 运行时的状态的运行状态。</span><span class="sxs-lookup"><span data-stu-id="c9016-103">Sometimes a cmdlet must modify the running state of the system, not just the state of the Windows PowerShell runtime.</span></span> <span data-ttu-id="c9016-104">在这些情况下，该 cmdlet 应允许用户确认要进行更改的机会。</span><span class="sxs-lookup"><span data-stu-id="c9016-104">In these cases, the cmdlet should allow the user a chance to confirm whether or not to make the change.</span></span>

<span data-ttu-id="c9016-105">若要支持确认 cmdlet 必须做两件事。</span><span class="sxs-lookup"><span data-stu-id="c9016-105">To support confirmation a cmdlet must do two things.</span></span>

- <span data-ttu-id="c9016-106">声明指定时，该 cmdlet，支持确认[System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute)通过将 SupportsShouldProcess 关键字设置为属性`true`。</span><span class="sxs-lookup"><span data-stu-id="c9016-106">Declare that the cmdlet supports confirmation when you specify the [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute by setting the SupportsShouldProcess keyword to `true`.</span></span>

- <span data-ttu-id="c9016-107">调用[System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) cmdlet （如下面的示例中所示） 执行的过程。</span><span class="sxs-lookup"><span data-stu-id="c9016-107">Call [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) during the execution of the cmdlet (as shown in the following example).</span></span>

<span data-ttu-id="c9016-108">通过支持确认，cmdlet 公开`Confirm`和`WhatIf`参数提供的 Windows PowerShell，也满足 cmdlet 的开发准则 （有关 cmdlet 开发指导原则的详细信息，请参阅[Cmdlet 开发指导原则](./cmdlet-development-guidelines.md)。)。</span><span class="sxs-lookup"><span data-stu-id="c9016-108">By supporting confirmation, a cmdlet exposes the `Confirm` and `WhatIf` parameters that are provided by Windows PowerShell, and also meets the development guidelines for cmdlets (For more information about cmdlet development guidelines, see [Cmdlet Development Guidelines](./cmdlet-development-guidelines.md).).</span></span>

## <a name="changing-the-system"></a><span data-ttu-id="c9016-109">更改系统</span><span class="sxs-lookup"><span data-stu-id="c9016-109">Changing the System</span></span>

<span data-ttu-id="c9016-110">"更改系统"的操作是指任何 cmdlet 的 Windows PowerShell 外部系统的状态可能会更改。</span><span class="sxs-lookup"><span data-stu-id="c9016-110">The act of "changing the system" refers to any cmdlet that potentially changes the state of the system outside Windows PowerShell.</span></span> <span data-ttu-id="c9016-111">例如，正在停止过程，启用或禁用用户帐户，或添加到数据库表的行都应确认在系统的所有更改。</span><span class="sxs-lookup"><span data-stu-id="c9016-111">For example, stopping a process, enabling or disabling a user account, or adding a row to a database table are all changes to the system that should be confirmed.</span></span> <span data-ttu-id="c9016-112">与此相反，读取数据或建立暂时性连接的操作不会更改系统，并且通常不需要确认。</span><span class="sxs-lookup"><span data-stu-id="c9016-112">In contrast, operations that read data or establish transient connections do not change the system and generally do not require confirmation.</span></span> <span data-ttu-id="c9016-113">其效果仅限于在 Windows PowerShell 运行时，如操作也不需要确认`set-variable`。</span><span class="sxs-lookup"><span data-stu-id="c9016-113">Confirmation is also not needed for actions whose effect is limited to inside the Windows PowerShell runtime, such as `set-variable`.</span></span> <span data-ttu-id="c9016-114">Cmdlet 可能会或可能不提供持续性的更改应声明`SupportsShouldProcess`，并调用[System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)前提是这些要进行永久性更改。</span><span class="sxs-lookup"><span data-stu-id="c9016-114">Cmdlets that might or might not make a persistent change should declare `SupportsShouldProcess` and call [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) only if they are about to make a persistent change.</span></span>

> [!NOTE]
> <span data-ttu-id="c9016-115">ShouldProcess 确认仅适用于 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c9016-115">ShouldProcess confirmation applies only to cmdlets.</span></span> <span data-ttu-id="c9016-116">如果命令或脚本修改系统的运行状态，通过直接调用.NET 方法或属性，或者在 Windows PowerShell 之外调用应用程序，这种形式的确认将不可用。</span><span class="sxs-lookup"><span data-stu-id="c9016-116">If a command or script modifies the running state of a system by directly calling .NET methods or properties, or by calling applications outside of Windows PowerShell, this form of confirmation will not be available.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="c9016-117">StopProc Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c9016-117">The StopProc Cmdlet</span></span>

<span data-ttu-id="c9016-118">本主题介绍停止使用 Get-proc cmdlet 检索的进程会尝试停止进程 cmdlet (中所述[创建第一个 Cmdlet](./creating-a-cmdlet-without-parameters.md))。</span><span class="sxs-lookup"><span data-stu-id="c9016-118">This topic describes a Stop-Proc cmdlet that attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

<span data-ttu-id="c9016-119">在本部分中的主题包括：</span><span class="sxs-lookup"><span data-stu-id="c9016-119">Topics in this section include the following:</span></span>

- [<span data-ttu-id="c9016-120">定义 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c9016-120">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="c9016-121">系统修改为定义参数</span><span class="sxs-lookup"><span data-stu-id="c9016-121">Defining Parameters for System Modification</span></span>](#Defining-Parameters-for-System-Modification)

- [<span data-ttu-id="c9016-122">重写方法的处理的输入</span><span class="sxs-lookup"><span data-stu-id="c9016-122">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="c9016-123">调用 ShouldProcess 方法</span><span class="sxs-lookup"><span data-stu-id="c9016-123">Calling the ShouldProcess Method</span></span>](#Calling-the-ShouldProcess-Method)

- [<span data-ttu-id="c9016-124">调用 ShouldContinue 方法</span><span class="sxs-lookup"><span data-stu-id="c9016-124">Calling the ShouldContinue Method</span></span>](#Calling-the-ShouldContinue-Method)

- [<span data-ttu-id="c9016-125">正在停止输入的处理</span><span class="sxs-lookup"><span data-stu-id="c9016-125">Stopping Input Processing</span></span>](#Stopping-Input-Processing)

- [<span data-ttu-id="c9016-126">代码示例</span><span class="sxs-lookup"><span data-stu-id="c9016-126">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="c9016-127">定义对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="c9016-127">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="c9016-128">生成该 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c9016-128">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="c9016-129">测试 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c9016-129">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="c9016-130">定义 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c9016-130">Defining the Cmdlet</span></span>

<span data-ttu-id="c9016-131">Cmdlet 创建的第一步是始终命名 cmdlet 和实现该 cmdlet 的.NET 类声明。</span><span class="sxs-lookup"><span data-stu-id="c9016-131">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="c9016-132">因为你正在编写 cmdlet 来更改的系统，应相应地命名。</span><span class="sxs-lookup"><span data-stu-id="c9016-132">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="c9016-133">此 cmdlet 停止系统进程，因此在此处选择谓词名称是"停止"，定义[System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)类，使用名词"Proc"以指示该 cmdlet 停止的进程。</span><span class="sxs-lookup"><span data-stu-id="c9016-133">This cmdlet stops system processes, so the verb name chosen here is "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate that the cmdlet stops processes.</span></span> <span data-ttu-id="c9016-134">有关已批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 的动词名称](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="c9016-134">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="c9016-135">下面是此停止进程 cmdlet 的类定义。</span><span class="sxs-lookup"><span data-stu-id="c9016-135">The following is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

<span data-ttu-id="c9016-136">请注意，在[System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute)声明，`SupportsShouldProcess`属性关键字设置为`true`若要启用 cmdlet 来调用[System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)并[System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)。</span><span class="sxs-lookup"><span data-stu-id="c9016-136">Be aware that in the [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration, the `SupportsShouldProcess` attribute keyword is set to `true` to enable the cmdlet to make calls to [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="c9016-137">如果不设置此关键字，`Confirm`和`WhatIf`参数将不向用户提供。</span><span class="sxs-lookup"><span data-stu-id="c9016-137">Without this keyword set, the `Confirm` and `WhatIf` parameters will not be available to the user.</span></span>

### <a name="extremely-destructive-actions"></a><span data-ttu-id="c9016-138">极具破坏性操作</span><span class="sxs-lookup"><span data-stu-id="c9016-138">Extremely Destructive Actions</span></span>

<span data-ttu-id="c9016-139">某些操作是极具破坏性，如重新格式化活动硬盘分区。</span><span class="sxs-lookup"><span data-stu-id="c9016-139">Some operations are extremely destructive, such as reformatting an active hard disk partition.</span></span> <span data-ttu-id="c9016-140">在这些情况下，该 cmdlet 应设置`ConfirmImpact`  =  `ConfirmImpact.High`声明时[System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute)属性。</span><span class="sxs-lookup"><span data-stu-id="c9016-140">In these cases, the cmdlet should set `ConfirmImpact` = `ConfirmImpact.High` when declaring the [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute.</span></span> <span data-ttu-id="c9016-141">此设置为请求用户确认强制 cmdlet，即使用户未指定`Confirm`参数。</span><span class="sxs-lookup"><span data-stu-id="c9016-141">This setting forces the cmdlet to request user confirmation even when the user has not specified the `Confirm` parameter.</span></span> <span data-ttu-id="c9016-142">但是，cmdlet 开发人员应避免过度使用`ConfirmImpact`是只具有潜在破坏性，如删除用户帐户的操作。</span><span class="sxs-lookup"><span data-stu-id="c9016-142">However, cmdlet developers should avoid overusing `ConfirmImpact` for operations that are just potentially destructive, such as deleting a user account.</span></span> <span data-ttu-id="c9016-143">请记住，如果`ConfirmImpact`设置为[System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High)。</span><span class="sxs-lookup"><span data-stu-id="c9016-143">Remember that if `ConfirmImpact` is set to [System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High).</span></span>

<span data-ttu-id="c9016-144">同样，某些操作不太可能会破坏性，尽管它们在理论上修改 Windows PowerShell 外部系统的运行状态。</span><span class="sxs-lookup"><span data-stu-id="c9016-144">Similarly, some operations are unlikely to be destructive, although they do in theory modify the running state of a system outside Windows PowerShell.</span></span> <span data-ttu-id="c9016-145">此类 cmdlet 可以设置`ConfirmImpact`到[System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0)。</span><span class="sxs-lookup"><span data-stu-id="c9016-145">Such cmdlets can set `ConfirmImpact` to [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span></span> <span data-ttu-id="c9016-146">这将绕过其中已要求用户确认仅中影响和影响较大的操作的确认请求。</span><span class="sxs-lookup"><span data-stu-id="c9016-146">This will bypass confirmation requests where the user has asked to confirm only medium-impact and high-impact operations.</span></span>

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="c9016-147">系统修改为定义参数</span><span class="sxs-lookup"><span data-stu-id="c9016-147">Defining Parameters for System Modification</span></span>

<span data-ttu-id="c9016-148">本部分介绍如何定义 cmdlet 参数，包括所需的支持系统修改。</span><span class="sxs-lookup"><span data-stu-id="c9016-148">This section describes how to define the cmdlet parameters, including those that are needed to support system modification.</span></span> <span data-ttu-id="c9016-149">请参阅[添加该进程的命令行输入的参数](./adding-parameters-that-process-command-line-input.md)如果需要有关如何定义参数的常规信息。</span><span class="sxs-lookup"><span data-stu-id="c9016-149">See [Adding Parameters that Process CommandLine Input](./adding-parameters-that-process-command-line-input.md) if you need general information about defining parameters.</span></span>

<span data-ttu-id="c9016-150">停止进程 cmdlet 定义了三个参数： `Name`， `Force`，和`PassThru`。</span><span class="sxs-lookup"><span data-stu-id="c9016-150">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span>

<span data-ttu-id="c9016-151">`Name`参数对应于`Name`过程输入对象的属性。</span><span class="sxs-lookup"><span data-stu-id="c9016-151">The `Name` parameter corresponds to the `Name` property of the process input object.</span></span> <span data-ttu-id="c9016-152">请注意，`Name`在此示例中的参数是必需的因为如果它不具有已命名的进程停止，该 cmdlet 将会失败。</span><span class="sxs-lookup"><span data-stu-id="c9016-152">Be aware that the `Name` parameter in this sample is mandatory, as the cmdlet will fail if it does not have a named process to stop.</span></span>

<span data-ttu-id="c9016-153">`Force`参数允许用户重写调用[System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)。</span><span class="sxs-lookup"><span data-stu-id="c9016-153">The `Force` parameter allows the user to override calls to [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="c9016-154">事实上，用于调用的任何 cmdlet [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)应具有`Force`参数，以便当`Force`指定，则该 cmdlet 将跳过调用[System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)和继续执行该操作。</span><span class="sxs-lookup"><span data-stu-id="c9016-154">In fact, any cmdlet that calls [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) should have a `Force` parameter so that when `Force` is specified, the cmdlet skips the call to [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) and proceeds with the operation.</span></span> <span data-ttu-id="c9016-155">请注意这不会对的调用会影响[System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)。</span><span class="sxs-lookup"><span data-stu-id="c9016-155">Be aware that this does not affect calls to [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span></span>

<span data-ttu-id="c9016-156">`PassThru`参数允许用户指示是否 cmdlet 将传递给输出对象通过管道，在这种情况下后一个进程已停止。</span><span class="sxs-lookup"><span data-stu-id="c9016-156">The `PassThru` parameter allows the user to indicate whether the cmdlet passes an output object through the pipeline, in this case, after a process is stopped.</span></span> <span data-ttu-id="c9016-157">请注意此参数绑定到该 cmdlet 本身而不是属性的输入对象。</span><span class="sxs-lookup"><span data-stu-id="c9016-157">Be aware that this parameter is tied to the cmdlet itself instead of to a property of the input object.</span></span>

<span data-ttu-id="c9016-158">下面是停止进程 cmdlet 的参数声明。</span><span class="sxs-lookup"><span data-stu-id="c9016-158">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="c9016-159">重写方法的处理的输入</span><span class="sxs-lookup"><span data-stu-id="c9016-159">Overriding an Input Processing Method</span></span>

<span data-ttu-id="c9016-160">该 cmdlet 必须重写方法的处理的输入。</span><span class="sxs-lookup"><span data-stu-id="c9016-160">The cmdlet must override an input processing method.</span></span> <span data-ttu-id="c9016-161">下面的代码演示[System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)示例停止进程 cmdlet 中使用的重写。</span><span class="sxs-lookup"><span data-stu-id="c9016-161">The following code illustrates the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override used in the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="c9016-162">对于每个请求的进程名称，此方法可确保该过程不是一个特殊的过程、 尝试停止的进程，以及然后将输出对象发送如果`PassThru`指定参数。</span><span class="sxs-lookup"><span data-stu-id="c9016-162">For each requested process name, this method ensures that the process is not a special process, tries to stop the process, and then sends an output object if the `PassThru` parameter is specified.</span></span>

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
          // when the Name parameter reveives objects as input from the
          // pipeline. So to retain YesToAll and NoToAll input that the
          // user may enter across mutilple calls to ProcessRecord, this
          // information is stored as private members of the cmdlet.
          if (!ShouldContinue(message, "Warning!",
                              ref yesToAll,
                              ref noToAll))
          {
            continue;
          }
        } // if (cricicalProcess...
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

## <a name="calling-the-shouldprocess-method"></a><span data-ttu-id="c9016-163">调用 ShouldProcess 方法</span><span class="sxs-lookup"><span data-stu-id="c9016-163">Calling the ShouldProcess Method</span></span>

<span data-ttu-id="c9016-164">输入处理的 cmdlet 的方法应调用[System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法以确定执行操作之前对运行进行更改 （例如，删除文件）系统状态。</span><span class="sxs-lookup"><span data-stu-id="c9016-164">The input processing method of your cmdlet should call the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to confirm execution of an operation before a change (for example, deleting files) is made to the running state of the system.</span></span> <span data-ttu-id="c9016-165">这允许 Windows PowerShell 运行时提供在 shell 中的正确"WhatIf"和"确认"行为。</span><span class="sxs-lookup"><span data-stu-id="c9016-165">This allows the Windows PowerShell runtime to supply the correct "WhatIf" and "Confirm" behavior within the shell.</span></span>

> [!NOTE]
> <span data-ttu-id="c9016-166">如果 cmdlet 表明它支持应处理和无法做出[System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用时，用户可能意外修改系统。</span><span class="sxs-lookup"><span data-stu-id="c9016-166">If a cmdlet states that it supports should process and fails to make the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, the user might modify the system unexpectedly.</span></span>

<span data-ttu-id="c9016-167">在调用[System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)发送要更改对用户来说，与 Windows PowerShell 运行时将考虑在内的任何命令行设置或首选项变量的资源的名称在确定向用户应显示的内容。</span><span class="sxs-lookup"><span data-stu-id="c9016-167">The call to [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command-line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="c9016-168">下面的示例演示在调用[System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)重写[System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)中的方法示例停止进程 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c9016-168">The following example shows the call to [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) from the override of the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="c9016-169">调用 ShouldContinue 方法</span><span class="sxs-lookup"><span data-stu-id="c9016-169">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="c9016-170">在调用[System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法将辅助消息发送到用户。</span><span class="sxs-lookup"><span data-stu-id="c9016-170">The call to the [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method sends a secondary message to the user.</span></span> <span data-ttu-id="c9016-171">在调用后进行此调用[System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)返回`true`; 如果`Force`参数未设置为`true`。</span><span class="sxs-lookup"><span data-stu-id="c9016-171">This call is made after the call to [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returns `true` and if the `Force` parameter was not set to `true`.</span></span> <span data-ttu-id="c9016-172">用户可以提供反馈以说是否应继续执行该操作。</span><span class="sxs-lookup"><span data-stu-id="c9016-172">The user can then provide feedback to say whether the operation should be continued.</span></span> <span data-ttu-id="c9016-173">Cmdlet 调用[System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)作为额外检查潜在的危险系统修改或如果想要向用户提供是全部和否全部选项。</span><span class="sxs-lookup"><span data-stu-id="c9016-173">Your cmdlet calls [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) as an additional check for potentially dangerous system modifications or when you want to provide yes-to-all and no-to-all options to the user.</span></span>

<span data-ttu-id="c9016-174">下面的示例演示在调用[System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)重写[System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)中的方法示例停止进程 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c9016-174">The following example shows the call to [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) from the override of the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (criticalProcess &&!force)
{
  string message = String.Format
        ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
        processName);

  // It is possible that ProcessRecord is called multiple times
  // when the Name parameter reveives objects as input from the
  // pipeline. So to retain YesToAll and NoToAll input that the
  // user may enter across mutilple calls to ProcessRecord, this
  // information is stored as private members of the cmdlet.
  if (!ShouldContinue(message, "Warning!",
                      ref yesToAll,
                      ref noToAll))
  {
    continue;
  }
} // if (cricicalProcess...
```

## <a name="stopping-input-processing"></a><span data-ttu-id="c9016-175">正在停止输入的处理</span><span class="sxs-lookup"><span data-stu-id="c9016-175">Stopping Input Processing</span></span>

<span data-ttu-id="c9016-176">处理方法，使系统修改某个 cmdlet 的输入必须提供一种方法停止输入的处理。</span><span class="sxs-lookup"><span data-stu-id="c9016-176">The input processing method of a cmdlet that makes system modifications must provide a way of stopping the processing of input.</span></span> <span data-ttu-id="c9016-177">在此停止进程 cmdlet 的情况下调用了从[System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法[System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill)方法。</span><span class="sxs-lookup"><span data-stu-id="c9016-177">In the case of this Stop-Proc cmdlet, a call is made from the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to the [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) method.</span></span> <span data-ttu-id="c9016-178">因为`PassThru`参数设置为`true`， [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)还会调用[System.Management.Automation.Cmdlet.Writeobject\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)到将进程对象发送到管道。</span><span class="sxs-lookup"><span data-stu-id="c9016-178">Because the `PassThru` parameter is set to `true`, [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) also calls [System.Management.Automation.Cmdlet.Writeobject\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) to send the process object to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c9016-179">代码示例</span><span class="sxs-lookup"><span data-stu-id="c9016-179">Code Sample</span></span>

<span data-ttu-id="c9016-180">有关完整C#示例代码，请参阅[StopProcessSample01 示例](./stopprocesssample01-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="c9016-180">For the complete C# sample code, see [StopProcessSample01 Sample](./stopprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="c9016-181">定义对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="c9016-181">Defining Object Types and Formatting</span></span>

<span data-ttu-id="c9016-182">Windows PowerShell cmdlet 使用.Net 对象之间传递信息。</span><span class="sxs-lookup"><span data-stu-id="c9016-182">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="c9016-183">因此，一个 cmdlet 可能需要定义其自己的类型，或者该 cmdlet 可能需要扩展现有类型提供的另一个 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c9016-183">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="c9016-184">有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式设置](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。</span><span class="sxs-lookup"><span data-stu-id="c9016-184">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="c9016-185">生成该 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c9016-185">Building the Cmdlet</span></span>

<span data-ttu-id="c9016-186">执行后一个 cmdlet，它必须向注册 Windows PowerShell 通过 Windows PowerShell 管理单元。</span><span class="sxs-lookup"><span data-stu-id="c9016-186">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="c9016-187">有关注册 cmdlet 的详细信息，请参阅[如何注册 Cmdlet、 提供商和主机应用程序](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="c9016-187">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="c9016-188">测试 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c9016-188">Testing the Cmdlet</span></span>

<span data-ttu-id="c9016-189">当已使用 Windows PowerShell 注册你的 cmdlet 时，可以通过运行命令行上测试它。</span><span class="sxs-lookup"><span data-stu-id="c9016-189">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="c9016-190">以下是测试停止进程 cmdlet 的多个测试。</span><span class="sxs-lookup"><span data-stu-id="c9016-190">Here are several tests that test the Stop-Proc cmdlet.</span></span> <span data-ttu-id="c9016-191">有关使用命令行中的 cmdlet 的详细信息，请参阅[Windows PowerShell 入门学习](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="c9016-191">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="c9016-192">启动 Windows PowerShell 并停止进程 cmdlet 用于停止处理，如下所示。</span><span class="sxs-lookup"><span data-stu-id="c9016-192">Start Windows PowerShell and use the Stop-Proc cmdlet to stop processing as shown below.</span></span> <span data-ttu-id="c9016-193">因为该 cmdlet 指定`Name`为必需参数，该参数的 cmdlet 查询。</span><span class="sxs-lookup"><span data-stu-id="c9016-193">Because the cmdlet specifies the `Name` parameter as mandatory, the cmdlet queries for the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="c9016-194">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="c9016-194">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- <span data-ttu-id="c9016-195">现在让我们使用该 cmdlet 停止名为"NOTEPAD"的过程。</span><span class="sxs-lookup"><span data-stu-id="c9016-195">Now let's use the cmdlet to stop the process named "NOTEPAD".</span></span> <span data-ttu-id="c9016-196">该 cmdlet 会要求您确认该操作。</span><span class="sxs-lookup"><span data-stu-id="c9016-196">The cmdlet asks you to confirm the action.</span></span>

    ```powershell
    PS> stop-proc -Name notepad
    ```

<span data-ttu-id="c9016-197">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="c9016-197">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="c9016-198">使用停止的进程所示停止名为"WINLOGON"关键进程。</span><span class="sxs-lookup"><span data-stu-id="c9016-198">Use Stop-Proc as shown to stop the critical process named "WINLOGON".</span></span> <span data-ttu-id="c9016-199">您是系统提示，警告您执行此操作，因为这将导致操作系统重新启动。</span><span class="sxs-lookup"><span data-stu-id="c9016-199">You are prompted and warned about performing this action because it will cause the operating system to reboot.</span></span>

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

<span data-ttu-id="c9016-200">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="c9016-200">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- <span data-ttu-id="c9016-201">让我们现在尝试停止 WINLOGON 进程，而不会收到一条警告。</span><span class="sxs-lookup"><span data-stu-id="c9016-201">Let's now try to stop the WINLOGON process without receiving a warning.</span></span> <span data-ttu-id="c9016-202">请注意，此命令项使用`Force`参数来重写该警告。</span><span class="sxs-lookup"><span data-stu-id="c9016-202">Be aware that this command entry uses the `Force` parameter to override the warning.</span></span>

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

<span data-ttu-id="c9016-203">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="c9016-203">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="c9016-204">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c9016-204">See Also</span></span>

[<span data-ttu-id="c9016-205">添加处理命令行输入的参数</span><span class="sxs-lookup"><span data-stu-id="c9016-205">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="c9016-206">扩展对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="c9016-206">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="c9016-207">如何注册 Cmdlet、 提供程序，和托管应用程序</span><span class="sxs-lookup"><span data-stu-id="c9016-207">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="c9016-208">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c9016-208">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="c9016-209">Cmdlet 示例</span><span class="sxs-lookup"><span data-stu-id="c9016-209">Cmdlet Samples</span></span>](./cmdlet-samples.md)