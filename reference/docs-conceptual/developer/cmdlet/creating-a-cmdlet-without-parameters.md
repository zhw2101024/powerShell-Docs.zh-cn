---
title: 创建不带参数的 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmers Guide], creating
- cmdlets [PowerShell Programmers Guide], basic cmdlet
ms.assetid: 54236ef3-82db-45f8-9114-1ecb7ff65d3e
caps.latest.revision: 8
ms.openlocfilehash: 2685215f41c96955fc662d5eee27fc0e7a31da83
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369856"
---
# <a name="creating-a-cmdlet-without-parameters"></a><span data-ttu-id="370de-102">创建不具有参数的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="370de-102">Creating a Cmdlet without Parameters</span></span>

<span data-ttu-id="370de-103">本部分介绍如何创建一个 cmdlet，用于在不使用参数的情况下从本地计算机检索信息，然后将该信息写入管道。</span><span class="sxs-lookup"><span data-stu-id="370de-103">This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span> <span data-ttu-id="370de-104">此处所述的 cmdlet 是一个用于检索有关本地计算机的进程的信息，然后在命令行中显示该信息的 Get Proc cmdlet。</span><span class="sxs-lookup"><span data-stu-id="370de-104">The cmdlet described here is a Get-Proc cmdlet that retrieves information about the processes of the local computer, and then displays that information at the command line.</span></span>

> [!NOTE]
> <span data-ttu-id="370de-105">请注意，在编写 cmdlet 时，Windows PowerShell®引用程序集会下载到磁盘上（默认情况下，C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0）。</span><span class="sxs-lookup"><span data-stu-id="370de-105">Be aware that when writing cmdlets, the Windows PowerShell® reference assemblies are downloaded onto disk (by default at C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).</span></span> <span data-ttu-id="370de-106">它们未安装在全局程序集缓存（GAC）中。</span><span class="sxs-lookup"><span data-stu-id="370de-106">They are not installed in the Global Assembly Cache (GAC).</span></span>

## <a name="naming-the-cmdlet"></a><span data-ttu-id="370de-107">命名 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="370de-107">Naming the Cmdlet</span></span>

<span data-ttu-id="370de-108">Cmdlet 名称由指示 cmdlet 所采用的操作的谓词和指示该 cmdlet 操作的项的名词组成。</span><span class="sxs-lookup"><span data-stu-id="370de-108">A cmdlet name consists of a verb that indicates the action the cmdlet takes and a noun that indicates the items that the cmdlet acts upon.</span></span> <span data-ttu-id="370de-109">由于此示例处理程序 cmdlet 可检索进程对象，因此它使用由[Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon)枚举定义的谓词 "Get"，并使用名词 "Proc" 指示该 cmdlet 处理进程项。</span><span class="sxs-lookup"><span data-stu-id="370de-109">Because this sample Get-Proc cmdlet retrieves process objects, it uses the verb "Get", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeration, and the noun "Proc" to indicate that the cmdlet works on process items.</span></span>

<span data-ttu-id="370de-110">命名 cmdlet 时，请不要使用以下任何字符： #、（） {} [] &-/\ $;： "" < > &#124; ？</span><span class="sxs-lookup"><span data-stu-id="370de-110">When naming cmdlets, do not use any of the following characters: # , () {} [] & - /\ $ ; : " '<> &#124; ?</span></span> <span data-ttu-id="370de-111">@ \` .</span><span class="sxs-lookup"><span data-stu-id="370de-111">@ \` .</span></span>

### <a name="choosing-a-noun"></a><span data-ttu-id="370de-112">选择名词</span><span class="sxs-lookup"><span data-stu-id="370de-112">Choosing a Noun</span></span>

