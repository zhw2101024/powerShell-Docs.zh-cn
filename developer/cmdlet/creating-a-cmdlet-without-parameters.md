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
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733972"
---
# <a name="creating-a-cmdlet-without-parameters"></a><span data-ttu-id="56c71-102">创建不具有参数的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="56c71-102">Creating a Cmdlet without Parameters</span></span>

<span data-ttu-id="56c71-103">本部分介绍如何创建从本地计算机而不使用参数，检索的信息，然后将信息写入管道的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="56c71-103">This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span> <span data-ttu-id="56c71-104">此处所述的 cmdlet 是检索本地计算机的进程的信息，然后在命令行中显示该信息的 Get-proc cmdlet。</span><span class="sxs-lookup"><span data-stu-id="56c71-104">The cmdlet described here is a Get-Proc cmdlet that retrieves information about the processes of the local computer, and then displays that information at the command line.</span></span>

> [!NOTE]
> <span data-ttu-id="56c71-105">请注意，在编写 cmdlet，Windows PowerShell® 引用程序集下载到磁盘上 （通过默认位于 C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0）。</span><span class="sxs-lookup"><span data-stu-id="56c71-105">Be aware that when writing cmdlets, the Windows PowerShell® reference assemblies are downloaded onto disk (by default at C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).</span></span> <span data-ttu-id="56c71-106">它们不被安装在全局程序集缓存 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="56c71-106">They are not installed in the Global Assembly Cache (GAC).</span></span>

## <a name="naming-the-cmdlet"></a><span data-ttu-id="56c71-107">命名该 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="56c71-107">Naming the Cmdlet</span></span>

<span data-ttu-id="56c71-108">Cmdlet 名称由指示将该 cmdlet 的操作动词和名词，该值指示该 cmdlet 作用于的项组成。</span><span class="sxs-lookup"><span data-stu-id="56c71-108">A cmdlet name consists of a verb that indicates the action the cmdlet takes and a noun that indicates the items that the cmdlet acts upon.</span></span> <span data-ttu-id="56c71-109">由于此示例 Get-proc cmdlet 检索进程对象，它使用谓词"Get"，定义[System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon)枚举和名词"Proc"以指示该 cmdlet 适用于进程的项。</span><span class="sxs-lookup"><span data-stu-id="56c71-109">Because this sample Get-Proc cmdlet retrieves process objects, it uses the verb "Get", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeration, and the noun "Proc" to indicate that the cmdlet works on process items.</span></span>

<span data-ttu-id="56c71-110">当命名 cmdlet 时，请不要使用任何以下字符: #，（） {} [] &-/ \ $;:"<> &#124; ？</span><span class="sxs-lookup"><span data-stu-id="56c71-110">When naming cmdlets, do not use any of the following characters: # , () {} [] & - /\ $ ; : " '<> &#124; ?</span></span> <span data-ttu-id="56c71-111">@ \` .</span><span class="sxs-lookup"><span data-stu-id="56c71-111">@ \` .</span></span>

### <a name="choosing-a-noun"></a><span data-ttu-id="56c71-112">选择某个名词</span><span class="sxs-lookup"><span data-stu-id="56c71-112">Choosing a Noun</span></span>

<span data-ttu-id="56c71-113">应选择特定的名词。</span><span class="sxs-lookup"><span data-stu-id="56c71-113">You should choose a noun that is specific.</span></span> <span data-ttu-id="56c71-114">最好使用单数形式的名词前缀为产品名称的缩写形式。</span><span class="sxs-lookup"><span data-stu-id="56c71-114">It is best to use a singular noun prefixed with a shortened version of the product name.</span></span> <span data-ttu-id="56c71-115">此类型的示例 cmdlet 名称是"`Get-SQLServer`"。</span><span class="sxs-lookup"><span data-stu-id="56c71-115">An example cmdlet name of this type is "`Get-SQLServer`".</span></span>

### <a name="choosing-a-verb"></a><span data-ttu-id="56c71-116">选择谓词</span><span class="sxs-lookup"><span data-stu-id="56c71-116">Choosing a Verb</span></span>

