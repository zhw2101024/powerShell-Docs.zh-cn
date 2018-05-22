---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 9aa7e92632c671751020687ddbfc374eeda7148b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
---
# <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="d071f-102">PowerShell 5.0 中的新语言功能</span><span class="sxs-lookup"><span data-stu-id="d071f-102">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="d071f-103">PowerShell 5.0 引入了以下 Windows PowerShell 中的新语言元素：</span><span class="sxs-lookup"><span data-stu-id="d071f-103">PowerShell 5.0 introduces the following new language elements in Windows PowerShell:</span></span>

## <a name="class-keyword"></a><span data-ttu-id="d071f-104">Class 关键字</span><span class="sxs-lookup"><span data-stu-id="d071f-104">Class keyword</span></span>

<span data-ttu-id="d071f-105">**class** 关键字定义了一个新类。</span><span class="sxs-lookup"><span data-stu-id="d071f-105">The **class** keyword defines a new class.</span></span> <span data-ttu-id="d071f-106">这是真正的 .NET Framework 类型。</span><span class="sxs-lookup"><span data-stu-id="d071f-106">This is a true .NET Framework type.</span></span>
<span data-ttu-id="d071f-107">Class 成员是公开的，但仅在模块作用域内公开。</span><span class="sxs-lookup"><span data-stu-id="d071f-107">Class members are public, but only public within the module scope.</span></span>
<span data-ttu-id="d071f-108">不能引用类型名称作为字符串（例如，`New-Object` 不起作用），并且在此版本中，也不能在该类定义的脚本/模块外部使用类型文本（例如，`[MyClass]`）。</span><span class="sxs-lookup"><span data-stu-id="d071f-108">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script/module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="d071f-109">Enum 关键字和枚举</span><span class="sxs-lookup"><span data-stu-id="d071f-109">Enum keyword and enumerations</span></span>

<span data-ttu-id="d071f-110">已添加对 **enum** 关键字的支持，它使用换行符作为分隔符。</span><span class="sxs-lookup"><span data-stu-id="d071f-110">Support for the **enum** keyword has been added, which uses newline as the delimiter.</span></span>
<span data-ttu-id="d071f-111">当前局限：不能就枚举器本身定义枚举器，但可以根据另一个枚举初始化某个枚举，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="d071f-111">Current limitations: you cannot define an enumerator in terms of itself, but you can initialize an enum in terms of another enum, as shown in the following example.</span></span>
<span data-ttu-id="d071f-112">此外，当前不能指定基类型；它始终是 [int]。</span><span class="sxs-lookup"><span data-stu-id="d071f-112">Also, the base type cannot currently be specified; it is always [int].</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="d071f-113">枚举器值必须是分析时间常量；不能将其设置为调用命令的结果。</span><span class="sxs-lookup"><span data-stu-id="d071f-113">An enumerator value must be a parse time constant; you cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="d071f-114">枚举支持算术运算，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="d071f-114">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

## <a name="import-dscresource"></a><span data-ttu-id="d071f-115">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="d071f-115">Import-DscResource</span></span>

<span data-ttu-id="d071f-116">**Import-DscResource** 现在是一个真正的动态关键字。</span><span class="sxs-lookup"><span data-stu-id="d071f-116">**Import-DscResource** is now a true dynamic keyword.</span></span>
<span data-ttu-id="d071f-117">PowerShell 用于分析指定的模块的根模块，搜索包含 **DscResource** 属性的类。</span><span class="sxs-lookup"><span data-stu-id="d071f-117">PowerShell parses the specified module’s root module, searching for classes that contain the **DscResource** attribute.</span></span>

## <a name="implementingassembly"></a><span data-ttu-id="d071f-118">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="d071f-118">ImplementingAssembly</span></span>

<span data-ttu-id="d071f-119">已将新字段 **ImplementingAssembly** 添加到了 ModuleInfo。</span><span class="sxs-lookup"><span data-stu-id="d071f-119">A new field, **ImplementingAssembly**, has been added to ModuleInfo.</span></span> <span data-ttu-id="d071f-120">如果脚本模块定义类，或者二进制模块的加载程序集，则会将此字段设置为为脚本模块创建的动态程序集。</span><span class="sxs-lookup"><span data-stu-id="d071f-120">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="d071f-121">当 ModuleType = Manifest 时，不会对该字段进行设置。</span><span class="sxs-lookup"><span data-stu-id="d071f-121">It is not set when ModuleType = Manifest.</span></span>

