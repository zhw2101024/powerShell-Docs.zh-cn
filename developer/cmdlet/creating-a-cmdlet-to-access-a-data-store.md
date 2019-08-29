---
title: 创建用于访问数据存储的 Cmdlet
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 7acccbd48dcfb654b11e448a1f24835ad3668fae
ms.sourcegitcommit: a02ccbeaa17c0e513d6c4a21b877c88ac7725458
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104471"
---
# <a name="creating-a-cmdlet-to-access-a-data-store"></a><span data-ttu-id="09a07-102">创建用于访问数据存储的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="09a07-102">Creating a Cmdlet to Access a Data Store</span></span>

<span data-ttu-id="09a07-103">本部分介绍如何创建一个 cmdlet, 该 cmdlet 通过 Windows PowerShell 提供程序来访问存储的数据。</span><span class="sxs-lookup"><span data-stu-id="09a07-103">This section describes how to create a cmdlet that accesses stored data by way of a Windows PowerShell provider.</span></span> <span data-ttu-id="09a07-104">这种类型的 cmdlet 使用 windows PowerShell 运行时的 Windows PowerShell 提供程序基础结构, 因此, 该 cmdlet 类必须派生自[PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)基类。</span><span class="sxs-lookup"><span data-stu-id="09a07-104">This type of cmdlet uses the Windows PowerShell provider infrastructure of the Windows PowerShell runtime and, therefore, the cmdlet class must derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span>

<span data-ttu-id="09a07-105">此处所述的 Str cmdlet 可在文件或对象中查找并选择字符串。</span><span class="sxs-lookup"><span data-stu-id="09a07-105">The Select-Str cmdlet described here can locate and select strings in a file or object.</span></span> <span data-ttu-id="09a07-106">可通过`Path` cmdlet 的参数或`Script`通过参数隐式指定用于标识字符串的模式。</span><span class="sxs-lookup"><span data-stu-id="09a07-106">The patterns used to identify the string can be specified explicitly through the `Path` parameter of the cmdlet or implicitly through the `Script` parameter.</span></span>