<span data-ttu-id="56c71-117">应使用已批准的 cmdlet 的动词名称的集中的谓词。</span><span class="sxs-lookup"><span data-stu-id="56c71-117">You should use a verb from the set of approved cmdlet verb names.</span></span> <span data-ttu-id="56c71-118">有关已批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 的动词名称](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="56c71-118">For more information about the approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="56c71-119">定义在 Cmdlet 类</span><span class="sxs-lookup"><span data-stu-id="56c71-119">Defining the Cmdlet Class</span></span>

<span data-ttu-id="56c71-120">一旦您选择了 cmdlet 名称，定义一个.NET 类来实现该 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="56c71-120">Once you have chosen a cmdlet name, define a .NET class to implement the cmdlet.</span></span> <span data-ttu-id="56c71-121">下面是此示例 Get-proc cmdlet 类定义：</span><span class="sxs-lookup"><span data-stu-id="56c71-121">Here is the class definition for this sample Get-Proc cmdlet:</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

<span data-ttu-id="56c71-122">请注意，上一步类定义中， [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)属性，使用语法`[Cmdlet(verb, noun, ...)]`，用于标识此类作为一个 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="56c71-122">Notice that previous to the class definition, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute, with the syntax `[Cmdlet(verb, noun, ...)]`, is used to identify this class as a cmdlet.</span></span> <span data-ttu-id="56c71-123">这是唯一的必需的属性为所有的 cmdlet，并允许 Windows PowerShell 运行时，若要正确地调用它们。</span><span class="sxs-lookup"><span data-stu-id="56c71-123">This is the only required attribute for all cmdlets, and it allows the Windows PowerShell runtime to call them correctly.</span></span> <span data-ttu-id="56c71-124">可以设置属性关键字，以进一步声明类，如有必要。</span><span class="sxs-lookup"><span data-stu-id="56c71-124">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="56c71-125">请注意，我们的示例 GetProcCommand 类的特性声明声明了仅 Get-proc cmdlet 的名词和动词名称。</span><span class="sxs-lookup"><span data-stu-id="56c71-125">Be aware that the attribute declaration for our sample GetProcCommand class declares only the noun and verb names for the Get-Proc cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="56c71-126">对于所有 Windows PowerShell 属性类，可以设置的关键字对应于特性类的属性。</span><span class="sxs-lookup"><span data-stu-id="56c71-126">For all Windows PowerShell attribute classes, the keywords that you can set correspond to properties of the attribute class.</span></span>

<span data-ttu-id="56c71-127">命名该 cmdlet 的类，很好的做法，以反映类名称中的 cmdlet 名称。</span><span class="sxs-lookup"><span data-stu-id="56c71-127">When naming the class of the cmdlet, it is a good practice to reflect the cmdlet name in the class name.</span></span> <span data-ttu-id="56c71-128">若要执行此操作，使用窗体"VerbNounCommand"，并替换动词和名词的 cmdlet 名称中使用"谓词"和"名词"。</span><span class="sxs-lookup"><span data-stu-id="56c71-128">To do this, use the form "VerbNounCommand" and replace "Verb" and "Noun" with the verb and noun used in the cmdlet name.</span></span> <span data-ttu-id="56c71-129">示例 Get-proc cmdlet 以前的类定义中所示，定义一个名为 GetProcCommand，派生自类[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)基类。</span><span class="sxs-lookup"><span data-stu-id="56c71-129">As is shown in the previous class definition, the sample Get-Proc cmdlet defines a class called GetProcCommand, which derives from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="56c71-130">如果你想要定义一个 cmdlet，直接访问 Windows PowerShell 运行时，.NET 类应派生自[System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)基类。</span><span class="sxs-lookup"><span data-stu-id="56c71-130">If you want to define a cmdlet that accesses the Windows PowerShell runtime directly, your .NET class should derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span> <span data-ttu-id="56c71-131">有关此类的详细信息，请参阅[创建该定义的参数集的一个 Cmdlet](./adding-parameter-sets-to-a-cmdlet.md)。</span><span class="sxs-lookup"><span data-stu-id="56c71-131">For more information about this class, see [Creating a Cmdlet that Defines Parameter Sets](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

> [!NOTE]
> <span data-ttu-id="56c71-132">Cmdlet 类必须显式标记为公共。</span><span class="sxs-lookup"><span data-stu-id="56c71-132">The class for a cmdlet must be explicitly marked as public.</span></span> <span data-ttu-id="56c71-133">未标记为公共的类将默认为内部和 Windows PowerShell 运行时将不会找到。</span><span class="sxs-lookup"><span data-stu-id="56c71-133">Classes that are not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="56c71-134">使用 Windows PowerShell [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands)其 cmdlet 类的命名空间。</span><span class="sxs-lookup"><span data-stu-id="56c71-134">Windows PowerShell uses the [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namespace for its cmdlet classes.</span></span> <span data-ttu-id="56c71-135">建议将 cmdlet 类放置在你的 API 命名空间，例如，xxx.PS.Commands 命令命名空间。</span><span class="sxs-lookup"><span data-stu-id="56c71-135">It is recommended to place your cmdlet classes in a Commands namespace of your API namespace, for example, xxx.PS.Commands.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="56c71-136">重写方法的处理的输入</span><span class="sxs-lookup"><span data-stu-id="56c71-136">Overriding an Input Processing Method</span></span>

<span data-ttu-id="56c71-137">[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)类提供了三个主要的输入的处理方法，你的 cmdlet 必须在至少一个替代。</span><span class="sxs-lookup"><span data-stu-id="56c71-137">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides three main input processing methods, at least one of which your cmdlet must override.</span></span> <span data-ttu-id="56c71-138">有关 Windows PowerShell 如何处理记录的详细信息，请参阅[Windows PowerShell 的工作原理](/previous-versions//ms714658(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="56c71-138">For more information about how Windows PowerShell processes records, see [How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85)).</span></span>

<span data-ttu-id="56c71-139">对于所有类型的输入，Windows PowerShell 运行时调用[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)启用处理。</span><span class="sxs-lookup"><span data-stu-id="56c71-139">For all types of input, the Windows PowerShell runtime calls [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) to enable processing.</span></span> <span data-ttu-id="56c71-140">如果你的 cmdlet 必须执行一些预处理或安装程序，它可以执行此操作通过重写此方法。</span><span class="sxs-lookup"><span data-stu-id="56c71-140">If your cmdlet must perform some preprocessing or setup, it can do this by overriding this method.</span></span>

> [!NOTE]
> <span data-ttu-id="56c71-141">Windows PowerShell 使用术语"记录"来描述调用 cmdlet 时提供的参数值的组。</span><span class="sxs-lookup"><span data-stu-id="56c71-141">Windows PowerShell uses the term "record" to describe the set of parameter values supplied when a cmdlet is called.</span></span>

<span data-ttu-id="56c71-142">如果你的 cmdlet 接受管道输入，则必须重写[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，并选择性地[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。</span><span class="sxs-lookup"><span data-stu-id="56c71-142">If your cmdlet accepts pipeline input, it must override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, and optionally the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="56c71-143">例如，一个 cmdlet 可能会替代这两种方法，如果收集使用的所有输入[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) ，然后输入作为一个整体，而不是一个元素一次，作为运行`Sort-Object`cmdlet 的用途。</span><span class="sxs-lookup"><span data-stu-id="56c71-143">For example, a cmdlet might override both methods if it gathers all input using [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) and then operates on the input as a whole rather than one element at a time, as the `Sort-Object` cmdlet does.</span></span>

<span data-ttu-id="56c71-144">如果你的 cmdlet 不接受管道输入，应重写[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。</span><span class="sxs-lookup"><span data-stu-id="56c71-144">If your cmdlet does not take pipeline input, it should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="56c71-145">注意： 此方法经常用来代替到[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)时该 cmdlet 不能作用于一个元素一次排序 cmdlet 的情况一样。</span><span class="sxs-lookup"><span data-stu-id="56c71-145">Be aware that this method is frequently used in place of [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) when the cmdlet cannot operate on one element at a time, as is the case for a sorting cmdlet.</span></span>

<span data-ttu-id="56c71-146">此示例 Get-proc cmdlet 必须接收管道输入，因为它将替代[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，并使用的默认实现[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)并[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)。</span><span class="sxs-lookup"><span data-stu-id="56c71-146">Because this sample Get-Proc cmdlet must receive pipeline input, it overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method and uses the default implementations for [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) and [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span></span> <span data-ttu-id="56c71-147">[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)替代检索进程，并将其写入到命令行中使用[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法。</span><span class="sxs-lookup"><span data-stu-id="56c71-147">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override retrieves processes and writes them to the command line using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span>

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

#### <a name="things-to-remember-about-input-processing"></a><span data-ttu-id="56c71-148">要记住有关输入处理的事项</span><span class="sxs-lookup"><span data-stu-id="56c71-148">Things to Remember About Input Processing</span></span>

- <span data-ttu-id="56c71-149">输入的默认源是由命令行上的用户提供一个显式对象 （例如，字符串）。</span><span class="sxs-lookup"><span data-stu-id="56c71-149">The default source for input is an explicit object (for example, a string) provided by the user on the command line.</span></span> <span data-ttu-id="56c71-150">有关详细信息，请参阅[创建进程命令行输入到 Cmdlet](./adding-parameters-that-process-command-line-input.md)。</span><span class="sxs-lookup"><span data-stu-id="56c71-150">For more information, see [Creating a Cmdlet to Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

- <span data-ttu-id="56c71-151">输入处理方法，还可以从在管道上的上游 cmdlet 的输出对象接收输入。</span><span class="sxs-lookup"><span data-stu-id="56c71-151">An input processing method can also receive input from the output object of an upstream cmdlet on the pipeline.</span></span> <span data-ttu-id="56c71-152">有关详细信息，请参阅[创建到进程管道输入 Cmdlet](./adding-parameters-that-process-pipeline-input.md)。</span><span class="sxs-lookup"><span data-stu-id="56c71-152">For more information, see [Creating a Cmdlet to Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="56c71-153">请注意 cmdlet 可以接收来自命令行组成的输入和管道源。</span><span class="sxs-lookup"><span data-stu-id="56c71-153">Be aware that your cmdlet can receive input from a combination of command-line and pipeline sources.</span></span>

- <span data-ttu-id="56c71-154">对于较长时间，或根本不可能不会返回下游 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="56c71-154">The downstream cmdlet might not return for a long time, or not at all.</span></span> <span data-ttu-id="56c71-155">因此，处理您的 cmdlet 中的方法的输入应不持有的锁期间调用到[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)，尤其是为其范围超出 cmdlet 实例的锁。</span><span class="sxs-lookup"><span data-stu-id="56c71-155">For that reason, the input processing method in your cmdlet should not hold locks during calls to [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especially locks for which the scope extends beyond the cmdlet instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="56c71-156">Cmdlet 应永远不会调用[System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine)或其等效项。</span><span class="sxs-lookup"><span data-stu-id="56c71-156">Cmdlets should never call [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) or its equivalent.</span></span>

- <span data-ttu-id="56c71-157">Cmdlet 可能具有对象变量来完成后清理处理 (例如，如果该表已打开的文件句柄[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法，并保留句柄打开供使用[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord))。</span><span class="sxs-lookup"><span data-stu-id="56c71-157">Your cmdlet might have object variables to clean up when it is finished processing (for example, if it opens a file handle in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span></span> <span data-ttu-id="56c71-158">务必要记住 Windows PowerShell 运行时不会始终调用[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法，应执行对象清理。</span><span class="sxs-lookup"><span data-stu-id="56c71-158">It is important to remember that the Windows PowerShell runtime does not always call the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, which should perform object cleanup.</span></span>

<span data-ttu-id="56c71-159">例如， [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)如果正中取消该 cmdlet，或者如果终止该 cmdlet 的任何部分中会发生错误可能不会调用。</span><span class="sxs-lookup"><span data-stu-id="56c71-159">For example, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) might not be called if the cmdlet is canceled midway or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="56c71-160">因此，需要对象清理 cmdlet 应实现的完整[System.IDisposable](/dotnet/api/System.IDisposable)模式，以便在运行时可以调用都包括终结器， [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)并[System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose)处理结束时。</span><span class="sxs-lookup"><span data-stu-id="56c71-160">Therefore, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including the finalizer, so that the runtime can call both [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) at the end of processing.</span></span>

## <a name="code-sample"></a><span data-ttu-id="56c71-161">代码示例</span><span class="sxs-lookup"><span data-stu-id="56c71-161">Code Sample</span></span>

<span data-ttu-id="56c71-162">有关完整C#示例代码，请参阅[GetProcessSample01 Sample](./getprocesssample01-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="56c71-162">For the complete C# sample code, see [GetProcessSample01 Sample](./getprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="56c71-163">定义对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="56c71-163">Defining Object Types and Formatting</span></span>

<span data-ttu-id="56c71-164">Windows PowerShell cmdlet 使用.NET 对象之间传递信息。</span><span class="sxs-lookup"><span data-stu-id="56c71-164">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="56c71-165">因此，一个 cmdlet 可能需要定义其自己的类型，或者该 cmdlet 可能需要扩展现有类型提供的另一个 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="56c71-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="56c71-166">有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式设置](/previous-versions//ms714665(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="56c71-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="56c71-167">生成该 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="56c71-167">Building the Cmdlet</span></span>

<span data-ttu-id="56c71-168">实现一个 cmdlet 之后, 您必须注册它使用 Windows PowerShell 通过 Windows PowerShell 管理单元。</span><span class="sxs-lookup"><span data-stu-id="56c71-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="56c71-169">有关注册 cmdlet 的详细信息，请参阅[如何注册 Cmdlet、 提供商和主机应用程序](/previous-versions//ms714644(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="56c71-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="56c71-170">测试 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="56c71-170">Testing the Cmdlet</span></span>

<span data-ttu-id="56c71-171">当已使用 Windows PowerShell 注册你的 cmdlet 时，可以通过运行命令行上测试它。</span><span class="sxs-lookup"><span data-stu-id="56c71-171">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="56c71-172">我们示例 Get-proc cmdlet 的代码较小，但它仍使用 Windows PowerShell 运行时和现有的.NET 对象，就足以使其发挥作用。</span><span class="sxs-lookup"><span data-stu-id="56c71-172">The code for our sample Get-Proc cmdlet is small, but it still uses the Windows PowerShell runtime and an existing .NET object, which is enough to make it useful.</span></span> <span data-ttu-id="56c71-173">让我们测试，以更好地了解 Get-proc 可以执行的操作以及可以如何使用其输出。</span><span class="sxs-lookup"><span data-stu-id="56c71-173">Let's test it to better understand what Get-Proc can do and how its output can be used.</span></span> <span data-ttu-id="56c71-174">有关使用命令行中的 cmdlet 的详细信息，请参阅[Windows PowerShell 入门学习](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="56c71-174">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

1. <span data-ttu-id="56c71-175">启动 Windows PowerShell，并获取当前进程在计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="56c71-175">Start Windows PowerShell, and get the current processes running on the computer.</span></span>

    ```powershell
    get-proc
    ```

    <span data-ttu-id="56c71-176">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="56c71-176">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. <span data-ttu-id="56c71-177">将一个变量分配给 cmdlet 结果以便于操作。</span><span class="sxs-lookup"><span data-stu-id="56c71-177">Assign a variable to the cmdlet results for easier manipulation.</span></span>

    ```powershell
    $p=get-proc
    ```

3. <span data-ttu-id="56c71-178">获取进程数。</span><span class="sxs-lookup"><span data-stu-id="56c71-178">Get the number of processes.</span></span>

    ```powershell
    $p.length
    ```

    <span data-ttu-id="56c71-179">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="56c71-179">The following output appears.</span></span>

    ```output
    63
    ```

4. <span data-ttu-id="56c71-180">检索特定的进程。</span><span class="sxs-lookup"><span data-stu-id="56c71-180">Retrieve a specific process.</span></span>

    ```powershell
    $p[6]
    ```

    <span data-ttu-id="56c71-181">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="56c71-181">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. <span data-ttu-id="56c71-182">获取此进程的开始时间。</span><span class="sxs-lookup"><span data-stu-id="56c71-182">Get the start time of this process.</span></span>

    ```powershell
    $p[6].starttime
    ```

    <span data-ttu-id="56c71-183">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="56c71-183">The following output appears.</span></span>

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. <span data-ttu-id="56c71-184">获取进程的句柄计数大于 500，并对结果进行排序。</span><span class="sxs-lookup"><span data-stu-id="56c71-184">Get the processes for which the handle count is greater than 500, and sort the result.</span></span>

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    <span data-ttu-id="56c71-185">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="56c71-185">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. <span data-ttu-id="56c71-186">使用`Get-Member`cmdlet 可列出可用于每个进程的属性。</span><span class="sxs-lookup"><span data-stu-id="56c71-186">Use the `Get-Member` cmdlet to list the properties available for each process.</span></span>

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    <span data-ttu-id="56c71-187">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="56c71-187">The following output appears.</span></span>

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a><span data-ttu-id="56c71-188">另请参阅</span><span class="sxs-lookup"><span data-stu-id="56c71-188">See Also</span></span>

[<span data-ttu-id="56c71-189">创建用于处理命令行输入的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="56c71-189">Creating a Cmdlet to Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="56c71-190">创建用于处理管道输入的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="56c71-190">Creating a Cmdlet to Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="56c71-191">如何创建 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="56c71-191">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="56c71-192">[扩展对象类型和格式设置](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="56c71-192">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="56c71-193">[Windows PowerShell 的工作原理](/previous-versions//ms714658(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="56c71-193">[How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85))</span></span>

<span data-ttu-id="56c71-194">[如何注册 Cmdlet、 提供程序，和托管应用程序](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="56c71-194">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="56c71-195">Windows PowerShell 参考</span><span class="sxs-lookup"><span data-stu-id="56c71-195">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="56c71-196">Cmdlet 示例</span><span class="sxs-lookup"><span data-stu-id="56c71-196">Cmdlet Samples</span></span>](./cmdlet-samples.md)