<span data-ttu-id="d071f-122">**ImplementingAssembly** 字段上的反射可发现模块中的资源。</span><span class="sxs-lookup"><span data-stu-id="d071f-122">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="d071f-123">这意味着你可以发现用 PowerShell 或其他托管语言编写的资源。</span><span class="sxs-lookup"><span data-stu-id="d071f-123">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="d071f-124">具有初始值设定项的字段：</span><span class="sxs-lookup"><span data-stu-id="d071f-124">Fields with initializers:</span></span>

```powershell
[int] $i = 5
```

<span data-ttu-id="d071f-125">支持静态；其工作原理类似属性，类型约束也是如此，因此它可以按任意顺序指定。</span><span class="sxs-lookup"><span data-stu-id="d071f-125">Static is supported; it works like an attribute, as do the type constraints, so it can be specified in any order.</span></span>

```powershell
static [int] $count = 0
```

<span data-ttu-id="d071f-126">可选类型。</span><span class="sxs-lookup"><span data-stu-id="d071f-126">A type is optional.</span></span>

```powershell
$s = "hello"
```

<span data-ttu-id="d071f-127">所有成员都是公开的。</span><span class="sxs-lookup"><span data-stu-id="d071f-127">All members are public.</span></span>

## <a name="constructors-and-instantiation"></a><span data-ttu-id="d071f-128">构造函数和实例化</span><span class="sxs-lookup"><span data-stu-id="d071f-128">Constructors and instantiation</span></span>

<span data-ttu-id="d071f-129">Windows PowerShell 类具有很多构造函数。它们具有与其类相同的名称。</span><span class="sxs-lookup"><span data-stu-id="d071f-129">Windows PowerShell classes can have constructors; they have the same name as their class.</span></span> <span data-ttu-id="d071f-130">这些构造函数可进行重载。</span><span class="sxs-lookup"><span data-stu-id="d071f-130">Constructors can be overloaded.</span></span> <span data-ttu-id="d071f-131">支持静态构造函数。</span><span class="sxs-lookup"><span data-stu-id="d071f-131">Static constructors are supported.</span></span> <span data-ttu-id="d071f-132">在运行构造函数中的任何代码之前，将初始化具有初始化表达式的属性。</span><span class="sxs-lookup"><span data-stu-id="d071f-132">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="d071f-133">静态属性在静态构造函数的主体之前进行初始化，而实例属性则在非静态构造函数的主体之前进行初始化。</span><span class="sxs-lookup"><span data-stu-id="d071f-133">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="d071f-134">目前，没有用于从另一个构造函数中调用某个构造函数的语法（例如，C\# 语法“: this()”）。</span><span class="sxs-lookup"><span data-stu-id="d071f-134">Currently, there is no syntax for calling a constructor from another constructor (like the C\# syntax ": this()").</span></span> <span data-ttu-id="d071f-135">解决方法是定义一种常用的 Init 方法。</span><span class="sxs-lookup"><span data-stu-id="d071f-135">The workaround is to define a common Init method.</span></span>

<span data-ttu-id="d071f-136">下面是此版本中的实例化类的方法。</span><span class="sxs-lookup"><span data-stu-id="d071f-136">The following are ways of instantiating classes in this release.</span></span>

<span data-ttu-id="d071f-137">使用默认构造函数实例化。</span><span class="sxs-lookup"><span data-stu-id="d071f-137">Instantiating by using the default constructor.</span></span> <span data-ttu-id="d071f-138">请注意，此版本不支持 New-Object。</span><span class="sxs-lookup"><span data-stu-id="d071f-138">Note that New-Object is not supported in this release.</span></span>

```powershell
$a = [MyClass]::new()
```

<span data-ttu-id="d071f-139">调用带参数的构造函数</span><span class="sxs-lookup"><span data-stu-id="d071f-139">Calling a constructor with a parameter</span></span>

```powershell
$b = [MyClass]::new(42)
```

