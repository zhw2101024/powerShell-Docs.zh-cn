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
ms.openlocfilehash: c380b28570c955de6f41152fd617f5c1b0f9e4bd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054690"
---
# <a name="creating-a-cmdlet-without-parameters"></a><span data-ttu-id="6dd98-102">创建不具有参数的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6dd98-102">Creating a Cmdlet without Parameters</span></span>

<span data-ttu-id="6dd98-103">本部分介绍如何创建从本地计算机而不使用参数，检索的信息，然后将信息写入管道的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6dd98-103">This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span> <span data-ttu-id="6dd98-104">此处所述的 cmdlet 是检索本地计算机的进程的信息，然后在命令行中显示该信息的 Get-proc cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6dd98-104">The cmdlet described here is a Get-Proc cmdlet that retrieves information about the processes of the local computer, and then displays that information at the command line.</span></span>

<span data-ttu-id="6dd98-105">在本部分中的主题包括：</span><span class="sxs-lookup"><span data-stu-id="6dd98-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="6dd98-106">命名该 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6dd98-106">Naming the Cmdlet</span></span>](#Naming-the-Cmdlet)

- [<span data-ttu-id="6dd98-107">定义在 Cmdlet 类</span><span class="sxs-lookup"><span data-stu-id="6dd98-107">Defining the Cmdlet Class</span></span>](#Defining-the-Cmdlet-Class)

- [<span data-ttu-id="6dd98-108">重写方法的处理的输入</span><span class="sxs-lookup"><span data-stu-id="6dd98-108">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="6dd98-109">代码示例</span><span class="sxs-lookup"><span data-stu-id="6dd98-109">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="6dd98-110">定义对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="6dd98-110">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="6dd98-111">生成该 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6dd98-111">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="6dd98-112">测试 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6dd98-112">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

> [!NOTE]
> <span data-ttu-id="6dd98-113">请注意，在编写 cmdlet，Windows PowerShell® 引用程序集下载到磁盘上 （通过默认位于 C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0）。它们不被安装在全局程序集缓存 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="6dd98-113">Be aware that when writing cmdlets, the Windows PowerShell® reference assemblies are downloaded onto disk (by default at C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).They are not installed in the Global Assembly Cache (GAC).</span></span>

## <a name="naming-the-cmdlet"></a><span data-ttu-id="6dd98-114">命名该 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6dd98-114">Naming the Cmdlet</span></span>

<span data-ttu-id="6dd98-115">Cmdlet 名称由指示将该 cmdlet 的操作动词和名词，该值指示该 cmdlet 作用于的项组成。</span><span class="sxs-lookup"><span data-stu-id="6dd98-115">A cmdlet name consists of a verb that indicates the action the cmdlet takes and a noun that indicates the items that the cmdlet acts upon.</span></span> <span data-ttu-id="6dd98-116">由于此示例 Get-proc cmdlet 检索进程对象，它使用谓词"Get"，定义[System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon)枚举和名词"Proc"以指示该 cmdlet 适用于进程的项。</span><span class="sxs-lookup"><span data-stu-id="6dd98-116">Because this sample Get-Proc cmdlet retrieves process objects, it uses the verb "Get", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeration, and the noun "Proc" to indicate that the cmdlet works on process items.</span></span>

<span data-ttu-id="6dd98-117">当命名 cmdlet 时，请不要使用任何以下字符: #，（） {} [] &-/ \ $;:"<> &#124; ？</span><span class="sxs-lookup"><span data-stu-id="6dd98-117">When naming cmdlets, do not use any of the following characters: # , () {} [] & - /\ $ ; : " '<> &#124; ?</span></span> <span data-ttu-id="6dd98-118">@ \` .</span><span class="sxs-lookup"><span data-stu-id="6dd98-118">@ \` .</span></span>

### <a name="choosing-a-noun"></a><span data-ttu-id="6dd98-119">选择某个名词</span><span class="sxs-lookup"><span data-stu-id="6dd98-119">Choosing a Noun</span></span>

<span data-ttu-id="6dd98-120">应选择特定的名词。</span><span class="sxs-lookup"><span data-stu-id="6dd98-120">You should choose a noun that is specific.</span></span> <span data-ttu-id="6dd98-121">最好使用单数形式的名词前缀为产品名称的缩写形式。</span><span class="sxs-lookup"><span data-stu-id="6dd98-121">It is best to use a singular noun prefixed with a shortened version of the product name.</span></span> <span data-ttu-id="6dd98-122">此类型的示例 cmdlet 名称是"`Get-SQLServer`"。</span><span class="sxs-lookup"><span data-stu-id="6dd98-122">An example cmdlet name of this type is "`Get-SQLServer`".</span></span>

### <a name="choosing-a-verb"></a><span data-ttu-id="6dd98-123">选择谓词</span><span class="sxs-lookup"><span data-stu-id="6dd98-123">Choosing a Verb</span></span>

<span data-ttu-id="6dd98-124">应使用已批准的 cmdlet 的动词名称的集中的谓词。</span><span class="sxs-lookup"><span data-stu-id="6dd98-124">You should use a verb from the set of approved cmdlet verb names.</span></span> <span data-ttu-id="6dd98-125">有关已批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 的动词名称](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="6dd98-125">For more information about the approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="6dd98-126">定义在 Cmdlet 类</span><span class="sxs-lookup"><span data-stu-id="6dd98-126">Defining the Cmdlet Class</span></span>

<span data-ttu-id="6dd98-127">一旦您选择了 cmdlet 名称，定义一个.NET 类来实现该 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6dd98-127">Once you have chosen a cmdlet name, define a .NET class to implement the cmdlet.</span></span> <span data-ttu-id="6dd98-128">下面是此示例 Get-proc cmdlet 类定义：</span><span class="sxs-lookup"><span data-stu-id="6dd98-128">Here is the class definition for this sample Get-Proc cmdlet:</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

<span data-ttu-id="6dd98-129">请注意，上一步类定义中， [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)属性，使用语法`[Cmdlet(verb, noun, ...)]`，用于标识此类作为一个 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6dd98-129">Notice that previous to the class definition, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute, with the syntax `[Cmdlet(verb, noun, ...)]`, is used to identify this class as a cmdlet.</span></span> <span data-ttu-id="6dd98-130">这是唯一的必需的属性为所有的 cmdlet，并允许 Windows PowerShell 运行时，若要正确地调用它们。</span><span class="sxs-lookup"><span data-stu-id="6dd98-130">This is the only required attribute for all cmdlets, and it allows the Windows PowerShell runtime to call them correctly.</span></span> <span data-ttu-id="6dd98-131">可以设置属性关键字，以进一步声明类，如有必要。</span><span class="sxs-lookup"><span data-stu-id="6dd98-131">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="6dd98-132">请注意，我们的示例 GetProcCommand 类的特性声明声明了仅 Get-proc cmdlet 的名词和动词名称。</span><span class="sxs-lookup"><span data-stu-id="6dd98-132">Be aware that the attribute declaration for our sample GetProcCommand class declares only the noun and verb names for the Get-Proc cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="6dd98-133">对于所有 Windows PowerShell 属性类，可以设置的关键字对应于特性类的属性。</span><span class="sxs-lookup"><span data-stu-id="6dd98-133">For all Windows PowerShell attribute classes, the keywords that you can set correspond to properties of the attribute class.</span></span>

<span data-ttu-id="6dd98-134">命名该 cmdlet 的类，很好的做法，以反映类名称中的 cmdlet 名称。</span><span class="sxs-lookup"><span data-stu-id="6dd98-134">When naming the class of the cmdlet, it is a good practice to reflect the cmdlet name in the class name.</span></span> <span data-ttu-id="6dd98-135">若要执行此操作，使用窗体"VerbNounCommand"，并替换动词和名词的 cmdlet 名称中使用"谓词"和"名词"。</span><span class="sxs-lookup"><span data-stu-id="6dd98-135">To do this, use the form "VerbNounCommand" and replace "Verb" and "Noun" with the verb and noun used in the cmdlet name.</span></span> <span data-ttu-id="6dd98-136">示例 Get-proc cmdlet 以前的类定义中所示，定义一个名为 GetProcCommand，派生自类[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)基类。</span><span class="sxs-lookup"><span data-stu-id="6dd98-136">As is shown in the previous class definition, the sample Get-Proc cmdlet defines a class called GetProcCommand, which derives from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6dd98-137">如果你想要定义一个 cmdlet，直接访问 Windows PowerShell 运行时，.NET 类应派生自[System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)基类。</span><span class="sxs-lookup"><span data-stu-id="6dd98-137">If you want to define a cmdlet that accesses the Windows PowerShell runtime directly, your .NET class should derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span> <span data-ttu-id="6dd98-138">有关此类的详细信息，请参阅[创建该定义的参数集的一个 Cmdlet](./adding-parameter-sets-to-a-cmdlet.md)。</span><span class="sxs-lookup"><span data-stu-id="6dd98-138">For more information about this class, see [Creating a Cmdlet that Defines Parameter Sets](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

> [!NOTE]
> <span data-ttu-id="6dd98-139">Cmdlet 类必须显式标记为公共。</span><span class="sxs-lookup"><span data-stu-id="6dd98-139">The class for a cmdlet must be explicitly marked as public.</span></span> <span data-ttu-id="6dd98-140">未标记为公共的类将默认为内部和 Windows PowerShell 运行时将不会找到。</span><span class="sxs-lookup"><span data-stu-id="6dd98-140">Classes that are not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="6dd98-141">使用 Windows PowerShell [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands)其 cmdlet 类的命名空间。</span><span class="sxs-lookup"><span data-stu-id="6dd98-141">Windows PowerShell uses the [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namespace for its cmdlet classes.</span></span> <span data-ttu-id="6dd98-142">建议将 cmdlet 类放置在你的 API 命名空间，例如，xxx.PS.Commands 命令命名空间。</span><span class="sxs-lookup"><span data-stu-id="6dd98-142">It is recommended to place your cmdlet classes in a Commands namespace of your API namespace, for example, xxx.PS.Commands.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="6dd98-143">重写方法的处理的输入</span><span class="sxs-lookup"><span data-stu-id="6dd98-143">Overriding an Input Processing Method</span></span>

<span data-ttu-id="6dd98-144">[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)类提供了三个主要的输入的处理方法，你的 cmdlet 必须在至少一个替代。</span><span class="sxs-lookup"><span data-stu-id="6dd98-144">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides three main input processing methods, at least one of which your cmdlet must override.</span></span> <span data-ttu-id="6dd98-145">有关 Windows PowerShell 如何处理记录的详细信息，请参阅[Windows PowerShell 的工作原理](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)。</span><span class="sxs-lookup"><span data-stu-id="6dd98-145">For more information about how Windows PowerShell processes records, see [How Windows PowerShell Works](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span></span>

<span data-ttu-id="6dd98-146">对于所有类型的输入，Windows PowerShell 运行时调用[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)启用处理。</span><span class="sxs-lookup"><span data-stu-id="6dd98-146">For all types of input, the Windows PowerShell runtime calls [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) to enable processing.</span></span> <span data-ttu-id="6dd98-147">如果你的 cmdlet 必须执行一些预处理或安装程序，它可以执行此操作通过重写此方法。</span><span class="sxs-lookup"><span data-stu-id="6dd98-147">If your cmdlet must perform some preprocessing or setup, it can do this by overriding this method.</span></span>

> [!NOTE]
> <span data-ttu-id="6dd98-148">Windows PowerShell 使用术语"记录"来描述调用 cmdlet 时提供的参数值的组。</span><span class="sxs-lookup"><span data-stu-id="6dd98-148">Windows PowerShell uses the term "record" to describe the set of parameter values supplied when a cmdlet is called.</span></span>

<span data-ttu-id="6dd98-149">如果你的 cmdlet 接受管道输入，则必须重写[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，并选择性地[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。</span><span class="sxs-lookup"><span data-stu-id="6dd98-149">If your cmdlet accepts pipeline input, it must override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, and optionally the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="6dd98-150">例如，一个 cmdlet 可能会替代这两种方法，如果收集使用的所有输入[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) ，然后输入作为一个整体，而不是一个元素一次，作为运行`Sort-Object`cmdlet 的用途。</span><span class="sxs-lookup"><span data-stu-id="6dd98-150">For example, a cmdlet might override both methods if it gathers all input using [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) and then operates on the input as a whole rather than one element at a time, as the `Sort-Object` cmdlet does.</span></span>

<span data-ttu-id="6dd98-151">如果你的 cmdlet 不接受管道输入，应重写[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。</span><span class="sxs-lookup"><span data-stu-id="6dd98-151">If your cmdlet does not take pipeline input, it should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="6dd98-152">注意： 此方法经常用来代替到[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)时该 cmdlet 不能作用于一个元素一次排序 cmdlet 的情况一样。</span><span class="sxs-lookup"><span data-stu-id="6dd98-152">Be aware that this method is frequently used in place of [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) when the cmdlet cannot operate on one element at a time, as is the case for a sorting cmdlet.</span></span>

<span data-ttu-id="6dd98-153">此示例 Get-proc cmdlet 必须接收管道输入，因为它将替代[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，并使用的默认实现[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)并[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)。</span><span class="sxs-lookup"><span data-stu-id="6dd98-153">Because this sample Get-Proc cmdlet must receive pipeline input, it overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method and uses the default implementations for [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) and [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span></span> <span data-ttu-id="6dd98-154">[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)替代检索进程，并将其写入到命令行中使用[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法。</span><span class="sxs-lookup"><span data-stu-id="6dd98-154">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override retrieves processes and writes them to the command line using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span>

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

#### <a name="things-to-remember-about-input-processing"></a><span data-ttu-id="6dd98-155">要记住有关输入处理的事项</span><span class="sxs-lookup"><span data-stu-id="6dd98-155">Things to Remember About Input Processing</span></span>

- <span data-ttu-id="6dd98-156">输入的默认源是由命令行上的用户提供一个显式对象 （例如，字符串）。</span><span class="sxs-lookup"><span data-stu-id="6dd98-156">The default source for input is an explicit object (for example, a string) provided by the user on the command line.</span></span> <span data-ttu-id="6dd98-157">有关详细信息，请参阅[创建进程命令行输入到 Cmdlet](./adding-parameters-that-process-command-line-input.md)。</span><span class="sxs-lookup"><span data-stu-id="6dd98-157">For more information, see [Creating a Cmdlet to Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

- <span data-ttu-id="6dd98-158">输入处理方法，还可以从在管道上的上游 cmdlet 的输出对象接收输入。</span><span class="sxs-lookup"><span data-stu-id="6dd98-158">An input processing method can also receive input from the output object of an upstream cmdlet on the pipeline.</span></span> <span data-ttu-id="6dd98-159">有关详细信息，请参阅[创建到进程管道输入 Cmdlet](./adding-parameters-that-process-pipeline-input.md)。</span><span class="sxs-lookup"><span data-stu-id="6dd98-159">For more information, see [Creating a Cmdlet to Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="6dd98-160">请注意 cmdlet 可以接收来自命令行组成的输入和管道源。</span><span class="sxs-lookup"><span data-stu-id="6dd98-160">Be aware that your cmdlet can receive input from a combination of command-line and pipeline sources.</span></span>

- <span data-ttu-id="6dd98-161">对于较长时间，或根本不可能不会返回下游 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6dd98-161">The downstream cmdlet might not return for a long time, or not at all.</span></span> <span data-ttu-id="6dd98-162">因此，处理您的 cmdlet 中的方法的输入应不持有的锁期间调用到[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)，尤其是为其范围超出 cmdlet 实例的锁。</span><span class="sxs-lookup"><span data-stu-id="6dd98-162">For that reason, the input processing method in your cmdlet should not hold locks during calls to [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especially locks for which the scope extends beyond the cmdlet instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6dd98-163">Cmdlet 应永远不会调用[System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine)或其等效项。</span><span class="sxs-lookup"><span data-stu-id="6dd98-163">Cmdlets should never call [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) or its equivalent.</span></span>

- <span data-ttu-id="6dd98-164">Cmdlet 可能具有对象变量来完成后清理处理 (例如，如果该表已打开的文件句柄[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法，并保留句柄打开供使用[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord))。</span><span class="sxs-lookup"><span data-stu-id="6dd98-164">Your cmdlet might have object variables to clean up when it is finished processing (for example, if it opens a file handle in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span></span> <span data-ttu-id="6dd98-165">务必要记住 Windows PowerShell 运行时不会始终调用[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法，应执行对象清理。</span><span class="sxs-lookup"><span data-stu-id="6dd98-165">It is important to remember that the Windows PowerShell runtime does not always call the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, which should perform object cleanup.</span></span>

<span data-ttu-id="6dd98-166">例如， [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)如果正中取消该 cmdlet，或者如果终止该 cmdlet 的任何部分中会发生错误可能不会调用。</span><span class="sxs-lookup"><span data-stu-id="6dd98-166">For example, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) might not be called if the cmdlet is canceled midway or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="6dd98-167">因此，需要对象清理 cmdlet 应实现的完整[System.IDisposable](/dotnet/api/System.IDisposable)模式，以便在运行时可以调用都包括终结器， [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)并[System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose)处理结束时。</span><span class="sxs-lookup"><span data-stu-id="6dd98-167">Therefore, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including the finalizer, so that the runtime can call both [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) at the end of processing.</span></span>

## <a name="code-sample"></a><span data-ttu-id="6dd98-168">代码示例</span><span class="sxs-lookup"><span data-stu-id="6dd98-168">Code Sample</span></span>

<span data-ttu-id="6dd98-169">有关完整C#示例代码，请参阅[GetProcessSample01 Sample](./getprocesssample01-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="6dd98-169">For the complete C# sample code, see [GetProcessSample01 Sample](./getprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="6dd98-170">定义对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="6dd98-170">Defining Object Types and Formatting</span></span>

<span data-ttu-id="6dd98-171">Windows PowerShell cmdlet 使用.NET 对象之间传递信息。</span><span class="sxs-lookup"><span data-stu-id="6dd98-171">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="6dd98-172">因此，一个 cmdlet 可能需要定义其自己的类型，或者该 cmdlet 可能需要扩展现有类型提供的另一个 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6dd98-172">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="6dd98-173">有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式设置](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。</span><span class="sxs-lookup"><span data-stu-id="6dd98-173">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="6dd98-174">生成该 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6dd98-174">Building the Cmdlet</span></span>

<span data-ttu-id="6dd98-175">实现一个 cmdlet 之后, 您必须注册它使用 Windows PowerShell 通过 Windows PowerShell 管理单元。</span><span class="sxs-lookup"><span data-stu-id="6dd98-175">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="6dd98-176">有关注册 cmdlet 的详细信息，请参阅[如何注册 Cmdlet、 提供商和主机应用程序](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="6dd98-176">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="6dd98-177">测试 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6dd98-177">Testing the Cmdlet</span></span>

<span data-ttu-id="6dd98-178">当已使用 Windows PowerShell 注册你的 cmdlet 时，可以通过运行命令行上测试它。</span><span class="sxs-lookup"><span data-stu-id="6dd98-178">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="6dd98-179">我们示例 Get-proc cmdlet 的代码较小，但它仍使用 Windows PowerShell 运行时和现有的.NET 对象，就足以使其发挥作用。</span><span class="sxs-lookup"><span data-stu-id="6dd98-179">The code for our sample Get-Proc cmdlet is small, but it still uses the Windows PowerShell runtime and an existing .NET object, which is enough to make it useful.</span></span> <span data-ttu-id="6dd98-180">让我们测试，以更好地了解 Get-proc 可以执行的操作以及可以如何使用其输出。</span><span class="sxs-lookup"><span data-stu-id="6dd98-180">Let's test it to better understand what Get-Proc can do and how its output can be used.</span></span> <span data-ttu-id="6dd98-181">有关使用命令行中的 cmdlet 的详细信息，请参阅[Windows PowerShell 入门学习](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="6dd98-181">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

1. <span data-ttu-id="6dd98-182">启动 Windows PowerShell，并获取当前进程在计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="6dd98-182">Start Windows PowerShell, and get the current processes running on the computer.</span></span>

    ```powershell
    get-proc
    ```

    <span data-ttu-id="6dd98-183">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="6dd98-183">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. <span data-ttu-id="6dd98-184">将一个变量分配给 cmdlet 结果以便于操作。</span><span class="sxs-lookup"><span data-stu-id="6dd98-184">Assign a variable to the cmdlet results for easier manipulation.</span></span>

    ```powershell
    $p=get-proc
    ```

3. <span data-ttu-id="6dd98-185">获取进程数。</span><span class="sxs-lookup"><span data-stu-id="6dd98-185">Get the number of processes.</span></span>

    ```powershell
    $p.length
    ```

    <span data-ttu-id="6dd98-186">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="6dd98-186">The following output appears.</span></span>

    ```output
    63
    ```

4. <span data-ttu-id="6dd98-187">检索特定的进程。</span><span class="sxs-lookup"><span data-stu-id="6dd98-187">Retrieve a specific process.</span></span>

    ```powershell
    $p[6]
    ```

    <span data-ttu-id="6dd98-188">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="6dd98-188">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. <span data-ttu-id="6dd98-189">获取此进程的开始时间。</span><span class="sxs-lookup"><span data-stu-id="6dd98-189">Get the start time of this process.</span></span>

    ```powershell
    $p[6].starttime
    ```

    <span data-ttu-id="6dd98-190">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="6dd98-190">The following output appears.</span></span>

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. <span data-ttu-id="6dd98-191">获取进程的句柄计数大于 500，并对结果进行排序。</span><span class="sxs-lookup"><span data-stu-id="6dd98-191">Get the processes for which the handle count is greater than 500, and sort the result.</span></span>

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    <span data-ttu-id="6dd98-192">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="6dd98-192">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. <span data-ttu-id="6dd98-193">使用`Get-Member`cmdlet 可列出可用于每个进程的属性。</span><span class="sxs-lookup"><span data-stu-id="6dd98-193">Use the `Get-Member` cmdlet to list the properties available for each process.</span></span>

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    <span data-ttu-id="6dd98-194">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="6dd98-194">The following output appears.</span></span>

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a><span data-ttu-id="6dd98-195">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6dd98-195">See Also</span></span>

[<span data-ttu-id="6dd98-196">创建用于处理命令行输入的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6dd98-196">Creating a Cmdlet to Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="6dd98-197">创建用于处理管道输入的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6dd98-197">Creating a Cmdlet to Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="6dd98-198">如何创建 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6dd98-198">How to Create a Windows PowerShell Cmdlet</span></span>](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="6dd98-199">扩展对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="6dd98-199">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="6dd98-200">Windows PowerShell 的工作原理</span><span class="sxs-lookup"><span data-stu-id="6dd98-200">How Windows PowerShell Works</span></span>](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[<span data-ttu-id="6dd98-201">如何注册 Cmdlet、 提供程序，和托管应用程序</span><span class="sxs-lookup"><span data-stu-id="6dd98-201">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="6dd98-202">Windows PowerShell 参考</span><span class="sxs-lookup"><span data-stu-id="6dd98-202">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="6dd98-203">Cmdlet 示例</span><span class="sxs-lookup"><span data-stu-id="6dd98-203">Cmdlet Samples</span></span>](./cmdlet-samples.md)