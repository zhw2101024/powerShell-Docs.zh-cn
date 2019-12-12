---
title: 向 Cmdlet 添加参数集 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameter sets [PowerShell Programmer's Guide]
ms.assetid: a6131db4-fd6e-45f1-bd47-17e7174afd56
caps.latest.revision: 8
ms.openlocfilehash: c9c0b9a7a587e856efc82b4d277cee373e3f8b38
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416324"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a><span data-ttu-id="b4c06-102">向 Cmdlet 添加参数集</span><span class="sxs-lookup"><span data-stu-id="b4c06-102">Adding Parameter Sets to a Cmdlet</span></span>

## <a name="things-to-know-about-parameter-sets"></a><span data-ttu-id="b4c06-103">有关参数集的信息</span><span class="sxs-lookup"><span data-stu-id="b4c06-103">Things to Know About Parameter Sets</span></span>

<span data-ttu-id="b4c06-104">Windows PowerShell 将参数集定义为一组一起操作的参数。</span><span class="sxs-lookup"><span data-stu-id="b4c06-104">Windows PowerShell defines a parameter set as a group of parameters that operate together.</span></span> <span data-ttu-id="b4c06-105">通过对 cmdlet 的参数进行分组，可以创建单个 cmdlet，该 cmdlet 可以根据用户指定的参数组来更改其功能。</span><span class="sxs-lookup"><span data-stu-id="b4c06-105">By grouping the parameters of a cmdlet, you can create a single cmdlet that can change its functionality based on what group of parameters the user specifies.</span></span>

<span data-ttu-id="b4c06-106">使用两个参数集来定义不同功能的 cmdlet 示例是 Windows PowerShell 提供的 `Get-EventLog` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b4c06-106">An example of a cmdlet that uses two parameter sets to define different functionalities is the `Get-EventLog` cmdlet that is provided by Windows PowerShell.</span></span> <span data-ttu-id="b4c06-107">当用户指定 `List` 或 `LogName` 参数时，此 cmdlet 将返回不同的信息。</span><span class="sxs-lookup"><span data-stu-id="b4c06-107">This cmdlet returns different information when the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="b4c06-108">如果指定了 `LogName` 参数，则该 cmdlet 将返回有关给定事件日志中的事件的信息。</span><span class="sxs-lookup"><span data-stu-id="b4c06-108">If the `LogName` parameter is specified, the cmdlet returns information about the events in a given event log.</span></span> <span data-ttu-id="b4c06-109">如果指定了 `List` 参数，则该 cmdlet 将返回有关日志文件本身的信息（而不是它们所包含的事件信息）。</span><span class="sxs-lookup"><span data-stu-id="b4c06-109">If the `List` parameter is specified, the cmdlet returns information about the log files themselves (not the event information they contain).</span></span> <span data-ttu-id="b4c06-110">在这种情况下，`List` 和 `LogName` 参数标识两个单独的参数集。</span><span class="sxs-lookup"><span data-stu-id="b4c06-110">In this case, the `List` and `LogName` parameters identify two separate parameter sets.</span></span>

<span data-ttu-id="b4c06-111">有关参数集的两个重要事项是： Windows PowerShell 运行时仅对特定输入使用一个参数集，并且每个参数集必须至少有一个参数集唯一的参数。</span><span class="sxs-lookup"><span data-stu-id="b4c06-111">Two important things to remember about parameter sets is that the Windows PowerShell runtime uses only one parameter set for a particular input, and that each parameter set must have at least one parameter that is unique for that parameter set.</span></span>

<span data-ttu-id="b4c06-112">为了说明最后一点，此 Stop 过程 cmdlet 使用三个参数集： `ProcessName`、`ProcessId`和 `InputObject`。</span><span class="sxs-lookup"><span data-stu-id="b4c06-112">To illustrate that last point, this Stop-Proc cmdlet uses three parameter sets: `ProcessName`, `ProcessId`, and `InputObject`.</span></span> <span data-ttu-id="b4c06-113">其中每个参数集都具有一个不在其他参数集中的参数。</span><span class="sxs-lookup"><span data-stu-id="b4c06-113">Each of these parameter sets has one parameter that is not in the other parameter sets.</span></span> <span data-ttu-id="b4c06-114">参数集可以共享其他参数，但 cmdlet 使用唯一参数 `ProcessName`、`ProcessId`和 `InputObject` 来确定 Windows PowerShell 运行时应使用的参数集。</span><span class="sxs-lookup"><span data-stu-id="b4c06-114">The parameter sets could share other parameters, but the cmdlet uses the unique parameters `ProcessName`, `ProcessId`, and `InputObject` to identify which set of parameters that the Windows PowerShell runtime should use.</span></span>

## <a name="declaring-the-cmdlet-class"></a><span data-ttu-id="b4c06-115">声明 Cmdlet 类</span><span class="sxs-lookup"><span data-stu-id="b4c06-115">Declaring the Cmdlet Class</span></span>

<span data-ttu-id="b4c06-116">创建 cmdlet 的第一步是始终命名 cmdlet 并声明实现 cmdlet 的 .NET 类。</span><span class="sxs-lookup"><span data-stu-id="b4c06-116">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="b4c06-117">对于此 cmdlet，将使用生命周期谓词 "Stop"，因为该 cmdlet 将停止系统进程。</span><span class="sxs-lookup"><span data-stu-id="b4c06-117">For this cmdlet, the life-cycle verb "Stop" is used because the cmdlet stops system processes.</span></span> <span data-ttu-id="b4c06-118">之所以使用名词名称 "Proc"，是因为该 cmdlet 适用于进程。</span><span class="sxs-lookup"><span data-stu-id="b4c06-118">The noun name "Proc" is used because the cmdlet works on processes.</span></span> <span data-ttu-id="b4c06-119">请注意，在下面的声明中，cmdlet 谓词和名词名称反映在 cmdlet 类的名称中。</span><span class="sxs-lookup"><span data-stu-id="b4c06-119">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span>

> [!NOTE]
> <span data-ttu-id="b4c06-120">有关已批准的 cmdlet 谓词名称的详细信息，请参阅[Cmdlet 谓词名称](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="b4c06-120">For more information about approved cmdlet verb names, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="b4c06-121">下面的代码是此 Stop Proc cmdlet 的类定义。</span><span class="sxs-lookup"><span data-stu-id="b4c06-121">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        DefaultParameterSetName = "ProcessId",
        SupportsShouldProcess = true)]
