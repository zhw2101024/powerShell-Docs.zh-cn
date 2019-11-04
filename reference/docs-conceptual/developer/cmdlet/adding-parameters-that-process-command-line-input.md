---
title: 添加用于处理命令行输入的参数 |Microsoft Docs
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
ms.openlocfilehash: 7db93af33717dc4802ed915793f6cd570cfb48f6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364626"
---
# <a name="adding-parameters-that-process-command-line-input"></a><span data-ttu-id="cdb65-102">添加用于处理命令行输入的参数</span><span class="sxs-lookup"><span data-stu-id="cdb65-102">Adding Parameters That Process Command-Line Input</span></span>

<span data-ttu-id="cdb65-103">一个 cmdlet 的输入源是命令行。</span><span class="sxs-lookup"><span data-stu-id="cdb65-103">One source of input for a cmdlet is the command line.</span></span> <span data-ttu-id="cdb65-104">本主题介绍如何将参数添加到**get-help** cmdlet （在[创建第一个 cmdlet](./creating-a-cmdlet-without-parameters.md)中进行了介绍），以便该 cmdlet 可以基于传递到 cmdlet 的显式对象处理来自本地计算机的输入。</span><span class="sxs-lookup"><span data-stu-id="cdb65-104">This topic describes how to add a parameter to the **Get-Proc** cmdlet (which is described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process input from the local computer based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="cdb65-105">此处**所述的过程 cmdlet 根据**名称检索进程，然后在命令提示符下显示有关进程的信息。</span><span class="sxs-lookup"><span data-stu-id="cdb65-105">The **Get-Proc** cmdlet described here retrieves processes based on their names, and then displays information about the processes at a command prompt.</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="cdb65-106">定义 Cmdlet 类</span><span class="sxs-lookup"><span data-stu-id="cdb65-106">Defining the Cmdlet Class</span></span>

<span data-ttu-id="cdb65-107">Cmdlet 创建的第一步是 cmdlet 命名和实现 cmdlet .NET Framework 类的声明。</span><span class="sxs-lookup"><span data-stu-id="cdb65-107">The first step in cmdlet creation is cmdlet naming and the declaration of the .NET Framework class that implements the cmdlet.</span></span> <span data-ttu-id="cdb65-108">此 cmdlet 检索进程信息，因此此处选择的谓词名称为 "Get"。</span><span class="sxs-lookup"><span data-stu-id="cdb65-108">This cmdlet retrieves process information, so the verb name chosen here is "Get."</span></span> <span data-ttu-id="cdb65-109">（几乎任何能够检索信息的 cmdlet 都可以处理命令行输入。）有关批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 谓词名称](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="cdb65-109">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="cdb65-110">下面是用于**获取处理器**cmdlet 的类声明。</span><span class="sxs-lookup"><span data-stu-id="cdb65-110">Here's the class declaration for the **Get-Proc** cmdlet.</span></span> <span data-ttu-id="cdb65-111">[创建第一个 Cmdlet](./creating-a-cmdlet-without-parameters.md)中提供了有关此定义的详细信息。</span><span class="sxs-lookup"><span data-stu-id="cdb65-111">Details about this definition are provided in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a><span data-ttu-id="cdb65-112">声明参数</span><span class="sxs-lookup"><span data-stu-id="cdb65-112">Declaring Parameters</span></span>

<span data-ttu-id="cdb65-113">Cmdlet 参数使用户能够向 cmdlet 提供输入。</span><span class="sxs-lookup"><span data-stu-id="cdb65-113">A cmdlet parameter enables the user to provide input to the cmdlet.</span></span> <span data-ttu-id="cdb65-114">在以下示例中， **get-help**和 `Get-Member` 是流水线 cmdlet 的名称，`MemberType` 是 `Get-Member` cmdlet 的参数。</span><span class="sxs-lookup"><span data-stu-id="cdb65-114">In the following example, **Get-Proc** and `Get-Member` are the names of pipelined cmdlets, and `MemberType` is a parameter for the `Get-Member` cmdlet.</span></span> <span data-ttu-id="cdb65-115">参数的参数为 "属性"。</span><span class="sxs-lookup"><span data-stu-id="cdb65-115">The parameter has the argument "property."</span></span>

<span data-ttu-id="cdb65-116">**PS > `get-member` membertype 属性**</span><span class="sxs-lookup"><span data-stu-id="cdb65-116">**PS> get-proc ; `get-member` -membertype property**</span></span>

<span data-ttu-id="cdb65-117">若要声明 cmdlet 的参数，必须首先定义表示参数的属性。</span><span class="sxs-lookup"><span data-stu-id="cdb65-117">To declare parameters for a cmdlet, you must first define the properties that represent the parameters.</span></span> <span data-ttu-id="cdb65-118">在**get-help** cmdlet 中，仅 `Name` 参数，在此示例中，它表示要检索的 .NET Framework 进程对象的名称。</span><span class="sxs-lookup"><span data-stu-id="cdb65-118">In the **Get-Proc** cmdlet, the only parameter is `Name`, which in this case represents the name of the .NET Framework process object to retrieve.</span></span> <span data-ttu-id="cdb65-119">因此，cmdlet 类定义类型字符串的属性以接受名称数组。</span><span class="sxs-lookup"><span data-stu-id="cdb65-119">Therefore, the cmdlet class defines a property of type string to accept an array of names.</span></span>

<span data-ttu-id="cdb65-120">下面是用于**获取处理器**cmdlet 的 `Name` 参数的参数声明。</span><span class="sxs-lookup"><span data-stu-id="cdb65-120">Here's the parameter declaration for the `Name` parameter of the **Get-Proc** cmdlet.</span></span>

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

<span data-ttu-id="cdb65-121">若要通知 Windows PowerShell 运行时此属性是 `Name` 参数，请将[Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)特性添加到属性定义。</span><span class="sxs-lookup"><span data-stu-id="cdb65-121">To inform the Windows PowerShell runtime that this property is the `Name` parameter, a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute is added to the property definition.</span></span> <span data-ttu-id="cdb65-122">用于声明此属性的基本语法是 `[Parameter()]`。</span><span class="sxs-lookup"><span data-stu-id="cdb65-122">The basic syntax for declaring this attribute is `[Parameter()]`.</span></span>

> [!NOTE]
> <span data-ttu-id="cdb65-123">参数必须显式标记为公共。</span><span class="sxs-lookup"><span data-stu-id="cdb65-123">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="cdb65-124">未标记为 "公共" 的参数默认为内部参数，而不是由 Windows PowerShell 运行时找到。</span><span class="sxs-lookup"><span data-stu-id="cdb65-124">Parameters that are not marked as public default to internal and are not found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="cdb65-125">此 cmdlet 对 `Name` 参数使用字符串数组。</span><span class="sxs-lookup"><span data-stu-id="cdb65-125">This cmdlet uses an array of strings for the `Name` parameter.</span></span> <span data-ttu-id="cdb65-126">如果可能，cmdlet 还应将参数定义为数组，因为这允许 cmdlet 接受多个项。</span><span class="sxs-lookup"><span data-stu-id="cdb65-126">If possible, your cmdlet should also define a parameter as an array, because this allows the cmdlet to accept more than one item.</span></span>

#### <a name="things-to-remember-about-parameter-definitions"></a><span data-ttu-id="cdb65-127">有关参数定义的注意事项</span><span class="sxs-lookup"><span data-stu-id="cdb65-127">Things to Remember About Parameter Definitions</span></span>

- <span data-ttu-id="cdb65-128">应尽可能多地重复使用预定义的 Windows PowerShell 参数名称和数据类型，确保 cmdlet 与 Windows PowerShell cmdlet 兼容。</span><span class="sxs-lookup"><span data-stu-id="cdb65-128">Predefined Windows PowerShell parameter names and data types should be reused as much as possible to ensure that your cmdlet is compatible with Windows PowerShell cmdlets.</span></span> <span data-ttu-id="cdb65-129">例如，如果所有 cmdlet 都使用预定义的 `Id` 参数名称来标识资源，则无论使用哪种 cmdlet，用户都可以轻松地了解参数的含义。</span><span class="sxs-lookup"><span data-stu-id="cdb65-129">For example, if all cmdlets use the predefined `Id` parameter name to identify a resource, user will easily understand the meaning of the parameter, regardless of what cmdlet they are using.</span></span> <span data-ttu-id="cdb65-130">基本上，参数名称与公共语言运行时（CLR）中用于变量名称的规则遵循相同的规则。</span><span class="sxs-lookup"><span data-stu-id="cdb65-130">Basically, parameter names follow the same rules as those used for variable names in the common language runtime (CLR).</span></span> <span data-ttu-id="cdb65-131">有关参数命名的详细信息，请参阅[Cmdlet 参数名称](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb)。</span><span class="sxs-lookup"><span data-stu-id="cdb65-131">For more information about parameter naming, see [Cmdlet Parameter Names](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span></span>

- <span data-ttu-id="cdb65-132">Windows PowerShell 保留了几个参数名称，以便提供一致的用户体验。</span><span class="sxs-lookup"><span data-stu-id="cdb65-132">Windows PowerShell reserves a few parameter names to provide a consistent user experience.</span></span> <span data-ttu-id="cdb65-133">不要使用以下参数名称： `WhatIf`、`Confirm`、`Verbose`、`Debug`、`Warn`、`ErrorAction`、`ErrorVariable`、`OutVariable` 和 `OutBuffer`。</span><span class="sxs-lookup"><span data-stu-id="cdb65-133">Do not use these parameter names: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, and `OutBuffer`.</span></span> <span data-ttu-id="cdb65-134">此外，还保留了这些参数名称的以下别名： `vb`、`db`、`ea`、`ev`、`ov` 和 `ob`。</span><span class="sxs-lookup"><span data-stu-id="cdb65-134">Additionally, the following aliases for these parameter names are reserved: `vb`, `db`, `ea`, `ev`, `ov`, and `ob`.</span></span>

- <span data-ttu-id="cdb65-135">`Name` 是一个简单的通用参数名称，建议在 cmdlet 中使用。</span><span class="sxs-lookup"><span data-stu-id="cdb65-135">`Name` is a simple and common parameter name, recommended for use in your cmdlets.</span></span> <span data-ttu-id="cdb65-136">最好选择与特定 cmdlet 唯一的复杂名称类似的参数名称，并且很难记住。</span><span class="sxs-lookup"><span data-stu-id="cdb65-136">It is better to choose a parameter name like this than a complex name that is unique to a specific cmdlet and hard to remember.</span></span>

- <span data-ttu-id="cdb65-137">默认情况下，参数在 Windows PowerShell 中不区分大小写，但在默认情况下，shell 保留大小写。</span><span class="sxs-lookup"><span data-stu-id="cdb65-137">Parameters are case-insensitive in Windows PowerShell, although by default the shell preserves case.</span></span> <span data-ttu-id="cdb65-138">参数的区分大小写取决于 cmdlet 的操作。</span><span class="sxs-lookup"><span data-stu-id="cdb65-138">Case-sensitivity of the arguments depends on the operation of the cmdlet.</span></span> <span data-ttu-id="cdb65-139">参数会传递到命令行中指定的参数。</span><span class="sxs-lookup"><span data-stu-id="cdb65-139">Arguments are passed to a parameter as specified at the command line.</span></span>

- <span data-ttu-id="cdb65-140">有关其他参数声明的示例，请参阅[Cmdlet 参数](./cmdlet-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="cdb65-140">For examples of other parameter declarations, see [Cmdlet Parameters](./cmdlet-parameters.md).</span></span>

## <a name="declaring-parameters-as-positional-or-named"></a><span data-ttu-id="cdb65-141">将参数声明为位置或命名</span><span class="sxs-lookup"><span data-stu-id="cdb65-141">Declaring Parameters as Positional or Named</span></span>

<span data-ttu-id="cdb65-142">Cmdlet 必须将每个参数都设置为位置或命名参数。</span><span class="sxs-lookup"><span data-stu-id="cdb65-142">A cmdlet must set each parameter as either a positional or named parameter.</span></span> <span data-ttu-id="cdb65-143">这两种参数都接受单个参数、用逗号分隔的多个参数以及布尔值设置。</span><span class="sxs-lookup"><span data-stu-id="cdb65-143">Both kinds of parameters accept single arguments, multiple arguments separated by commas, and Boolean settings.</span></span> <span data-ttu-id="cdb65-144">布尔参数（也称为*开关*）仅处理布尔值设置。</span><span class="sxs-lookup"><span data-stu-id="cdb65-144">A Boolean parameter, also called a *switch*, handles only Boolean settings.</span></span> <span data-ttu-id="cdb65-145">开关用于确定参数的状态。</span><span class="sxs-lookup"><span data-stu-id="cdb65-145">The switch is used to determine the presence of the parameter.</span></span> <span data-ttu-id="cdb65-146">建议的默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="cdb65-146">The recommended default is `false`.</span></span>

<span data-ttu-id="cdb65-147">示例**获取处理器**cmdlet 将 `Name` 参数定义为位置为0的位置参数。</span><span class="sxs-lookup"><span data-stu-id="cdb65-147">The sample **Get-Proc** cmdlet defines the `Name` parameter as a positional parameter with position 0.</span></span> <span data-ttu-id="cdb65-148">这意味着，用户在命令行中输入的第一个参数会自动插入此参数。</span><span class="sxs-lookup"><span data-stu-id="cdb65-148">This means that the first argument the user enters on the command line is automatically inserted for this parameter.</span></span> <span data-ttu-id="cdb65-149">如果要定义命名参数（用户必须从命令行指定参数名称），请将 `Position` 关键字保留在属性声明之外。</span><span class="sxs-lookup"><span data-stu-id="cdb65-149">If you want to define a named parameter, for which the user must specify the parameter name from the command line, leave the `Position` keyword out of the attribute declaration.</span></span>

> [!NOTE]
> <span data-ttu-id="cdb65-150">除非参数必须命名，否则建议您将最常用的参数设置为 "位置"，以使用户不必键入参数名称。</span><span class="sxs-lookup"><span data-stu-id="cdb65-150">Unless parameters must be named, we recommend that you make the most-used parameters positional so that users will not have to type the parameter name.</span></span>

## <a name="declaring-parameters-as-mandatory-or-optional"></a><span data-ttu-id="cdb65-151">将参数声明为必需或可选</span><span class="sxs-lookup"><span data-stu-id="cdb65-151">Declaring Parameters as Mandatory or Optional</span></span>

<span data-ttu-id="cdb65-152">Cmdlet 必须将每个参数都设置为可选参数或强制参数。</span><span class="sxs-lookup"><span data-stu-id="cdb65-152">A cmdlet must set each parameter as either an optional or a mandatory parameter.</span></span> <span data-ttu-id="cdb65-153">在**示例中**，将 `Name` 参数定义为可选，因为未在属性声明中设置 `Mandatory` 关键字。</span><span class="sxs-lookup"><span data-stu-id="cdb65-153">In the sample **Get-Proc** cmdlet, the `Name` parameter is defined as optional because the `Mandatory` keyword is not set in the attribute declaration.</span></span>

## <a name="supporting-parameter-validation"></a><span data-ttu-id="cdb65-154">支持参数验证</span><span class="sxs-lookup"><span data-stu-id="cdb65-154">Supporting Parameter Validation</span></span>

<span data-ttu-id="cdb65-155">示例 **Get-Proc** cmdlet 向 `Name` 参数添加一个输入验证特性 [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute)，以便验证输入既不是 `null` 也不是空的。</span><span class="sxs-lookup"><span data-stu-id="cdb65-155">The sample **Get-Proc** cmdlet adds an input validation attribute, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), to the `Name` parameter to enable validation that the input is neither `null` nor empty.</span></span> <span data-ttu-id="cdb65-156">此属性是 Windows PowerShell 提供的多个验证属性之一。</span><span class="sxs-lookup"><span data-stu-id="cdb65-156">This attribute is one of several validation attributes provided by Windows PowerShell.</span></span> <span data-ttu-id="cdb65-157">有关其他验证属性的示例，请参阅[验证参数输入](./validating-parameter-input.md)。</span><span class="sxs-lookup"><span data-stu-id="cdb65-157">For examples of other validation attributes, see [Validating Parameter Input](./validating-parameter-input.md).</span></span>

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="cdb65-158">重写输入处理方法</span><span class="sxs-lookup"><span data-stu-id="cdb65-158">Overriding an Input Processing Method</span></span>

<span data-ttu-id="cdb65-159">如果 cmdlet 要处理命令行输入，则必须重写相应的输入处理方法。</span><span class="sxs-lookup"><span data-stu-id="cdb65-159">If your cmdlet is to handle command-line input, it must override the appropriate input processing methods.</span></span> <span data-ttu-id="cdb65-160">基本输入处理方法在[创建第一个 Cmdlet](./creating-a-cmdlet-without-parameters.md)时引入。</span><span class="sxs-lookup"><span data-stu-id="cdb65-160">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="cdb65-161">**Get-Proc** cmdlet 将重写 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 方法，以处理用户或脚本提供的 `Name` 参数输入的参数。</span><span class="sxs-lookup"><span data-stu-id="cdb65-161">The **Get-Proc** cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="cdb65-162">此方法获取每个请求的进程名称的进程，如果未提供任何名称，则获取所有进程的进程。</span><span class="sxs-lookup"><span data-stu-id="cdb65-162">This method gets the processes for each requested process name, or all for processes if no name is provided.</span></span> <span data-ttu-id="cdb65-163">请注意，在[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)中，对[WriteObject% 28system.object% 2csystem.string% %29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)的调用是用于将输出对象发送到该对象的输出机制。条.</span><span class="sxs-lookup"><span data-stu-id="cdb65-163">Notice that in [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="cdb65-164">此调用 `enumerateCollection` 的第二个参数设置为 `true`，以通知 Windows PowerShell 运行时枚举进程对象的输出数组，并一次将一个进程写入命令行。</span><span class="sxs-lookup"><span data-stu-id="cdb65-164">The second parameter of this call, `enumerateCollection`, is set to `true` to inform the Windows PowerShell runtime to enumerate the output array of process objects and write one process at a time to the command line.</span></span>

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

## <a name="code-sample"></a><span data-ttu-id="cdb65-165">代码示例</span><span class="sxs-lookup"><span data-stu-id="cdb65-165">Code Sample</span></span>

<span data-ttu-id="cdb65-166">有关完整C#的示例代码，请参阅[GetProcessSample02 示例](./getprocesssample02-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="cdb65-166">For the complete C# sample code, see [GetProcessSample02 Sample](./getprocesssample02-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="cdb65-167">定义对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="cdb65-167">Defining Object Types and Formatting</span></span>

<span data-ttu-id="cdb65-168">Windows PowerShell 通过使用 .NET Framework 对象在 cmdlet 之间传递信息。</span><span class="sxs-lookup"><span data-stu-id="cdb65-168">Windows PowerShell passes information between cmdlets by using .NET Framework objects.</span></span> <span data-ttu-id="cdb65-169">因此，cmdlet 可能需要定义自己的类型，或者 cmdlet 可能需要扩展另一个 cmdlet 提供的现有类型。</span><span class="sxs-lookup"><span data-stu-id="cdb65-169">Consequently, a cmdlet might need to define its own type, or a cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="cdb65-170">有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。</span><span class="sxs-lookup"><span data-stu-id="cdb65-170">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="cdb65-171">构建 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="cdb65-171">Building the Cmdlet</span></span>

<span data-ttu-id="cdb65-172">实现 cmdlet 后，必须使用 Windows PowerShell 管理单元将其注册到 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="cdb65-172">After you implement a cmdlet, you must register it with Windows PowerShell by using a Windows PowerShell snap-in.</span></span> <span data-ttu-id="cdb65-173">有关注册 cmdlet 的详细信息，请参阅[如何注册 cmdlet、提供程序和主机应用程序](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="cdb65-173">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="cdb65-174">测试 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="cdb65-174">Testing the Cmdlet</span></span>

<span data-ttu-id="cdb65-175">向 Windows PowerShell 注册 cmdlet 后，可以通过在命令行上运行 cmdlet 来对其进行测试。</span><span class="sxs-lookup"><span data-stu-id="cdb65-175">When your cmdlet is registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="cdb65-176">可以通过两种方法来测试示例 cmdlet 的代码。</span><span class="sxs-lookup"><span data-stu-id="cdb65-176">Here are two ways to test the code for the sample cmdlet.</span></span> <span data-ttu-id="cdb65-177">有关从命令行使用 cmdlet 的详细信息，请参阅[使用 Windows PowerShell 入门](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="cdb65-177">For more information about using cmdlets from the command line, see [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="cdb65-178">在 Windows PowerShell 提示符下，使用以下命令列出名为 "IEXPLORE" 的 Internet Explorer 进程。</span><span class="sxs-lookup"><span data-stu-id="cdb65-178">At the Windows PowerShell prompt, use the following command to list the Internet Explorer process, which is named "IEXPLORE."</span></span>

    ```powershell
    PS> get-proc -name iexplore
    ```

<span data-ttu-id="cdb65-179">此时将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="cdb65-179">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- <span data-ttu-id="cdb65-180">若要列出名为 "IEXPLORE"、"OUTLOOK" 和 "NOTEPAD" 的 Internet Explorer、Outlook 和记事本进程，请使用以下命令。</span><span class="sxs-lookup"><span data-stu-id="cdb65-180">To list the Internet Explorer, Outlook, and Notepad processes named "IEXPLORE," "OUTLOOK," and "NOTEPAD," use the following command.</span></span> <span data-ttu-id="cdb65-181">如果有多个进程，则显示所有进程。</span><span class="sxs-lookup"><span data-stu-id="cdb65-181">If there are multiple processes, all of them are displayed.</span></span>

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

<span data-ttu-id="cdb65-182">此时将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="cdb65-182">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a><span data-ttu-id="cdb65-183">请参阅</span><span class="sxs-lookup"><span data-stu-id="cdb65-183">See Also</span></span>

[<span data-ttu-id="cdb65-184">添加处理管道输入的参数</span><span class="sxs-lookup"><span data-stu-id="cdb65-184">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="cdb65-185">创建第一个 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="cdb65-185">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="cdb65-186">扩展对象类型和格式</span><span class="sxs-lookup"><span data-stu-id="cdb65-186">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="cdb65-187">如何注册 Cmdlet、提供程序和主机应用程序</span><span class="sxs-lookup"><span data-stu-id="cdb65-187">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="cdb65-188">Windows PowerShell 参考</span><span class="sxs-lookup"><span data-stu-id="cdb65-188">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="cdb65-189">Cmdlet 示例</span><span class="sxs-lookup"><span data-stu-id="cdb65-189">Cmdlet Samples</span></span>](./cmdlet-samples.md)
