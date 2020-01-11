---
title: 向 Cmdlet 添加非终止错误报告 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: ec29d1cffa083e4cce667d3e1efbd4eeecbffb51
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870109"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a><span data-ttu-id="5b362-102">向 Cmdlet 添加非终止错误报告</span><span class="sxs-lookup"><span data-stu-id="5b362-102">Adding Non-Terminating Error Reporting to Your Cmdlet</span></span>

<span data-ttu-id="5b362-103">Cmdlet 可以通过调用["WriteError"。][]方法来报告非终止错误，并继续对当前输入对象或更多传入管道对象执行操作。</span><span class="sxs-lookup"><span data-stu-id="5b362-103">Cmdlets can report nonterminating errors by calling the [System.Management.Automation.Cmdlet.WriteError][] method and still continue to operate on the current input object or on further incoming pipeline objects.</span></span> <span data-ttu-id="5b362-104">本部分介绍如何创建一个 cmdlet，该 cmdlet 报告来自其输入处理方法的非终止错误。</span><span class="sxs-lookup"><span data-stu-id="5b362-104">This section explains how to create a cmdlet that reports nonterminating errors from its input processing methods.</span></span>

<span data-ttu-id="5b362-105">对于非终止错误（以及终止错误），该 cmdlet 必须通过标识错误的[System.web. ErrorRecord][]对象。</span><span class="sxs-lookup"><span data-stu-id="5b362-105">For nonterminating errors (as well as terminating errors), the cmdlet must pass an [System.Management.Automation.ErrorRecord][] object identifying the error.</span></span> <span data-ttu-id="5b362-106">每个错误记录均由名为 "错误标识符" 的唯一字符串标识。</span><span class="sxs-lookup"><span data-stu-id="5b362-106">Each error record is identified by a unique string called the "error identifier".</span></span> <span data-ttu-id="5b362-107">除了标识符以外，每个错误的类别都由[System.web. ErrorCategory][]枚举定义的常量指定。</span><span class="sxs-lookup"><span data-stu-id="5b362-107">In addition to the identifier, the category of each error is specified by constants defined by a [System.Management.Automation.ErrorCategory][] enumeration.</span></span> <span data-ttu-id="5b362-108">用户可以通过将 `$ErrorView` 变量设置为 "CategoryView" 来基于其类别查看错误。</span><span class="sxs-lookup"><span data-stu-id="5b362-108">The user can view errors based on their category by setting the `$ErrorView` variable to "CategoryView".</span></span>

<span data-ttu-id="5b362-109">有关错误记录的详细信息，请参阅[Windows PowerShell 错误记录](./windows-powershell-error-records.md)。</span><span class="sxs-lookup"><span data-stu-id="5b362-109">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="5b362-110">定义 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5b362-110">Defining the Cmdlet</span></span>