public class StopProcCommand : PSCmdlet
```

```vb
<Cmdlet(VerbsLifecycle.Stop, "Proc", DefaultParameterSetName:="ProcessId", _
SupportsShouldProcess:=True)> _
Public Class StopProcCommand
    Inherits PSCmdlet
```

## <a name="declaring-the-parameters-of-the-cmdlet"></a><span data-ttu-id="b4c06-122">声明 Cmdlet 的参数</span><span class="sxs-lookup"><span data-stu-id="b4c06-122">Declaring the Parameters of the Cmdlet</span></span>

<span data-ttu-id="b4c06-123">此 cmdlet 将定义所需的三个参数作为 cmdlet 的输入（这些参数也定义参数集），并定义一个 `Force` 参数，该参数用于管理 cmdlet 的作用，以及一个确定 cmdlet 是否通过管道发送输出对象的 `PassThru` 参数。</span><span class="sxs-lookup"><span data-stu-id="b4c06-123">This cmdlet defines three parameters needed as input to the cmdlet (these parameters also define the parameter sets), as well as a `Force` parameter that manages what the cmdlet does and a `PassThru` parameter that determines whether the cmdlet sends an output object through the pipeline.</span></span> <span data-ttu-id="b4c06-124">默认情况下，此 cmdlet 不通过管道传递对象。</span><span class="sxs-lookup"><span data-stu-id="b4c06-124">By default, this cmdlet does not pass an object through the pipeline.</span></span> <span data-ttu-id="b4c06-125">有关最后两个参数的详细信息，请参阅[创建修改系统的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="b4c06-125">For more information about these last two parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

### <a name="declaring-the-name-parameter"></a><span data-ttu-id="b4c06-126">声明 Name 参数</span><span class="sxs-lookup"><span data-stu-id="b4c06-126">Declaring the Name Parameter</span></span>

<span data-ttu-id="b4c06-127">此输入参数允许用户指定要停止的进程的名称。</span><span class="sxs-lookup"><span data-stu-id="b4c06-127">This input parameter allows the user to specify the names of the processes to be stopped.</span></span> <span data-ttu-id="b4c06-128">请注意， [Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)属性的 `ParameterSetName` attribute 关键字指定为此参数设置的 `ProcessName` 参数。</span><span class="sxs-lookup"><span data-stu-id="b4c06-128">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessName` parameter set for this parameter.</span></span>