<span data-ttu-id="d071f-140">将数组传递给带多个参数的构造函数</span><span class="sxs-lookup"><span data-stu-id="d071f-140">Passing an array to a constructor with multiple parameters</span></span>
```powershell
$c = [MyClass]::new(@(42,43,44), "Hello")
```

<span data-ttu-id="d071f-141">在此版本中，New-Object 不适用于 Windows PowerShell 中定义的类。</span><span class="sxs-lookup"><span data-stu-id="d071f-141">In this release, New-Object does not work with classes defined in Windows PowerShell.</span></span> <span data-ttu-id="d071f-142">此外对于此版本，类型名称只在词法上可见，意思是在定义类的模块或脚本外部不可见。</span><span class="sxs-lookup"><span data-stu-id="d071f-142">Also for this release, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="d071f-143">函数可以返回 Windows PowerShell 中定义的类的实例，并且实例在模块或脚本外部也同样有效。</span><span class="sxs-lookup"><span data-stu-id="d071f-143">Functions can return instances of a class defined in Windows PowerShell, and instances work well outside of the module or script.</span></span>

<span data-ttu-id="d071f-144">`Get-Member -Static` 列出了构造函数，以便你可以像任何其他方法一样查看重载。</span><span class="sxs-lookup"><span data-stu-id="d071f-144">`Get-Member -Static` lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="d071f-145">此语法的性能比 New-Object 快得多。</span><span class="sxs-lookup"><span data-stu-id="d071f-145">The performance of this syntax is also considerably faster than New-Object.</span></span>

<span data-ttu-id="d071f-146">名为 **new** 的伪静态方法适用于 .NET 类型，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="d071f-146">The pseudo-static method named **new** works with .NET types, as shown in the following example.</span></span>

```powershell
[hashtable]::new()
```

<span data-ttu-id="d071f-147">你现在可以使用 Get-member 查看构造函数重载，或如此示例所示：</span><span class="sxs-lookup"><span data-stu-id="d071f-147">You can now see constructor overloads with Get-Member, or as shown in this example:</span></span>

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

## <a name="methods"></a><span data-ttu-id="d071f-148">方法</span><span class="sxs-lookup"><span data-stu-id="d071f-148">Methods</span></span>

<span data-ttu-id="d071f-149">Windows PowerShell 类方法被实现为仅有一个结束块的 ScriptBlock。</span><span class="sxs-lookup"><span data-stu-id="d071f-149">A Windows PowerShell class method is implemented as a ScriptBlock that has only an end block.</span></span> <span data-ttu-id="d071f-150">所有方法都是公开的。</span><span class="sxs-lookup"><span data-stu-id="d071f-150">All methods are public.</span></span> <span data-ttu-id="d071f-151">下面介绍了定义一个名为 **DoSomething** 的方法的示例。</span><span class="sxs-lookup"><span data-stu-id="d071f-151">The following shows an example of defining a method named **DoSomething**.</span></span>

```powershell
class MyClass
{
    DoSomething($x)
    {
        $this._doSomething($x) # method syntax
    }
    private _doSomething($a) {}
}
```

<span data-ttu-id="d071f-152">方法调用：</span><span class="sxs-lookup"><span data-stu-id="d071f-152">Method invocation:</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

<span data-ttu-id="d071f-153">还支持重载方法（即，那些与现有方法命名相同，但由其指定的值进行区分的方法）。</span><span class="sxs-lookup"><span data-stu-id="d071f-153">Overloaded methods--that is, those that are named the same as an existing method, but differentiated by their specified values--are also supported.</span></span>

## <a name="properties"></a><span data-ttu-id="d071f-154">“属性”</span><span class="sxs-lookup"><span data-stu-id="d071f-154">Properties</span></span>

<span data-ttu-id="d071f-155">所有属性都是公开的。</span><span class="sxs-lookup"><span data-stu-id="d071f-155">All properties are public.</span></span> <span data-ttu-id="d071f-156">属性要求使用换行符或分号。</span><span class="sxs-lookup"><span data-stu-id="d071f-156">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="d071f-157">如果未指定任何对象类型，则该属性类型是对象。</span><span class="sxs-lookup"><span data-stu-id="d071f-157">If no object type is specified, the property type is object.</span></span>