<span data-ttu-id="09a07-107">此 cmdlet 旨在使用派生自[Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)的任何 Windows PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="09a07-107">The cmdlet is designed to use any Windows PowerShell provider that derives from [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider).</span></span> <span data-ttu-id="09a07-108">例如, cmdlet 可以指定 Windows PowerShell 提供的 FileSystem 提供程序或变量提供程序。</span><span class="sxs-lookup"><span data-stu-id="09a07-108">For example, the cmdlet can specify the FileSystem provider or the Variable provider that is provided by Windows PowerShell.</span></span> <span data-ttu-id="09a07-109">AboutWindows PowerShell 提供程序的详细信息, 请参阅[设计 Windows PowerShell 提供程序](../prog-guide/designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="09a07-109">For more information aboutWindows PowerShell providers, see [Designing Your Windows PowerShell provider](../prog-guide/designing-your-windows-powershell-provider.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="09a07-110">定义 Cmdlet 类</span><span class="sxs-lookup"><span data-stu-id="09a07-110">Defining the Cmdlet Class</span></span>

<span data-ttu-id="09a07-111">创建 cmdlet 的第一步是始终命名 cmdlet 并声明实现 cmdlet 的 .NET 类。</span><span class="sxs-lookup"><span data-stu-id="09a07-111">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="09a07-112">此 cmdlet 将检测某些字符串, 因此在此处选择的谓词名称为 "Select", 由[Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon)类定义。</span><span class="sxs-lookup"><span data-stu-id="09a07-112">This cmdlet detects certain strings, so the verb name chosen here is "Select", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) class.</span></span> <span data-ttu-id="09a07-113">使用名词 name "Str", 因为该 cmdlet 作用于字符串。</span><span class="sxs-lookup"><span data-stu-id="09a07-113">The noun name "Str" is used because the cmdlet acts upon strings.</span></span> <span data-ttu-id="09a07-114">请注意, 在下面的声明中, cmdlet 谓词和名词名称反映在 cmdlet 类的名称中。</span><span class="sxs-lookup"><span data-stu-id="09a07-114">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span> <span data-ttu-id="09a07-115">有关批准的 cmdlet 谓词的详细信息, 请参阅[Cmdlet 谓词名称](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="09a07-115">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="09a07-116">此 cmdlet 的 .NET 类必须派生自[PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)基类, 因为它提供 windows powershell 运行时用于公开 windows powershell 提供程序基础结构所需的支持。</span><span class="sxs-lookup"><span data-stu-id="09a07-116">The .NET class for this cmdlet must derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class, because it provides the support needed by the Windows PowerShell runtime to expose the Windows PowerShell provider infrastructure.</span></span> <span data-ttu-id="09a07-117">请注意, 此 cmdlet 还利用 .NET Framework 正则表达式类, 如[system.text.regularexpressions](/dotnet/api/System.Text.RegularExpressions.Regex)。</span><span class="sxs-lookup"><span data-stu-id="09a07-117">Note that this cmdlet also makes use of the .NET Framework regular expressions classes, such as [System.Text.Regularexpressions.Regex](/dotnet/api/System.Text.RegularExpressions.Regex).</span></span>

<span data-ttu-id="09a07-118">下面的代码是此 Str cmdlet 的类定义。</span><span class="sxs-lookup"><span data-stu-id="09a07-118">The following code is the class definition for this Select-Str cmdlet.</span></span>

```csharp
[Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
public class SelectStringCommand : PSCmdlet
```

<span data-ttu-id="09a07-119">此 cmdlet 通过将`DefaultParameterSetName` attribute 关键字添加到类声明来定义默认参数集。</span><span class="sxs-lookup"><span data-stu-id="09a07-119">This cmdlet defines a default parameter set by adding the `DefaultParameterSetName` attribute keyword to the class declaration.</span></span> <span data-ttu-id="09a07-120">如果未指定`PatternParameterSet` 参数,则使用默认参数集。`Script`</span><span class="sxs-lookup"><span data-stu-id="09a07-120">The default parameter set `PatternParameterSet` is used when the `Script` parameter is not specified.</span></span> <span data-ttu-id="09a07-121">有关此参数集的详细信息, 请参阅`Pattern`下`Script`一节中的和参数讨论。</span><span class="sxs-lookup"><span data-stu-id="09a07-121">For more information about this parameter set, see the `Pattern` and `Script` parameter discussion in the following section.</span></span>

## <a name="defining-parameters-for-data-access"></a><span data-ttu-id="09a07-122">定义用于数据访问的参数</span><span class="sxs-lookup"><span data-stu-id="09a07-122">Defining Parameters for Data Access</span></span>

<span data-ttu-id="09a07-123">此 cmdlet 定义允许用户访问和检查存储数据的多个参数。</span><span class="sxs-lookup"><span data-stu-id="09a07-123">This cmdlet defines several parameters that allow the user to access and examine stored data.</span></span> <span data-ttu-id="09a07-124">这些参数包括一个`Path`参数, 该参数指示数据存储区的位置、 `Pattern`一个指定在搜索中使用的模式的参数, 以及一些支持搜索执行方式的其他参数。</span><span class="sxs-lookup"><span data-stu-id="09a07-124">These parameters include a `Path` parameter that indicates the location of the data store, a `Pattern` parameter that specifies the pattern to be used in the search, and several other parameters that support how the search is performed.</span></span>

> [!NOTE]
> <span data-ttu-id="09a07-125">有关定义参数的基础知识的详细信息, 请参阅[添加处理命令行输入的参数](./adding-parameters-that-process-command-line-input.md)。</span><span class="sxs-lookup"><span data-stu-id="09a07-125">For more information about the basics of defining parameters, see [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

### <a name="declaring-the-path-parameter"></a><span data-ttu-id="09a07-126">声明 Path 参数</span><span class="sxs-lookup"><span data-stu-id="09a07-126">Declaring the Path Parameter</span></span>

<span data-ttu-id="09a07-127">若要定位数据存储, 此 cmdlet 必须使用 Windows PowerShell 路径来标识用于访问数据存储区的 Windows PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="09a07-127">To locate the data store, this cmdlet must use a Windows PowerShell path to identify the Windows PowerShell provider that is designed to access the data store.</span></span> <span data-ttu-id="09a07-128">因此, 它定义`Path`了类型字符串数组的参数, 以指示提供程序的位置。</span><span class="sxs-lookup"><span data-stu-id="09a07-128">Therefore, it defines a `Path` parameter of type string array to indicate the location of the provider.</span></span>

```csharp
[Parameter(
           Position = 0,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
[Parameter(
           Position = 0,
           ParameterSetName = "PatternParameterSet",
           ValueFromPipeline = true,
           Mandatory = true)]
           [Alias("PSPath")]
public string[] Path
{
  get { return paths; }
  set { paths = value; }
}
private string[] paths;
```

<span data-ttu-id="09a07-129">请注意, 此参数属于两个不同的参数集, 并且具有别名。</span><span class="sxs-lookup"><span data-stu-id="09a07-129">Note that this parameter belongs to two different parameter sets and that it has an alias.</span></span>

<span data-ttu-id="09a07-130">两个[Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)特性声明`Path`该`ScriptParameterSet`参数属于和的`PatternParameterSet`。</span><span class="sxs-lookup"><span data-stu-id="09a07-130">Two [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributes declare that the `Path` parameter belongs to the `ScriptParameterSet` and the `PatternParameterSet`.</span></span> <span data-ttu-id="09a07-131">有关参数集的详细信息, 请参阅[将参数集添加到 Cmdlet](./adding-parameter-sets-to-a-cmdlet.md)。</span><span class="sxs-lookup"><span data-stu-id="09a07-131">For more information about parameter sets, see [Adding Parameter Sets to a Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

<span data-ttu-id="09a07-132">[Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)特性为`PSPath` `Path`参数声明一个别名。)</span><span class="sxs-lookup"><span data-stu-id="09a07-132">The [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute declares a `PSPath` alias for the `Path` parameter.</span></span> <span data-ttu-id="09a07-133">为了与访问 Windows PowerShell 提供程序的其他 cmdlet 保持一致, 强烈建议声明此别名。</span><span class="sxs-lookup"><span data-stu-id="09a07-133">Declaring this alias is strongly recommended for consistency with other cmdlets that access Windows PowerShell providers.</span></span> <span data-ttu-id="09a07-134">AboutWindows PowerShell 路径的详细信息, 请参阅[Windows powershell 的工作](/previous-versions//ms714658(v=vs.85))原理中的 "PowerShell 路径概念"。</span><span class="sxs-lookup"><span data-stu-id="09a07-134">For more information aboutWindows PowerShell paths, see "PowerShell Path Concepts" in [How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85)).</span></span>

### <a name="declaring-the-pattern-parameter"></a><span data-ttu-id="09a07-135">声明模式参数</span><span class="sxs-lookup"><span data-stu-id="09a07-135">Declaring the Pattern Parameter</span></span>

<span data-ttu-id="09a07-136">若要指定要搜索的模式, 此 cmdlet 将声明`Pattern`一个字符串数组参数。</span><span class="sxs-lookup"><span data-stu-id="09a07-136">To specify the patterns to search for, this cmdlet declares a `Pattern` parameter that is an array of strings.</span></span> <span data-ttu-id="09a07-137">在数据存储区中找到任何模式时, 将返回一个正值结果。</span><span class="sxs-lookup"><span data-stu-id="09a07-137">A positive result is returned when any of the patterns are found in the data store.</span></span> <span data-ttu-id="09a07-138">请注意, 这些模式可编译为已编译的正则表达式的数组或用于文本搜索的通配符模式的数组。</span><span class="sxs-lookup"><span data-stu-id="09a07-138">Note that these patterns can be compiled into an array of compiled regular expressions or an array of wildcard patterns used for literal searches.</span></span>

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "PatternParameterSet",
           Mandatory = true)]
public string[] Pattern
{
  get { return patterns; }
  set { patterns = value; }
}
private string[] patterns;
private Regex[] regexPattern;
private WildcardPattern[] wildcardPattern;
```

<span data-ttu-id="09a07-139">如果指定此参数, 则 cmdlet 将使用默认参数集`PatternParameterSet`。</span><span class="sxs-lookup"><span data-stu-id="09a07-139">When this parameter is specified, the cmdlet uses the default parameter set `PatternParameterSet`.</span></span> <span data-ttu-id="09a07-140">在这种情况下, 该 cmdlet 使用此处指定的模式来选择字符串。</span><span class="sxs-lookup"><span data-stu-id="09a07-140">In this case, the cmdlet uses the patterns specified here to select strings.</span></span> <span data-ttu-id="09a07-141">与`Script`此相反, 参数还可用于提供包含模式的脚本。</span><span class="sxs-lookup"><span data-stu-id="09a07-141">In contrast, the `Script` parameter could also be used to provide a script that contains the patterns.</span></span> <span data-ttu-id="09a07-142">`Script` 和`Pattern`参数定义两个单独的参数集, 因此它们互相排斥。</span><span class="sxs-lookup"><span data-stu-id="09a07-142">The `Script` and `Pattern` parameters define two separate parameter sets, so they are mutually exclusive.</span></span>

### <a name="declaring-search-support-parameters"></a><span data-ttu-id="09a07-143">声明搜索支持参数</span><span class="sxs-lookup"><span data-stu-id="09a07-143">Declaring Search Support Parameters</span></span>

<span data-ttu-id="09a07-144">此 cmdlet 定义以下支持参数, 这些参数可用于修改 cmdlet 的搜索功能。</span><span class="sxs-lookup"><span data-stu-id="09a07-144">This cmdlet defines the following support parameters that can be used to modify the search capabilities of the cmdlet.</span></span>

<span data-ttu-id="09a07-145">`Script`参数指定可用于为 cmdlet 提供备用搜索机制的脚本块。</span><span class="sxs-lookup"><span data-stu-id="09a07-145">The `Script` parameter specifies a script block that can be used to provide an alternate search mechanism for the cmdlet.</span></span> <span data-ttu-id="09a07-146">脚本必须包含用于匹配的模式, 并返回一个[system.web](/dotnet/api/System.Management.Automation.PSObject)对象。</span><span class="sxs-lookup"><span data-stu-id="09a07-146">The script must contain the patterns used for matching and return a [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) object.</span></span> <span data-ttu-id="09a07-147">请注意, 此参数也是用于标识`ScriptParameterSet`参数集的唯一参数。</span><span class="sxs-lookup"><span data-stu-id="09a07-147">Note that this parameter is also the unique parameter that identifies the `ScriptParameterSet` parameter set.</span></span> <span data-ttu-id="09a07-148">当 Windows PowerShell 运行时发现此参数时, 它仅使用属于`ScriptParameterSet`参数集的参数。</span><span class="sxs-lookup"><span data-stu-id="09a07-148">When the Windows PowerShell runtime sees this parameter, it uses only parameters that belong to the `ScriptParameterSet` parameter set.</span></span>

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
public ScriptBlock Script
{
  set { script = value; }
  get { return script; }
}
ScriptBlock script;
```

<span data-ttu-id="09a07-149">`SimpleMatch`参数是一个开关参数, 该参数指示 cmdlet 是否在提供时显式匹配模式。</span><span class="sxs-lookup"><span data-stu-id="09a07-149">The `SimpleMatch` parameter is a switch parameter that indicates whether the cmdlet is to explicitly match the patterns as they are supplied.</span></span> <span data-ttu-id="09a07-150">当用户在命令行 (`true`) 中指定参数时, 该 cmdlet 将在提供时使用模式。</span><span class="sxs-lookup"><span data-stu-id="09a07-150">When the user specifies the parameter at the command line (`true`), the cmdlet uses the patterns as they are supplied.</span></span> <span data-ttu-id="09a07-151">如果未指定参数 (`false`), 则 cmdlet 将使用正则表达式。</span><span class="sxs-lookup"><span data-stu-id="09a07-151">If the parameter is not specified (`false`), the cmdlet uses regular expressions.</span></span> <span data-ttu-id="09a07-152">此参数的默认值为`false`。</span><span class="sxs-lookup"><span data-stu-id="09a07-152">The default for this parameter is `false`.</span></span>

```csharp
[Parameter]
public SwitchParameter SimpleMatch
{
  get { return simpleMatch; }
  set { simpleMatch = value; }
}
private bool simpleMatch;
```

<span data-ttu-id="09a07-153">`CaseSensitive`参数是一个开关参数, 用于指示是否执行区分大小写的搜索。</span><span class="sxs-lookup"><span data-stu-id="09a07-153">The `CaseSensitive` parameter is a switch parameter that indicates whether a case-sensitive search is performed.</span></span> <span data-ttu-id="09a07-154">当用户在命令行 (`true`) 中指定参数时, 该 cmdlet 将在比较模式时检查字符的大小写。</span><span class="sxs-lookup"><span data-stu-id="09a07-154">When the user specifies the parameter at the command line (`true`), the cmdlet checks for the uppercase and lowercase of characters when comparing patterns.</span></span> <span data-ttu-id="09a07-155">如果未指定参数 (`false`), 则 cmdlet 不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="09a07-155">If the parameter is not specified (`false`), the cmdlet does not distinguish between uppercase and lowercase.</span></span> <span data-ttu-id="09a07-156">例如, "Myfile.txt" 和 "myfile.txt" 都将作为正命中返回。</span><span class="sxs-lookup"><span data-stu-id="09a07-156">For example "MyFile" and "myfile" would both be returned as positive hits.</span></span> <span data-ttu-id="09a07-157">此参数的默认值为`false`。</span><span class="sxs-lookup"><span data-stu-id="09a07-157">The default for this parameter is `false`.</span></span>

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

<span data-ttu-id="09a07-158">`Exclude` 和`Include`参数标识在搜索中显式排除或包括在搜索中的项。</span><span class="sxs-lookup"><span data-stu-id="09a07-158">The `Exclude` and `Include` parameters identify items that are explicitly excluded from or included in the search.</span></span> <span data-ttu-id="09a07-159">默认情况下, 该 cmdlet 将搜索数据存储区中的所有项。</span><span class="sxs-lookup"><span data-stu-id="09a07-159">By default, the cmdlet will search all items in the data store.</span></span> <span data-ttu-id="09a07-160">但是, 若要限制 cmdlet 执行的搜索, 可以使用这些参数来显式指示要包括在搜索中或省略的项。</span><span class="sxs-lookup"><span data-stu-id="09a07-160">However, to limit the search performed by the cmdlet, these parameters can be used to explicitly indicate items to be included in the search or omitted.</span></span>

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

```csharp
[Parameter]
[ValidateNotNullOrEmpty]
public string[] Include
{
  get
  {
    return includeStrings;
  }
  set
  {
    includeStrings = value;

    this.include = new WildcardPattern[includeStrings.Length];
    for (int i = 0; i < includeStrings.Length; i++)
    {
      this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
    }
  }
}

internal string[] includeStrings = null;
internal WildcardPattern[] include = null;
```

### <a name="declaring-parameter-sets"></a><span data-ttu-id="09a07-161">声明参数集</span><span class="sxs-lookup"><span data-stu-id="09a07-161">Declaring Parameter Sets</span></span>

<span data-ttu-id="09a07-162">此 cmdlet 使用两个参数集`ScriptParameterSet` ( `PatternParameterSet`默认值) 作为数据访问中使用的两个参数集的名称。</span><span class="sxs-lookup"><span data-stu-id="09a07-162">This cmdlet uses two parameter sets (`ScriptParameterSet` and `PatternParameterSet`, which is the default) as the names of two parameter sets used in data access.</span></span> <span data-ttu-id="09a07-163">`PatternParameterSet`默认参数集, 并且在指定`Pattern`参数时使用。</span><span class="sxs-lookup"><span data-stu-id="09a07-163">`PatternParameterSet` is the default parameter set and is used when the `Pattern` parameter is specified.</span></span> <span data-ttu-id="09a07-164">`ScriptParameterSet`当用户通过`Script`参数指定替代搜索机制时使用。</span><span class="sxs-lookup"><span data-stu-id="09a07-164">`ScriptParameterSet` is used when the user specifies an alternate search mechanism through the `Script` parameter.</span></span> <span data-ttu-id="09a07-165">有关参数集的详细信息, 请参阅[将参数集添加到 Cmdlet](./adding-parameter-sets-to-a-cmdlet.md)。</span><span class="sxs-lookup"><span data-stu-id="09a07-165">For more information about parameter sets, see [Adding Parameter Sets to a Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="09a07-166">重写输入处理方法</span><span class="sxs-lookup"><span data-stu-id="09a07-166">Overriding Input Processing Methods</span></span>

<span data-ttu-id="09a07-167">Cmdlet 必须重写[PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)类的一个或多个输入处理方法。</span><span class="sxs-lookup"><span data-stu-id="09a07-167">Cmdlets must override one or more of the input processing methods for the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span> <span data-ttu-id="09a07-168">有关输入处理方法的详细信息, 请参阅[创建第一个 Cmdlet](./creating-a-cmdlet-without-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="09a07-168">For more information about the input processing methods, see [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="09a07-169">此 cmdlet 将重写[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法, 以便在启动时生成已编译的正则表达式的数组。</span><span class="sxs-lookup"><span data-stu-id="09a07-169">This cmdlet overrides the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to build an array of compiled regular expressions at startup.</span></span> <span data-ttu-id="09a07-170">这会提高不使用简单匹配的搜索过程中的性能。</span><span class="sxs-lookup"><span data-stu-id="09a07-170">This increases performance during searches that do not use simple matching.</span></span>

```csharp
protected override void BeginProcessing()
{
  WriteDebug("Validating patterns.");
  if (patterns != null)
  {
    foreach(string pattern in patterns)
    {
      if (pattern == null)
      ThrowTerminatingError(new ErrorRecord(
                            new ArgumentNullException(
                            "Search pattern cannot be null."),
                            "NullSearchPattern",
                            ErrorCategory.InvalidArgument,
                            pattern)
                            );
    }

    WriteVerbose("Search pattern(s) are valid.");

    // If a simple match is not specified, then
    // compile the regular expressions once.
    if (!simpleMatch)
    {
      WriteDebug("Compiling search regular expressions.");

      RegexOptions regexOptions = RegexOptions.Compiled;
      if (!caseSensitive)
         regexOptions |= RegexOptions.Compiled;
      regexPattern = new Regex[patterns.Length];

      for (int i = 0; i < patterns.Length; i++)
      {
        try
        {
          regexPattern[i] = new Regex(patterns[i], regexOptions);
        }
        catch (ArgumentException ex)
        {
          ThrowTerminatingError(new ErrorRecord(
                        ex,
                        "InvalidRegularExpression",
                        ErrorCategory.InvalidArgument,
                        patterns[i]
                     ));
        }
      } //Loop through patterns to create RegEx objects.

      WriteVerbose("Pattern(s) compiled into regular expressions.");
    }// If not a simple match.

    // If a simple match is specified, then compile the
    // wildcard patterns once.
    else
    {
      WriteDebug("Compiling search wildcards.");

      WildcardOptions wildcardOptions = WildcardOptions.Compiled;

      if (!caseSensitive)
      {
        wildcardOptions |= WildcardOptions.IgnoreCase;
      }

      wildcardPattern = new WildcardPattern[patterns.Length];
      for (int i = 0; i < patterns.Length; i++)
      {
        wildcardPattern[i] =
                     new WildcardPattern(patterns[i], wildcardOptions);
      }

      WriteVerbose("Pattern(s) compiled into wildcard expressions.");
    }// If match is a simple match.
  }// If valid patterns are available.
}// End of function BeginProcessing().
```

<span data-ttu-id="09a07-171">此 cmdlet 还将重写[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法, 以处理用户在命令行上进行的字符串选择。</span><span class="sxs-lookup"><span data-stu-id="09a07-171">This cmdlet also overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the string selections that the user makes on the command line.</span></span> <span data-ttu-id="09a07-172">它通过调用私有**MatchString**方法, 以自定义对象的形式写入字符串选择的结果。</span><span class="sxs-lookup"><span data-stu-id="09a07-172">It writes the results of string selection in the form of a custom object by calling a private **MatchString** method.</span></span>

```csharp
protected override void ProcessRecord()
{
  UInt64 lineNumber = 0;
  MatchInfo result;
  ArrayList nonMatches = new ArrayList();

  // Walk the list of paths and search the contents for
  // any of the specified patterns.
  foreach (string psPath in paths)
  {
    // Once the filepaths are expanded, we may have more than one
    // path, so process all referenced paths.
    foreach(PathInfo path in
            SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
           )
    {
      WriteVerbose("Processing path " + path.Path);

      // Check if the path represents one of the items to be
      // excluded. If so, continue to next path.
      if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
         continue;

      // Get the content reader for the item(s) at the
      // specified path.
      Collection<IContentReader> readerCollection = null;
      try
      {
        readerCollection =
                    this.InvokeProvider.Content.GetReader(path.Path);
      }
      catch (PSNotSupportedException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "ContentAccessNotSupported",
                    ErrorCategory.NotImplemented,
                    path.Path)
                   );
        return;
      }

      foreach(IContentReader reader in readerCollection)
      {
        // Reset the line number for this path.
        lineNumber = 0;

        // Read in a single block (line in case of a file)
        // from the object.
        IList items = reader.Read(1);

        // Read and process one block(line) at a time until
        // no more blocks(lines) exist.
        while (items != null && items.Count == 1)
        {
          // Increment the line number each time a line is
          // processed.
          lineNumber++;

          String message = String.Format("Testing line {0} : {1}",
                                        lineNumber, items[0]);

          WriteDebug(message);

          result = SelectString(items[0]);

          if (result != null)
          {
            result.Path = path.Path;
            result.LineNumber = lineNumber;

            WriteObject(result);
          }
          else
          {
            // Add the block(line) that did not match to the
            // collection of non matches , which will be stored
            // in the SessionState variable $NonMatches
            nonMatches.Add(items[0]);
          }

          // Get the next line from the object.
          items = reader.Read(1);

        }// While loop for reading one line at a time.
      }// Foreach loop for reader collection.
    }// Foreach loop for processing referenced paths.
  }// Foreach loop for walking of path list.

  // Store the list of non-matches in the
  // session state variable $NonMatches.
  try
  {
    this.SessionState.PSVariable.Set("NonMatches", nonMatches);
  }
  catch (SessionStateUnauthorizedAccessException ex)
  {
    WriteError(new ErrorRecord(ex,
               "CannotWriteVariableNonMatches",
               ErrorCategory.InvalidOperation,
               nonMatches)
              );
  }

}// End of protected override void ProcessRecord().
```

## <a name="accessing-content"></a><span data-ttu-id="09a07-173">访问内容</span><span class="sxs-lookup"><span data-stu-id="09a07-173">Accessing Content</span></span>

<span data-ttu-id="09a07-174">你的 cmdlet 必须打开 Windows PowerShell 路径指示的提供程序, 以便它可以访问数据。</span><span class="sxs-lookup"><span data-stu-id="09a07-174">Your cmdlet must open the provider indicated by the Windows PowerShell path so that it can access the data.</span></span> <span data-ttu-id="09a07-175">运行空间的[Sessionstate](/dotnet/api/System.Management.Automation.SessionState)对象用于访问该提供程序, 而该 Cmdlet 的[PSCmdlet. Invokeprovider \*](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider)属性用于打开该提供程序时使用的属性。</span><span class="sxs-lookup"><span data-stu-id="09a07-175">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) object for the runspace is used for access to the provider, while the [System.Management.Automation.PSCmdlet.Invokeprovider\*](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider) property of the cmdlet is used to open the provider.</span></span> <span data-ttu-id="09a07-176">通过检索打开的提供程序的[Providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics)对象来提供对内容的访问。</span><span class="sxs-lookup"><span data-stu-id="09a07-176">Access to content is provided by retrieval of the [System.Management.Automation.Providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics) object for the provider opened.</span></span>

<span data-ttu-id="09a07-177">此示例 Select-Str cmdlet 使用[Providerintrinsics \*](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content)属性来公开要扫描的内容。</span><span class="sxs-lookup"><span data-stu-id="09a07-177">This sample Select-Str cmdlet uses the [System.Management.Automation.Providerintrinsics.Content\*](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content) property to expose the content to scan.</span></span> <span data-ttu-id="09a07-178">然后, 它可以调用[Contentcmdletproviderintrinsics. system.diagnostics.symbolstore.isymbolbinder1.getreader \*](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader)方法, 并传递所需的 Windows PowerShell 路径。</span><span class="sxs-lookup"><span data-stu-id="09a07-178">It can then call the [System.Management.Automation.Contentcmdletproviderintrinsics.Getreader\*](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader) method, passing the required Windows PowerShell path.</span></span>

## <a name="code-sample"></a><span data-ttu-id="09a07-179">代码示例</span><span class="sxs-lookup"><span data-stu-id="09a07-179">Code Sample</span></span>

<span data-ttu-id="09a07-180">下面的代码演示此版本的 Select-Str cmdlet 的实现。</span><span class="sxs-lookup"><span data-stu-id="09a07-180">The following code shows the implementation of this version of this Select-Str cmdlet.</span></span> <span data-ttu-id="09a07-181">请注意, 此代码包括 cmdlet、cmdlet 使用的私有方法和用于注册 cmdlet 的 Windows PowerShell 管理单元代码。</span><span class="sxs-lookup"><span data-stu-id="09a07-181">Note that this code includes the cmdlet class, private methods used by the cmdlet, and the Windows PowerShell snap-in code used to register the cmdlet.</span></span> <span data-ttu-id="09a07-182">有关注册 cmdlet 的详细信息, 请参阅[生成 cmdlet](#defining-the-cmdlet-class)。</span><span class="sxs-lookup"><span data-stu-id="09a07-182">For more information about registering the cmdlet, see [Building the Cmdlet](#defining-the-cmdlet-class).</span></span>

```csharp
//
// Copyright (c) 2006 Microsoft Corporation. All rights reserved.
//
// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
// PARTICULAR PURPOSE.
//
using System;
using System.Text.RegularExpressions;
using System.Collections;
using System.Collections.ObjectModel;
using System.Management.Automation;
using System.Management.Automation.Provider;
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{
  #region SelectStringCommand
  /// <summary>
  /// This cmdlet searches through PSObjects for particular patterns.
  /// </summary>
  /// <remarks>
  /// This cmdlet can be used to search any object, such as a file or a
  /// variable, whose provider exposes methods for reading and writing
  /// content.
  /// </remarks>
  [Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
  public class SelectStringCommand : PSCmdlet
  {
    #region Parameters
    /// <summary>
    /// Declare a Path parameter that specifies where the data is stored.
    /// This parameter must specify a PowerShell that indicates the
    /// PowerShell provider that is used to access the objects to be
    /// searched for matching patterns. This parameter should also have
    /// a PSPath alias to provide consistency with other cmdlets that use
    /// PowerShell providers.
    /// </summary>
    /// <value>Path of the object(s) to search.</value>
    [Parameter(
               Position = 0,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    [Parameter(
               Position = 0,
               ParameterSetName = "PatternParameterSet",
               ValueFromPipeline = true,
               Mandatory = true)]
               [Alias("PSPath")]
    public string[] Path
    {
      get { return paths; }
      set { paths = value; }
    }
    private string[] paths;

    /// <summary>
    /// Declare a Pattern parameter that specifies the pattern(s)
    /// used to find matching patterns in the string representation
    /// of the objects. A positive result will be returned
    /// if any of the patterns are found in the objects.
    /// </summary>
    /// <remarks>
    /// The patterns will be compiled into an array of wildcard
    /// patterns for a simple match (literal string matching),
    /// or the patterns will be converted into an array of compiled
    /// regular expressions.
    /// </remarks>
    /// <value>Array of patterns to search.</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "PatternParameterSet",
               Mandatory = true)]
    public string[] Pattern
    {
      get { return patterns; }
      set { patterns = value; }
    }
    private string[] patterns;
    private Regex[] regexPattern;
    private WildcardPattern[] wildcardPattern;

    /// <summary>
    /// Declare a Script parameter that specifies a script block
    /// that is called to perform the matching operations
    /// instead of the matching performed by the cmdlet.
    /// </summary>
    /// <value>Script block that will be called for matching</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    public ScriptBlock Script
    {
      set { script = value; }
      get { return script; }
    }
    ScriptBlock script;

    /// <summary>
    /// Declare a switch parameter that specifies if the pattern(s) are used
    /// literally. If not (default), searching is
    /// done using regular expressions.
    /// </summary>
    /// <value>If True, a literal pattern is used.</value>
    [Parameter]
    public SwitchParameter SimpleMatch
    {
      get { return simpleMatch; }
      set { simpleMatch = value; }
    }
    private bool simpleMatch;

    /// <summary>
    /// Declare a switch parameter that specifies if a case-sensitive
    /// search is performed.  If not (default), a case-insensitive search
    /// is performed.
    /// </summary>
    /// <value>If True, a case-sensitive search is made.</value>
    [Parameter]
    public SwitchParameter CaseSensitive
    {
      get { return caseSensitive; }
      set { caseSensitive = value; }
    }
    private bool caseSensitive;

    /// <summary>
    /// Declare an Include parameter that species which
    /// specific items are searched.  When this parameter
    /// is used, items that are not listed here are omitted
    /// from the search.
    /// </summary>
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Include
    {
      get
      {
        return includeStrings;
      }
      set
      {
        includeStrings = value;

        this.include = new WildcardPattern[includeStrings.Length];
        for (int i = 0; i < includeStrings.Length; i++)
        {
          this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }

    internal string[] includeStrings = null;
    internal WildcardPattern[] include = null;

    /// <summary>
    /// Declare an Exclude parameter that species which
    /// specific items are omitted from the search.
    /// </summary>
    ///
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Exclude
    {
      get
      {
        return excludeStrings;
      }
      set
      {
        excludeStrings = value;

        this.exclude = new WildcardPattern[excludeStrings.Length];
        for (int i = 0; i < excludeStrings.Length; i++)
        {
          this.exclude[i] = new WildcardPattern(excludeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }
    internal string[] excludeStrings;
    internal WildcardPattern[] exclude;

    #endregion Parameters

    #region Overrides
    /// <summary>
    /// If regular expressions are used for pattern matching,
    /// then build an array of compiled regular expressions
    /// at startup. This increases performance during scanning
    /// operations when simple matching is not used.
    /// </summary>
    protected override void BeginProcessing()
    {
      WriteDebug("Validating patterns.");
      if (patterns != null)
      {
        foreach(string pattern in patterns)
        {
          if (pattern == null)
          ThrowTerminatingError(new ErrorRecord(
                                new ArgumentNullException(
                                "Search pattern cannot be null."),
                                "NullSearchPattern",
                                ErrorCategory.InvalidArgument,
                                pattern)
                                );
        }

        WriteVerbose("Search pattern(s) are valid.");

        // If a simple match is not specified, then
        // compile the regular expressions once.
        if (!simpleMatch)
        {
          WriteDebug("Compiling search regular expressions.");

          RegexOptions regexOptions = RegexOptions.Compiled;
          if (!caseSensitive)
             regexOptions |= RegexOptions.Compiled;
          regexPattern = new Regex[patterns.Length];

          for (int i = 0; i < patterns.Length; i++)
          {
            try
            {
              regexPattern[i] = new Regex(patterns[i], regexOptions);
            }
            catch (ArgumentException ex)
            {
              ThrowTerminatingError(new ErrorRecord(
                            ex,
                            "InvalidRegularExpression",
                            ErrorCategory.InvalidArgument,
                            patterns[i]
                         ));
            }
          } //Loop through patterns to create RegEx objects.

          WriteVerbose("Pattern(s) compiled into regular expressions.");
        }// If not a simple match.

        // If a simple match is specified, then compile the
        // wildcard patterns once.
        else
        {
          WriteDebug("Compiling search wildcards.");

          WildcardOptions wildcardOptions = WildcardOptions.Compiled;

          if (!caseSensitive)
          {
            wildcardOptions |= WildcardOptions.IgnoreCase;
          }

          wildcardPattern = new WildcardPattern[patterns.Length];
          for (int i = 0; i < patterns.Length; i++)
          {
            wildcardPattern[i] =
                         new WildcardPattern(patterns[i], wildcardOptions);
          }

          WriteVerbose("Pattern(s) compiled into wildcard expressions.");
        }// If match is a simple match.
      }// If valid patterns are available.
    }// End of function BeginProcessing().

    /// <summary>
    /// Process the input and search for the specified patterns.
    /// </summary>
    protected override void ProcessRecord()
    {
      UInt64 lineNumber = 0;
      MatchInfo result;
      ArrayList nonMatches = new ArrayList();

      // Walk the list of paths and search the contents for
      // any of the specified patterns.
      foreach (string psPath in paths)
      {
        // Once the filepaths are expanded, we may have more than one
        // path, so process all referenced paths.
        foreach(PathInfo path in
                SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
               )
        {
          WriteVerbose("Processing path " + path.Path);

          // Check if the path represents one of the items to be
          // excluded. If so, continue to next path.
          if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
             continue;

          // Get the content reader for the item(s) at the
          // specified path.
          Collection<IContentReader> readerCollection = null;
          try
          {
            readerCollection =
                        this.InvokeProvider.Content.GetReader(path.Path);
          }
          catch (PSNotSupportedException ex)
          {
            WriteError(new ErrorRecord(ex,
                       "ContentAccessNotSupported",
                        ErrorCategory.NotImplemented,
                        path.Path)
                       );
            return;
          }

          foreach(IContentReader reader in readerCollection)
          {
            // Reset the line number for this path.
            lineNumber = 0;

            // Read in a single block (line in case of a file)
            // from the object.
            IList items = reader.Read(1);

            // Read and process one block(line) at a time until
            // no more blocks(lines) exist.
            while (items != null && items.Count == 1)
            {
              // Increment the line number each time a line is
              // processed.
              lineNumber++;

              String message = String.Format("Testing line {0} : {1}",
                                            lineNumber, items[0]);

              WriteDebug(message);

              result = SelectString(items[0]);

              if (result != null)
              {
                result.Path = path.Path;
                result.LineNumber = lineNumber;

                WriteObject(result);
              }
              else
              {
                // Add the block(line) that did not match to the
                // collection of non matches , which will be stored
                // in the SessionState variable $NonMatches
                nonMatches.Add(items[0]);
              }

              // Get the next line from the object.
              items = reader.Read(1);

            }// While loop for reading one line at a time.
          }// Foreach loop for reader collection.
        }// Foreach loop for processing referenced paths.
      }// Foreach loop for walking of path list.

      // Store the list of non-matches in the
      // session state variable $NonMatches.
      try
      {
        this.SessionState.PSVariable.Set("NonMatches", nonMatches);
      }
      catch (SessionStateUnauthorizedAccessException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "CannotWriteVariableNonMatches",
                   ErrorCategory.InvalidOperation,
                   nonMatches)
                  );
      }

    }// End of protected override void ProcessRecord().
    #endregion Overrides

    #region PrivateMethods
    /// <summary>
    /// Check for a match using the input string and the pattern(s)
    /// specified.
    /// </summary>
    /// <param name="input">The string to test.</param>
    /// <returns>MatchInfo object containing information about
    /// result of a match</returns>
    private MatchInfo SelectString(object input)
    {
      string line = null;

      try
      {
        // Convert the object to a string type
        // safely using language support methods
        line = (string)LanguagePrimitives.ConvertTo(
                                                    input,
                                                    typeof(string)
                                                    );
        line = line.Trim(' ','\t');
      }
      catch (PSInvalidCastException ex)
      {
        WriteError(new ErrorRecord(
                   ex,
                   "CannotCastObjectToString",
                   ErrorCategory.InvalidOperation,
                   input)
                   );

        return null;
      }

      MatchInfo result = null;

      // If a scriptblock has been specified, call it
      // with the path for processing.  It will return
      // one object.
      if (script != null)
      {
        WriteDebug("Executing script block.");

        Collection<PSObject> psObjects =
                             script.Invoke(
                                           line,
                                           simpleMatch,
                                           caseSensitive
                                          );

        foreach (PSObject psObject in psObjects)
        {
          if (LanguagePrimitives.IsTrue(psObject))
          {
            result = new MatchInfo();
            result.Line = line;
            result.IgnoreCase = !caseSensitive;

            break;
          } //End of If.
        } //End ForEach loop.
      } // End of If if script exists.

      // If script block exists, see if this line matches any
      // of the match patterns.
      else
      {
        int patternIndex = 0;

        while (patternIndex < patterns.Length)
        {
          if ((simpleMatch &&
              wildcardPattern[patternIndex].IsMatch(line))
              || (regexPattern != null
              && regexPattern[patternIndex].IsMatch(line))
             )
          {
            result = new MatchInfo();
            result.IgnoreCase = !caseSensitive;
            result.Line = line;
            result.Pattern = patterns[patternIndex];

            break;
          }

          patternIndex++;

        }// While loop through patterns.
      }// Else for no script block specified.

      return result;

    }// End of SelectString

    /// <summary>
    /// Check whether the supplied name meets the include/exclude criteria.
    /// That is - it's on the include list if the include list was
    /// specified, and not on the exclude list if the exclude list was specified.
    /// </summary>
    /// <param name="path">path to validate</param>
    /// <returns>True if the path is acceptable.</returns>
    private bool MeetsIncludeExcludeCriteria(string path)
    {
      bool ok = false;

      // See if the file is on the include list.
      if (this.include != null)
      {
        foreach (WildcardPattern patternItem in this.include)
        {
          if (patternItem.IsMatch(path))
          {
            ok = true;
            break;
          }
        }
      }
      else
      {
        ok = true;
      }

      if (!ok)
         return false;

      // See if the file is on the exclude list.
      if (this.exclude != null)
      {
        foreach (WildcardPattern patternItem in this.exclude)
        {
          if (patternItem.IsMatch(path))
          {
            ok = false;
            break;
          }
        }
      }

      return ok;
    } //MeetsIncludeExcludeCriteria
    #endregion Private Methods

  }// class SelectStringCommand

  #endregion SelectStringCommand

  #region MatchInfo

  /// <summary>
  /// Class representing the result of a pattern/literal match
  /// that is passed through the pipeline by the Select-Str cmdlet.
  /// </summary>
  public class MatchInfo
  {
    /// <summary>
    /// Indicates if the match was done ignoring case.
    /// </summary>
    /// <value>True if case was ignored.</value>
    public bool IgnoreCase
    {
      get { return ignoreCase; }
      set { ignoreCase = value; }
    }
    private bool ignoreCase;

    /// <summary>
    /// Specifies the number of the matching line.
    /// </summary>
    /// <value>The number of the matching line.</value>
    public UInt64 LineNumber
    {
      get { return lineNumber; }
      set { lineNumber = value; }
    }
    private UInt64 lineNumber;

    /// <summary>
    /// Specifies the text of the matching line.
    /// </summary>
    /// <value>The text of the matching line.</value>
    public string Line
    {
      get { return line; }
      set { line = value; }
    }
    private string line;

    /// <summary>
    /// Specifies the full path of the object(file) containing the
    /// matching line.
    /// </summary>
    /// <remarks>
    /// It will be "inputStream" if the object came from the input
    /// stream.
    /// </remarks>
    /// <value>The path name</value>
    public string Path
    {
      get { return path; }
      set
      {
        pathSet = true;
        path = value;
      }
    }
    private string path;
    private bool pathSet;

    /// <summary>
    /// Specifies the pattern that was used in the match.
    /// </summary>
    /// <value>The pattern string</value>
    public string Pattern
    {
      get { return pattern; }
      set { pattern = value; }
    }
    private string pattern;

    private const string MatchFormat = "{0}:{1}:{2}";

    /// <summary>
    /// Returns the string representation of this object. The format
    /// depends on whether a path has been set for this object or
    /// not.
    /// </summary>
    /// <remarks>
    /// If the path component is set, as would be the case when
    /// matching in a file, ToString() returns the path, line
    /// number and line text.  If path is not set, then just the
    /// line text is presented.
    /// </remarks>
    /// <returns>The string representation of the match object.</returns>
    public override string ToString()
    {
      if (pathSet)
         return String.Format(
         System.Threading.Thread.CurrentThread.CurrentCulture,
         MatchFormat,
         this.path,
         this.lineNumber,
         this.line
         );
      else
         return this.line;
    }
  }// End class MatchInfo

  #endregion

  #region PowerShell snap-in

  /// <summary>
  /// Create a PowerShell snap-in for the Select-Str cmdlet.
  /// </summary>
  [RunInstaller(true)]
  public class SelectStringPSSnapIn : PSSnapIn
  {
    /// <summary>
    /// Create an instance of the SelectStrPSSnapin class.
    /// </summary>
    public SelectStringPSSnapIn()
           : base()
    {
    }

    /// <summary>
    /// Specify the name of the PowerShell snap-in.
    /// </summary>
    public override string Name
    {
      get
      {
        return "SelectStrPSSnapIn";
      }
    }

    /// <summary>
    /// Specify the vendor of the PowerShell snap-in.
    /// </summary>
    public override string Vendor
    {
      get
      {
        return "Microsoft";
      }
    }

    /// <summary>
    /// Specify the localization resource information for the vendor.
    /// Use the format: SnapinName,VendorName.
    /// </summary>
    public override string VendorResource
    {
      get
      {
        return "SelectStrSnapIn,Microsoft";
      }
    }

    /// <summary>
    /// Specify the description of the PowerShell snap-in.
    /// </summary>
    public override string Description
    {
      get
        {
          return "This is a PowerShell snap-in for the Select-Str cmdlet.";
        }
    }

    /// <summary>
    /// Specify the localization resource information for the description.
    /// Use the format: SnapinName,Description.

    /// </summary>
    public override string DescriptionResource
    {
      get
      {
          return "SelectStrSnapIn,This is a PowerShell snap-in for the Select-Str cmdlet.";
      }
    }
  }
  #endregion PowerShell snap-in

} //namespace Microsoft.Samples.PowerShell.Commands;
```

## <a name="building-the-cmdlet"></a><span data-ttu-id="09a07-183">构建 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="09a07-183">Building the Cmdlet</span></span>

<span data-ttu-id="09a07-184">实现 cmdlet 后, 必须通过 Windows PowerShell 管理单元将其注册到 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="09a07-184">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="09a07-185">有关注册 cmdlet 的详细信息, 请参阅[如何注册 cmdlet、提供程序和主机应用程序](/previous-versions//ms714644(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="09a07-185">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="09a07-186">测试 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="09a07-186">Testing the Cmdlet</span></span>

<span data-ttu-id="09a07-187">向 Windows PowerShell 注册 cmdlet 后, 可以通过在命令行上运行 cmdlet 来对其进行测试。</span><span class="sxs-lookup"><span data-stu-id="09a07-187">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="09a07-188">以下过程可用于测试示例 Select-Str cmdlet。</span><span class="sxs-lookup"><span data-stu-id="09a07-188">The following procedure can be used to test the sample Select-Str cmdlet.</span></span>

1. <span data-ttu-id="09a07-189">启动 Windows PowerShell, 在 Notes 文件中搜索表达式为 ".NET" 的行。</span><span class="sxs-lookup"><span data-stu-id="09a07-189">Start Windows PowerShell, and search the Notes file for occurrences of lines with the expression ".NET".</span></span> <span data-ttu-id="09a07-190">请注意, 仅当路径包含多个单词时, 才需要在路径名称两侧加上引号。</span><span class="sxs-lookup"><span data-stu-id="09a07-190">Note that the quotation marks around the name of the path are required only if the path consists of more than one word.</span></span>

    ```powershell
    select-str -Path "notes" -Pattern ".NET" -SimpleMatch=$false
    ```

    <span data-ttu-id="09a07-191">此时将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="09a07-191">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 8
    Line         : Because Windows PowerShell works directly with .NET objects, there is often a .NET object
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    IgnoreCase   : True
    LineNumber   : 21
    Line         : You should normally define the class for a cmdlet in a .NET namespace
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    ```

2. <span data-ttu-id="09a07-192">在 Notes 文件中搜索单词 "over" 后跟任何其他文本的行。</span><span class="sxs-lookup"><span data-stu-id="09a07-192">Search the Notes file for occurrences of lines with the word "over", followed by any other text.</span></span> <span data-ttu-id="09a07-193">参数使用的默认`false`值。 `SimpleMatch`</span><span class="sxs-lookup"><span data-stu-id="09a07-193">The `SimpleMatch` parameter is using the default value of `false`.</span></span> <span data-ttu-id="09a07-194">搜索不区分大小写, 因为`CaseSensitive`参数设置为。 `false`</span><span class="sxs-lookup"><span data-stu-id="09a07-194">The search is case-insensitive because the `CaseSensitive` parameter is set to `false`.</span></span>

    ```powershell
    select-str -Path notes -Pattern "over*" -SimpleMatch -CaseSensitive:$false
    ```

    <span data-ttu-id="09a07-195">此时将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="09a07-195">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 45
    Line         : Override StopProcessing
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    IgnoreCase   : True
    LineNumber   : 49
    Line         : overriding the StopProcessing method
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    ```

3. <span data-ttu-id="09a07-196">使用正则表达式作为模式搜索说明文件。</span><span class="sxs-lookup"><span data-stu-id="09a07-196">Search the Notes file using a regular expression as the pattern.</span></span> <span data-ttu-id="09a07-197">Cmdlet 将搜索括在括号中的字母字符和空格。</span><span class="sxs-lookup"><span data-stu-id="09a07-197">The cmdlet searches for alphabetical characters and blank spaces enclosed in parentheses.</span></span>

    ```powershell
    select-str -Path notes -Pattern "\([A-Za-z:blank:]" -SimpleMatch:$false
    ```

    <span data-ttu-id="09a07-198">此时将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="09a07-198">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : Advisory Guidelines (Consider Following)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    IgnoreCase   : True
    LineNumber   : 53
    Line         : If your cmdlet has objects that are not disposed of (written to the pipeline)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    ```

4. <span data-ttu-id="09a07-199">对说明文件执行区分大小写的搜索, 查找单词 "Parameter" 的匹配项。</span><span class="sxs-lookup"><span data-stu-id="09a07-199">Perform a case-sensitive search of the Notes file for occurrences of the word "Parameter".</span></span>

    ```powershell
    select-str -Path notes -Pattern Parameter -CaseSensitive
    ```

    <span data-ttu-id="09a07-200">此时将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="09a07-200">The following output appears.</span></span>

    ```output
    IgnoreCase   : False
    LineNumber   : 6
    Line         : Support an InputObject Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    IgnoreCase   : False
    LineNumber   : 30
    Line         : Support Force Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    ```

5. <span data-ttu-id="09a07-201">搜索随 Windows PowerShell 提供的变量提供程序, 获取数值介于0到9之间的变量。</span><span class="sxs-lookup"><span data-stu-id="09a07-201">Search the variable provider shipped with Windows PowerShell for variables that have numerical values from 0 through 9.</span></span>

    ```powershell
    select-str -Path * -Pattern "[0-9]"
    ```

    <span data-ttu-id="09a07-202">此时将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="09a07-202">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : 64
    Path         : Variable:\MaximumHistoryCount
    Pattern      : [0-9]
    ```

6. <span data-ttu-id="09a07-203">使用脚本块在文件 SelectStrCommandSample.cs 中搜索字符串 "Pos"。</span><span class="sxs-lookup"><span data-stu-id="09a07-203">Use a script block to search the file SelectStrCommandSample.cs for the string "Pos".</span></span> <span data-ttu-id="09a07-204">脚本的**cmatch**函数执行不区分大小写的模式匹配。</span><span class="sxs-lookup"><span data-stu-id="09a07-204">The **cmatch** function for the script performs a case-insensitive pattern match.</span></span>

    ```powershell
    select-str -Path "SelectStrCommandSample.cs" -Script { if ($args[0] -cmatch "Pos"){ return $true } return $false }
    ```

    <span data-ttu-id="09a07-205">此时将显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="09a07-205">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 37
    Line         :    Position = 0.
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\SelectStrCommandSample.cs
    Pattern      :
    ```

## <a name="see-also"></a><span data-ttu-id="09a07-206">另请参阅</span><span class="sxs-lookup"><span data-stu-id="09a07-206">See Also</span></span>

[<span data-ttu-id="09a07-207">如何创建 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="09a07-207">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[<span data-ttu-id="09a07-208">创建第一个 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="09a07-208">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="09a07-209">创建修改系统的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="09a07-209">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="09a07-210">设计你的 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="09a07-210">Design Your Windows PowerShell Provider</span></span>](../prog-guide/designing-your-windows-powershell-provider.md)

<span data-ttu-id="09a07-211">[Windows PowerShell 的工作原理](/previous-versions//ms714658(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="09a07-211">[How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85))</span></span>

<span data-ttu-id="09a07-212">[如何注册 Cmdlet、提供程序和主机应用程序](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="09a07-212">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="09a07-213">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="09a07-213">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
