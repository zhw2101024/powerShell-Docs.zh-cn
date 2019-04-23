---
title: 添加非终止错误报告到 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: 3741982f81efa04d8fe7ab448fba5f2fdf4b0c01
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984232"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a><span data-ttu-id="b1de8-102">向 Cmdlet 添加非终止错误报告</span><span class="sxs-lookup"><span data-stu-id="b1de8-102">Adding Non-Terminating Error Reporting to Your Cmdlet</span></span>

<span data-ttu-id="b1de8-103">Cmdlet 可以通过调用报告非终止错误[System.Management.Automation.Cmdlet.WriteError][]方法和仍继续运行当前的输入对象或更多传入管道对象。</span><span class="sxs-lookup"><span data-stu-id="b1de8-103">Cmdlets can report nonterminating errors by calling the [System.Management.Automation.Cmdlet.WriteError][] method and still continue to operate on the current input object or on further incoming pipeline objects.</span></span>
<span data-ttu-id="b1de8-104">本部分介绍如何创建 cmdlet，它报告从其输入的处理方法的非终止错误。</span><span class="sxs-lookup"><span data-stu-id="b1de8-104">This section explains how to create a cmdlet that reports nonterminating errors from its input processing methods.</span></span>

<span data-ttu-id="b1de8-105">非终止错误 （以及终止错误） 必须通过该 cmdlet [System.Management.Automation.ErrorRecord][]标识错误的对象。</span><span class="sxs-lookup"><span data-stu-id="b1de8-105">For nonterminating errors (as well as terminating errors), the cmdlet must pass an [System.Management.Automation.ErrorRecord][] object identifying the error.</span></span>
<span data-ttu-id="b1de8-106">每个错误记录都由名为"错误标识符"的唯一字符串标识。</span><span class="sxs-lookup"><span data-stu-id="b1de8-106">Each error record is identified by a unique string called the "error identifier".</span></span>
<span data-ttu-id="b1de8-107">指定定义常量的标识符，除了每个错误的类别[System.Management.Automation.ErrorCategory][]枚举。</span><span class="sxs-lookup"><span data-stu-id="b1de8-107">In addition to the identifier, the category of each error is specified by constants defined by a [System.Management.Automation.ErrorCategory][] enumeration.</span></span>
<span data-ttu-id="b1de8-108">用户可以查看根据其类别设置的错误`$ErrorView`"CategoryView"变量。</span><span class="sxs-lookup"><span data-stu-id="b1de8-108">The user can view errors based on their category by setting the `$ErrorView` variable to "CategoryView".</span></span>

<span data-ttu-id="b1de8-109">错误记录的详细信息，请参阅[Windows PowerShell 错误记录](./windows-powershell-error-records.md)。</span><span class="sxs-lookup"><span data-stu-id="b1de8-109">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="b1de8-110">定义 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b1de8-110">Defining the Cmdlet</span></span>