<span data-ttu-id="d071f-158">使用验证属性或参数转换属性的属性（例如 `[ValidateSet("aaa")]`）按预期方式运行。</span><span class="sxs-lookup"><span data-stu-id="d071f-158">Properties that use validation attributes or argument transformation attributes (e.g. `[ValidateSet("aaa")]`) work as expected.</span></span>

## <a name="hidden"></a><span data-ttu-id="d071f-159">Hidden</span><span class="sxs-lookup"><span data-stu-id="d071f-159">Hidden</span></span>

<span data-ttu-id="d071f-160">已添加新的关键字 **Hidden**。</span><span class="sxs-lookup"><span data-stu-id="d071f-160">A new keyword, **Hidden**, has been added.</span></span> <span data-ttu-id="d071f-161">**Hidden** 可应用于属性和方法（包括构造函数）。</span><span class="sxs-lookup"><span data-stu-id="d071f-161">**Hidden** can be applied to properties and methods (including constructors).</span></span>

<span data-ttu-id="d071f-162">Hidden 成员是公开的，除非添加了 -Force 参数，否则不出现在 Get-member 的输出中。</span><span class="sxs-lookup"><span data-stu-id="d071f-162">Hidden members are public, but do not appear in the output of Get-Member unless the -Force parameter is added.</span></span>

<span data-ttu-id="d071f-163">当选项卡完成或使用 Intellisense 时，除非完成发生在定义 Hidden 成员的类中，否则不包括 Hidden 成员。</span><span class="sxs-lookup"><span data-stu-id="d071f-163">Hidden members are not included when tab completing or using Intellisense unless the completion occurs in the class defining the hidden member.</span></span>

<span data-ttu-id="d071f-164">已添加新的属性 **System.Management.Automation.HiddenAttribute**，以便 C# 代码可以在 Windows PowerShell 中具有相同的语义。</span><span class="sxs-lookup"><span data-stu-id="d071f-164">A new attribute, **System.Management.Automation.HiddenAttribute** has been added so that C# code can have the same semantics within Windows PowerShell.</span></span>

## <a name="return-types"></a><span data-ttu-id="d071f-165">返回类型</span><span class="sxs-lookup"><span data-stu-id="d071f-165">Return types</span></span>

<span data-ttu-id="d071f-166">返回类型是一种构造；返回值将被转换为预期类型。</span><span class="sxs-lookup"><span data-stu-id="d071f-166">Return type is a contract; the return value is converted to the expected type.</span></span> <span data-ttu-id="d071f-167">如果没有指定返回类型，则返回类型为 void。</span><span class="sxs-lookup"><span data-stu-id="d071f-167">If no return type is specified, the return type is void.</span></span> <span data-ttu-id="d071f-168">没有对象流；不能有意或无意将对象写入管道。</span><span class="sxs-lookup"><span data-stu-id="d071f-168">There is no streaming of objects; objects cannot be written to the pipeline either intentionally or by accident.</span></span>

## <a name="attributes"></a><span data-ttu-id="d071f-169">属性</span><span class="sxs-lookup"><span data-stu-id="d071f-169">Attributes</span></span>

<span data-ttu-id="d071f-170">添加了 **DscResource** 和 **DscProperty** 这两个新属性。</span><span class="sxs-lookup"><span data-stu-id="d071f-170">Two new attributes, **DscResource** and **DscProperty** have been added.</span></span>

## <a name="lexical-scoping-of-variables"></a><span data-ttu-id="d071f-171">变量的词法作用域</span><span class="sxs-lookup"><span data-stu-id="d071f-171">Lexical scoping of variables</span></span>

<span data-ttu-id="d071f-172">下例介绍了词法作用域在此版本中的工作原理。</span><span class="sxs-lookup"><span data-stu-id="d071f-172">The following shows an example of how lexical scoping works in this release.</span></span>

```powershell
$d = 42 # Script scope

function bar
{
    $d = 0 # Function scope
    [MyClass]::DoSomething()
}

class MyClass
{
    static [object] DoSomething()
    {
        return $d # error, not found dynamically
        return $script:d # no error
        $d = $script:d
        return $d # no error, found lexically
    }
}

$v = bar
$v -eq $d # true
```

