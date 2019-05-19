---
title: 将处理命令行输入的参数添加 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], parameters
- Get-Proc cmdlet [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], command line input
- command line input [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], creating
ms.assetid: da0b32f8-7b51-440e-a061-3177b5759e0e
caps.latest.revision: 9
ms.openlocfilehash: c9ad84c5bcb6826fcf51db9a1f1a578a65a1f275
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854946"
---
# <a name="adding-parameters-that-process-command-line-input"></a><span data-ttu-id="77dfe-102">添加用于处理命令行输入的参数</span><span class="sxs-lookup"><span data-stu-id="77dfe-102">Adding Parameters That Process Command-Line Input</span></span>

<span data-ttu-id="77dfe-103">一个用于某个 cmdlet 的源是输入的命令行。</span><span class="sxs-lookup"><span data-stu-id="77dfe-103">One source of input for a cmdlet is the command line.</span></span> <span data-ttu-id="77dfe-104">本主题介绍如何将参数添加到**Get-proc** cmdlet (中所述[创建第一个 Cmdlet](./creating-a-cmdlet-without-parameters.md))，以便该 cmdlet 可以处理来自基于显式的本地计算机的输入对象传递给 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="77dfe-104">This topic describes how to add a parameter to the **Get-Proc** cmdlet (which is described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process input from the local computer based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="77dfe-105">**Get-proc**所述的 cmdlet 此处检索的过程基于它们的名称，然后显示在命令提示符下的进程的信息。</span><span class="sxs-lookup"><span data-stu-id="77dfe-105">The **Get-Proc** cmdlet described here retrieves processes based on their names, and then displays information about the processes at a command prompt.</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="77dfe-106">定义在 Cmdlet 类</span><span class="sxs-lookup"><span data-stu-id="77dfe-106">Defining the Cmdlet Class</span></span>

<span data-ttu-id="77dfe-107">Cmdlet 创建的第一步是 cmdlet 命名和.NET Framework 类实现该 cmdlet 的声明。</span><span class="sxs-lookup"><span data-stu-id="77dfe-107">The first step in cmdlet creation is cmdlet naming and the declaration of the .NET Framework class that implements the cmdlet.</span></span> <span data-ttu-id="77dfe-108">此 cmdlet 检索进程信息，因此在此处选择谓词名称为"Get"。</span><span class="sxs-lookup"><span data-stu-id="77dfe-108">This cmdlet retrieves process information, so the verb name chosen here is "Get."</span></span> <span data-ttu-id="77dfe-109">（几乎任何类型的检索信息的 cmdlet 可以处理命令行输入）。有关已批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 的动词名称](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="77dfe-109">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="77dfe-110">下面是有关在类声明**Get-proc** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="77dfe-110">Here's the class declaration for the **Get-Proc** cmdlet.</span></span> <span data-ttu-id="77dfe-111">中提供了有关此定义的详细信息[创建第一个 Cmdlet](./creating-a-cmdlet-without-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="77dfe-111">Details about this definition are provided in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a><span data-ttu-id="77dfe-112">声明参数</span><span class="sxs-lookup"><span data-stu-id="77dfe-112">Declaring Parameters</span></span>

<span data-ttu-id="77dfe-113">Cmdlet 参数使用户能够向该 cmdlet 提供输入。</span><span class="sxs-lookup"><span data-stu-id="77dfe-113">A cmdlet parameter enables the user to provide input to the cmdlet.</span></span> <span data-ttu-id="77dfe-114">在以下示例中， **Get-proc**并`Get-Member`是通过管道传递 cmdlet 的名称和`MemberType`是一个参数为`Get-Member`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="77dfe-114">In the following example, **Get-Proc** and `Get-Member` are the names of pipelined cmdlets, and `MemberType` is a parameter for the `Get-Member` cmdlet.</span></span> <span data-ttu-id="77dfe-115">该参数具有参数"属性"。</span><span class="sxs-lookup"><span data-stu-id="77dfe-115">The parameter has the argument "property."</span></span>

<span data-ttu-id="77dfe-116">**PS > 获取进程;`get-member` -membertype 属性**</span><span class="sxs-lookup"><span data-stu-id="77dfe-116">**PS> get-proc ; `get-member` -membertype property**</span></span>

<span data-ttu-id="77dfe-117">若要声明 cmdlet 的参数，必须首先定义表示参数的属性。</span><span class="sxs-lookup"><span data-stu-id="77dfe-117">To declare parameters for a cmdlet, you must first define the properties that represent the parameters.</span></span> <span data-ttu-id="77dfe-118">在中**Get-proc** cmdlet，唯一的参数是`Name`，在这种情况下表示要检索的.NET Framework 进程对象的名称。</span><span class="sxs-lookup"><span data-stu-id="77dfe-118">In the **Get-Proc** cmdlet, the only parameter is `Name`, which in this case represents the name of the .NET Framework process object to retrieve.</span></span> <span data-ttu-id="77dfe-119">因此，在 cmdlet 类定义为接受名称的数组为类型字符串的属性。</span><span class="sxs-lookup"><span data-stu-id="77dfe-119">Therefore, the cmdlet class defines a property of type string to accept an array of names.</span></span>

<span data-ttu-id="77dfe-120">下面是参数声明`Name`的参数**Get-proc** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="77dfe-120">Here's the parameter declaration for the `Name` parameter of the **Get-Proc** cmdlet.</span></span>

```csharp
/// <summary>
/// Specify the cmdlet Name parameter.
/// </summary>
  [Parameter(Position = 0)]
  [ValidateNotNullOrEmpty]
  public string[] Name
  {
    get { return processNames; }
    set { processNames = value; }
  }
  private string[] processNames;

  #endregion Parameters
```

```vb
<Parameter(Position:=0), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

<span data-ttu-id="77dfe-121">若要通知的 Windows PowerShell 运行此属性时`Name`参数， [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)属性添加到属性定义。</span><span class="sxs-lookup"><span data-stu-id="77dfe-121">To inform the Windows PowerShell runtime that this property is the `Name` parameter, a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute is added to the property definition.</span></span> <span data-ttu-id="77dfe-122">声明此属性的基本语法是`[Parameter()]`。</span><span class="sxs-lookup"><span data-stu-id="77dfe-122">The basic syntax for declaring this attribute is `[Parameter()]`.</span></span>

> [!NOTE]
> <span data-ttu-id="77dfe-123">参数必须显式标记为公共。</span><span class="sxs-lookup"><span data-stu-id="77dfe-123">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="77dfe-124">未标记为公共的默认为内部和通过 Windows PowerShell 运行时找不到的参数。</span><span class="sxs-lookup"><span data-stu-id="77dfe-124">Parameters that are not marked as public default to internal and are not found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="77dfe-125">此 cmdlet 使用的字符串数组`Name`参数。</span><span class="sxs-lookup"><span data-stu-id="77dfe-125">This cmdlet uses an array of strings for the `Name` parameter.</span></span> <span data-ttu-id="77dfe-126">如果可能，你的 cmdlet 还应定义参数作为一个数组，因为这允许该 cmdlet 将接受多个项。</span><span class="sxs-lookup"><span data-stu-id="77dfe-126">If possible, your cmdlet should also define a parameter as an array, because this allows the cmdlet to accept more than one item.</span></span>

#### <a name="things-to-remember-about-parameter-definitions"></a><span data-ttu-id="77dfe-127">要记住有关参数定义的事项</span><span class="sxs-lookup"><span data-stu-id="77dfe-127">Things to Remember About Parameter Definitions</span></span>

- <span data-ttu-id="77dfe-128">预定义的 Windows PowerShell 参数名称和数据类型应重复使用尽可能多地以确保你的 cmdlet 使用 Windows PowerShell cmdlet 兼容。</span><span class="sxs-lookup"><span data-stu-id="77dfe-128">Predefined Windows PowerShell parameter names and data types should be reused as much as possible to ensure that your cmdlet is compatible with Windows PowerShell cmdlets.</span></span> <span data-ttu-id="77dfe-129">例如，如果所有 cmdlet 都使用预定义`Id`参数名称，若要轻松地识别资源，用户将可理解的参数，而不考虑他们使用哪些 cmdlet 的含义。</span><span class="sxs-lookup"><span data-stu-id="77dfe-129">For example, if all cmdlets use the predefined `Id` parameter name to identify a resource, user will easily understand the meaning of the parameter, regardless of what cmdlet they are using.</span></span> <span data-ttu-id="77dfe-130">基本上，参数名称遵循相同的规则所使用的公共语言运行时 (CLR) 中的变量名称。</span><span class="sxs-lookup"><span data-stu-id="77dfe-130">Basically, parameter names follow the same rules as those used for variable names in the common language runtime (CLR).</span></span> <span data-ttu-id="77dfe-131">有关参数命名的详细信息，请参阅[Cmdlet 参数名称](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb)。</span><span class="sxs-lookup"><span data-stu-id="77dfe-131">For more information about parameter naming, see [Cmdlet Parameter Names](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span></span>

- <span data-ttu-id="77dfe-132">Windows PowerShell 保留几个参数名称，以提供一致的用户体验。</span><span class="sxs-lookup"><span data-stu-id="77dfe-132">Windows PowerShell reserves a few parameter names to provide a consistent user experience.</span></span> <span data-ttu-id="77dfe-133">不使用这些参数名称： `WhatIf`， `Confirm`， `Verbose`， `Debug`， `Warn`， `ErrorAction`， `ErrorVariable`， `OutVariable`，和`OutBuffer`。</span><span class="sxs-lookup"><span data-stu-id="77dfe-133">Do not use these parameter names: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, and `OutBuffer`.</span></span> <span data-ttu-id="77dfe-134">此外，保留这些参数名称的下列别名： `vb`， `db`， `ea`， `ev`， `ov`，并`ob`。</span><span class="sxs-lookup"><span data-stu-id="77dfe-134">Additionally, the following aliases for these parameter names are reserved: `vb`, `db`, `ea`, `ev`, `ov`, and `ob`.</span></span>

- <span data-ttu-id="77dfe-135">`Name` 是简单和常见的参数名称，建议在 cmdlet 中使用。</span><span class="sxs-lookup"><span data-stu-id="77dfe-135">`Name` is a simple and common parameter name, recommended for use in your cmdlets.</span></span> <span data-ttu-id="77dfe-136">最好选择类似下面的参数名称是唯一的一个特定的 cmdlet 和难以记住的复杂名称。</span><span class="sxs-lookup"><span data-stu-id="77dfe-136">It is better to choose a parameter name like this than a complex name that is unique to a specific cmdlet and hard to remember.</span></span>

- <span data-ttu-id="77dfe-137">参数是在 Windows PowerShell 中，不区分大小写的尽管默认情况下在 shell 保留大小写。</span><span class="sxs-lookup"><span data-stu-id="77dfe-137">Parameters are case-insensitive in Windows PowerShell, although by default the shell preserves case.</span></span> <span data-ttu-id="77dfe-138">参数区分大小写取决于该 cmdlet 的操作。</span><span class="sxs-lookup"><span data-stu-id="77dfe-138">Case-sensitivity of the arguments depends on the operation of the cmdlet.</span></span> <span data-ttu-id="77dfe-139">参数指定在命令行传递到参数。</span><span class="sxs-lookup"><span data-stu-id="77dfe-139">Arguments are passed to a parameter as specified at the command line.</span></span>

- <span data-ttu-id="77dfe-140">有关其他参数声明的示例，请参阅[Cmdlet 参数](./cmdlet-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="77dfe-140">For examples of other parameter declarations, see [Cmdlet Parameters](./cmdlet-parameters.md).</span></span>

## <a name="declaring-parameters-as-positional-or-named"></a><span data-ttu-id="77dfe-141">将参数声明为位置或命名</span><span class="sxs-lookup"><span data-stu-id="77dfe-141">Declaring Parameters as Positional or Named</span></span>

<span data-ttu-id="77dfe-142">Cmdlet 必须为位置或命名参数设置每个参数。</span><span class="sxs-lookup"><span data-stu-id="77dfe-142">A cmdlet must set each parameter as either a positional or named parameter.</span></span> <span data-ttu-id="77dfe-143">这两种类型的参数采用单个参数，用逗号隔开和布尔值设置的多个自变量。</span><span class="sxs-lookup"><span data-stu-id="77dfe-143">Both kinds of parameters accept single arguments, multiple arguments separated by commas, and Boolean settings.</span></span> <span data-ttu-id="77dfe-144">一个布尔型参数，也称为*切换*，处理仅布尔设置。</span><span class="sxs-lookup"><span data-stu-id="77dfe-144">A Boolean parameter, also called a *switch*, handles only Boolean settings.</span></span> <span data-ttu-id="77dfe-145">开关用于确定参数存在。</span><span class="sxs-lookup"><span data-stu-id="77dfe-145">The switch is used to determine the presence of the parameter.</span></span> <span data-ttu-id="77dfe-146">建议的默认值是`false`。</span><span class="sxs-lookup"><span data-stu-id="77dfe-146">The recommended default is `false`.</span></span>

<span data-ttu-id="77dfe-147">该示例**Get-proc** cmdlet 定义`Name`参数用作位置参数具有位置 0。</span><span class="sxs-lookup"><span data-stu-id="77dfe-147">The sample **Get-Proc** cmdlet defines the `Name` parameter as a positional parameter with position 0.</span></span> <span data-ttu-id="77dfe-148">这意味着用户输入的命令行的第一个参数将自动插入此参数。</span><span class="sxs-lookup"><span data-stu-id="77dfe-148">This means that the first argument the user enters on the command line is automatically inserted for this parameter.</span></span> <span data-ttu-id="77dfe-149">如果你想要定义一个命名的参数，用户必须指定用于将参数名称从命令行中，将保留`Position`带特性声明的关键字。</span><span class="sxs-lookup"><span data-stu-id="77dfe-149">If you want to define a named parameter, for which the user must specify the parameter name from the command line, leave the `Position` keyword out of the attribute declaration.</span></span>

> [!NOTE]
> <span data-ttu-id="77dfe-150">除非必须命名参数，否则我们建议您进行最常用的参数位置，以便用户不需要键入参数名称。</span><span class="sxs-lookup"><span data-stu-id="77dfe-150">Unless parameters must be named, we recommend that you make the most-used parameters positional so that users will not have to type the parameter name.</span></span>

## <a name="declaring-parameters-as-mandatory-or-optional"></a><span data-ttu-id="77dfe-151">将参数声明为必需或可选</span><span class="sxs-lookup"><span data-stu-id="77dfe-151">Declaring Parameters as Mandatory or Optional</span></span>

<span data-ttu-id="77dfe-152">Cmdlet 必须设置每个参数为可选或必需的参数。</span><span class="sxs-lookup"><span data-stu-id="77dfe-152">A cmdlet must set each parameter as either an optional or a mandatory parameter.</span></span> <span data-ttu-id="77dfe-153">在此示例中**Get-proc** cmdlet，`Name`参数定义为可选，因为`Mandatory`在特性声明中未设置关键字。</span><span class="sxs-lookup"><span data-stu-id="77dfe-153">In the sample **Get-Proc** cmdlet, the `Name` parameter is defined as optional because the `Mandatory` keyword is not set in the attribute declaration.</span></span>

## <a name="supporting-parameter-validation"></a><span data-ttu-id="77dfe-154">支持的参数验证</span><span class="sxs-lookup"><span data-stu-id="77dfe-154">Supporting Parameter Validation</span></span>

<span data-ttu-id="77dfe-155">该示例**Get-proc** cmdlet 添加输入的验证属性[System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute)到`Name`参数来启用验证，既不是输入`null`也不为空。</span><span class="sxs-lookup"><span data-stu-id="77dfe-155">The sample **Get-Proc** cmdlet adds an input validation attribute, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), to the `Name` parameter to enable validation that the input is neither `null` nor empty.</span></span> <span data-ttu-id="77dfe-156">此属性是由 Windows PowerShell 提供的多个验证属性之一。</span><span class="sxs-lookup"><span data-stu-id="77dfe-156">This attribute is one of several validation attributes provided by Windows PowerShell.</span></span> <span data-ttu-id="77dfe-157">有关其他验证特性的示例，请参阅[验证参数输入](./validating-parameter-input.md)。</span><span class="sxs-lookup"><span data-stu-id="77dfe-157">For examples of other validation attributes, see [Validating Parameter Input](./validating-parameter-input.md).</span></span>

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="77dfe-158">重写方法的处理的输入</span><span class="sxs-lookup"><span data-stu-id="77dfe-158">Overriding an Input Processing Method</span></span>

<span data-ttu-id="77dfe-159">如果你的 cmdlet 将处理命令行输入，则必须重写相应的输入处理方法。</span><span class="sxs-lookup"><span data-stu-id="77dfe-159">If your cmdlet is to handle command-line input, it must override the appropriate input processing methods.</span></span> <span data-ttu-id="77dfe-160">中引入的基本输入的处理方法[创建第一个 Cmdlet](./creating-a-cmdlet-without-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="77dfe-160">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="77dfe-161">**Get-proc** cmdlet 将重写[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法以处理`Name`参数输入提供的用户或脚本。</span><span class="sxs-lookup"><span data-stu-id="77dfe-161">The **Get-Proc** cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="77dfe-162">如果未提供名称，此方法获取每个请求的进程名称，或全部进程的进程。</span><span class="sxs-lookup"><span data-stu-id="77dfe-162">This method gets the processes for each requested process name, or all for processes if no name is provided.</span></span> <span data-ttu-id="77dfe-163">请注意，在[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)，在调用[System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)是输出机制，用于将输出发送到管道对象。</span><span class="sxs-lookup"><span data-stu-id="77dfe-163">Notice that in [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="77dfe-164">此调用，第二个参数`enumerateCollection`，设置为`true`以通知 Windows PowerShell 运行时枚举的进程对象的输出数组和一个进程一次写入命令行。</span><span class="sxs-lookup"><span data-stu-id="77dfe-164">The second parameter of this call, `enumerateCollection`, is set to `true` to inform the Windows PowerShell runtime to enumerate the output array of process objects and write one process at a time to the command line.</span></span>

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
    }
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        Dim processes As Process()
        processes = Process.GetProcesses()
    End If

    '/ If process names are specified, write the processes to the
    '/ pipeline to display them or make them available to the next cmdlet.

    For Each name As String In processNames
        '/ The second parameter of this call tells PowerShell to enumerate the
        '/ array, and send one process at a time to the pipeline.
        WriteObject(Process.GetProcessesByName(name), True)
    Next

End Sub 'ProcessRecord
```

## <a name="code-sample"></a><span data-ttu-id="77dfe-165">代码示例</span><span class="sxs-lookup"><span data-stu-id="77dfe-165">Code Sample</span></span>

<span data-ttu-id="77dfe-166">有关完整C#示例代码，请参阅[GetProcessSample02 示例](./getprocesssample02-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="77dfe-166">For the complete C# sample code, see [GetProcessSample02 Sample](./getprocesssample02-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="77dfe-167">定义对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="77dfe-167">Defining Object Types and Formatting</span></span>

<span data-ttu-id="77dfe-168">Windows PowerShell cmdlet 通过使用.NET Framework 对象之间传递信息。</span><span class="sxs-lookup"><span data-stu-id="77dfe-168">Windows PowerShell passes information between cmdlets by using .NET Framework objects.</span></span> <span data-ttu-id="77dfe-169">因此，一个 cmdlet 可能需要定义其自己的类型，或者一个 cmdlet 可能需要扩展现有类型提供的另一个 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="77dfe-169">Consequently, a cmdlet might need to define its own type, or a cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="77dfe-170">有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式设置](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。</span><span class="sxs-lookup"><span data-stu-id="77dfe-170">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="77dfe-171">生成该 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="77dfe-171">Building the Cmdlet</span></span>

<span data-ttu-id="77dfe-172">实现一个 cmdlet 后，必须使用 Windows PowerShell 使用 Windows PowerShell 管理单元来注册它。</span><span class="sxs-lookup"><span data-stu-id="77dfe-172">After you implement a cmdlet, you must register it with Windows PowerShell by using a Windows PowerShell snap-in.</span></span> <span data-ttu-id="77dfe-173">有关注册 cmdlet 的详细信息，请参阅[如何注册 Cmdlet、 提供商和主机应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="77dfe-173">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="77dfe-174">测试 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="77dfe-174">Testing the Cmdlet</span></span>

<span data-ttu-id="77dfe-175">使用 Windows PowerShell 注册 cmdlet 时，可以通过运行命令行上对它进行测试。</span><span class="sxs-lookup"><span data-stu-id="77dfe-175">When your cmdlet is registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="77dfe-176">以下是两种方法来测试该示例 cmdlet 的代码。</span><span class="sxs-lookup"><span data-stu-id="77dfe-176">Here are two ways to test the code for the sample cmdlet.</span></span> <span data-ttu-id="77dfe-177">有关使用命令行中的 cmdlet 的详细信息，请参阅[Windows PowerShell 入门学习](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="77dfe-177">For more information about using cmdlets from the command line, see [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="77dfe-178">在 Windows PowerShell 提示符下，使用以下命令列出 Internet Explorer 进程，名为"IEXPLORE。"</span><span class="sxs-lookup"><span data-stu-id="77dfe-178">At the Windows PowerShell prompt, use the following command to list the Internet Explorer process, which is named "IEXPLORE."</span></span>

    ```powershell
    PS> get-proc -name iexplore
    ```

<span data-ttu-id="77dfe-179">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="77dfe-179">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- <span data-ttu-id="77dfe-180">若要列出名为"IEXPLORE"的 Internet Explorer、 Outlook 和记事本进程，"OUTLOOK"和"记事本"，请使用以下命令。</span><span class="sxs-lookup"><span data-stu-id="77dfe-180">To list the Internet Explorer, Outlook, and Notepad processes named "IEXPLORE," "OUTLOOK," and "NOTEPAD," use the following command.</span></span> <span data-ttu-id="77dfe-181">如果有多个进程，将显示所有这些。</span><span class="sxs-lookup"><span data-stu-id="77dfe-181">If there are multiple processes, all of them are displayed.</span></span>

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

<span data-ttu-id="77dfe-182">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="77dfe-182">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a><span data-ttu-id="77dfe-183">另请参阅</span><span class="sxs-lookup"><span data-stu-id="77dfe-183">See Also</span></span>

[<span data-ttu-id="77dfe-184">添加进程管道输入的参数</span><span class="sxs-lookup"><span data-stu-id="77dfe-184">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="77dfe-185">创建第一个 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="77dfe-185">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="77dfe-186">扩展对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="77dfe-186">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="77dfe-187">如何注册 Cmdlet、 提供程序，和托管应用程序</span><span class="sxs-lookup"><span data-stu-id="77dfe-187">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="77dfe-188">Windows PowerShell 参考</span><span class="sxs-lookup"><span data-stu-id="77dfe-188">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="77dfe-189">Cmdlet 示例</span><span class="sxs-lookup"><span data-stu-id="77dfe-189">Cmdlet Samples</span></span>](./cmdlet-samples.md)
