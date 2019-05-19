---
title: 添加别名，通配符扩展，并帮助对 Cmdlet 参数 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: 946b71e4480a47ac6ccd6930be445d7efb4fb62d
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854891"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="098aa-102">向 Cmdlet 参数添加别名、通配符扩展和帮助</span><span class="sxs-lookup"><span data-stu-id="098aa-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="098aa-103">本部分介绍如何添加别名，通配符扩展和帮助消息到停止进程 cmdlet 的参数 (中所述[创建一个 Cmdlet 来修改系统](./creating-a-cmdlet-that-modifies-the-system.md))。</span><span class="sxs-lookup"><span data-stu-id="098aa-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="098aa-104">此停止进程 cmdlet 会尝试停止使用 Get-proc cmdlet 检索的进程 (中所述[创建第一个 Cmdlet](./creating-a-cmdlet-without-parameters.md))。</span><span class="sxs-lookup"><span data-stu-id="098aa-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="098aa-105">定义 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="098aa-105">Defining the Cmdlet</span></span>

<span data-ttu-id="098aa-106">Cmdlet 创建的第一步是始终命名 cmdlet 和实现该 cmdlet 的.NET 类声明。</span><span class="sxs-lookup"><span data-stu-id="098aa-106">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="098aa-107">因为你正在编写 cmdlet 来更改的系统，应相应地命名。</span><span class="sxs-lookup"><span data-stu-id="098aa-107">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="098aa-108">此 cmdlet 停止系统进程，因为它使用定义的谓词"停止" [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)类，使用名词"Proc"以指示过程。</span><span class="sxs-lookup"><span data-stu-id="098aa-108">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="098aa-109">有关已批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 的动词名称](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="098aa-109">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="098aa-110">以下代码是此停止进程 cmdlet 的类定义。</span><span class="sxs-lookup"><span data-stu-id="098aa-110">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="098aa-111">系统修改为定义参数</span><span class="sxs-lookup"><span data-stu-id="098aa-111">Defining Parameters for System Modification</span></span>

<span data-ttu-id="098aa-112">Cmdlet 需要该支持系统修改和用户反馈定义参数。</span><span class="sxs-lookup"><span data-stu-id="098aa-112">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="098aa-113">该 cmdlet 应定义`Name`参数或等效身份，以便该 cmdlet 将能够通过某种形式的标识符修改系统。</span><span class="sxs-lookup"><span data-stu-id="098aa-113">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="098aa-114">此外，该 cmdlet 应定义`Force`和`PassThru`参数。</span><span class="sxs-lookup"><span data-stu-id="098aa-114">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="098aa-115">有关这些参数的详细信息，请参阅[创建一个 Cmdlet 来修改系统](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="098aa-115">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="098aa-116">定义参数别名</span><span class="sxs-lookup"><span data-stu-id="098aa-116">Defining a Parameter Alias</span></span>

<span data-ttu-id="098aa-117">参数别名可以是一个备用名称或 cmdlet 参数的定义完善 1 号或两个字母短名称。</span><span class="sxs-lookup"><span data-stu-id="098aa-117">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="098aa-118">在这两种情况下，使用别名的目标是简化从命令行的用户条目。</span><span class="sxs-lookup"><span data-stu-id="098aa-118">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="098aa-119">Windows PowerShell 支持通过参数别名[System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute，它使用声明语法 [Alias()]。</span><span class="sxs-lookup"><span data-stu-id="098aa-119">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="098aa-120">下面的代码演示如何将别名添加到`Name`参数。</span><span class="sxs-lookup"><span data-stu-id="098aa-120">The following code shows how an alias is added to the `Name` parameter.</span></span>

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

<span data-ttu-id="098aa-121">除了使用之外[System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)属性中，Windows PowerShell 运行时执行部分名称匹配，即使不指定了任何别名。</span><span class="sxs-lookup"><span data-stu-id="098aa-121">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="098aa-122">例如，如果你的 cmdlet 具有`FileName`参数，即开头的唯一参数`F`，用户可以输入`Filename`， `Filenam`， `File`， `Fi`，或`F`和仍然识别项作为`FileName`参数。</span><span class="sxs-lookup"><span data-stu-id="098aa-122">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="098aa-123">创建参数的帮助</span><span class="sxs-lookup"><span data-stu-id="098aa-123">Creating Help for Parameters</span></span>

<span data-ttu-id="098aa-124">Windows PowerShell 允许你为 cmdlet 参数创建帮助。</span><span class="sxs-lookup"><span data-stu-id="098aa-124">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="098aa-125">执行此操作用于系统修改和用户反馈的任何参数。</span><span class="sxs-lookup"><span data-stu-id="098aa-125">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="098aa-126">对于以支持帮助每个参数，可以设置`HelpMessage`属性中的关键字[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)特性声明。</span><span class="sxs-lookup"><span data-stu-id="098aa-126">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="098aa-127">此关键字定义中使用参数的帮助针对向用户显示的文本。</span><span class="sxs-lookup"><span data-stu-id="098aa-127">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="098aa-128">您还可以设置`HelpMessageBaseName`关键字来标识要用于消息的资源的基名称。</span><span class="sxs-lookup"><span data-stu-id="098aa-128">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="098aa-129">如果设置此关键字，则还必须设置`HelpMessageResourceId`关键字来指定资源标识符。</span><span class="sxs-lookup"><span data-stu-id="098aa-129">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="098aa-130">此停止进程 cmdlet 中的以下代码定义`HelpMessage`属性的关键字`Name`参数。</span><span class="sxs-lookup"><span data-stu-id="098aa-130">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="098aa-131">重写方法的处理的输入</span><span class="sxs-lookup"><span data-stu-id="098aa-131">Overriding an Input Processing Method</span></span>

<span data-ttu-id="098aa-132">你的 cmdlet 必须重写方法的处理的输入，这是最常[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)。</span><span class="sxs-lookup"><span data-stu-id="098aa-132">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="098aa-133">该 cmdlet 时修改系统，应调用[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)并[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，允许用户若要进行更改之前，请提供反馈。</span><span class="sxs-lookup"><span data-stu-id="098aa-133">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="098aa-134">有关这些方法的详细信息，请参阅[创建一个 Cmdlet 来修改系统](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="098aa-134">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="098aa-135">支持通配符扩展</span><span class="sxs-lookup"><span data-stu-id="098aa-135">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="098aa-136">若要允许选择多个对象，你的 cmdlet 可以使用[System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern)并[System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions)类来提供输入参数的通配符扩展支持。</span><span class="sxs-lookup"><span data-stu-id="098aa-136">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="098aa-137">通配符模式的示例包括 lsa \* \*.txt 和 [a-c]\*。</span><span class="sxs-lookup"><span data-stu-id="098aa-137">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="098aa-138">模式包含应按原义使用的字符时，请使用反引号字符 （'） 作为转义符。</span><span class="sxs-lookup"><span data-stu-id="098aa-138">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="098aa-139">通配符扩展的文件和路径名称是该 cmdlet 可能想要允许对路径输入的支持，需要选择多个对象时的常见方案的示例。</span><span class="sxs-lookup"><span data-stu-id="098aa-139">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="098aa-140">常见的情况是在文件系统中，用户要查看当前文件夹中驻留的所有文件。</span><span class="sxs-lookup"><span data-stu-id="098aa-140">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="098aa-141">您应只是偶尔需要自定义的通配符模式匹配实现。</span><span class="sxs-lookup"><span data-stu-id="098aa-141">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="098aa-142">在这种情况下，你的 cmdlet 应支持完整的 POSIX 1003.2、 3.13 规范通配符扩展或以下的简化的子集：</span><span class="sxs-lookup"><span data-stu-id="098aa-142">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="098aa-143">**问号 （？）。**</span><span class="sxs-lookup"><span data-stu-id="098aa-143">**Question mark (?).**</span></span> <span data-ttu-id="098aa-144">匹配任何字符的指定位置。</span><span class="sxs-lookup"><span data-stu-id="098aa-144">Matches any character at the specified location.</span></span>

- <span data-ttu-id="098aa-145">**星号 (\*)。**</span><span class="sxs-lookup"><span data-stu-id="098aa-145">**Asterisk (\*).**</span></span> <span data-ttu-id="098aa-146">匹配零个或多个字符的指定位置开始。</span><span class="sxs-lookup"><span data-stu-id="098aa-146">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="098aa-147">**左大括号 ([])。**</span><span class="sxs-lookup"><span data-stu-id="098aa-147">**Open bracket ([).**</span></span> <span data-ttu-id="098aa-148">引入了可以包含字符或一系列字符模式大括号表达式。</span><span class="sxs-lookup"><span data-stu-id="098aa-148">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="098aa-149">如果范围是必需的连字符 （-） 用于指示该范围。</span><span class="sxs-lookup"><span data-stu-id="098aa-149">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="098aa-150">**右大括号 (])。**</span><span class="sxs-lookup"><span data-stu-id="098aa-150">**Close bracket (]).**</span></span> <span data-ttu-id="098aa-151">结束模式括号表达式。</span><span class="sxs-lookup"><span data-stu-id="098aa-151">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="098aa-152">**反引号转义符 （'）。**</span><span class="sxs-lookup"><span data-stu-id="098aa-152">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="098aa-153">指示应按字面解释的下一个字符。</span><span class="sxs-lookup"><span data-stu-id="098aa-153">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="098aa-154">请注意，在指定的反引号字符，从命令行 （而不是以编程方式指定） 时，反引号转义符必须指定两次。</span><span class="sxs-lookup"><span data-stu-id="098aa-154">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="098aa-155">有关通配符模式的详细信息，请参阅[中的 Cmdlet 参数支持通配符](./supporting-wildcard-characters-in-cmdlet-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="098aa-155">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="098aa-156">下面的代码演示如何设置通配符选项和定义用于解析的通配符模式`Name`对于此 cmdlet 的参数。</span><span class="sxs-lookup"><span data-stu-id="098aa-156">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="098aa-157">下面的代码显示了如何测试进程名称是否与定义的通配符模式匹配。</span><span class="sxs-lookup"><span data-stu-id="098aa-157">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="098aa-158">请注意，在这种情况下，是否进程名称不匹配模式，该 cmdlet 将继续上获取下一步的过程名称。</span><span class="sxs-lookup"><span data-stu-id="098aa-158">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="098aa-159">代码示例</span><span class="sxs-lookup"><span data-stu-id="098aa-159">Code Sample</span></span>

<span data-ttu-id="098aa-160">有关完整C#示例代码，请参阅[StopProcessSample03 示例](./stopprocesssample03-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="098aa-160">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="098aa-161">定义对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="098aa-161">Define Object Types and Formatting</span></span>

<span data-ttu-id="098aa-162">Windows PowerShell cmdlet 使用.Net 对象之间传递信息。</span><span class="sxs-lookup"><span data-stu-id="098aa-162">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="098aa-163">因此，一个 cmdlet 可能需要定义其自己的类型，或者该 cmdlet 可能需要扩展现有类型提供的另一个 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="098aa-163">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="098aa-164">有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式设置](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。</span><span class="sxs-lookup"><span data-stu-id="098aa-164">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="098aa-165">生成该 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="098aa-165">Building the Cmdlet</span></span>

<span data-ttu-id="098aa-166">执行后一个 cmdlet，它必须向注册 Windows PowerShell 通过 Windows PowerShell 管理单元。</span><span class="sxs-lookup"><span data-stu-id="098aa-166">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="098aa-167">有关注册 cmdlet 的详细信息，请参阅[如何注册 Cmdlet、 提供商和主机应用程序](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="098aa-167">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="098aa-168">测试 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="098aa-168">Testing the Cmdlet</span></span>

<span data-ttu-id="098aa-169">当已使用 Windows PowerShell 注册你的 cmdlet 时，可以通过运行命令行上测试它。</span><span class="sxs-lookup"><span data-stu-id="098aa-169">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="098aa-170">让我们测试示例停止进程 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="098aa-170">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="098aa-171">有关使用命令行中的 cmdlet 的详细信息，请参阅[Windows PowerShell 入门学习](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="098aa-171">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="098aa-172">启动 Windows PowerShell 并使用停止的进程来停止使用的 ProcessName 别名的进程`Name`参数。</span><span class="sxs-lookup"><span data-stu-id="098aa-172">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

<span data-ttu-id="098aa-173">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="098aa-173">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="098aa-174">请在命令行上的以下条目。</span><span class="sxs-lookup"><span data-stu-id="098aa-174">Make the following entry on the command line.</span></span> <span data-ttu-id="098aa-175">Name 参数是必需的因为系统会提示输入它。</span><span class="sxs-lookup"><span data-stu-id="098aa-175">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="098aa-176">输入"！？"</span><span class="sxs-lookup"><span data-stu-id="098aa-176">Entering "!?"</span></span> <span data-ttu-id="098aa-177">将显示与参数关联的帮助文本。</span><span class="sxs-lookup"><span data-stu-id="098aa-177">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="098aa-178">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="098aa-178">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="098aa-179">现在，请停止与通配符模式匹配的所有进程的以下条目"\* 注意\*"。</span><span class="sxs-lookup"><span data-stu-id="098aa-179">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="098aa-180">系统会提示停止与模式匹配每个进程之前。</span><span class="sxs-lookup"><span data-stu-id="098aa-180">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

<span data-ttu-id="098aa-181">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="098aa-181">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

<span data-ttu-id="098aa-182">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="098aa-182">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

<span data-ttu-id="098aa-183">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="098aa-183">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="098aa-184">另请参阅</span><span class="sxs-lookup"><span data-stu-id="098aa-184">See Also</span></span>

[<span data-ttu-id="098aa-185">创建用于修改系统的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="098aa-185">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="098aa-186">如何创建 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="098aa-186">How to Create a Windows PowerShell Cmdlet</span></span>](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="098aa-187">扩展对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="098aa-187">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="098aa-188">如何注册 Cmdlet、 提供程序，和托管应用程序</span><span class="sxs-lookup"><span data-stu-id="098aa-188">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="098aa-189">中的 Cmdlet 参数支持通配符</span><span class="sxs-lookup"><span data-stu-id="098aa-189">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="098aa-190">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="098aa-190">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
