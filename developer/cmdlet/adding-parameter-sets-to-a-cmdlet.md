---
title: 将参数添加到 Cmdlet 设置 |Microsoft Docs
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
ms.openlocfilehash: f0bff11618c18bf53b9c2a185445795a17306fa3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068831"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a><span data-ttu-id="b81db-102">向 Cmdlet 添加参数集</span><span class="sxs-lookup"><span data-stu-id="b81db-102">Adding Parameter Sets to a Cmdlet</span></span>

<span data-ttu-id="b81db-103">本部分介绍如何添加参数设置为 Stop Proc cmdlet (中所述[创建一个 Cmdlet 来修改系统](./creating-a-cmdlet-that-modifies-the-system.md))。</span><span class="sxs-lookup"><span data-stu-id="b81db-103">This section describes how to add parameter sets to the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span> <span data-ttu-id="b81db-104">类似于此编程人员的指南中所述的其他进程停止外 cmdlet，此 cmdlet 会尝试停止使用 Get-proc cmdlet 检索的进程 (中所述[创建第一个 Cmdlet](./creating-a-cmdlet-without-parameters.md))。</span><span class="sxs-lookup"><span data-stu-id="b81db-104">Similar to the other Stop-Proc cmdlets described in this Programmer's Guide, this cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

<span data-ttu-id="b81db-105">在本部分中的主题包括：</span><span class="sxs-lookup"><span data-stu-id="b81db-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="b81db-106">关于参数集点提示</span><span class="sxs-lookup"><span data-stu-id="b81db-106">Things to Know About Parameter Sets</span></span>](#Adding-Parameter-Sets-to-a-Cmdlet)

