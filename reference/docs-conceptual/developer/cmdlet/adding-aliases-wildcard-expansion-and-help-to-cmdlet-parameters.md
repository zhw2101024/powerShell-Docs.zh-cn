---
title: 向 Cmdlet 参数添加别名、通配符扩展和帮助 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: d210a852a90d94df2ab360dd86f0b83a396330e3
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74415657"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="057fb-102">向 Cmdlet 参数添加别名、通配符扩展和帮助</span><span class="sxs-lookup"><span data-stu-id="057fb-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="057fb-103">本部分介绍如何将别名、通配符扩展和帮助消息添加到 Stop Proc cmdlet 的参数（如[创建修改系统的 cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)中所述）。</span><span class="sxs-lookup"><span data-stu-id="057fb-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="057fb-104">此 Stop Proc cmdlet 尝试使用 Get-help cmdlet （在[创建第一个 cmdlet](./creating-a-cmdlet-without-parameters.md)时进行介绍）来停止检索的进程。</span><span class="sxs-lookup"><span data-stu-id="057fb-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="057fb-105">定义 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="057fb-105">Defining the Cmdlet</span></span>

<span data-ttu-id="057fb-106">创建 cmdlet 的第一步是始终命名 cmdlet 并声明实现 cmdlet 的 .NET 类。</span><span class="sxs-lookup"><span data-stu-id="057fb-106">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="057fb-107">因为你要编写一个 cmdlet 来更改系统，所以应该相应地对其进行命名。</span><span class="sxs-lookup"><span data-stu-id="057fb-107">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="057fb-108">由于此 cmdlet 停止系统进程，因此它使用由[Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)类定义的谓词 "Stop"，名词 "Proc" 表示进程。</span><span class="sxs-lookup"><span data-stu-id="057fb-108">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="057fb-109">有关批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 谓词名称](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="057fb-109">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="057fb-110">下面的代码是此 Stop Proc cmdlet 的类定义。</span><span class="sxs-lookup"><span data-stu-id="057fb-110">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="057fb-111">定义系统修改的参数</span><span class="sxs-lookup"><span data-stu-id="057fb-111">Defining Parameters for System Modification</span></span>

<span data-ttu-id="057fb-112">Cmdlet 需要定义支持系统修改和用户反馈的参数。</span><span class="sxs-lookup"><span data-stu-id="057fb-112">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="057fb-113">该 cmdlet 应定义 `Name` 参数或等效参数，以便该 cmdlet 能够通过某种标识符修改系统。</span><span class="sxs-lookup"><span data-stu-id="057fb-113">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="057fb-114">此外，该 cmdlet 还应定义 `Force` 和 `PassThru` 参数。</span><span class="sxs-lookup"><span data-stu-id="057fb-114">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="057fb-115">有关这些参数的详细信息，请参阅[创建修改系统的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="057fb-115">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="057fb-116">定义参数别名</span><span class="sxs-lookup"><span data-stu-id="057fb-116">Defining a Parameter Alias</span></span>

<span data-ttu-id="057fb-117">参数别名可以是 cmdlet 参数的替代名称，也可以是定义完善的1个字母或2个字母的短名称。</span><span class="sxs-lookup"><span data-stu-id="057fb-117">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="057fb-118">在这两种情况下，使用别名的目标是简化命令行中的用户输入。</span><span class="sxs-lookup"><span data-stu-id="057fb-118">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="057fb-119">Windows PowerShell 通过使用声明语法 [Alias （）] 的[Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)特性支持参数别名。</span><span class="sxs-lookup"><span data-stu-id="057fb-119">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="057fb-120">下面的代码演示如何将别名添加到 `Name` 参数中。</span><span class="sxs-lookup"><span data-stu-id="057fb-120">The following code shows how an alias is added to the `Name` parameter.</span></span>

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
[Alias("ProcessName")]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

<span data-ttu-id="057fb-121">除了使用[Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)属性，Windows PowerShell 运行时还执行部分名称匹配，即使未指定别名。</span><span class="sxs-lookup"><span data-stu-id="057fb-121">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="057fb-122">例如，如果你的 cmdlet 具有 `FileName` 参数并且是以 `F`开头的唯一参数，则用户可以输入 `Filename`、`Filenam`、`File`、`Fi`或 `F` 并仍将该条目识别为 `FileName` 参数。</span><span class="sxs-lookup"><span data-stu-id="057fb-122">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="057fb-123">创建参数的帮助</span><span class="sxs-lookup"><span data-stu-id="057fb-123">Creating Help for Parameters</span></span>

<span data-ttu-id="057fb-124">Windows PowerShell 允许你为 cmdlet 参数创建帮助。</span><span class="sxs-lookup"><span data-stu-id="057fb-124">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="057fb-125">对用于系统修改和用户反馈的任何参数执行此操作。</span><span class="sxs-lookup"><span data-stu-id="057fb-125">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="057fb-126">对于每个支持帮助的参数，可以在[Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)特性声明中设置 `HelpMessage` attribute 关键字。</span><span class="sxs-lookup"><span data-stu-id="057fb-126">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="057fb-127">此关键字定义要向用户显示的文本，以便在使用参数时获得帮助。</span><span class="sxs-lookup"><span data-stu-id="057fb-127">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="057fb-128">还可以设置 `HelpMessageBaseName` 关键字，以确定用于消息的资源的基本名称。</span><span class="sxs-lookup"><span data-stu-id="057fb-128">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="057fb-129">如果设置了此关键字，则还必须设置 `HelpMessageResourceId` 关键字来指定资源标识符。</span><span class="sxs-lookup"><span data-stu-id="057fb-129">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="057fb-130">此 Stop Proc cmdlet 中的以下代码定义 `Name` 参数的 `HelpMessage` attribute 关键字。</span><span class="sxs-lookup"><span data-stu-id="057fb-130">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="057fb-131">重写输入处理方法</span><span class="sxs-lookup"><span data-stu-id="057fb-131">Overriding an Input Processing Method</span></span>

<span data-ttu-id="057fb-132">Cmdlet 必须重写输入处理方法，最常见的情况是[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)。</span><span class="sxs-lookup"><span data-stu-id="057fb-132">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="057fb-133">当修改系统时，cmdlet 应调用[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，以允许用户在进行更改之前提供反馈信息。 "请确保用户在进行更改之前提供反馈。</span><span class="sxs-lookup"><span data-stu-id="057fb-133">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="057fb-134">有关这些方法的详细信息，请参阅[创建修改系统的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="057fb-134">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="057fb-135">支持通配符扩展</span><span class="sxs-lookup"><span data-stu-id="057fb-135">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="057fb-136">若要允许选择多个对象，你的 cmdlet 可以使用[Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern)和[Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions)类来为参数输入提供通配符扩展支持。</span><span class="sxs-lookup"><span data-stu-id="057fb-136">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="057fb-137">通配符模式的示例包括 lsa \*、\*.txt 和 [c]\*。</span><span class="sxs-lookup"><span data-stu-id="057fb-137">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="057fb-138">如果模式包含应按原义使用的字符，则使用后引号字符（'）作为转义符。</span><span class="sxs-lookup"><span data-stu-id="057fb-138">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="057fb-139">文件和路径名的通配符扩展是常见方案的示例，其中，cmdlet 可能需要在需要选择多个对象时允许对路径输入提供支持。</span><span class="sxs-lookup"><span data-stu-id="057fb-139">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="057fb-140">常见的情况是在文件系统中，用户想要查看位于当前文件夹中的所有文件。</span><span class="sxs-lookup"><span data-stu-id="057fb-140">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="057fb-141">只需很少使用自定义通配符模式匹配实现。</span><span class="sxs-lookup"><span data-stu-id="057fb-141">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="057fb-142">在这种情况下，你的 cmdlet 应支持通配符扩展的完整 POSIX 1003.2、3.13 规范或以下简化子集：</span><span class="sxs-lookup"><span data-stu-id="057fb-142">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="057fb-143">**问号（？）。**</span><span class="sxs-lookup"><span data-stu-id="057fb-143">**Question mark (?).**</span></span> <span data-ttu-id="057fb-144">匹配指定位置的任何字符。</span><span class="sxs-lookup"><span data-stu-id="057fb-144">Matches any character at the specified location.</span></span>

- <span data-ttu-id="057fb-145">**星号（\*）。**</span><span class="sxs-lookup"><span data-stu-id="057fb-145">**Asterisk (\*).**</span></span> <span data-ttu-id="057fb-146">匹配从指定位置开始的零个或多个字符。</span><span class="sxs-lookup"><span data-stu-id="057fb-146">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="057fb-147">**左方括号（[）。**</span><span class="sxs-lookup"><span data-stu-id="057fb-147">**Open bracket ([).**</span></span> <span data-ttu-id="057fb-148">引入一个可包含字符或一系列字符的模式括号表达式。</span><span class="sxs-lookup"><span data-stu-id="057fb-148">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="057fb-149">如果范围是必需的，则使用连字符（-）指示范围。</span><span class="sxs-lookup"><span data-stu-id="057fb-149">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="057fb-150">**右方括号（]）。**</span><span class="sxs-lookup"><span data-stu-id="057fb-150">**Close bracket (]).**</span></span> <span data-ttu-id="057fb-151">结束模式方括号表达式。</span><span class="sxs-lookup"><span data-stu-id="057fb-151">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="057fb-152">**后引号转义符（'）。**</span><span class="sxs-lookup"><span data-stu-id="057fb-152">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="057fb-153">指示应按原义取下一个字符。</span><span class="sxs-lookup"><span data-stu-id="057fb-153">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="057fb-154">请注意，当从命令行（而不是以编程方式指定它）中指定后引号字符时，必须两次指定后引号转义符。</span><span class="sxs-lookup"><span data-stu-id="057fb-154">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="057fb-155">有关通配符模式的详细信息，请参阅[在 Cmdlet 参数中支持通配符](./supporting-wildcard-characters-in-cmdlet-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="057fb-155">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="057fb-156">下面的代码演示如何设置通配符选项，并定义用于解析此 cmdlet 的 `Name` 参数的通配符模式。</span><span class="sxs-lookup"><span data-stu-id="057fb-156">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="057fb-157">下面的代码演示如何测试进程名称是否与定义的通配符模式匹配。</span><span class="sxs-lookup"><span data-stu-id="057fb-157">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="057fb-158">请注意，在这种情况下，如果进程名称与模式不匹配，该 cmdlet 将继续获取下一个进程名称。</span><span class="sxs-lookup"><span data-stu-id="057fb-158">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="057fb-159">代码示例</span><span class="sxs-lookup"><span data-stu-id="057fb-159">Code Sample</span></span>

<span data-ttu-id="057fb-160">有关完整C#的示例代码，请参阅[StopProcessSample03 示例](./stopprocesssample03-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="057fb-160">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="057fb-161">定义对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="057fb-161">Define Object Types and Formatting</span></span>

<span data-ttu-id="057fb-162">Windows PowerShell 使用 .Net 对象在 cmdlet 之间传递信息。</span><span class="sxs-lookup"><span data-stu-id="057fb-162">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="057fb-163">因此，cmdlet 可能需要定义自己的类型，或者该 cmdlet 可能需要扩展另一个 cmdlet 提供的现有类型。</span><span class="sxs-lookup"><span data-stu-id="057fb-163">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="057fb-164">有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式](/previous-versions//ms714665(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="057fb-164">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="057fb-165">构建 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="057fb-165">Building the Cmdlet</span></span>

<span data-ttu-id="057fb-166">实现 cmdlet 后，必须通过 Windows PowerShell 管理单元向 Windows PowerShell 注册它。</span><span class="sxs-lookup"><span data-stu-id="057fb-166">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="057fb-167">有关注册 cmdlet 的详细信息，请参阅[如何注册 cmdlet、提供程序和主机应用程序](/previous-versions//ms714644(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="057fb-167">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="057fb-168">测试 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="057fb-168">Testing the Cmdlet</span></span>

<span data-ttu-id="057fb-169">向 Windows PowerShell 注册 cmdlet 后，可以通过在命令行上运行 cmdlet 来对其进行测试。</span><span class="sxs-lookup"><span data-stu-id="057fb-169">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="057fb-170">接下来，请测试示例的停止过程 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="057fb-170">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="057fb-171">有关从命令行使用 cmdlet 的详细信息，请参阅[使用 Windows PowerShell 的入门](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="057fb-171">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="057fb-172">启动 Windows PowerShell 并使用 "停止进程" 停止进程，并使用 `Name` 参数的 ProcessName 别名。</span><span class="sxs-lookup"><span data-stu-id="057fb-172">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

<span data-ttu-id="057fb-173">此时将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="057fb-173">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="057fb-174">在命令行上生成以下项。</span><span class="sxs-lookup"><span data-stu-id="057fb-174">Make the following entry on the command line.</span></span> <span data-ttu-id="057fb-175">因为 Name 参数是必需的，所以系统会提示你输入。</span><span class="sxs-lookup"><span data-stu-id="057fb-175">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="057fb-176">正在输入 "！？"</span><span class="sxs-lookup"><span data-stu-id="057fb-176">Entering "!?"</span></span> <span data-ttu-id="057fb-177">显示与参数相关联的帮助文本。</span><span class="sxs-lookup"><span data-stu-id="057fb-177">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="057fb-178">此时将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="057fb-178">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="057fb-179">现在，请执行以下条目来停止所有匹配通配符模式 "\* note\*" 的进程。</span><span class="sxs-lookup"><span data-stu-id="057fb-179">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="057fb-180">在停止每个与模式匹配的进程之前，系统将提示您。</span><span class="sxs-lookup"><span data-stu-id="057fb-180">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

<span data-ttu-id="057fb-181">此时将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="057fb-181">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

<span data-ttu-id="057fb-182">此时将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="057fb-182">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

<span data-ttu-id="057fb-183">此时将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="057fb-183">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="057fb-184">请参阅</span><span class="sxs-lookup"><span data-stu-id="057fb-184">See Also</span></span>

[<span data-ttu-id="057fb-185">创建用于修改系统的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="057fb-185">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="057fb-186">如何创建 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="057fb-186">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="057fb-187">[扩展对象类型和格式](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="057fb-187">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="057fb-188">[如何注册 Cmdlet、提供程序和主机应用程序](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="057fb-188">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="057fb-189">支持 Cmdlet 参数中的通配符</span><span class="sxs-lookup"><span data-stu-id="057fb-189">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="057fb-190">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="057fb-190">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