<span data-ttu-id="5b362-111">创建 cmdlet 的第一步是始终命名 cmdlet 并声明实现 cmdlet 的 .NET 类。</span><span class="sxs-lookup"><span data-stu-id="5b362-111">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="5b362-112">此 cmdlet 检索进程信息，因此此处选择的谓词名称为 "Get"。</span><span class="sxs-lookup"><span data-stu-id="5b362-112">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="5b362-113">（几乎任何能够检索信息的 cmdlet 都可以处理命令行输入。）有关批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 谓词名称](approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="5b362-113">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="5b362-114">下面是此 `Get-Proc` cmdlet 的定义。</span><span class="sxs-lookup"><span data-stu-id="5b362-114">The following is the definition for this `Get-Proc` cmdlet.</span></span> <span data-ttu-id="5b362-115">[创建第一个 Cmdlet](creating-a-cmdlet-without-parameters.md)中提供了此定义的详细信息。</span><span class="sxs-lookup"><span data-stu-id="5b362-115">Details of this definition are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a><span data-ttu-id="5b362-116">定义参数</span><span class="sxs-lookup"><span data-stu-id="5b362-116">Defining Parameters</span></span>

<span data-ttu-id="5b362-117">如果需要，cmdlet 必须定义用于处理输入的参数。</span><span class="sxs-lookup"><span data-stu-id="5b362-117">If necessary, your cmdlet must define parameters for processing input.</span></span> <span data-ttu-id="5b362-118">此获取处理器 cmdlet 定义一个**Name**参数[，如添加处理命令行输入的参数](adding-parameters-that-process-command-line-input.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="5b362-118">This Get-Proc cmdlet defines a **Name** parameter as described in [Adding Parameters that Process Command-Line Input](adding-parameters-that-process-command-line-input.md).</span></span>

<span data-ttu-id="5b362-119">下面是此 Get-help cmdlet 的**Name**参数的参数声明。</span><span class="sxs-lookup"><span data-stu-id="5b362-119">Here is the parameter declaration for the **Name** parameter of this Get-Proc cmdlet.</span></span>

```csharp
[Parameter(
           Position = 0,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
[ValidateNotNullOrEmpty]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="5b362-120">重写输入处理方法</span><span class="sxs-lookup"><span data-stu-id="5b362-120">Overriding Input Processing Methods</span></span>

<span data-ttu-id="5b362-121">所有 cmdlet 必须重写由[System.object。][]类提供的输入处理方法中的至少一个。</span><span class="sxs-lookup"><span data-stu-id="5b362-121">All cmdlets must override at least one of the input processing methods provided by the [System.Management.Automation.Cmdlet][] class.</span></span> <span data-ttu-id="5b362-122">这些方法在[创建第一个 Cmdlet](creating-a-cmdlet-without-parameters.md)中进行了介绍。</span><span class="sxs-lookup"><span data-stu-id="5b362-122">These methods are discussed in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="5b362-123">你的 cmdlet 应尽可能独立地处理每条记录。</span><span class="sxs-lookup"><span data-stu-id="5b362-123">Your cmdlet should handle each record as independently as possible.</span></span>

<span data-ttu-id="5b362-124">此 Get-Proc cmdlet 将重写["ProcessRecord"。][]方法，以处理用户或脚本提供的输入的 **Name** 参数的名称。</span><span class="sxs-lookup"><span data-stu-id="5b362-124">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord][] method to handle the **Name** parameter for input provided by the user or a script.</span></span> <span data-ttu-id="5b362-125">如果未提供任何名称，则此方法将获取每个请求的进程名称或所有进程的进程。</span><span class="sxs-lookup"><span data-stu-id="5b362-125">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="5b362-126">[创建第一个 Cmdlet](creating-a-cmdlet-without-parameters.md)时提供了此替代的详细信息。</span><span class="sxs-lookup"><span data-stu-id="5b362-126">Details of this override are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

### <a name="things-to-remember-when-reporting-errors"></a><span data-ttu-id="5b362-127">报告错误时要记住的问题</span><span class="sxs-lookup"><span data-stu-id="5b362-127">Things to Remember When Reporting Errors</span></span>

<span data-ttu-id="5b362-128">在写入错误时 cmdlet 传递的[System.web. ErrorRecord][]对象在其核心处需要异常。</span><span class="sxs-lookup"><span data-stu-id="5b362-128">The [System.Management.Automation.ErrorRecord][] object that the cmdlet passes when writing an error requires an exception at its core.</span></span> <span data-ttu-id="5b362-129">确定要使用的异常时，请遵循 .NET 指导原则。</span><span class="sxs-lookup"><span data-stu-id="5b362-129">Follow the .NET guidelines when determining the exception to use.</span></span>
<span data-ttu-id="5b362-130">基本上，如果错误与现有异常在语义上相同，则该 cmdlet 应使用或派生自该异常。</span><span class="sxs-lookup"><span data-stu-id="5b362-130">Basically, if the error is semantically the same as an existing exception, the cmdlet should use or derive from that exception.</span></span> <span data-ttu-id="5b362-131">否则，它应直接从[System.Exception][]新的异常或异常层次结构。</span><span class="sxs-lookup"><span data-stu-id="5b362-131">Otherwise, it should derive a new exception or exception hierarchy directly from the [System.Exception][] class.</span></span>

<span data-ttu-id="5b362-132">创建错误标识符（通过 ErrorRecord 类的 FullyQualifiedErrorId 属性访问）时，请记住以下事项。</span><span class="sxs-lookup"><span data-stu-id="5b362-132">When creating error identifiers (accessed through the FullyQualifiedErrorId property of the ErrorRecord class) keep the following in mind.</span></span>

- <span data-ttu-id="5b362-133">使用针对诊断目的的字符串，以便在检查完全限定的标识符时，可以确定错误是什么，以及错误来自何处。</span><span class="sxs-lookup"><span data-stu-id="5b362-133">Use strings that are targeted for diagnostic purposes so that when inspecting the fully qualified identifier you can determine what the error is and where the error came from.</span></span>

- <span data-ttu-id="5b362-134">格式正确的完全限定的错误标识符可能如下所示。</span><span class="sxs-lookup"><span data-stu-id="5b362-134">A well formed fully qualified error identifier might be as follows.</span></span>

  `CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

<span data-ttu-id="5b362-135">请注意，在前面的示例中，错误标识符（第一个标记）指定了错误的含义，剩余部分指示错误来自何处。</span><span class="sxs-lookup"><span data-stu-id="5b362-135">Notice that in the previous example, the error identifier (the first token) designates what the error is and the remaining part indicates where the error came from.</span></span>

- <span data-ttu-id="5b362-136">对于更复杂的方案，错误标识符可以是可以在检查时进行分析的以句点分隔的标记。</span><span class="sxs-lookup"><span data-stu-id="5b362-136">For more complex scenarios, the error identifier can be a dot separated token that can be parsed on inspection.</span></span> <span data-ttu-id="5b362-137">这允许你过于按错误标识符的部分以及错误标识符和错误类别进行分支。</span><span class="sxs-lookup"><span data-stu-id="5b362-137">This allows you too branch on the parts of the error identifier as well as the error identifier and error category.</span></span>

<span data-ttu-id="5b362-138">该 cmdlet 应将特定的错误标识符分配给不同的代码路径。</span><span class="sxs-lookup"><span data-stu-id="5b362-138">The cmdlet should assign specific error identifiers to different code paths.</span></span> <span data-ttu-id="5b362-139">请记住以下信息以分配错误标识符：</span><span class="sxs-lookup"><span data-stu-id="5b362-139">Keep the following information in mind for assignment of error identifiers:</span></span>

- <span data-ttu-id="5b362-140">错误标识符在整个 cmdlet 生命周期中应保持不变。</span><span class="sxs-lookup"><span data-stu-id="5b362-140">An error identifier should remain constant throughout the cmdlet life cycle.</span></span> <span data-ttu-id="5b362-141">不要更改 cmdlet 版本之间的错误标识符的语义。</span><span class="sxs-lookup"><span data-stu-id="5b362-141">Do not change the semantics of an error identifier between cmdlet versions.</span></span>
- <span data-ttu-id="5b362-142">使用文本作为 tersely 与所报告错误相对应的错误标识符。</span><span class="sxs-lookup"><span data-stu-id="5b362-142">Use text for an error identifier that tersely corresponds to the error being reported.</span></span> <span data-ttu-id="5b362-143">不要使用空格或标点。</span><span class="sxs-lookup"><span data-stu-id="5b362-143">Do not use white space or punctuation.</span></span>
- <span data-ttu-id="5b362-144">让 cmdlet 仅生成可重现的错误标识符。</span><span class="sxs-lookup"><span data-stu-id="5b362-144">Have your cmdlet generate only error identifiers that are reproducible.</span></span> <span data-ttu-id="5b362-145">例如，它不应生成包含进程标识符的标识符。</span><span class="sxs-lookup"><span data-stu-id="5b362-145">For example, it should not generate an identifier that includes a process identifier.</span></span> <span data-ttu-id="5b362-146">仅当用户与遇到相同问题的其他用户所见的标识符对应时，错误标识符才适用于用户。</span><span class="sxs-lookup"><span data-stu-id="5b362-146">Error identifiers are useful to a user only when they correspond to identifiers that are seen by other users experiencing the same problem.</span></span>

<span data-ttu-id="5b362-147">未处理的异常在以下情况下不会被 PowerShell 捕获：</span><span class="sxs-lookup"><span data-stu-id="5b362-147">Unhandled exceptions are not caught by PowerShell in the following conditions:</span></span>

- <span data-ttu-id="5b362-148">如果 cmdlet 创建新线程，并且在该线程中运行的代码引发了未经处理的异常，则 PowerShell 将不会捕获该错误，将终止该进程。</span><span class="sxs-lookup"><span data-stu-id="5b362-148">If a cmdlet creates a new thread and code running in that thread throws an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>
- <span data-ttu-id="5b362-149">如果对象在其析构函数或 Dispose 方法中包含导致未经处理的异常的代码，则 PowerShell 将不会捕获该错误，将终止该进程。</span><span class="sxs-lookup"><span data-stu-id="5b362-149">If an object has code in its destructor or Dispose methods that causes an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="5b362-150">报告非终止错误</span><span class="sxs-lookup"><span data-stu-id="5b362-150">Reporting Nonterminating Errors</span></span>

<span data-ttu-id="5b362-151">输入处理方法中的任何一种都可以使用["WriteError"。][]方法将非终止错误报告给输出流。</span><span class="sxs-lookup"><span data-stu-id="5b362-151">Any one of the input processing methods can report a nonterminating error to the output stream using the [System.Management.Automation.Cmdlet.WriteError][] method.</span></span>

<span data-ttu-id="5b362-152">下面是来自此 WriteError cmdlet 的代码示例，该代码示例演示了如何从["ProcessRecord"。][]方法的重写中调用对["WriteError"。][] 的调用。</span><span class="sxs-lookup"><span data-stu-id="5b362-152">Here is a code example from this Get-Proc cmdlet that illustrates the call to [System.Management.Automation.Cmdlet.WriteError][] from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord][] method.</span></span> <span data-ttu-id="5b362-153">在这种情况下，如果 cmdlet 找不到指定进程标识符的进程，则调用。</span><span class="sxs-lookup"><span data-stu-id="5b362-153">In this case, the call is made if the cmdlet cannot find a process for a specified process identifier.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no name parameter passed to cmdlet, get all processes.
  if (processNames == null)
  {
    WriteObject(Process.GetProcesses(), true);
  }
    else
    {
      // If a name parameter is passed to cmdlet, get and write
      // the associated processes.
      // Write a nonterminating error for failure to retrieve
      // a process.
      foreach (string name in processNames)
      {
        Process[] processes;

        try
        {
          processes = Process.GetProcessesByName(name);
        }
        catch (InvalidOperationException ex)
        {
          WriteError(new ErrorRecord(
                     ex,
                     "NameNotFound",
                     ErrorCategory.InvalidOperation,
                     name));
          continue;
        }

        WriteObject(processes, true);
      } // foreach (...
    } // else
  }
