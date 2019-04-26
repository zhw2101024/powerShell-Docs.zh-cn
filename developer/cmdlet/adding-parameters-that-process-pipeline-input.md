---
title: 添加处理管道的输入参数 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programmer's Guide], pipeline input
ms.assetid: 09bf70a9-7c76-4ffe-b3f0-a1d5f10a0931
caps.latest.revision: 8
ms.openlocfilehash: bd52dc8aee7975d0899083a5c2f595b17690dc33
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068753"
---
# <a name="adding-parameters-that-process-pipeline-input"></a><span data-ttu-id="c31d2-102">添加用于处理管道输入的参数</span><span class="sxs-lookup"><span data-stu-id="c31d2-102">Adding Parameters that Process Pipeline Input</span></span>

<span data-ttu-id="c31d2-103">一个源的一个 cmdlet 是输入的源自于上游 cmdlet 在管道上的对象。</span><span class="sxs-lookup"><span data-stu-id="c31d2-103">One source of input for a cmdlet is an object on the pipeline that originates from an upstream cmdlet.</span></span> <span data-ttu-id="c31d2-104">本部分介绍如何将参数添加到 Get-proc cmdlet (中所述[创建第一个 Cmdlet](./creating-a-cmdlet-without-parameters.md))，以便该 cmdlet 可以处理管道对象。</span><span class="sxs-lookup"><span data-stu-id="c31d2-104">This section describes how to add a parameter to the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process pipeline objects.</span></span>

<span data-ttu-id="c31d2-105">此 Get-proc cmdlet 使用`Name`接受来自管道对象的输入参数从基于提供的名称，在本地计算机检索进程信息，然后在命令行中显示有关进程的信息。</span><span class="sxs-lookup"><span data-stu-id="c31d2-105">This Get-Proc cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

<span data-ttu-id="c31d2-106">在本部分中的主题包括：</span><span class="sxs-lookup"><span data-stu-id="c31d2-106">Topics in this section include the following:</span></span>

