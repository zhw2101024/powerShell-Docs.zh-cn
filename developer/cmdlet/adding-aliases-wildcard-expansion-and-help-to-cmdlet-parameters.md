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
ms.openlocfilehash: 0f025213087e6f308adf8e597fc01c1320251f76
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859323"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="54c8e-102">向 Cmdlet 参数添加别名、通配符扩展和帮助</span><span class="sxs-lookup"><span data-stu-id="54c8e-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="54c8e-103">本部分介绍如何添加别名，通配符扩展和帮助消息到停止进程 cmdlet 的参数 (中所述[创建一个 Cmdlet 来修改系统](./creating-a-cmdlet-that-modifies-the-system.md))。</span><span class="sxs-lookup"><span data-stu-id="54c8e-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="54c8e-104">此停止进程 cmdlet 会尝试停止使用 Get-proc cmdlet 检索的进程 (中所述[创建第一个 Cmdlet](./creating-a-cmdlet-without-parameters.md))。</span><span class="sxs-lookup"><span data-stu-id="54c8e-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

<span data-ttu-id="54c8e-105">在本部分中的主题包括：</span><span class="sxs-lookup"><span data-stu-id="54c8e-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="54c8e-106">定义 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="54c8e-106">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="54c8e-107">系统修改为定义参数</span><span class="sxs-lookup"><span data-stu-id="54c8e-107">Defining Parameters for System Modification</span></span>](#Defining-Parameters-for-System-Modification)