```

### <a name="things-to-remember-about-writing-nonterminating-errors"></a><span data-ttu-id="5b362-154">有关编写非终止错误的注意事项</span><span class="sxs-lookup"><span data-stu-id="5b362-154">Things to Remember About Writing Nonterminating Errors</span></span>

<span data-ttu-id="5b362-155">对于非终止错误，cmdlet 必须为每个特定输入对象生成特定的错误标识符。</span><span class="sxs-lookup"><span data-stu-id="5b362-155">For a nonterminating error, the cmdlet must generate a specific error identifier for each specific input object.</span></span>

<span data-ttu-id="5b362-156">Cmdlet 经常需要修改非终止错误产生的 PowerShell 操作。</span><span class="sxs-lookup"><span data-stu-id="5b362-156">A cmdlet frequently needs to modify the PowerShell action produced by a nonterminating error.</span></span> <span data-ttu-id="5b362-157">它可以通过定义 `ErrorAction` 和 `ErrorVariable` 参数来实现此目的。</span><span class="sxs-lookup"><span data-stu-id="5b362-157">It can do this by defining the `ErrorAction` and `ErrorVariable` parameters.</span></span> <span data-ttu-id="5b362-158">如果定义 `ErrorAction` 参数，该 cmdlet 将提供用户选项[System.web. ActionPreference][]，还可以通过设置 `$ErrorActionPreference` 变量直接影响该操作。</span><span class="sxs-lookup"><span data-stu-id="5b362-158">If defining the `ErrorAction` parameter, the cmdlet presents the user options [System.Management.Automation.ActionPreference][], you can also directly influence the action by setting the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="5b362-159">该 cmdlet 可以使用 `ErrorVariable` 参数将非终止错误保存到变量，此参数不受 `ErrorAction`的设置影响。</span><span class="sxs-lookup"><span data-stu-id="5b362-159">The cmdlet can save nonterminating errors to a variable using the `ErrorVariable` parameter, which is not affected by the setting of `ErrorAction`.</span></span> <span data-ttu-id="5b362-160">可以通过将加号（+）添加到变量名前面来向现有错误变量追加失败。</span><span class="sxs-lookup"><span data-stu-id="5b362-160">Failures can be appended to an existing error variable by adding a plus sign (+) to the front of the variable name.</span></span>

## <a name="code-sample"></a><span data-ttu-id="5b362-161">代码示例</span><span class="sxs-lookup"><span data-stu-id="5b362-161">Code Sample</span></span>

<span data-ttu-id="5b362-162">有关完整C#的示例代码，请参阅[GetProcessSample04 示例](./getprocesssample04-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="5b362-162">For the complete C# sample code, see [GetProcessSample04 Sample](./getprocesssample04-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="5b362-163">定义对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="5b362-163">Define Object Types and Formatting</span></span>

<span data-ttu-id="5b362-164">PowerShell 使用 .NET 对象在 cmdlet 之间传递信息。</span><span class="sxs-lookup"><span data-stu-id="5b362-164">PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="5b362-165">因此，cmdlet 可能需要定义自己的类型，或者该 cmdlet 可能需要扩展另一个 cmdlet 提供的现有类型。</span><span class="sxs-lookup"><span data-stu-id="5b362-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="5b362-166">有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式](/previous-versions/ms714665(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="5b362-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions/ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="5b362-167">构建 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5b362-167">Building the Cmdlet</span></span>

<span data-ttu-id="5b362-168">实现 cmdlet 后，必须通过 Windows PowerShell 管理单元将其注册到 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="5b362-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="5b362-169">有关注册 cmdlet 的详细信息，请参阅[如何注册 cmdlet、提供程序和主机应用程序](/previous-versions//ms714644(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="5b362-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="5b362-170">测试 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5b362-170">Testing the Cmdlet</span></span>

<span data-ttu-id="5b362-171">向 PowerShell 注册 cmdlet 后，可以通过在命令行上运行 cmdlet 来对其进行测试。</span><span class="sxs-lookup"><span data-stu-id="5b362-171">When your cmdlet has been registered with PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="5b362-172">让我们测试该示例的 Get Proc cmdlet，以查看它是否报告错误：</span><span class="sxs-lookup"><span data-stu-id="5b362-172">Let's test the sample Get-Proc cmdlet to see whether it reports an error:</span></span>

- <span data-ttu-id="5b362-173">启动 PowerShell，并使用 Get-help cmdlet 检索名为 "TEST" 的进程。</span><span class="sxs-lookup"><span data-stu-id="5b362-173">Start PowerShell, and use the Get-Proc cmdlet to retrieve the processes named "TEST".</span></span>

  ```powershell
  get-proc -name test
  ```

  <span data-ttu-id="5b362-174">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="5b362-174">The following output appears.</span></span>

  ```
  get-proc : Operation is not valid due to the current state of the object.
  At line:1 char:9
  + get-proc  <<<< -name test
  ```

## <a name="see-also"></a><span data-ttu-id="5b362-175">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5b362-175">See Also</span></span>

[<span data-ttu-id="5b362-176">添加处理管道输入的参数</span><span class="sxs-lookup"><span data-stu-id="5b362-176">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="5b362-177">添加用于处理命令行输入的参数</span><span class="sxs-lookup"><span data-stu-id="5b362-177">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="5b362-178">创建第一个 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5b362-178">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

<span data-ttu-id="5b362-179">[扩展对象类型和格式](/previous-versions/ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="5b362-179">[Extending Object Types and Formatting](/previous-versions/ms714665(v=vs.85))</span></span>

<span data-ttu-id="5b362-180">[如何注册 Cmdlet、提供程序和主机应用程序](/previous-versions/ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="5b362-180">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85))</span></span>

<span data-ttu-id="5b362-181">[Windows PowerShell Reference](../windows-powershell-reference.md)（Windows PowerShell 参考）</span><span class="sxs-lookup"><span data-stu-id="5b362-181">[Windows PowerShell Reference](../windows-powershell-reference.md)</span></span>

[<span data-ttu-id="5b362-182">Cmdlet 示例</span><span class="sxs-lookup"><span data-stu-id="5b362-182">Cmdlet Samples</span></span>](./cmdlet-samples.md)

[System.Exception]: /dotnet/api/System.Exception
[System.web. ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
[System.Management.Automation.ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
["ProcessRecord"。]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System.Management.Automation.Cmdlet.ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
["WriteError"。]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System.Management.Automation.Cmdlet.WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System.object。]: /dotnet/api/System.Management.Automation.Cmdlet
[System.Management.Automation.Cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System.web. ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System.Management.Automation.ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System.web. ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
[System.Management.Automation.ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