<span data-ttu-id="370de-113">应选择特定的名词。</span><span class="sxs-lookup"><span data-stu-id="370de-113">You should choose a noun that is specific.</span></span> <span data-ttu-id="370de-114">最好使用带有缩写形式的产品名称的单数名词。</span><span class="sxs-lookup"><span data-stu-id="370de-114">It is best to use a singular noun prefixed with a shortened version of the product name.</span></span> <span data-ttu-id="370de-115">此类型的示例 cmdlet 名称为 "`Get-SQLServer`"。</span><span class="sxs-lookup"><span data-stu-id="370de-115">An example cmdlet name of this type is "`Get-SQLServer`".</span></span>

### <a name="choosing-a-verb"></a><span data-ttu-id="370de-116">选择谓词</span><span class="sxs-lookup"><span data-stu-id="370de-116">Choosing a Verb</span></span>

<span data-ttu-id="370de-117">应使用已批准的 cmdlet 动词名称集中的动词。</span><span class="sxs-lookup"><span data-stu-id="370de-117">You should use a verb from the set of approved cmdlet verb names.</span></span> <span data-ttu-id="370de-118">有关批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 谓词名称](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="370de-118">For more information about the approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="370de-119">定义 Cmdlet 类</span><span class="sxs-lookup"><span data-stu-id="370de-119">Defining the Cmdlet Class</span></span>

<span data-ttu-id="370de-120">选择了 cmdlet 名称后，定义一个 .NET 类来实现该 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="370de-120">Once you have chosen a cmdlet name, define a .NET class to implement the cmdlet.</span></span> <span data-ttu-id="370de-121">下面是此示例的 Get Proc cmdlet 的类定义：</span><span class="sxs-lookup"><span data-stu-id="370de-121">Here is the class definition for this sample Get-Proc cmdlet:</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

<span data-ttu-id="370de-122">请注意，在类定义之前， [CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)属性（带有语法 `[Cmdlet(verb, noun, ...)]`）用于将此类标识为 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="370de-122">Notice that previous to the class definition, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute, with the syntax `[Cmdlet(verb, noun, ...)]`, is used to identify this class as a cmdlet.</span></span> <span data-ttu-id="370de-123">这是所有 cmdlet 的唯一必需的属性，它允许 Windows PowerShell 运行时正确调用它们。</span><span class="sxs-lookup"><span data-stu-id="370de-123">This is the only required attribute for all cmdlets, and it allows the Windows PowerShell runtime to call them correctly.</span></span> <span data-ttu-id="370de-124">如有必要，可以设置属性关键字以进一步声明该类。</span><span class="sxs-lookup"><span data-stu-id="370de-124">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="370de-125">请注意，我们的示例 GetProcCommand 类的属性声明仅声明了 Get-help cmdlet 的名词和动词名称。</span><span class="sxs-lookup"><span data-stu-id="370de-125">Be aware that the attribute declaration for our sample GetProcCommand class declares only the noun and verb names for the Get-Proc cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="370de-126">对于所有 Windows PowerShell 特性类，可以设置的关键字与特性类的属性相对应。</span><span class="sxs-lookup"><span data-stu-id="370de-126">For all Windows PowerShell attribute classes, the keywords that you can set correspond to properties of the attribute class.</span></span>

<span data-ttu-id="370de-127">命名 cmdlet 的类时，最好在类名称中反映 cmdlet 名称。</span><span class="sxs-lookup"><span data-stu-id="370de-127">When naming the class of the cmdlet, it is a good practice to reflect the cmdlet name in the class name.</span></span> <span data-ttu-id="370de-128">为此，请使用格式 "VerbNounCommand"，并将 "Verb" 和 "名词" 替换为 cmdlet 名称中使用的动词和名词。</span><span class="sxs-lookup"><span data-stu-id="370de-128">To do this, use the form "VerbNounCommand" and replace "Verb" and "Noun" with the verb and noun used in the cmdlet name.</span></span> <span data-ttu-id="370de-129">如前一类定义中所示，示例获取处理器 cmdlet 定义了一个名为[GetProcCommand 的类](/dotnet/api/System.Management.Automation.Cmdlet)，该类派生自一个</span><span class="sxs-lookup"><span data-stu-id="370de-129">As is shown in the previous class definition, the sample Get-Proc cmdlet defines a class called GetProcCommand, which derives from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="370de-130">如果要定义直接访问 Windows PowerShell 运行时的 cmdlet，你的 .NET 类应派生自[PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)基类。</span><span class="sxs-lookup"><span data-stu-id="370de-130">If you want to define a cmdlet that accesses the Windows PowerShell runtime directly, your .NET class should derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span> <span data-ttu-id="370de-131">有关此类的详细信息，请参阅[创建定义参数集的 Cmdlet](./adding-parameter-sets-to-a-cmdlet.md)。</span><span class="sxs-lookup"><span data-stu-id="370de-131">For more information about this class, see [Creating a Cmdlet that Defines Parameter Sets](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

> [!NOTE]
> <span data-ttu-id="370de-132">Cmdlet 的类必须显式标记为公共。</span><span class="sxs-lookup"><span data-stu-id="370de-132">The class for a cmdlet must be explicitly marked as public.</span></span> <span data-ttu-id="370de-133">未标记为 "公共" 的类将默认为内部类，且不会由 Windows PowerShell 运行时找到。</span><span class="sxs-lookup"><span data-stu-id="370de-133">Classes that are not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="370de-134">Windows PowerShell 使用其 cmdlet 类[的 "the](/dotnet/api/Microsoft.PowerShell.Commands) " 命名空间。</span><span class="sxs-lookup"><span data-stu-id="370de-134">Windows PowerShell uses the [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namespace for its cmdlet classes.</span></span> <span data-ttu-id="370de-135">建议将 cmdlet 类放在 API 命名空间的命令命名空间中，例如，xxx。</span><span class="sxs-lookup"><span data-stu-id="370de-135">It is recommended to place your cmdlet classes in a Commands namespace of your API namespace, for example, xxx.PS.Commands.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="370de-136">重写输入处理方法</span><span class="sxs-lookup"><span data-stu-id="370de-136">Overriding an Input Processing Method</span></span>

<span data-ttu-id="370de-137">[System.web](/dotnet/api/System.Management.Automation.Cmdlet)类提供三个主要的输入处理方法，其中至少有一个 Cmdlet 必须重写。</span><span class="sxs-lookup"><span data-stu-id="370de-137">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides three main input processing methods, at least one of which your cmdlet must override.</span></span> <span data-ttu-id="370de-138">有关 Windows PowerShell 如何处理记录的详细信息，请参阅[Windows powershell 的工作](/previous-versions//ms714658(v=vs.85))原理。</span><span class="sxs-lookup"><span data-stu-id="370de-138">For more information about how Windows PowerShell processes records, see [How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85)).</span></span>

<span data-ttu-id="370de-139">对于所有类型的输入，Windows PowerShell 运行时都会调用[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)来启用处理。</span><span class="sxs-lookup"><span data-stu-id="370de-139">For all types of input, the Windows PowerShell runtime calls [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) to enable processing.</span></span> <span data-ttu-id="370de-140">如果 cmdlet 必须执行一些预处理或设置，则可以通过重写此方法来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="370de-140">If your cmdlet must perform some preprocessing or setup, it can do this by overriding this method.</span></span>

> [!NOTE]
> <span data-ttu-id="370de-141">Windows PowerShell 使用术语 "记录" 来描述在调用 cmdlet 时提供的参数值集。</span><span class="sxs-lookup"><span data-stu-id="370de-141">Windows PowerShell uses the term "record" to describe the set of parameter values supplied when a cmdlet is called.</span></span>

<span data-ttu-id="370de-142">如果你的 cmdlet 接受管道输入，则它必须重写[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，还可以重[写方法（可选）。](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)</span><span class="sxs-lookup"><span data-stu-id="370de-142">If your cmdlet accepts pipeline input, it must override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, and optionally the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="370de-143">例如，如果 cmdlet 收集所有使用 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 的输入，则它可能会重写这两种方法，然后一次对输入（而不是一个元素）进行操作，因为 `Sort-Object` cmdlet 执行。</span><span class="sxs-lookup"><span data-stu-id="370de-143">For example, a cmdlet might override both methods if it gathers all input using [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) and then operates on the input as a whole rather than one element at a time, as the `Sort-Object` cmdlet does.</span></span>

<span data-ttu-id="370de-144">如果 cmdlet 不接受管道输入，则它应重写[system.web](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。</span><span class="sxs-lookup"><span data-stu-id="370de-144">If your cmdlet does not take pipeline input, it should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="370de-145">请注意，当 cmdlet 无法一次对一个元素进行操作时，此方法经常用于替代[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) ，这与排序 Cmdlet 的情况相同。</span><span class="sxs-lookup"><span data-stu-id="370de-145">Be aware that this method is frequently used in place of [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) when the cmdlet cannot operate on one element at a time, as is the case for a sorting cmdlet.</span></span>

<span data-ttu-id="370de-146">由于此示例中的ProcessRecord cmdlet 必须接收管道输入，因此它将重写 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 方法，并使用默认的[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 和 [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 实现方法。</span><span class="sxs-lookup"><span data-stu-id="370de-146">Because this sample Get-Proc cmdlet must receive pipeline input, it overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method and uses the default implementations for [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) and [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span></span> <span data-ttu-id="370de-147">[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)重写将检索进程，并使用[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法将这些进程写入命令行的命令行中。</span><span class="sxs-lookup"><span data-stu-id="370de-147">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override retrieves processes and writes them to the command line using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Get the current processes
  Process[] processes = Process.GetProcesses();

  // Write the processes to the pipeline making them available
  // to the next cmdlet. The second parameter of this call tells
  // PowerShell to enumerate the array, and send one process at a
  // time to the pipeline.
  WriteObject(processes, true);
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ Get the current processes.
    Dim processes As Process()
    processes = Process.GetProcesses()

    '/ Write the processes to the pipeline making them available
    '/ to the next cmdlet. The second parameter of this call tells
    '/ PowerShell to enumerate the array, and send one process at a
    '/ time to the pipeline.
    WriteObject(processes, True)

End Sub 'ProcessRecord
```

#### <a name="things-to-remember-about-input-processing"></a><span data-ttu-id="370de-148">有关输入处理的注意事项</span><span class="sxs-lookup"><span data-stu-id="370de-148">Things to Remember About Input Processing</span></span>

- <span data-ttu-id="370de-149">输入的默认源是用户在命令行上提供的显式对象（例如，字符串）。</span><span class="sxs-lookup"><span data-stu-id="370de-149">The default source for input is an explicit object (for example, a string) provided by the user on the command line.</span></span> <span data-ttu-id="370de-150">有关详细信息，请参阅[创建 Cmdlet 来处理命令行输入](./adding-parameters-that-process-command-line-input.md)。</span><span class="sxs-lookup"><span data-stu-id="370de-150">For more information, see [Creating a Cmdlet to Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

- <span data-ttu-id="370de-151">输入处理方法还可以从管道上的上游 cmdlet 的输出对象接收输入。</span><span class="sxs-lookup"><span data-stu-id="370de-151">An input processing method can also receive input from the output object of an upstream cmdlet on the pipeline.</span></span> <span data-ttu-id="370de-152">有关详细信息，请参阅[创建用于处理管道输入的 Cmdlet](./adding-parameters-that-process-pipeline-input.md)。</span><span class="sxs-lookup"><span data-stu-id="370de-152">For more information, see [Creating a Cmdlet to Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="370de-153">请注意，cmdlet 可以从命令行和管道源的组合接收输入。</span><span class="sxs-lookup"><span data-stu-id="370de-153">Be aware that your cmdlet can receive input from a combination of command-line and pipeline sources.</span></span>

- <span data-ttu-id="370de-154">下游 cmdlet 可能不会长时间返回，或者根本不会返回。</span><span class="sxs-lookup"><span data-stu-id="370de-154">The downstream cmdlet might not return for a long time, or not at all.</span></span> <span data-ttu-id="370de-155">出于此原因，在调用[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)期间，cmdlet 中的输入处理方法不应持有锁，尤其是范围超出 cmdlet 实例的锁。</span><span class="sxs-lookup"><span data-stu-id="370de-155">For that reason, the input processing method in your cmdlet should not hold locks during calls to [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especially locks for which the scope extends beyond the cmdlet instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="370de-156">Cmdlet 不应调用 system.exception [\*](/dotnet/api/System.Console.WriteLine)或其等效的。</span><span class="sxs-lookup"><span data-stu-id="370de-156">Cmdlets should never call [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) or its equivalent.</span></span>

- <span data-ttu-id="370de-157">Cmdlet 在处理完成后，可能会有要清理的对象变量（例如，如果它打开[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法中的文件句柄，并使句柄处于打开状态以供使用[。ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)）（）。</span><span class="sxs-lookup"><span data-stu-id="370de-157">Your cmdlet might have object variables to clean up when it is finished processing (for example, if it opens a file handle in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span></span> <span data-ttu-id="370de-158">请记住，Windows PowerShell 运行时并不总是调用应执行对象清理的[system.web](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法，这一点很重要。</span><span class="sxs-lookup"><span data-stu-id="370de-158">It is important to remember that the Windows PowerShell runtime does not always call the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, which should perform object cleanup.</span></span>

<span data-ttu-id="370de-159">例如，如果 cmdlet 在中间取消或在 cmdlet 的任何部分中出现终止错误，则可能不会调用[system.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 。</span><span class="sxs-lookup"><span data-stu-id="370de-159">For example, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) might not be called if the cmdlet is canceled midway or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="370de-160">因此，需要对象清理的 cmdlet 应该实现完整的 [System.IDisposable](/dotnet/api/System.IDisposable) 模式（包括终结器），以便运行时可以调用 [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 和 [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) 处理结束时 IDisposable \*。</span><span class="sxs-lookup"><span data-stu-id="370de-160">Therefore, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including the finalizer, so that the runtime can call both [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) at the end of processing.</span></span>

## <a name="code-sample"></a><span data-ttu-id="370de-161">代码示例</span><span class="sxs-lookup"><span data-stu-id="370de-161">Code Sample</span></span>

<span data-ttu-id="370de-162">有关完整C#的示例代码，请参阅[GetProcessSample01 示例](./getprocesssample01-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="370de-162">For the complete C# sample code, see [GetProcessSample01 Sample](./getprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="370de-163">定义对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="370de-163">Defining Object Types and Formatting</span></span>

<span data-ttu-id="370de-164">Windows PowerShell 使用 .NET 对象在 cmdlet 之间传递信息。</span><span class="sxs-lookup"><span data-stu-id="370de-164">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="370de-165">因此，cmdlet 可能需要定义自己的类型，或者该 cmdlet 可能需要扩展另一个 cmdlet 提供的现有类型。</span><span class="sxs-lookup"><span data-stu-id="370de-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="370de-166">有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式](/previous-versions//ms714665(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="370de-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="370de-167">构建 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="370de-167">Building the Cmdlet</span></span>

<span data-ttu-id="370de-168">实现 cmdlet 后，必须通过 Windows PowerShell 管理单元将其注册到 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="370de-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="370de-169">有关注册 cmdlet 的详细信息，请参阅[如何注册 cmdlet、提供程序和主机应用程序](/previous-versions//ms714644(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="370de-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="370de-170">测试 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="370de-170">Testing the Cmdlet</span></span>

<span data-ttu-id="370de-171">向 Windows PowerShell 注册 cmdlet 后，可以通过在命令行上运行 cmdlet 来对其进行测试。</span><span class="sxs-lookup"><span data-stu-id="370de-171">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="370de-172">示例处理器 cmdlet 的代码很小，但它仍使用 Windows PowerShell 运行时和现有的 .NET 对象，这足以使其变得非常有用。</span><span class="sxs-lookup"><span data-stu-id="370de-172">The code for our sample Get-Proc cmdlet is small, but it still uses the Windows PowerShell runtime and an existing .NET object, which is enough to make it useful.</span></span> <span data-ttu-id="370de-173">让我们对它进行测试，以便更好地了解该过程的功能，以及如何使用其输出。</span><span class="sxs-lookup"><span data-stu-id="370de-173">Let's test it to better understand what Get-Proc can do and how its output can be used.</span></span> <span data-ttu-id="370de-174">有关从命令行使用 cmdlet 的详细信息，请参阅[使用 Windows PowerShell 的入门](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="370de-174">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

1. <span data-ttu-id="370de-175">启动 Windows PowerShell，并获取正在计算机上运行的当前进程。</span><span class="sxs-lookup"><span data-stu-id="370de-175">Start Windows PowerShell, and get the current processes running on the computer.</span></span>

    ```powershell
    get-proc
    ```

    <span data-ttu-id="370de-176">此时将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="370de-176">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. <span data-ttu-id="370de-177">将一个变量分配给 cmdlet 结果，以便更轻松地执行操作。</span><span class="sxs-lookup"><span data-stu-id="370de-177">Assign a variable to the cmdlet results for easier manipulation.</span></span>

    ```powershell
    $p=get-proc
    ```

3. <span data-ttu-id="370de-178">获取进程数。</span><span class="sxs-lookup"><span data-stu-id="370de-178">Get the number of processes.</span></span>

    ```powershell
    $p.length
    ```

    <span data-ttu-id="370de-179">此时将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="370de-179">The following output appears.</span></span>

    ```output
    63
    ```

4. <span data-ttu-id="370de-180">检索特定进程。</span><span class="sxs-lookup"><span data-stu-id="370de-180">Retrieve a specific process.</span></span>

    ```powershell
    $p[6]
    ```

    <span data-ttu-id="370de-181">此时将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="370de-181">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. <span data-ttu-id="370de-182">获取此过程的开始时间。</span><span class="sxs-lookup"><span data-stu-id="370de-182">Get the start time of this process.</span></span>

    ```powershell
    $p[6].starttime
    ```

    <span data-ttu-id="370de-183">此时将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="370de-183">The following output appears.</span></span>

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. <span data-ttu-id="370de-184">获取句柄计数大于500的进程，并对结果进行排序。</span><span class="sxs-lookup"><span data-stu-id="370de-184">Get the processes for which the handle count is greater than 500, and sort the result.</span></span>

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    <span data-ttu-id="370de-185">此时将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="370de-185">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. <span data-ttu-id="370de-186">使用 `Get-Member` cmdlet 列出可用于每个进程的属性。</span><span class="sxs-lookup"><span data-stu-id="370de-186">Use the `Get-Member` cmdlet to list the properties available for each process.</span></span>

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    <span data-ttu-id="370de-187">此时将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="370de-187">The following output appears.</span></span>

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a><span data-ttu-id="370de-188">另请参阅</span><span class="sxs-lookup"><span data-stu-id="370de-188">See Also</span></span>

[<span data-ttu-id="370de-189">创建 Cmdlet 来处理命令行输入</span><span class="sxs-lookup"><span data-stu-id="370de-189">Creating a Cmdlet to Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="370de-190">创建用于处理管道输入的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="370de-190">Creating a Cmdlet to Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="370de-191">如何创建 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="370de-191">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="370de-192">[扩展对象类型和格式](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="370de-192">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="370de-193">[Windows PowerShell 的工作原理](/previous-versions//ms714658(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="370de-193">[How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85))</span></span>

<span data-ttu-id="370de-194">[如何注册 Cmdlet、提供程序和主机应用程序](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="370de-194">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="370de-195">Windows PowerShell 参考</span><span class="sxs-lookup"><span data-stu-id="370de-195">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="370de-196">Cmdlet 示例</span><span class="sxs-lookup"><span data-stu-id="370de-196">Cmdlet Samples</span></span>](./cmdlet-samples.md)