[!code-csharp[StopProcessSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

```vb
<Parameter(Position:=0, ParameterSetName:="ProcessName", _
Mandatory:=True, _
ValueFromPipeline:=True, ValueFromPipelineByPropertyName:=True, _
HelpMessage:="The name of one or more processes to stop. " & _
    "Wildcards are permitted."), [Alias]("ProcessName")> _
Public Property Name() As String()
    Get
        Return processNames
    End Get
    Set(ByVal value As String())
        processNames = value
    End Set
End Property

Private processNames() As String
```

<span data-ttu-id="b4c06-129">另请注意，将别名 "ProcessName" 提供给此参数。</span><span class="sxs-lookup"><span data-stu-id="b4c06-129">Note also that the alias "ProcessName" is given to this parameter.</span></span>

### <a name="declaring-the-id-parameter"></a><span data-ttu-id="b4c06-130">声明 Id 参数</span><span class="sxs-lookup"><span data-stu-id="b4c06-130">Declaring the Id Parameter</span></span>

<span data-ttu-id="b4c06-131">此输入参数允许用户指定要停止的进程的标识符。</span><span class="sxs-lookup"><span data-stu-id="b4c06-131">This input parameter allows the user to specify the identifiers of the processes to be stopped.</span></span> <span data-ttu-id="b4c06-132">请注意， [Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)属性的 `ParameterSetName` attribute 关键字指定 `ProcessId` 参数集。</span><span class="sxs-lookup"><span data-stu-id="b4c06-132">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessId` parameter set.</span></span>

```csharp
[Parameter(
           ParameterSetName = "ProcessId",
           Mandatory = true,
           ValueFromPipelineByPropertyName = true,
           ValueFromPipeline = true
)]
[Alias("ProcessId")]
public int[] Id
{
  get { return processIds; }
  set { processIds = value; }
}
private int[] processIds;
```

```vb
<Parameter(ParameterSetName:="ProcessId", _
Mandatory:=True, _
ValueFromPipelineByPropertyName:=True, _
ValueFromPipeline:=True), [Alias]("ProcessId")> _
Public Property Id() As Integer()
    Get
        Return processIds
    End Get
    Set(ByVal value As Integer())
        processIds = value
    End Set
End Property
Private processIds() As Integer
```

<span data-ttu-id="b4c06-133">另请注意，将别名 "ProcessId" 提供给此参数。</span><span class="sxs-lookup"><span data-stu-id="b4c06-133">Note also that the alias "ProcessId" is given to this parameter.</span></span>

### <a name="declaring-the-inputobject-parameter"></a><span data-ttu-id="b4c06-134">声明 InputObject 参数</span><span class="sxs-lookup"><span data-stu-id="b4c06-134">Declaring the InputObject Parameter</span></span>

<span data-ttu-id="b4c06-135">此输入参数允许用户指定输入对象，该对象包含要停止的进程的相关信息。</span><span class="sxs-lookup"><span data-stu-id="b4c06-135">This input parameter allows the user to specify an input object that contains information about the processes to be stopped.</span></span> <span data-ttu-id="b4c06-136">请注意， [Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)属性的 `ParameterSetName` attribute 关键字指定为此参数设置的 `InputObject` 参数。</span><span class="sxs-lookup"><span data-stu-id="b4c06-136">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `InputObject` parameter set for this parameter.</span></span>

```csharp
[Parameter(
           ParameterSetName = "InputObject",
           Mandatory = true,
           ValueFromPipeline = true)]
public Process[] InputObject
{
  get { return inputObject; }
  set { inputObject = value; }
}
private Process[] inputObject;
```

```vb
<Parameter(ParameterSetName:="InputObject", _
Mandatory:=True, ValueFromPipeline:=True)> _
Public Property InputObject() As Process()
    Get
        Return myInputObject
    End Get
    Set(ByVal value As Process())
        myInputObject = value
    End Set
End Property
Private myInputObject() As Process
```

<span data-ttu-id="b4c06-137">另请注意，此参数没有别名。</span><span class="sxs-lookup"><span data-stu-id="b4c06-137">Note also that this parameter has no alias.</span></span>

### <a name="declaring-parameters-in-multiple-parameter-sets"></a><span data-ttu-id="b4c06-138">在多个参数集中声明参数</span><span class="sxs-lookup"><span data-stu-id="b4c06-138">Declaring Parameters in Multiple Parameter Sets</span></span>

<span data-ttu-id="b4c06-139">尽管每个参数集必须有一个唯一参数，但参数可以属于多个参数集。</span><span class="sxs-lookup"><span data-stu-id="b4c06-139">Although there must be a unique parameter for each parameter set, parameters can belong to more than one parameter set.</span></span> <span data-ttu-id="b4c06-140">在这些情况下，为共享参数提供参数所属的每个集合的[Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)特性声明。</span><span class="sxs-lookup"><span data-stu-id="b4c06-140">In these cases, give the shared parameter a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration for each set to which that the parameter belongs.</span></span> <span data-ttu-id="b4c06-141">如果参数在所有参数集中，只需声明参数属性一次，且无需指定参数集名称。</span><span class="sxs-lookup"><span data-stu-id="b4c06-141">If a parameter is in all parameter sets, you only have to declare the parameter attribute once and do not need to specify the parameter set name.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="b4c06-142">重写输入处理方法</span><span class="sxs-lookup"><span data-stu-id="b4c06-142">Overriding an Input Processing Method</span></span>

<span data-ttu-id="b4c06-143">每个 cmdlet 都必须重写输入处理方法，这通常是[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。</span><span class="sxs-lookup"><span data-stu-id="b4c06-143">Every cmdlet must override an input processing method, most often this will be the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="b4c06-144">在此 cmdlet 中，将重写[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，以使 cmdlet 能够处理任意数量的进程。</span><span class="sxs-lookup"><span data-stu-id="b4c06-144">In this cmdlet, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden so that the cmdlet can process any number of processes.</span></span> <span data-ttu-id="b4c06-145">它包含一个 Select 语句，该语句基于用户指定的参数来调用其他方法。</span><span class="sxs-lookup"><span data-stu-id="b4c06-145">It contains a Select statement that calls a different method based on which parameter set the user has specified.</span></span>

```csharp
protected override void ProcessRecord()
{
  switch (ParameterSetName)
  {
    case "ProcessName":
         ProcessByName();
         break;

    case "ProcessId":
         ProcessById();
         break;

    case "InputObject":
         foreach (Process process in inputObject)
         {
           SafeStopProcess(process);
         }
         break;

    default:
         throw new ArgumentException("Bad ParameterSet Name");
  } // switch (ParameterSetName...
} // ProcessRecord
```

```vb
Protected Overrides Sub ProcessRecord()
    Select Case ParameterSetName
        Case "ProcessName"
            ProcessByName()

        Case "ProcessId"
            ProcessById()

        Case "InputObject"
            Dim process As Process
            For Each process In myInputObject
                SafeStopProcess(process)
            Next process

        Case Else
            Throw New ArgumentException("Bad ParameterSet Name")
    End Select

End Sub 'ProcessRecord ' ProcessRecord
```

<span data-ttu-id="b4c06-146">此处未介绍 Select 语句调用的帮助器方法，但您可以在下一节的完整代码示例中看到它们的实现。</span><span class="sxs-lookup"><span data-stu-id="b4c06-146">The Helper methods called by the Select statement are not described here, but you can see their implementation in the complete code sample in the next section.</span></span>

## <a name="code-sample"></a><span data-ttu-id="b4c06-147">代码示例</span><span class="sxs-lookup"><span data-stu-id="b4c06-147">Code Sample</span></span>

<span data-ttu-id="b4c06-148">有关完整C#的示例代码，请参阅[StopProcessSample04 示例](./stopprocesssample04-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="b4c06-148">For the complete C# sample code, see [StopProcessSample04 Sample](./stopprocesssample04-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="b4c06-149">定义对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="b4c06-149">Defining Object Types and Formatting</span></span>

<span data-ttu-id="b4c06-150">Windows PowerShell 使用 .NET 对象在 cmdlet 之间传递信息。</span><span class="sxs-lookup"><span data-stu-id="b4c06-150">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="b4c06-151">因此，cmdlet 可能需要定义自己的类型，或者该 cmdlet 可能需要扩展另一个 cmdlet 提供的现有类型。</span><span class="sxs-lookup"><span data-stu-id="b4c06-151">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="b4c06-152">有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式](/previous-versions//ms714665(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="b4c06-152">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="b4c06-153">构建 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b4c06-153">Building the Cmdlet</span></span>

<span data-ttu-id="b4c06-154">实现 cmdlet 后，必须通过 Windows PowerShell 管理单元将其注册到 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="b4c06-154">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="b4c06-155">有关注册 cmdlet 的详细信息，请参阅[如何注册 cmdlet、提供程序和主机应用程序](/previous-versions//ms714644(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="b4c06-155">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="b4c06-156">测试 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b4c06-156">Testing the Cmdlet</span></span>

<span data-ttu-id="b4c06-157">向 Windows PowerShell 注册 cmdlet 后，通过在命令行上运行它来对其进行测试。</span><span class="sxs-lookup"><span data-stu-id="b4c06-157">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="b4c06-158">下面是一些测试，演示如何使用 `ProcessId` 和 `InputObject` 参数来测试它们的参数集以停止进程。</span><span class="sxs-lookup"><span data-stu-id="b4c06-158">Here are some tests that show how the `ProcessId` and `InputObject` parameters can be used to test their parameter sets to stop a process.</span></span>

- <span data-ttu-id="b4c06-159">启动 Windows PowerShell 后，运行带有 `ProcessId` 参数设置的停止过程 cmdlet，以根据其标识符停止进程。</span><span class="sxs-lookup"><span data-stu-id="b4c06-159">With Windows PowerShell started, run the Stop-Proc cmdlet with the `ProcessId` parameter set to stop a process based on its identifier.</span></span> <span data-ttu-id="b4c06-160">在这种情况下，该 cmdlet 使用 `ProcessId` 参数集来停止该进程。</span><span class="sxs-lookup"><span data-stu-id="b4c06-160">In this case, the cmdlet is using the `ProcessId` parameter set to stop the process.</span></span>

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="b4c06-161">启动 Windows PowerShell 后，运行带有 `InputObject` 参数设置的停止过程 cmdlet，以停止 `Get-Process` 命令检索到的 Notepad 对象上的进程。</span><span class="sxs-lookup"><span data-stu-id="b4c06-161">With Windows PowerShell started, run the Stop-Proc cmdlet with the `InputObject` parameter set to stop processes on the Notepad object retrieved by the `Get-Process` command.</span></span>

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="b4c06-162">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b4c06-162">See Also</span></span>

[<span data-ttu-id="b4c06-163">创建修改系统的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b4c06-163">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="b4c06-164">如何创建 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b4c06-164">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="b4c06-165">[扩展对象类型和格式](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="b4c06-165">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="b4c06-166">[如何注册 Cmdlet、提供程序和主机应用程序](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="b4c06-166">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="b4c06-167">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b4c06-167">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