- [<span data-ttu-id="b81db-107">声明 Cmdlet 类</span><span class="sxs-lookup"><span data-stu-id="b81db-107">Declaring the Cmdlet Class</span></span>](#Declaring-the-Cmdlet-Class)

- [<span data-ttu-id="b81db-108">声明 Cmdlet 的参数</span><span class="sxs-lookup"><span data-stu-id="b81db-108">Declaring the Parameters of the Cmdlet</span></span>](#Declaring-the-Parameters-of-the-Cmdlet)

- [<span data-ttu-id="b81db-109">重写方法的处理的输入</span><span class="sxs-lookup"><span data-stu-id="b81db-109">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="b81db-110">代码示例</span><span class="sxs-lookup"><span data-stu-id="b81db-110">Code Sample</span></span>](#Declaring-the-Parameters-of-the-Cmdlet)

- [<span data-ttu-id="b81db-111">定义对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="b81db-111">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="b81db-112">生成该 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b81db-112">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="b81db-113">测试 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b81db-113">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="things-to-know-about-parameter-sets"></a><span data-ttu-id="b81db-114">关于参数集点提示</span><span class="sxs-lookup"><span data-stu-id="b81db-114">Things to Know About Parameter Sets</span></span>

<span data-ttu-id="b81db-115">Windows PowerShell 定义参数设置为一起运行的参数组。</span><span class="sxs-lookup"><span data-stu-id="b81db-115">Windows PowerShell defines a parameter set as a group of parameters that operate together.</span></span> <span data-ttu-id="b81db-116">通过对 cmdlet 的参数进行分组，可以创建的单个 cmdlet，可以更改基于参数哪组用户指定其功能。</span><span class="sxs-lookup"><span data-stu-id="b81db-116">By grouping the parameters of a cmdlet, you can create a single cmdlet that can change its functionality based on what group of parameters the user specifies.</span></span>

<span data-ttu-id="b81db-117">使用两个参数集来定义不同功能的 cmdlet 的一个示例是`Get-EventLog`提供的 Windows PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b81db-117">An example of a cmdlet that uses two parameter sets to define different functionalities is the `Get-EventLog` cmdlet that is provided by Windows PowerShell.</span></span> <span data-ttu-id="b81db-118">此 cmdlet 将返回不同的信息时用户指定`List`或`LogName`参数。</span><span class="sxs-lookup"><span data-stu-id="b81db-118">This cmdlet returns different information when the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="b81db-119">如果`LogName`指定参数，则该 cmdlet 返回给定事件日志中有关事件的信息。</span><span class="sxs-lookup"><span data-stu-id="b81db-119">If the `LogName` parameter is specified, the cmdlet returns information about the events in a given event log.</span></span> <span data-ttu-id="b81db-120">如果`List`指定参数，该 cmdlet 将返回有关日志的信息文件本身 （而非它们所包含事件信息）。</span><span class="sxs-lookup"><span data-stu-id="b81db-120">If the `List` parameter is specified, the cmdlet returns information about the log files themselves (not the event information they contain).</span></span> <span data-ttu-id="b81db-121">在这种情况下，`List`和`LogName`参数标识两个单独的参数集。</span><span class="sxs-lookup"><span data-stu-id="b81db-121">In this case, the `List` and `LogName` parameters identify two separate parameter sets.</span></span>

<span data-ttu-id="b81db-122">需要记住有关参数集的两个重要事项是，Windows PowerShell 运行时使用只有一个参数设置为某一特定的输入，以及每个参数集必须具有至少一个参数，是唯一的参数集。</span><span class="sxs-lookup"><span data-stu-id="b81db-122">Two important things to remember about parameter sets is that the Windows PowerShell runtime uses only one parameter set for a particular input, and that each parameter set must have at least one parameter that is unique for that parameter set.</span></span>

<span data-ttu-id="b81db-123">为了说明该最后一个点，此停止进程 cmdlet 使用三个参数集： `ProcessName`， `ProcessId`，和`InputObject`。</span><span class="sxs-lookup"><span data-stu-id="b81db-123">To illustrate that last point, this Stop-Proc cmdlet uses three parameter sets: `ProcessName`, `ProcessId`, and `InputObject`.</span></span> <span data-ttu-id="b81db-124">每个这些参数集有一个参数，它不在其他参数集。</span><span class="sxs-lookup"><span data-stu-id="b81db-124">Each of these parameter sets has one parameter that is not in the other parameter sets.</span></span> <span data-ttu-id="b81db-125">参数集可能共享其他参数，但此 cmdlet 将使用唯一的参数`ProcessName`， `ProcessId`，和`InputObject`来标识的组的 Windows PowerShell 运行时应使用的参数。</span><span class="sxs-lookup"><span data-stu-id="b81db-125">The parameter sets could share other parameters, but the cmdlet uses the unique parameters `ProcessName`, `ProcessId`, and `InputObject` to identify which set of parameters that the Windows PowerShell runtime should use.</span></span>

## <a name="declaring-the-cmdlet-class"></a><span data-ttu-id="b81db-126">声明 Cmdlet 类</span><span class="sxs-lookup"><span data-stu-id="b81db-126">Declaring the Cmdlet Class</span></span>

<span data-ttu-id="b81db-127">Cmdlet 创建的第一步是始终命名 cmdlet 和实现该 cmdlet 的.NET 类声明。</span><span class="sxs-lookup"><span data-stu-id="b81db-127">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="b81db-128">对于此 cmdlet，因为该 cmdlet 会停止系统进程使用生命周期谓词"Stop"。</span><span class="sxs-lookup"><span data-stu-id="b81db-128">For this cmdlet, the life-cycle verb "Stop" is used because the cmdlet stops system processes.</span></span> <span data-ttu-id="b81db-129">由于 cmdlet 适用于进程，则使用名词名称"过程"。</span><span class="sxs-lookup"><span data-stu-id="b81db-129">The noun name "Proc" is used because the cmdlet works on processes.</span></span> <span data-ttu-id="b81db-130">在以下声明中，请注意 cmdlet 动词和名词名称将反映在 cmdlet 类的名称。</span><span class="sxs-lookup"><span data-stu-id="b81db-130">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span>

> [!NOTE]
> <span data-ttu-id="b81db-131">已批准的 cmdlet 的动词名称有关的详细信息，请参阅[Cmdlet 的动词名称](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="b81db-131">For more information about approved cmdlet verb names, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="b81db-132">以下代码是此停止进程 cmdlet 的类定义。</span><span class="sxs-lookup"><span data-stu-id="b81db-132">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

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

## <a name="declaring-the-parameters-of-the-cmdlet"></a><span data-ttu-id="b81db-133">声明 Cmdlet 的参数</span><span class="sxs-lookup"><span data-stu-id="b81db-133">Declaring the Parameters of the Cmdlet</span></span>

<span data-ttu-id="b81db-134">此 cmdlet 定义作为到 cmdlet （这些参数定义的参数集），输入所需的三个参数以及`Force`管理 cmdlet 的用途的参数和一个`PassThru`确定是否将发送该 cmdlet 的参数通过管道的输出对象。</span><span class="sxs-lookup"><span data-stu-id="b81db-134">This cmdlet defines three parameters needed as input to the cmdlet (these parameters also define the parameter sets), as well as a `Force` parameter that manages what the cmdlet does and a `PassThru` parameter that determines whether the cmdlet sends an output object through the pipeline.</span></span> <span data-ttu-id="b81db-135">默认情况下，此 cmdlet 不将传递的对象通过管道。</span><span class="sxs-lookup"><span data-stu-id="b81db-135">By default, this cmdlet does not pass an object through the pipeline.</span></span> <span data-ttu-id="b81db-136">有关这些最后两个参数的详细信息，请参阅[创建一个 Cmdlet 来修改系统](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="b81db-136">For more information about these last two parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

### <a name="declaring-the-name-parameter"></a><span data-ttu-id="b81db-137">声明名称参数</span><span class="sxs-lookup"><span data-stu-id="b81db-137">Declaring the Name Parameter</span></span>

<span data-ttu-id="b81db-138">此输入的参数允许用户以指定要停止的进程的名称。</span><span class="sxs-lookup"><span data-stu-id="b81db-138">This input parameter allows the user to specify the names of the processes to be stopped.</span></span> <span data-ttu-id="b81db-139">请注意，`ParameterSetName`属性的关键字[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)特性指定`ProcessName`参数设置为此参数。</span><span class="sxs-lookup"><span data-stu-id="b81db-139">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessName` parameter set for this parameter.</span></span>

[!code-csharp[StopProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

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

<span data-ttu-id="b81db-140">此外请注意，此参数为给定别名"ProcessName"。</span><span class="sxs-lookup"><span data-stu-id="b81db-140">Note also that the alias "ProcessName" is given to this parameter.</span></span>

### <a name="declaring-the-id-parameter"></a><span data-ttu-id="b81db-141">声明的 Id 参数</span><span class="sxs-lookup"><span data-stu-id="b81db-141">Declaring the Id Parameter</span></span>

<span data-ttu-id="b81db-142">此输入的参数允许用户指定要停止的进程的标识符。</span><span class="sxs-lookup"><span data-stu-id="b81db-142">This input parameter allows the user to specify the identifiers of the processes to be stopped.</span></span> <span data-ttu-id="b81db-143">请注意，`ParameterSetName`属性的关键字[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)特性指定`ProcessId`参数集。</span><span class="sxs-lookup"><span data-stu-id="b81db-143">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessId` parameter set.</span></span>

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

<span data-ttu-id="b81db-144">此外请注意，此参数为给定别名"ProcessId"。</span><span class="sxs-lookup"><span data-stu-id="b81db-144">Note also that the alias "ProcessId" is given to this parameter.</span></span>

### <a name="declaring-the-inputobject-parameter"></a><span data-ttu-id="b81db-145">InputObject 参数声明</span><span class="sxs-lookup"><span data-stu-id="b81db-145">Declaring the InputObject Parameter</span></span>

<span data-ttu-id="b81db-146">此输入的参数允许用户指定包含要停止的进程有关的信息的输入的对象。</span><span class="sxs-lookup"><span data-stu-id="b81db-146">This input parameter allows the user to specify an input object that contains information about the processes to be stopped.</span></span> <span data-ttu-id="b81db-147">请注意，`ParameterSetName`属性的关键字[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)特性指定`InputObject`参数设置为此参数。</span><span class="sxs-lookup"><span data-stu-id="b81db-147">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `InputObject` parameter set for this parameter.</span></span>

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

<span data-ttu-id="b81db-148">另请注意，此参数有无别名。</span><span class="sxs-lookup"><span data-stu-id="b81db-148">Note also that this parameter has no alias.</span></span>

### <a name="declaring-parameters-in-multiple-parameter-sets"></a><span data-ttu-id="b81db-149">声明中多个参数集的参数</span><span class="sxs-lookup"><span data-stu-id="b81db-149">Declaring Parameters in Multiple Parameter Sets</span></span>

<span data-ttu-id="b81db-150">尽管必须为每个参数集的唯一参数，参数可以属于多个参数集。</span><span class="sxs-lookup"><span data-stu-id="b81db-150">Although there must be a unique parameter for each parameter set, parameters can belong to more than one parameter set.</span></span> <span data-ttu-id="b81db-151">在这些情况下，提供共享的参数[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)特性声明的每个设置该参数属于。</span><span class="sxs-lookup"><span data-stu-id="b81db-151">In these cases, give the shared parameter a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration for each set to which that the parameter belongs.</span></span> <span data-ttu-id="b81db-152">如果参数是在所有参数集，只有一次声明参数属性且不需要指定该参数设置名称。</span><span class="sxs-lookup"><span data-stu-id="b81db-152">If a parameter is in all parameter sets, you only have to declare the parameter attribute once and do not need to specify the parameter set name.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="b81db-153">重写方法的处理的输入</span><span class="sxs-lookup"><span data-stu-id="b81db-153">Overriding an Input Processing Method</span></span>

<span data-ttu-id="b81db-154">每个 cmdlet 必须重写方法的处理的输入，这是最常[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。</span><span class="sxs-lookup"><span data-stu-id="b81db-154">Every cmdlet must override an input processing method, most often this will be the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="b81db-155">此 cmdlet 中[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法被重写，以便该 cmdlet 可以处理任意数量的进程。</span><span class="sxs-lookup"><span data-stu-id="b81db-155">In this cmdlet, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden so that the cmdlet can process any number of processes.</span></span> <span data-ttu-id="b81db-156">它包含用户对哪些参数集基于另一种方法的调用具有指定的 Select 语句。</span><span class="sxs-lookup"><span data-stu-id="b81db-156">It contains a Select statement that calls a different method based on which parameter set the user has specified.</span></span>

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

<span data-ttu-id="b81db-157">不在这里，介绍 Select 语句调用的帮助器方法，但您可以看到其实现中下一节中的完整代码示例。</span><span class="sxs-lookup"><span data-stu-id="b81db-157">The Helper methods called by the Select statement are not described here, but you can see their implementation in the complete code sample in the next section.</span></span>

## <a name="code-sample"></a><span data-ttu-id="b81db-158">代码示例</span><span class="sxs-lookup"><span data-stu-id="b81db-158">Code Sample</span></span>

<span data-ttu-id="b81db-159">有关完整C#示例代码，请参阅[StopProcessSample04 示例](./stopprocesssample04-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="b81db-159">For the complete C# sample code, see [StopProcessSample04 Sample](./stopprocesssample04-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="b81db-160">定义对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="b81db-160">Defining Object Types and Formatting</span></span>

<span data-ttu-id="b81db-161">Windows PowerShell cmdlet 使用.NET 对象之间传递信息。</span><span class="sxs-lookup"><span data-stu-id="b81db-161">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="b81db-162">因此，一个 cmdlet 可能需要定义其自己的类型，或者该 cmdlet 可能需要扩展现有类型提供的另一个 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b81db-162">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="b81db-163">有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式设置](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。</span><span class="sxs-lookup"><span data-stu-id="b81db-163">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="b81db-164">生成该 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b81db-164">Building the Cmdlet</span></span>

<span data-ttu-id="b81db-165">实现一个 cmdlet 之后, 您必须注册它使用 Windows PowerShell 通过 Windows PowerShell 管理单元。</span><span class="sxs-lookup"><span data-stu-id="b81db-165">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="b81db-166">有关注册 cmdlet 的详细信息，请参阅[如何注册 Cmdlet、 提供商和主机应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="b81db-166">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="b81db-167">测试 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b81db-167">Testing the Cmdlet</span></span>

<span data-ttu-id="b81db-168">你的 cmdlet 具有已注册到 Windows PowerShell，通过命令行上运行测试。</span><span class="sxs-lookup"><span data-stu-id="b81db-168">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="b81db-169">以下是显示一些测试如何`ProcessId`和`InputObject`参数可用于测试及其参数集，若要停止的进程。</span><span class="sxs-lookup"><span data-stu-id="b81db-169">Here are some tests that show how the `ProcessId` and `InputObject` parameters can be used to test their parameter sets to stop a process.</span></span>

- <span data-ttu-id="b81db-170">借助启动 Windows PowerShell，运行停止进程 cmdlet 与`ProcessId`参数设置为停止进程根据其标识符。</span><span class="sxs-lookup"><span data-stu-id="b81db-170">With Windows PowerShell started, run the Stop-Proc cmdlet with the `ProcessId` parameter set to stop a process based on its identifier.</span></span> <span data-ttu-id="b81db-171">在这种情况下，使用该 cmdlet`ProcessId`参数设置为停止进程。</span><span class="sxs-lookup"><span data-stu-id="b81db-171">In this case, the cmdlet is using the `ProcessId` parameter set to stop the process.</span></span>

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="b81db-172">借助启动 Windows PowerShell，运行停止进程 cmdlet 与`InputObject`参数设置为记事本对象来检索上停止进程`Get-Process`命令。</span><span class="sxs-lookup"><span data-stu-id="b81db-172">With Windows PowerShell started, run the Stop-Proc cmdlet with the `InputObject` parameter set to stop processes on the Notepad object retrieved by the `Get-Process` command.</span></span>

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="b81db-173">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b81db-173">See Also</span></span>

[<span data-ttu-id="b81db-174">创建一个 Cmdlet 来修改系统</span><span class="sxs-lookup"><span data-stu-id="b81db-174">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="b81db-175">如何创建 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b81db-175">How to Create a Windows PowerShell Cmdlet</span></span>](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="b81db-176">扩展对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="b81db-176">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="b81db-177">如何注册 Cmdlet、 提供程序，和托管应用程序</span><span class="sxs-lookup"><span data-stu-id="b81db-177">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="b81db-178">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b81db-178">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