## <a name="end-to-end-example"></a><span data-ttu-id="d071f-173">端到端示例</span><span class="sxs-lookup"><span data-stu-id="d071f-173">End-to-End Example</span></span>

<span data-ttu-id="d071f-174">下面的示例创建了几个新的自定义类来实现 HTML 动态样式表语言 (DSL)。</span><span class="sxs-lookup"><span data-stu-id="d071f-174">The following example creates several new, custom classes to implement an HTML dynamic style sheet language (DSL).</span></span>
<span data-ttu-id="d071f-175">然后，由于不能在模块的范围之外使用类型，因此，该示例还添加了帮助程序函数来创建特定的元素类型作为元素类的一部分（如标题样式和表）。</span><span class="sxs-lookup"><span data-stu-id="d071f-175">Then, the example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

```powershell
# Classes that define the structure of the document
#
class Html
{
    [string] $docType
    [HtmlHead] $Head
    [Element[]] $Body

    [string] Render()
    {
        $text = "<html>`n<head>`n"
        $text += $this.Head
        $text += "`n</head>`n<body>`n"
        $text += $this.Body -join "`n" # Render all of the body elements
        $text += "</body>`n</html>"
        return $text
    }
    [string] ToString() { return $this.Render() }
}

class HtmlHead
{
    $Title
    $Base
    $Link
    $Style
    $Meta
    $Script
    [string] Render() { return "<title>$($this.Title)</title>" }
    [string] ToString() { return $this.Render() }
}

class Element
{
    [string] $Tag
    [string] $Text
    [hashtable] $Attributes
    [string] Render() {
        $attributesText= ""
        if ($this.Attributes)
        {
            foreach ($attr in $this.Attributes.Keys)
            {
                #BUGBUG - need to validate keys against attribute
                $attributesText += " $attr=`"$($this.Attributes[$attr])\`""
            }
        }
        return "<$($this.tag)${attributesText}>$($this.text)</$($this.tag)>`n"
    }
[string] ToString() { return $this.Render() }
}

#
# Helper functions for creating specific element types on top of the classes.
# These are required because types aren’t visible outside of the module.
#

function H1 { [Element] @{ Tag = "H1" ; Text = $args.foreach{$_} -join " " }}
function H2 { [Element] @{ Tag = "H2" ; Text = $args.foreach{$_} -join " " }}
function H3 { [Element] @{ Tag = "H3" ; Text = $args.foreach{$_} -join " " }}
function P { [Element] @{ Tag = "P" ; Text = $args.foreach{$_} -join " " }}
function B { [Element] @{ Tag = "B" ; Text = $args.foreach{$_} -join " " }}
function I { [Element] @{ Tag = "I" ; Text = $args.foreach{$_} -join " " }}
function HREF
{
    param (
        $Name,
        $Link
    )
    return [Element] @{
        Tag = "A"
        Attributes = @{ HREF = $link }
        Text = $name
    }
}
function Table
{
    param (
    [Parameter(Mandatory)]
    [object[]]
        $Data,
    [Parameter()]
    [string[]]
        $Properties = "*",
    [Parameter()]
    [hashtable]
        $Attributes = @{ border=2; cellpadding=2; cellspacing=2 }
    )
$bodyText = ""
# Add the header tags
$bodyText += $Properties.foreach{TH $_}
# Add the rows
$bodyText += foreach ($row in $Data)
    {
        TR (-join $Properties.Foreach{ TD ($row.$\_) } )
    }

    $table = [Element] @{
        Tag = "Table"
        Attributes = $Attributes
        Text = $bodyText
    }
$table
}
function TH { ([Element] @{ Tag = "TH" ; Text = $args.foreach{$_} -join " " }) }
function TR { ([Element] @{ Tag = "TR" ; Text = $args.foreach{$_} -join " " }) }
function TD { ([Element] @{ Tag = "TD" ; Text = $args.foreach{$_} -join " " }) }
function Style

{
    return [Element] @{
        Tag = "style"
        Text = "$args"
    }
}

# Takes a hash table, casts it to and HTML document
# and then returns the resulting type.
#
function Html ([HTML] $doc) { return $doc }
```