<span data-ttu-id="b1de8-111">Cmdlet 创建的第一步是始终命名 cmdlet 和实现该 cmdlet 的.NET 类声明。</span><span class="sxs-lookup"><span data-stu-id="b1de8-111">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span>
<span data-ttu-id="b1de8-112">此 cmdlet 检索进程信息，因此在此处选择谓词名称为"Get"。</span><span class="sxs-lookup"><span data-stu-id="b1de8-112">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span>
<span data-ttu-id="b1de8-113">（几乎任何类型的检索信息的 cmdlet 可以处理命令行输入）。有关已批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 的动词名称](approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="b1de8-113">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="b1de8-114">下面是此 Get-proc cmdlet 的定义。</span><span class="sxs-lookup"><span data-stu-id="b1de8-114">The following is the definition for this Get-Proc cmdlet.</span></span>
<span data-ttu-id="b1de8-115">此定义的详细信息中提供了[创建第一个 Cmdlet](creating-a-cmdlet-without-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="b1de8-115">Details of this definition are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a><span data-ttu-id="b1de8-116">定义参数</span><span class="sxs-lookup"><span data-stu-id="b1de8-116">Defining Parameters</span></span>

<span data-ttu-id="b1de8-117">如有必要，你的 cmdlet 必须定义用于处理输入的参数。</span><span class="sxs-lookup"><span data-stu-id="b1de8-117">If necessary, your cmdlet must define parameters for processing input.</span></span>
<span data-ttu-id="b1de8-118">定义此 Get-proc cmdlet**名称**参数中所述[添加该进程的命令行输入的参数](adding-parameters-that-process-command-line-input.md)。</span><span class="sxs-lookup"><span data-stu-id="b1de8-118">This Get-Proc cmdlet defines a **Name** parameter as described in [Adding Parameters that Process Command-Line Input](adding-parameters-that-process-command-line-input.md).</span></span>

<span data-ttu-id="b1de8-119">下面是参数声明**名称**此 Get-proc cmdlet 的参数。</span><span class="sxs-lookup"><span data-stu-id="b1de8-119">Here is the parameter declaration for the **Name** parameter of this Get-Proc cmdlet.</span></span>

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

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="b1de8-120">重写输入处理方法</span><span class="sxs-lookup"><span data-stu-id="b1de8-120">Overriding Input Processing Methods</span></span>

<span data-ttu-id="b1de8-121">所有 cmdlet 必须重都写的输入处理方法提供的至少[System.Management.Automation.Cmdlet][]类。</span><span class="sxs-lookup"><span data-stu-id="b1de8-121">All cmdlets must override at least one of the input processing methods provided by the [System.Management.Automation.Cmdlet][] class.</span></span>
<span data-ttu-id="b1de8-122">在讨论这些方法[创建第一个 Cmdlet](creating-a-cmdlet-without-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="b1de8-122">These methods are discussed in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b1de8-123">你的 cmdlet 应尽可能独立处理每条记录。</span><span class="sxs-lookup"><span data-stu-id="b1de8-123">Your cmdlet should handle each record as independently as possible.</span></span>

<span data-ttu-id="b1de8-124">此 Get-proc cmdlet 覆盖[System.Management.Automation.Cmdlet.ProcessRecord][]方法以处理**名称**输入提供的用户或脚本的参数。</span><span class="sxs-lookup"><span data-stu-id="b1de8-124">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord][] method to handle the **Name** parameter for input provided by the user or a script.</span></span>
<span data-ttu-id="b1de8-125">如果未提供名称，此方法将获取每个请求的进程名称或所有进程的进程。</span><span class="sxs-lookup"><span data-stu-id="b1de8-125">This method will get the processes for each requested process name or all processes if no name is provided.</span></span>
<span data-ttu-id="b1de8-126">此替代的详细信息中提供了[创建第一个 Cmdlet](creating-a-cmdlet-without-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="b1de8-126">Details of this override are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

### <a name="things-to-remember-when-reporting-errors"></a><span data-ttu-id="b1de8-127">要记住时报告错误的事项</span><span class="sxs-lookup"><span data-stu-id="b1de8-127">Things to Remember When Reporting Errors</span></span>

<span data-ttu-id="b1de8-128">[System.Management.Automation.ErrorRecord][] cmdlet 将写入错误需要在其核心异常时传递给对象。</span><span class="sxs-lookup"><span data-stu-id="b1de8-128">The [System.Management.Automation.ErrorRecord][] object that the cmdlet passes when writing an error requires an exception at its core.</span></span>
<span data-ttu-id="b1de8-129">确定要使用的异常时，请遵循.NET 准则。</span><span class="sxs-lookup"><span data-stu-id="b1de8-129">Follow the .NET guidelines when determining the exception to use.</span></span>
<span data-ttu-id="b1de8-130">基本上，如果错误是在语义上与现有异常不同，该 cmdlet 应使用或派生自该异常。</span><span class="sxs-lookup"><span data-stu-id="b1de8-130">Basically, if the error is semantically the same as an existing exception, the cmdlet should use or derive from that exception.</span></span>
<span data-ttu-id="b1de8-131">否则，它应派生的新异常或直接从异常层次结构[System.Exception][]类。</span><span class="sxs-lookup"><span data-stu-id="b1de8-131">Otherwise, it should derive a new exception or exception hierarchy directly from the [System.Exception][] class.</span></span>

<span data-ttu-id="b1de8-132">创建错误标识符 （通过 ErrorRecord 类的 FullyQualifiedErrorId 属性访问） 时请记住以下。</span><span class="sxs-lookup"><span data-stu-id="b1de8-132">When creating error identifiers (accessed through the FullyQualifiedErrorId property of the ErrorRecord class) keep the following in mind.</span></span>

- <span data-ttu-id="b1de8-133">为诊断目的，以便检查完全限定的标识符时能够确定哪些错误以及错误来自针对使用字符串。</span><span class="sxs-lookup"><span data-stu-id="b1de8-133">Use strings that are targeted for diagnostic purposes so that when inspecting the fully qualified identifier you can determine what the error is and where the error came from.</span></span>

- <span data-ttu-id="b1de8-134">格式正确的完全限定的错误标识符可能按如下所示。</span><span class="sxs-lookup"><span data-stu-id="b1de8-134">A well formed fully qualified error identifier might be as follows.</span></span>

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

<span data-ttu-id="b1de8-135">请注意，在上一示例中，错误标识符 （第一个标记） 指定的错误和剩余部分指示错误来自。</span><span class="sxs-lookup"><span data-stu-id="b1de8-135">Notice that in the previous example, the error identifier (the first token) designates what the error is and the remaining part indicates where the error came from.</span></span>

- <span data-ttu-id="b1de8-136">对于更复杂的方案，错误标识符可以是可以分析在检查点分隔标记。</span><span class="sxs-lookup"><span data-stu-id="b1de8-136">For more complex scenarios, the error identifier can be a dot separated token that can be parsed on inspection.</span></span>
  <span data-ttu-id="b1de8-137">这允许过分支上的部分错误标识符，以及错误标识符和错误类别。</span><span class="sxs-lookup"><span data-stu-id="b1de8-137">This allows you too branch on the parts of the error identifier as well as the error identifier and error category.</span></span>

<span data-ttu-id="b1de8-138">该 cmdlet 应将特定的错误标识符分配给不同的代码路径。</span><span class="sxs-lookup"><span data-stu-id="b1de8-138">The cmdlet should assign specific error identifiers to different code paths.</span></span>
<span data-ttu-id="b1de8-139">请注意分配错误标识符的以下信息：</span><span class="sxs-lookup"><span data-stu-id="b1de8-139">Keep the following information in mind for assignment of error identifiers:</span></span>

- <span data-ttu-id="b1de8-140">错误标识符应保持不变 cmdlet 生命周期内。</span><span class="sxs-lookup"><span data-stu-id="b1de8-140">An error identifier should remain constant throughout the cmdlet life cycle.</span></span>
  <span data-ttu-id="b1de8-141">不要更改错误标识符 cmdlet 版本之间的语义。</span><span class="sxs-lookup"><span data-stu-id="b1de8-141">Do not change the semantics of an error identifier between cmdlet versions.</span></span>

- <span data-ttu-id="b1de8-142">使用文本 tersely 对应于所报告的错误的错误标识符。</span><span class="sxs-lookup"><span data-stu-id="b1de8-142">Use text for an error identifier that tersely corresponds to the error being reported.</span></span>
  <span data-ttu-id="b1de8-143">不要使用空格或标点。</span><span class="sxs-lookup"><span data-stu-id="b1de8-143">Do not use white space or punctuation.</span></span>

- <span data-ttu-id="b1de8-144">具有你生成仅是可重现的错误标识符的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b1de8-144">Have your cmdlet generate only error identifiers that are reproducible.</span></span>
  <span data-ttu-id="b1de8-145">例如，它不应生成包括进程标识符的标识符。</span><span class="sxs-lookup"><span data-stu-id="b1de8-145">For example, it should not generate an identifier that includes a process identifier.</span></span>
  <span data-ttu-id="b1de8-146">仅当它们对应于被其他用户遇到相同问题的标识符时，错误标识符是对用户有用。</span><span class="sxs-lookup"><span data-stu-id="b1de8-146">Error identifiers are useful to a user only when they correspond to identifiers that are seen by other users experiencing the same problem.</span></span>

<span data-ttu-id="b1de8-147">未经处理的异常不会捕获 PowerShell 在下列情况：</span><span class="sxs-lookup"><span data-stu-id="b1de8-147">Unhandled exceptions are not caught by PowerShell in the following conditions:</span></span>

- <span data-ttu-id="b1de8-148">如果 cmdlet 创建新线程并运行，因为线程引发未经处理的异常的代码，PowerShell 将不会捕获该错误，并将终止进程。</span><span class="sxs-lookup"><span data-stu-id="b1de8-148">If a cmdlet creates a new thread and code running in that thread throws an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

- <span data-ttu-id="b1de8-149">如果一个对象将在其析构函数或 Dispose 方法会导致未经处理的异常的代码，PowerShell 将不会捕获该错误，并将终止进程。</span><span class="sxs-lookup"><span data-stu-id="b1de8-149">If an object has code in its destructor or Dispose methods that causes an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="b1de8-150">报告非终止错误</span><span class="sxs-lookup"><span data-stu-id="b1de8-150">Reporting Nonterminating Errors</span></span>

<span data-ttu-id="b1de8-151">输入处理方法之一可以向输出流使用报告非终止错误[System.Management.Automation.Cmdlet.WriteError][]方法。</span><span class="sxs-lookup"><span data-stu-id="b1de8-151">Any one of the input processing methods can report a nonterminating error to the output stream using the [System.Management.Automation.Cmdlet.WriteError][] method.</span></span>

<span data-ttu-id="b1de8-152">下面是一个代码示例演示对调用此 Get-proc cmdlet [System.Management.Automation.Cmdlet.WriteError][]从在重写中的[System.Management.Automation.Cmdlet.ProcessRecord][]方法。</span><span class="sxs-lookup"><span data-stu-id="b1de8-152">Here is a code example from this Get-Proc cmdlet that illustrates the call to [System.Management.Automation.Cmdlet.WriteError][] from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord][] method.</span></span>
<span data-ttu-id="b1de8-153">在这种情况下，如果该 cmdlet 找不到指定的进程标识符的过程进行调用。</span><span class="sxs-lookup"><span data-stu-id="b1de8-153">In this case, the call is made if the cmdlet cannot find a process for a specified process identifier.</span></span>

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

### <a name="things-to-remember-about-writing-nonterminating-errors"></a><span data-ttu-id="b1de8-154">要记住有关编写非终止错误的事项</span><span class="sxs-lookup"><span data-stu-id="b1de8-154">Things to Remember About Writing Nonterminating Errors</span></span>

<span data-ttu-id="b1de8-155">对于非终止错误，该 cmdlet 必须生成每个特定的输入对象的特定错误标识符。</span><span class="sxs-lookup"><span data-stu-id="b1de8-155">For a nonterminating error, the cmdlet must generate a specific error identifier for each specific input object.</span></span>

<span data-ttu-id="b1de8-156">Cmdlet 常常需要修改 PowerShell 操作生成的非终止错误。</span><span class="sxs-lookup"><span data-stu-id="b1de8-156">A cmdlet frequently needs to modify the PowerShell action produced by a nonterminating error.</span></span>
<span data-ttu-id="b1de8-157">它可以执行此操作通过定义`ErrorAction`和`ErrorVariable`参数。</span><span class="sxs-lookup"><span data-stu-id="b1de8-157">It can do this by defining the `ErrorAction` and `ErrorVariable` parameters.</span></span>
<span data-ttu-id="b1de8-158">如果定义`ErrorAction`参数，cmdlet 提供的用户选项[System.Management.Automation.ActionPreference][]，您可以通过设置直接影响操作`$ErrorActionPreference`变量。</span><span class="sxs-lookup"><span data-stu-id="b1de8-158">If defining the `ErrorAction` parameter, the cmdlet presents the user options [System.Management.Automation.ActionPreference][], you can also directly influence the action by setting the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="b1de8-159">该 cmdlet 可以将非终止错误保存到变量使用`ErrorVariable`参数，它的设置不影响`ErrorAction`。</span><span class="sxs-lookup"><span data-stu-id="b1de8-159">The cmdlet can save nonterminating errors to a variable using the `ErrorVariable` parameter, which is not affected by the setting of `ErrorAction`.</span></span>
<span data-ttu-id="b1de8-160">故障可以将追加到现有错误变量通过添加一个加号 （+） 向变量名称的开头。</span><span class="sxs-lookup"><span data-stu-id="b1de8-160">Failures can be appended to an existing error variable by adding a plus sign (+) to the front of the variable name.</span></span>

## <a name="code-sample"></a><span data-ttu-id="b1de8-161">代码示例</span><span class="sxs-lookup"><span data-stu-id="b1de8-161">Code Sample</span></span>

<span data-ttu-id="b1de8-162">有关完整C#示例代码，请参阅[GetProcessSample04 示例](./getprocesssample04-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="b1de8-162">For the complete C# sample code, see [GetProcessSample04 Sample](./getprocesssample04-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="b1de8-163">定义对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="b1de8-163">Define Object Types and Formatting</span></span>

<span data-ttu-id="b1de8-164">PowerShell cmdlet 使用.NET 对象之间传递信息。</span><span class="sxs-lookup"><span data-stu-id="b1de8-164">PowerShell passes information between cmdlets using .NET objects.</span></span>
<span data-ttu-id="b1de8-165">因此，一个 cmdlet 可能需要定义其自己的类型，或者该 cmdlet 可能需要扩展现有类型提供的另一个 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b1de8-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span>
<span data-ttu-id="b1de8-166">有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式设置](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。</span><span class="sxs-lookup"><span data-stu-id="b1de8-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="b1de8-167">生成该 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b1de8-167">Building the Cmdlet</span></span>

<span data-ttu-id="b1de8-168">实现一个 cmdlet 之后, 您必须注册它使用 Windows PowerShell 通过 Windows PowerShell 管理单元。</span><span class="sxs-lookup"><span data-stu-id="b1de8-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span>
<span data-ttu-id="b1de8-169">有关注册 cmdlet 的详细信息，请参阅[如何注册 Cmdlet、 提供商和主机应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="b1de8-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="b1de8-170">测试 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b1de8-170">Testing the Cmdlet</span></span>

<span data-ttu-id="b1de8-171">当已使用 PowerShell 注册你的 cmdlet 时，可以通过运行命令行上测试它。</span><span class="sxs-lookup"><span data-stu-id="b1de8-171">When your cmdlet has been registered with PowerShell, you can test it by running it on the command line.</span></span>
<span data-ttu-id="b1de8-172">让我们测试示例 Get-proc cmdlet，以查看它是否报告了错误：</span><span class="sxs-lookup"><span data-stu-id="b1de8-172">Let's test the sample Get-Proc cmdlet to see whether it reports an error:</span></span>

- <span data-ttu-id="b1de8-173">启动 PowerShell，并使用 Get-proc cmdlet 来检索名为"TEST"的进程。</span><span class="sxs-lookup"><span data-stu-id="b1de8-173">Start PowerShell, and use the Get-Proc cmdlet to retrieve the processes named "TEST".</span></span>

    ```powershell
    PS> get-proc -name test
    ```

<span data-ttu-id="b1de8-174">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="b1de8-174">The following output appears.</span></span>

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a><span data-ttu-id="b1de8-175">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b1de8-175">See Also</span></span>

[<span data-ttu-id="b1de8-176">添加进程管道输入的参数</span><span class="sxs-lookup"><span data-stu-id="b1de8-176">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="b1de8-177">添加处理命令行输入的参数</span><span class="sxs-lookup"><span data-stu-id="b1de8-177">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="b1de8-178">创建第一个 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b1de8-178">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="b1de8-179">扩展对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="b1de8-179">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="b1de8-180">如何注册 Cmdlet、 提供程序，和托管应用程序</span><span class="sxs-lookup"><span data-stu-id="b1de8-180">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="b1de8-181">Windows PowerShell 参考</span><span class="sxs-lookup"><span data-stu-id="b1de8-181">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="b1de8-182">Cmdlet 示例</span><span class="sxs-lookup"><span data-stu-id="b1de8-182">Cmdlet Samples</span></span>](./cmdlet-samples.md)

[System.Exception]: /dotnet/api/System.Exception
[System.Management.Automation.ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
[System.Management.Automation.Cmdlet.ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System.Management.Automation.Cmdlet.WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System.Management.Automation.Cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System.Management.Automation.ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System.Management.Automation.ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