- [<span data-ttu-id="54c8e-108">定义参数别名</span><span class="sxs-lookup"><span data-stu-id="54c8e-108">Defining a Parameter Alias</span></span>](#Defining-a-Parameter-Alias)

- [<span data-ttu-id="54c8e-109">创建参数的帮助</span><span class="sxs-lookup"><span data-stu-id="54c8e-109">Creating Help for Parameters</span></span>](#Creating-Help-for-Parameters)

- [<span data-ttu-id="54c8e-110">重写方法的处理的输入</span><span class="sxs-lookup"><span data-stu-id="54c8e-110">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="54c8e-111">支持通配符扩展</span><span class="sxs-lookup"><span data-stu-id="54c8e-111">Supporting Wildcard Expansion</span></span>](#Supporting-Wildcard-Expansion)

- [<span data-ttu-id="54c8e-112">代码示例</span><span class="sxs-lookup"><span data-stu-id="54c8e-112">Code Sample</span></span>](#Defining-a-Parameter-Alias)

- [<span data-ttu-id="54c8e-113">定义对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="54c8e-113">Defining Object Types and Formatting</span></span>](#Define-Object-Types-and-Formatting)

- [<span data-ttu-id="54c8e-114">生成该 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="54c8e-114">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="54c8e-115">测试 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="54c8e-115">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="54c8e-116">定义 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="54c8e-116">Defining the Cmdlet</span></span>

<span data-ttu-id="54c8e-117">Cmdlet 创建的第一步是始终命名 cmdlet 和实现该 cmdlet 的.NET 类声明。</span><span class="sxs-lookup"><span data-stu-id="54c8e-117">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="54c8e-118">因为你正在编写 cmdlet 来更改的系统，应相应地命名。</span><span class="sxs-lookup"><span data-stu-id="54c8e-118">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="54c8e-119">此 cmdlet 停止系统进程，因为它使用定义的谓词"停止" [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)类，使用名词"Proc"以指示过程。</span><span class="sxs-lookup"><span data-stu-id="54c8e-119">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="54c8e-120">有关已批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 的动词名称](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="54c8e-120">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="54c8e-121">以下代码是此停止进程 cmdlet 的类定义。</span><span class="sxs-lookup"><span data-stu-id="54c8e-121">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="54c8e-122">系统修改为定义参数</span><span class="sxs-lookup"><span data-stu-id="54c8e-122">Defining Parameters for System Modification</span></span>

<span data-ttu-id="54c8e-123">Cmdlet 需要该支持系统修改和用户反馈定义参数。</span><span class="sxs-lookup"><span data-stu-id="54c8e-123">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="54c8e-124">该 cmdlet 应定义`Name`参数或等效身份，以便该 cmdlet 将能够通过某种形式的标识符修改系统。</span><span class="sxs-lookup"><span data-stu-id="54c8e-124">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="54c8e-125">此外，该 cmdlet 应定义`Force`和`PassThru`参数。</span><span class="sxs-lookup"><span data-stu-id="54c8e-125">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="54c8e-126">有关这些参数的详细信息，请参阅[创建一个 Cmdlet 来修改系统](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="54c8e-126">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="54c8e-127">定义参数别名</span><span class="sxs-lookup"><span data-stu-id="54c8e-127">Defining a Parameter Alias</span></span>

<span data-ttu-id="54c8e-128">参数别名可以是一个备用名称或 cmdlet 参数的定义完善 1 号或两个字母短名称。</span><span class="sxs-lookup"><span data-stu-id="54c8e-128">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="54c8e-129">在这两种情况下，使用别名的目标是简化从命令行的用户条目。</span><span class="sxs-lookup"><span data-stu-id="54c8e-129">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="54c8e-130">Windows PowerShell 支持通过参数别名[System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute，它使用声明语法 [Alias()]。</span><span class="sxs-lookup"><span data-stu-id="54c8e-130">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="54c8e-131">下面的代码演示如何将别名添加到`Name`参数。</span><span class="sxs-lookup"><span data-stu-id="54c8e-131">The following code shows how an alias is added to the `Name` parameter.</span></span>

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

<span data-ttu-id="54c8e-132">除了使用之外[System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)属性中，Windows PowerShell 运行时执行部分名称匹配，即使不指定了任何别名。</span><span class="sxs-lookup"><span data-stu-id="54c8e-132">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="54c8e-133">例如，如果你的 cmdlet 具有`FileName`参数，即开头的唯一参数`F`，用户可以输入`Filename`， `Filenam`， `File`， `Fi`，或`F`和仍然识别项作为`FileName`参数。</span><span class="sxs-lookup"><span data-stu-id="54c8e-133">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="54c8e-134">创建参数的帮助</span><span class="sxs-lookup"><span data-stu-id="54c8e-134">Creating Help for Parameters</span></span>

<span data-ttu-id="54c8e-135">Windows PowerShell 允许你为 cmdlet 参数创建帮助。</span><span class="sxs-lookup"><span data-stu-id="54c8e-135">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="54c8e-136">执行此操作用于系统修改和用户反馈的任何参数。</span><span class="sxs-lookup"><span data-stu-id="54c8e-136">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="54c8e-137">对于以支持帮助每个参数，可以设置`HelpMessage`属性中的关键字[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)特性声明。</span><span class="sxs-lookup"><span data-stu-id="54c8e-137">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="54c8e-138">此关键字定义中使用参数的帮助针对向用户显示的文本。</span><span class="sxs-lookup"><span data-stu-id="54c8e-138">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="54c8e-139">您还可以设置`HelpMessageBaseName`关键字来标识要用于消息的资源的基名称。</span><span class="sxs-lookup"><span data-stu-id="54c8e-139">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="54c8e-140">如果设置此关键字，则还必须设置`HelpMessageResourceId`关键字来指定资源标识符。</span><span class="sxs-lookup"><span data-stu-id="54c8e-140">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="54c8e-141">此停止进程 cmdlet 中的以下代码定义`HelpMessage`属性的关键字`Name`参数。</span><span class="sxs-lookup"><span data-stu-id="54c8e-141">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="54c8e-142">重写方法的处理的输入</span><span class="sxs-lookup"><span data-stu-id="54c8e-142">Overriding an Input Processing Method</span></span>

<span data-ttu-id="54c8e-143">你的 cmdlet 必须重写方法的处理的输入，这是最常[System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)。</span><span class="sxs-lookup"><span data-stu-id="54c8e-143">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="54c8e-144">在修改系统，该 cmdlet 应调用[System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)并[System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)允许方法若要提供反馈，然后进行更改的用户。</span><span class="sxs-lookup"><span data-stu-id="54c8e-144">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="54c8e-145">有关这些方法的详细信息，请参阅[创建一个 Cmdlet 来修改系统](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="54c8e-145">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="54c8e-146">支持通配符扩展</span><span class="sxs-lookup"><span data-stu-id="54c8e-146">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="54c8e-147">若要允许选择多个对象，你的 cmdlet 可以使用[System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern)并[System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions)类来提供输入参数的通配符扩展支持。</span><span class="sxs-lookup"><span data-stu-id="54c8e-147">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="54c8e-148">通配符模式的示例包括 lsa \* \*.txt 和 [a-c]\*。</span><span class="sxs-lookup"><span data-stu-id="54c8e-148">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="54c8e-149">模式包含应按原义使用的字符时，请使用反引号字符 （'） 作为转义符。</span><span class="sxs-lookup"><span data-stu-id="54c8e-149">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="54c8e-150">通配符扩展的文件和路径名称是该 cmdlet 可能想要允许对路径输入的支持，需要选择多个对象时的常见方案的示例。</span><span class="sxs-lookup"><span data-stu-id="54c8e-150">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="54c8e-151">常见的情况是在文件系统中，用户要查看当前文件夹中驻留的所有文件。</span><span class="sxs-lookup"><span data-stu-id="54c8e-151">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="54c8e-152">您应只是偶尔需要自定义的通配符模式匹配实现。</span><span class="sxs-lookup"><span data-stu-id="54c8e-152">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="54c8e-153">在这种情况下，你的 cmdlet 应支持完整的 POSIX 1003.2、 3.13 规范通配符扩展或以下的简化的子集：</span><span class="sxs-lookup"><span data-stu-id="54c8e-153">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="54c8e-154">**问号 （？）。**</span><span class="sxs-lookup"><span data-stu-id="54c8e-154">**Question mark (?).**</span></span> <span data-ttu-id="54c8e-155">匹配任何字符的指定位置。</span><span class="sxs-lookup"><span data-stu-id="54c8e-155">Matches any character at the specified location.</span></span>

- <span data-ttu-id="54c8e-156">**星号 (\*)。**</span><span class="sxs-lookup"><span data-stu-id="54c8e-156">**Asterisk (\*).**</span></span> <span data-ttu-id="54c8e-157">匹配零个或多个字符的指定位置开始。</span><span class="sxs-lookup"><span data-stu-id="54c8e-157">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="54c8e-158">**左大括号 ([])。**</span><span class="sxs-lookup"><span data-stu-id="54c8e-158">**Open bracket ([).**</span></span> <span data-ttu-id="54c8e-159">引入了可以包含字符或一系列字符模式大括号表达式。</span><span class="sxs-lookup"><span data-stu-id="54c8e-159">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="54c8e-160">如果范围是必需的连字符 （-） 用于指示该范围。</span><span class="sxs-lookup"><span data-stu-id="54c8e-160">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="54c8e-161">**右大括号 (])。**</span><span class="sxs-lookup"><span data-stu-id="54c8e-161">**Close bracket (]).**</span></span> <span data-ttu-id="54c8e-162">结束模式括号表达式。</span><span class="sxs-lookup"><span data-stu-id="54c8e-162">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="54c8e-163">**反引号转义符 （'）。**</span><span class="sxs-lookup"><span data-stu-id="54c8e-163">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="54c8e-164">指示应按字面解释的下一个字符。</span><span class="sxs-lookup"><span data-stu-id="54c8e-164">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="54c8e-165">请注意，在指定的反引号字符，从命令行 （而不是以编程方式指定） 时，反引号转义符必须指定两次。</span><span class="sxs-lookup"><span data-stu-id="54c8e-165">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="54c8e-166">有关通配符模式的详细信息，请参阅[中的 Cmdlet 参数支持通配符](./supporting-wildcard-characters-in-cmdlet-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="54c8e-166">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="54c8e-167">下面的代码演示如何设置通配符选项和定义用于解析的通配符模式`Name`对于此 cmdlet 的参数。</span><span class="sxs-lookup"><span data-stu-id="54c8e-167">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="54c8e-168">下面的代码显示了如何测试进程名称是否与定义的通配符模式匹配。</span><span class="sxs-lookup"><span data-stu-id="54c8e-168">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="54c8e-169">请注意，在这种情况下，是否进程名称不匹配模式，该 cmdlet 将继续上获取下一步的过程名称。</span><span class="sxs-lookup"><span data-stu-id="54c8e-169">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="54c8e-170">代码示例</span><span class="sxs-lookup"><span data-stu-id="54c8e-170">Code Sample</span></span>

<span data-ttu-id="54c8e-171">有关完整C#示例代码，请参阅[StopProcessSample03 示例](./stopprocesssample03-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="54c8e-171">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="54c8e-172">定义对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="54c8e-172">Define Object Types and Formatting</span></span>

<span data-ttu-id="54c8e-173">Windows PowerShell cmdlet 使用.Net 对象之间传递信息。</span><span class="sxs-lookup"><span data-stu-id="54c8e-173">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="54c8e-174">因此，一个 cmdlet 可能需要定义其自己的类型，或者该 cmdlet 可能需要扩展现有类型提供的另一个 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="54c8e-174">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="54c8e-175">有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式设置](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。</span><span class="sxs-lookup"><span data-stu-id="54c8e-175">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="54c8e-176">生成该 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="54c8e-176">Building the Cmdlet</span></span>

<span data-ttu-id="54c8e-177">执行后一个 cmdlet，它必须向注册 Windows PowerShell 通过 Windows PowerShell 管理单元。</span><span class="sxs-lookup"><span data-stu-id="54c8e-177">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="54c8e-178">有关注册 cmdlet 的详细信息，请参阅[如何注册 Cmdlet、 提供商和主机应用程序](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="54c8e-178">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="54c8e-179">测试 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="54c8e-179">Testing the Cmdlet</span></span>

<span data-ttu-id="54c8e-180">当已使用 Windows PowerShell 注册你的 cmdlet 时，可以通过运行命令行上测试它。</span><span class="sxs-lookup"><span data-stu-id="54c8e-180">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="54c8e-181">让我们测试示例停止进程 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="54c8e-181">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="54c8e-182">有关使用命令行中的 cmdlet 的详细信息，请参阅[Windows PowerShell 入门学习](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="54c8e-182">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="54c8e-183">启动 Windows PowerShell 并使用停止的进程来停止使用的 ProcessName 别名的进程`Name`参数。</span><span class="sxs-lookup"><span data-stu-id="54c8e-183">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

<span data-ttu-id="54c8e-184">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="54c8e-184">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="54c8e-185">请在命令行上的以下条目。</span><span class="sxs-lookup"><span data-stu-id="54c8e-185">Make the following entry on the command line.</span></span> <span data-ttu-id="54c8e-186">Name 参数是必需的因为系统会提示输入它。</span><span class="sxs-lookup"><span data-stu-id="54c8e-186">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="54c8e-187">输入"！？"</span><span class="sxs-lookup"><span data-stu-id="54c8e-187">Entering "!?"</span></span> <span data-ttu-id="54c8e-188">将显示与参数关联的帮助文本。</span><span class="sxs-lookup"><span data-stu-id="54c8e-188">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="54c8e-189">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="54c8e-189">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="54c8e-190">现在，请停止与通配符模式匹配的所有进程的以下条目"\* 注意\*"。</span><span class="sxs-lookup"><span data-stu-id="54c8e-190">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="54c8e-191">系统会提示停止与模式匹配每个进程之前。</span><span class="sxs-lookup"><span data-stu-id="54c8e-191">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

<span data-ttu-id="54c8e-192">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="54c8e-192">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

<span data-ttu-id="54c8e-193">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="54c8e-193">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

<span data-ttu-id="54c8e-194">将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="54c8e-194">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="54c8e-195">另请参阅</span><span class="sxs-lookup"><span data-stu-id="54c8e-195">See Also</span></span>

[<span data-ttu-id="54c8e-196">创建用于修改系统的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="54c8e-196">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="54c8e-197">如何创建 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="54c8e-197">How to Create a Windows PowerShell Cmdlet</span></span>](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="54c8e-198">扩展对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="54c8e-198">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="54c8e-199">如何注册 Cmdlet、 提供程序，和托管应用程序</span><span class="sxs-lookup"><span data-stu-id="54c8e-199">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="54c8e-200">中的 Cmdlet 参数支持通配符</span><span class="sxs-lookup"><span data-stu-id="54c8e-200">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="54c8e-201">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="54c8e-201">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)