- [<span data-ttu-id="c31d2-107">定义在 Cmdlet 类</span><span class="sxs-lookup"><span data-stu-id="c31d2-107">Defining the Cmdlet Class</span></span>](#Defining-the-Cmdlet-Class)

- [<span data-ttu-id="c31d2-108">定义来自管道的输入</span><span class="sxs-lookup"><span data-stu-id="c31d2-108">Defining Input from the Pipeline</span></span>](#Defining-Input-from-the-Pipeline)

- [<span data-ttu-id="c31d2-109">重写方法的处理的输入</span><span class="sxs-lookup"><span data-stu-id="c31d2-109">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="c31d2-110">代码示例</span><span class="sxs-lookup"><span data-stu-id="c31d2-110">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="c31d2-111">定义对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="c31d2-111">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="c31d2-112">生成该 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c31d2-112">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="c31d2-113">测试 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c31d2-113">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="c31d2-114">定义在 Cmdlet 类</span><span class="sxs-lookup"><span data-stu-id="c31d2-114">Defining the Cmdlet Class</span></span>

<span data-ttu-id="c31d2-115">Cmdlet 创建的第一步是始终命名 cmdlet 和实现该 cmdlet 的.NET 类声明。</span><span class="sxs-lookup"><span data-stu-id="c31d2-115">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="c31d2-116">此 cmdlet 检索进程信息，因此在此处选择谓词名称为"Get"。</span><span class="sxs-lookup"><span data-stu-id="c31d2-116">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="c31d2-117">（几乎任何类型的检索信息的 cmdlet 可以处理命令行输入）。有关已批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 的动词名称](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="c31d2-117">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="c31d2-118">下面是此 Get-proc cmdlet 的定义。</span><span class="sxs-lookup"><span data-stu-id="c31d2-118">The following is the definition for this Get-Proc cmdlet.</span></span> <span data-ttu-id="c31d2-119">此定义的详细信息中提供了[创建第一个 Cmdlet](./creating-a-cmdlet-without-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="c31d2-119">Details of this definition are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a><span data-ttu-id="c31d2-120">定义来自管道的输入</span><span class="sxs-lookup"><span data-stu-id="c31d2-120">Defining Input from the Pipeline</span></span>

<span data-ttu-id="c31d2-121">本部分介绍如何定义来自 cmdlet 的管道的输入。</span><span class="sxs-lookup"><span data-stu-id="c31d2-121">This section describes how to define input from the pipeline for a cmdlet.</span></span> <span data-ttu-id="c31d2-122">此 Get-proc cmdlet 定义了一个属性，表示`Name`参数中所述[添加该进程的命令行输入的参数](./adding-parameters-that-process-command-line-input.md)。</span><span class="sxs-lookup"><span data-stu-id="c31d2-122">This Get-Proc cmdlet defines a property that represents the `Name` parameter as described in [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span> <span data-ttu-id="c31d2-123">（请参阅该主题有关声明参数的常规信息。）</span><span class="sxs-lookup"><span data-stu-id="c31d2-123">(See that topic for general information about declaring parameters.)</span></span>

<span data-ttu-id="c31d2-124">但是，当一个 cmdlet 需要处理管道输入，它必须具有绑定到输入值通过 Windows PowerShell 运行时及其参数。</span><span class="sxs-lookup"><span data-stu-id="c31d2-124">However, when a cmdlet needs to process pipeline input, it must have its parameters bound to input values by the Windows PowerShell runtime.</span></span> <span data-ttu-id="c31d2-125">若要执行此操作，必须添加`ValueFromPipeline`关键字或添加`ValueFromPipelineByProperty`关键字[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)特性声明。</span><span class="sxs-lookup"><span data-stu-id="c31d2-125">To do this, you must add the `ValueFromPipeline` keyword or add the `ValueFromPipelineByProperty` keyword to the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="c31d2-126">指定`ValueFromPipeline`关键字，如果该 cmdlet 将访问完整的输入的对象。</span><span class="sxs-lookup"><span data-stu-id="c31d2-126">Specify the `ValueFromPipeline` keyword if the cmdlet accesses the complete input object.</span></span> <span data-ttu-id="c31d2-127">指定`ValueFromPipelineByProperty`如果该 cmdlet 将访问的对象的属性。</span><span class="sxs-lookup"><span data-stu-id="c31d2-127">Specify the `ValueFromPipelineByProperty` if the cmdlet accesses only a property of the object.</span></span>

<span data-ttu-id="c31d2-128">下面是参数声明为`Name`接受管道输入此 Get-proc cmdlet 的参数。</span><span class="sxs-lookup"><span data-stu-id="c31d2-128">Here is the parameter declaration for the `Name` parameter of this Get-Proc cmdlet that accepts pipeline input.</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

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

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#GetProc03VBNameParameter](Msh_samplesgetproc03#GetProc03VBNameParameter)]  -->

<span data-ttu-id="c31d2-129">以前的声明集`ValueFromPipeline`关键字`true`，以便如果对象是同一类型作为参数，Windows PowerShell 运行时将将参数绑定到传入的对象或可强制转换为同一类型。</span><span class="sxs-lookup"><span data-stu-id="c31d2-129">The previous declaration sets the `ValueFromPipeline` keyword to `true` so that the Windows PowerShell runtime will bind the parameter to the incoming object if the object is the same type as the parameter, or if it can be coerced to the same type.</span></span> <span data-ttu-id="c31d2-130">`ValueFromPipelineByPropertyName`关键字也设置为`true`，以便 Windows PowerShell 运行时将检查的传入对象`Name`属性。</span><span class="sxs-lookup"><span data-stu-id="c31d2-130">The `ValueFromPipelineByPropertyName` keyword is also set to `true` so that the Windows PowerShell runtime will check the incoming object for a `Name` property.</span></span> <span data-ttu-id="c31d2-131">如果传入的对象具有这种属性，将绑定在运行时`Name`参数`Name`传入对象的属性。</span><span class="sxs-lookup"><span data-stu-id="c31d2-131">If the incoming object has such a property, the runtime will bind the `Name` parameter to the `Name` property of the incoming object.</span></span>

> [!NOTE]
> <span data-ttu-id="c31d2-132">设置`ValueFromPipeline`属性 (attribute) 关键字参数优先于为设置`ValueFromPipelineByPropertyName`关键字。</span><span class="sxs-lookup"><span data-stu-id="c31d2-132">The setting of the `ValueFromPipeline` attribute keyword for a parameter takes precedence over the setting for the `ValueFromPipelineByPropertyName` keyword.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="c31d2-133">重写方法的处理的输入</span><span class="sxs-lookup"><span data-stu-id="c31d2-133">Overriding an Input Processing Method</span></span>

<span data-ttu-id="c31d2-134">如果你的 cmdlet 是处理管道输入，则需要重写相应的输入处理方法。</span><span class="sxs-lookup"><span data-stu-id="c31d2-134">If your cmdlet is to handle pipeline input, it needs to override the appropriate input processing methods.</span></span> <span data-ttu-id="c31d2-135">中引入的基本输入的处理方法[创建第一个 Cmdlet](./creating-a-cmdlet-without-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="c31d2-135">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="c31d2-136">此 Get-proc cmdlet 覆盖[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法以处理`Name`参数输入提供的用户或脚本。</span><span class="sxs-lookup"><span data-stu-id="c31d2-136">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="c31d2-137">如果未提供名称，此方法将获取每个请求的进程名称或所有进程的进程。</span><span class="sxs-lookup"><span data-stu-id="c31d2-137">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="c31d2-138">请注意，在[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)，在调用[System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29)是输出机制，用于将输出发送到管道对象。</span><span class="sxs-lookup"><span data-stu-id="c31d2-138">Notice that within [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="c31d2-139">此调用，第二个参数`enumerateCollection`，设置为`true`告诉 Windows PowerShell 运行时，若要枚举的进程对象的数组和一个进程一次写入命令行。</span><span class="sxs-lookup"><span data-stu-id="c31d2-139">The second parameter of this call, `enumerateCollection`, is set to `true` to tell the Windows PowerShell runtime to enumerate the array of process objects, and write one process at a time to the command line.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no process names are passed to the cmdlet, get all processes.
  if (processNames == null)
  {
      // Write the processes to the pipeline making them available
      // to the next cmdlet. The second argument of this call tells
      // PowerShell to enumerate the array, and send one process at a
      // time to the pipeline.
      WriteObject(Process.GetProcesses(), true);
  }
  else
  {
    // If process names are passed to the cmdlet, get and write
    // the associated processes.
    foreach (string name in processNames)
    {
      WriteObject(Process.GetProcessesByName(name), true);
    } // End foreach (string name...).
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()
    Dim processes As Process()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        processes = Process.GetProcesses()
    Else

        '/ If process names are specified, write the processes to the
        '/ pipeline to display them or make them available to the next cmdlet.
        For Each name As String In processNames
            '/ The second parameter of this call tells PowerShell to enumerate the
            '/ array, and send one process at a time to the pipeline.
            WriteObject(Process.GetProcessesByName(name), True)
        Next
    End If

End Sub 'ProcessRecord
```

## <a name="code-sample"></a><span data-ttu-id="c31d2-140">代码示例</span><span class="sxs-lookup"><span data-stu-id="c31d2-140">Code Sample</span></span>

<span data-ttu-id="c31d2-141">有关完整C#示例代码，请参阅[GetProcessSample03 示例](./getprocesssample03-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="c31d2-141">For the complete C# sample code, see [GetProcessSample03 Sample](./getprocesssample03-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="c31d2-142">定义对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="c31d2-142">Defining Object Types and Formatting</span></span>

<span data-ttu-id="c31d2-143">Windows PowerShell cmdlet 使用.Net 对象之间传递信息。</span><span class="sxs-lookup"><span data-stu-id="c31d2-143">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="c31d2-144">因此，一个 cmdlet 可能需要定义其自己的类型，或者该 cmdlet 可能需要扩展现有类型提供的另一个 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c31d2-144">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="c31d2-145">有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式设置](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。</span><span class="sxs-lookup"><span data-stu-id="c31d2-145">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="c31d2-146">生成该 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c31d2-146">Building the Cmdlet</span></span>

<span data-ttu-id="c31d2-147">实现必须将它注册使用通过 Windows PowerShell 的 Windows PowerShell cmdlet 后管理单元。</span><span class="sxs-lookup"><span data-stu-id="c31d2-147">After implementing a cmdlet it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="c31d2-148">有关注册 cmdlet 的详细信息，请参阅[如何注册 Cmdlet、 提供商和主机应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="c31d2-148">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="c31d2-149">测试 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c31d2-149">Testing the Cmdlet</span></span>

<span data-ttu-id="c31d2-150">你的 cmdlet 具有已注册到 Windows PowerShell，通过命令行上运行测试。</span><span class="sxs-lookup"><span data-stu-id="c31d2-150">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="c31d2-151">例如，测试的代码示例 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c31d2-151">For example, test the code for the sample cmdlet.</span></span> <span data-ttu-id="c31d2-152">有关使用命令行中的 cmdlet 的详细信息，请参阅[Windows PowerShell 入门学习](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="c31d2-152">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="c31d2-153">在 Windows PowerShell 提示符处，输入以下命令来检索通过管道的进程名称。</span><span class="sxs-lookup"><span data-stu-id="c31d2-153">At the Windows PowerShell prompt, enter the following commands to retrieve the process names through the pipeline.</span></span>

    ```powershell
    PS> type ProcessNames | get-proc
    ```

<span data-ttu-id="c31d2-154">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="c31d2-154">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- <span data-ttu-id="c31d2-155">输入以下行，以获取进程对象具有`Name`从名为"IEXPLORE"的进程的属性。</span><span class="sxs-lookup"><span data-stu-id="c31d2-155">Enter the following lines to get the process objects that have a `Name` property from the processes called "IEXPLORE".</span></span> <span data-ttu-id="c31d2-156">此示例使用`Get-Process`作为上游命令来检索"IEXPLORE"进程 cmdlet （由 Windows PowerShell 提供）。</span><span class="sxs-lookup"><span data-stu-id="c31d2-156">This example uses the `Get-Process` cmdlet (provided by Windows PowerShell) as an upstream command to retrieve the "IEXPLORE" processes.</span></span>

    ```powershell
    PS> get-process iexplore | get-proc
    ```

<span data-ttu-id="c31d2-157">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="c31d2-157">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a><span data-ttu-id="c31d2-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c31d2-158">See Also</span></span>

[<span data-ttu-id="c31d2-159">添加处理命令行输入的参数</span><span class="sxs-lookup"><span data-stu-id="c31d2-159">Adding Parameters that Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="c31d2-160">创建第一个 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c31d2-160">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="c31d2-161">扩展对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="c31d2-161">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="c31d2-162">如何注册 Cmdlet、 提供程序，和托管应用程序</span><span class="sxs-lookup"><span data-stu-id="c31d2-162">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="c31d2-163">Windows PowerShell 参考</span><span class="sxs-lookup"><span data-stu-id="c31d2-163">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="c31d2-164">Cmdlet 示例</span><span class="sxs-lookup"><span data-stu-id="c31d2-164">Cmdlet Samples</span></span>](./cmdlet-samples.md)
