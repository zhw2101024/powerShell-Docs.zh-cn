---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
title: 使用 PowerShell 类创建自定义类型
ms.openlocfilehash: c2c50fb65ce4931fcf6ae529b4146df391c831c4
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470931"
---
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="a5804-103">使用 PowerShell 类创建自定义类型</span><span class="sxs-lookup"><span data-stu-id="a5804-103">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="a5804-104">PowerShell 5.0 添加了使用类似于其他面向对象的编程语言的语法和语义定义类和其他用户定义的类型的功能。</span><span class="sxs-lookup"><span data-stu-id="a5804-104">PowerShell 5.0 added the ability to define classes and other user-defined types using formal syntax and semantics like other object-oriented programming languages.</span></span> <span data-ttu-id="a5804-105">目标是使开发人员和 IT 专业人员在更广泛的用例中使用 PowerShell，从而简化 PowerShell 项目开发（如 DSC 资源），并加速覆盖管理面。</span><span class="sxs-lookup"><span data-stu-id="a5804-105">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="a5804-106">此版本中受支持的方案</span><span class="sxs-lookup"><span data-stu-id="a5804-106">Supported scenarios in this release</span></span>

- <span data-ttu-id="a5804-107">使用 PowerShell 语言来定义 DSC 资源和与其关联的类型</span><span class="sxs-lookup"><span data-stu-id="a5804-107">Define DSC resources and their associated types by using the PowerShell language</span></span>
- <span data-ttu-id="a5804-108">使用熟悉的面向对象的编程构造（例如类、属性、方法等）在 PowerShell 中定义自定义类型。</span><span class="sxs-lookup"><span data-stu-id="a5804-108">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
- <span data-ttu-id="a5804-109">使用 PowerShell 中的类和基类 DSC 资源的继承支持</span><span class="sxs-lookup"><span data-stu-id="a5804-109">Inheritance support with class in PowerShell and class base DSC resource</span></span>
- <span data-ttu-id="a5804-110">使用 PowerShell 语言调试类型</span><span class="sxs-lookup"><span data-stu-id="a5804-110">Debug types by using the PowerShell language</span></span>
- <span data-ttu-id="a5804-111">使用正式的机制以及适当的级别生成和处理异常</span><span class="sxs-lookup"><span data-stu-id="a5804-111">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>

## <a name="declare-base-class"></a><span data-ttu-id="a5804-112">声明基类</span><span class="sxs-lookup"><span data-stu-id="a5804-112">Declare Base Class</span></span>

<span data-ttu-id="a5804-113">可以将 PowerShell 类声明为另一个 PowerShell 类的基类型。</span><span class="sxs-lookup"><span data-stu-id="a5804-113">You can declare a PowerShell class as a base type for another PowerShell class.</span></span>

```powershell
class bar
{
   [int]foo()
       {
           return 100500
       }
}

class baz : bar {}

[baz]::new().foo() # return 100500
```

<span data-ttu-id="a5804-114">此外，还可以使用现有的.NET Framework 类型作为基类：</span><span class="sxs-lookup"><span data-stu-id="a5804-114">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

### <a name="call-base-class-constructor"></a><span data-ttu-id="a5804-115">调用基类构造函数</span><span class="sxs-lookup"><span data-stu-id="a5804-115">Call Base Class Constructor</span></span>

<span data-ttu-id="a5804-116">若要从子类调用基类构造函数，请使用关键字 **base**：</span><span class="sxs-lookup"><span data-stu-id="a5804-116">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

```powershell
class A
{
    [int]$a

    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

[B]::new().a # return 103
```

<span data-ttu-id="a5804-117">如果一个基类具有一个默认（无参数）构造函数，则可以省略显式构造函数的调用：</span><span class="sxs-lookup"><span data-stu-id="a5804-117">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-method"></a><span data-ttu-id="a5804-118">调用基类方法</span><span class="sxs-lookup"><span data-stu-id="a5804-118">Call Base Class Method</span></span>

<span data-ttu-id="a5804-119">你可以重写子类中的现有方法。</span><span class="sxs-lookup"><span data-stu-id="a5804-119">You can override existing methods in subclasses.</span></span> <span data-ttu-id="a5804-120">若要执行此操作，请使用相同的名称和签名声明方法：</span><span class="sxs-lookup"><span data-stu-id="a5804-120">To do this, declare methods by using the same name and signature:</span></span>

```powershell
class baseClass
{
    [int]foo() {return 100500}
}

class childClass1 : baseClass
{
    [int]foo() {return 200600}
}

[childClass1]::new().foo() # return 200600
```

<span data-ttu-id="a5804-121">若要从重写实现中调用基类方法，请在调用时强制转换为基类 (`[baseClass]$this`)：</span><span class="sxs-lookup"><span data-stu-id="a5804-121">To call base class methods from overridden implementations, cast to the base class (`[baseClass]$this`) on invocation:</span></span>

```powershell
class childClass2 : baseClass
{
    [int]foo()
    {
        return 3 * ([baseClass]$this).foo()
    }
}

[childClass2]::new().foo() # return 301500
```

<span data-ttu-id="a5804-122">所有 PowerShell 方法都是虚拟的。</span><span class="sxs-lookup"><span data-stu-id="a5804-122">All PowerShell methods are virtual.</span></span> <span data-ttu-id="a5804-123">你可以像重写时那样使用相同的语法隐藏子类中的非虚拟 .NET 方法：使用相同的名称和签名声明方法。</span><span class="sxs-lookup"><span data-stu-id="a5804-123">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override, by declaring methods with same name and signature.</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```

### <a name="declare-implemented-interface"></a><span data-ttu-id="a5804-124">声明已实现的接口</span><span class="sxs-lookup"><span data-stu-id="a5804-124">Declare Implemented Interface</span></span>

<span data-ttu-id="a5804-125">如果未指定任何基类型，则可以在基类型或冒号 (:) 之后立即声明已实现的接口。</span><span class="sxs-lookup"><span data-stu-id="a5804-125">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="a5804-126">使用逗号分隔所有类型名称。</span><span class="sxs-lookup"><span data-stu-id="a5804-126">Separate all type names by using commas.</span></span> <span data-ttu-id="a5804-127">这与 C# 语法类似。</span><span class="sxs-lookup"><span data-stu-id="a5804-127">It's similar to C# syntax.</span></span>

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

## <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="a5804-128">PowerShell 5.0 中的新语言功能</span><span class="sxs-lookup"><span data-stu-id="a5804-128">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="a5804-129">PowerShell 5.0 引入了以下 PowerShell 中的新语言元素：</span><span class="sxs-lookup"><span data-stu-id="a5804-129">PowerShell 5.0 introduces the following new language elements in PowerShell:</span></span>

### <a name="class-keyword"></a><span data-ttu-id="a5804-130">Class 关键字</span><span class="sxs-lookup"><span data-stu-id="a5804-130">Class keyword</span></span>

<span data-ttu-id="a5804-131">`class` 关键字定义了一个新类。</span><span class="sxs-lookup"><span data-stu-id="a5804-131">The `class` keyword defines a new class.</span></span> <span data-ttu-id="a5804-132">这是真正的 .NET Framework 类型。</span><span class="sxs-lookup"><span data-stu-id="a5804-132">This is a true .NET Framework type.</span></span> <span data-ttu-id="a5804-133">Class 成员是公开的，但仅在模块作用域内公开。</span><span class="sxs-lookup"><span data-stu-id="a5804-133">Class members are public, but only public within the module scope.</span></span> <span data-ttu-id="a5804-134">不能引用类型名称作为字符串（例如，`New-Object` 不起作用），并且在此版本中，也不能在该类定义的脚本或模块文件外部使用类型文本（例如，`[MyClass]`）。</span><span class="sxs-lookup"><span data-stu-id="a5804-134">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script or module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="a5804-135">Enum 关键字和枚举</span><span class="sxs-lookup"><span data-stu-id="a5804-135">Enum keyword and enumerations</span></span>

<span data-ttu-id="a5804-136">已添加对 `enum` 关键字的支持，它使用换行符作为分隔符。</span><span class="sxs-lookup"><span data-stu-id="a5804-136">Support for the `enum` keyword has been added, which uses newline as the delimiter.</span></span> <span data-ttu-id="a5804-137">当前，不能根据自身定义枚举器。</span><span class="sxs-lookup"><span data-stu-id="a5804-137">Currently, you cannot define an enumerator in terms of itself.</span></span> <span data-ttu-id="a5804-138">但是，可以根据一个枚举初始化另一个枚举，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="a5804-138">However, you can initialize an enum in terms of another enum, as shown in the following example.</span></span> <span data-ttu-id="a5804-139">此外，不能指定基类型；它始终是 `[int]`。</span><span class="sxs-lookup"><span data-stu-id="a5804-139">Also, the base type cannot be specified; it is always `[int]`.</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="a5804-140">枚举器值必须是分析时间常量。</span><span class="sxs-lookup"><span data-stu-id="a5804-140">An enumerator value must be a parse time constant.</span></span> <span data-ttu-id="a5804-141">不能将其设置为调用命令的结果。</span><span class="sxs-lookup"><span data-stu-id="a5804-141">You cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="a5804-142">枚举支持算术运算，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="a5804-142">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="import-dscresource"></a><span data-ttu-id="a5804-143">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="a5804-143">Import-DscResource</span></span>

<span data-ttu-id="a5804-144">`Import-DscResource` 现在是一个真正的动态关键字。</span><span class="sxs-lookup"><span data-stu-id="a5804-144">`Import-DscResource` is now a true dynamic keyword.</span></span> <span data-ttu-id="a5804-145">PowerShell 用于分析指定的模块的根模块，搜索包含 DscResource  属性的类。</span><span class="sxs-lookup"><span data-stu-id="a5804-145">PowerShell parses the specified module's root module, searching for classes that contain the **DscResource** attribute.</span></span>

### <a name="implementingassembly"></a><span data-ttu-id="a5804-146">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="a5804-146">ImplementingAssembly</span></span>

<span data-ttu-id="a5804-147">已将新字段 ImplementingAssembly  添加到了 ModuleInfo  。</span><span class="sxs-lookup"><span data-stu-id="a5804-147">A new field, **ImplementingAssembly**, has been added to **ModuleInfo**.</span></span> <span data-ttu-id="a5804-148">如果脚本模块定义类，或者二进制模块的加载程序集，则会将此字段设置为为脚本模块创建的动态程序集。</span><span class="sxs-lookup"><span data-stu-id="a5804-148">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="a5804-149">当 ModuleType  为 Manifest  时，不会对该字段进行设置。</span><span class="sxs-lookup"><span data-stu-id="a5804-149">It is not set when **ModuleType** is **Manifest**.</span></span>

<span data-ttu-id="a5804-150">**ImplementingAssembly** 字段上的反射可发现模块中的资源。</span><span class="sxs-lookup"><span data-stu-id="a5804-150">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="a5804-151">这意味着你可以发现用 PowerShell 或其他托管语言编写的资源。</span><span class="sxs-lookup"><span data-stu-id="a5804-151">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="a5804-152">具有初始值设定项的字段：</span><span class="sxs-lookup"><span data-stu-id="a5804-152">Fields with initializers:</span></span>

```powershell
[int] $i = 5
```

<span data-ttu-id="a5804-153">支持 `Static`。</span><span class="sxs-lookup"><span data-stu-id="a5804-153">`Static` is supported.</span></span> <span data-ttu-id="a5804-154">其工作原理类似于属性，就像类型约束一样。</span><span class="sxs-lookup"><span data-stu-id="a5804-154">It works like an attribute, as do the type constraints.</span></span> <span data-ttu-id="a5804-155">可以按任意顺序指定。</span><span class="sxs-lookup"><span data-stu-id="a5804-155">It can be specified in any order.</span></span>

```powershell
static [int] $count = 0
```

<span data-ttu-id="a5804-156">可选类型。</span><span class="sxs-lookup"><span data-stu-id="a5804-156">A type is optional.</span></span>

```powershell
$s = "hello"
```

<span data-ttu-id="a5804-157">所有成员都是公开的。</span><span class="sxs-lookup"><span data-stu-id="a5804-157">All members are public.</span></span>

### <a name="constructors-and-instantiation"></a><span data-ttu-id="a5804-158">构造函数和实例化</span><span class="sxs-lookup"><span data-stu-id="a5804-158">Constructors and instantiation</span></span>

<span data-ttu-id="a5804-159">PowerShell 类可以具有构造函数。</span><span class="sxs-lookup"><span data-stu-id="a5804-159">PowerShell classes can have constructors.</span></span> <span data-ttu-id="a5804-160">它们与其类同名。</span><span class="sxs-lookup"><span data-stu-id="a5804-160">They have the same name as their class.</span></span> <span data-ttu-id="a5804-161">这些构造函数可进行重载。</span><span class="sxs-lookup"><span data-stu-id="a5804-161">Constructors can be overloaded.</span></span> <span data-ttu-id="a5804-162">支持静态构造函数。</span><span class="sxs-lookup"><span data-stu-id="a5804-162">Static constructors are supported.</span></span> <span data-ttu-id="a5804-163">在运行构造函数中的任何代码之前，将初始化具有初始化表达式的属性。</span><span class="sxs-lookup"><span data-stu-id="a5804-163">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="a5804-164">静态属性在静态构造函数的主体之前进行初始化，而实例属性则在非静态构造函数的主体之前进行初始化。</span><span class="sxs-lookup"><span data-stu-id="a5804-164">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="a5804-165">目前，没有用于从另一个构造函数中调用某个构造函数的语法（例如，C\# 语法“: this()”）。</span><span class="sxs-lookup"><span data-stu-id="a5804-165">Currently, there is no syntax for calling a constructor from another constructor (like the C\# syntax ": this()").</span></span> <span data-ttu-id="a5804-166">解决方法是定义一种常用的 `Init()` 方法。</span><span class="sxs-lookup"><span data-stu-id="a5804-166">The workaround is to define a common `Init()` method.</span></span>

#### <a name="creating-instances"></a><span data-ttu-id="a5804-167">创建实例</span><span class="sxs-lookup"><span data-stu-id="a5804-167">Creating instances</span></span>

> [!NOTE]
> <span data-ttu-id="a5804-168">在 PowerShell 5.0 中，`New-Object` 不适用于 PowerShell 中定义的类。</span><span class="sxs-lookup"><span data-stu-id="a5804-168">In PowerShell 5.0, `New-Object` does not work with classes defined in PowerShell.</span></span> <span data-ttu-id="a5804-169">此外，类型名称只在词法上可见，意思是在定义类的模块或脚本外部不可见。</span><span class="sxs-lookup"><span data-stu-id="a5804-169">Also, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="a5804-170">函数可以返回 PowerShell 中定义的类的实例。</span><span class="sxs-lookup"><span data-stu-id="a5804-170">Functions can return instances of a class defined in PowerShell.</span></span> <span data-ttu-id="a5804-171">这些实例在模块或脚本外部工作。</span><span class="sxs-lookup"><span data-stu-id="a5804-171">Those instances work outside of the module or script.</span></span>

1. <span data-ttu-id="a5804-172">使用默认构造函数实例化。</span><span class="sxs-lookup"><span data-stu-id="a5804-172">Instantiating by using the default constructor.</span></span>

   ```powershell
   $a = [MyClass]::new()
   ```

1. <span data-ttu-id="a5804-173">调用带参数的构造函数</span><span class="sxs-lookup"><span data-stu-id="a5804-173">Calling a constructor with a parameter</span></span>

   ```powershell
   $b = [MyClass]::new(42)
   ```

1. <span data-ttu-id="a5804-174">将数组传递给带多个参数的构造函数。</span><span class="sxs-lookup"><span data-stu-id="a5804-174">Passing an array to a constructor with multiple parameters.</span></span>

   ```powershell
   $c = [MyClass]::new(@(42,43,44), "Hello")
   ```

<span data-ttu-id="a5804-175">伪静态方法 `new()` 适用于 .NET 类型，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="a5804-175">The pseudo-static method `new()` works with .NET types, as shown in the following example.</span></span>

```powershell
[hashtable]::new()
```

#### <a name="discovering-constructors"></a><span data-ttu-id="a5804-176">发现构造函数</span><span class="sxs-lookup"><span data-stu-id="a5804-176">Discovering constructors</span></span>

<span data-ttu-id="a5804-177">你现在可以使用 `Get-Member` 查看构造函数重载，或如此示例所示：</span><span class="sxs-lookup"><span data-stu-id="a5804-177">You can now see constructor overloads with `Get-Member`, or as shown in this example:</span></span>

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

<span data-ttu-id="a5804-178">`Get-Member -Static` 列出了构造函数，以便你可以像任何其他方法一样查看重载。</span><span class="sxs-lookup"><span data-stu-id="a5804-178">`Get-Member -Static` lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="a5804-179">此语法的性能比 `New-Object` 快得多。</span><span class="sxs-lookup"><span data-stu-id="a5804-179">The performance of this syntax is also considerably faster than `New-Object`.</span></span>

### <a name="methods"></a><span data-ttu-id="a5804-180">方法</span><span class="sxs-lookup"><span data-stu-id="a5804-180">Methods</span></span>

<span data-ttu-id="a5804-181">PowerShell 类方法被实现为仅有一个结束块的 ScriptBlock  。</span><span class="sxs-lookup"><span data-stu-id="a5804-181">A PowerShell class method is implemented as a **ScriptBlock** that has only an end block.</span></span> <span data-ttu-id="a5804-182">所有方法都是公开的。</span><span class="sxs-lookup"><span data-stu-id="a5804-182">All methods are public.</span></span> <span data-ttu-id="a5804-183">下面介绍了定义一个名为 **DoSomething** 的方法的示例。</span><span class="sxs-lookup"><span data-stu-id="a5804-183">The following shows an example of defining a method named **DoSomething**.</span></span>

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

<span data-ttu-id="a5804-184">方法调用：</span><span class="sxs-lookup"><span data-stu-id="a5804-184">Method invocation:</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

<span data-ttu-id="a5804-185">还支持重载方法。</span><span class="sxs-lookup"><span data-stu-id="a5804-185">Overloaded methods are also supported.</span></span>

### <a name="properties"></a><span data-ttu-id="a5804-186">“属性”</span><span class="sxs-lookup"><span data-stu-id="a5804-186">Properties</span></span>

<span data-ttu-id="a5804-187">所有属性都是公开的。</span><span class="sxs-lookup"><span data-stu-id="a5804-187">All properties are public.</span></span> <span data-ttu-id="a5804-188">属性要求使用换行符或分号。</span><span class="sxs-lookup"><span data-stu-id="a5804-188">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="a5804-189">如果未指定任何对象类型，则该属性类型是对象。</span><span class="sxs-lookup"><span data-stu-id="a5804-189">If no object type is specified, the property type is object.</span></span>

<span data-ttu-id="a5804-190">使用验证或参数转换属性的属性（如 `[ValidateSet("aaa")]`）按预期方式运行。</span><span class="sxs-lookup"><span data-stu-id="a5804-190">Properties that use validation or argument transformation attributes (like `[ValidateSet("aaa")]`) work as expected.</span></span>

### <a name="hidden"></a><span data-ttu-id="a5804-191">Hidden</span><span class="sxs-lookup"><span data-stu-id="a5804-191">Hidden</span></span>

<span data-ttu-id="a5804-192">已添加新的关键字 `Hidden`。</span><span class="sxs-lookup"><span data-stu-id="a5804-192">A new keyword, `Hidden`, has been added.</span></span> <span data-ttu-id="a5804-193">`Hidden` 可应用于属性和方法（包括构造函数）。</span><span class="sxs-lookup"><span data-stu-id="a5804-193">`Hidden` can be applied to properties and methods (including constructors).</span></span>

<span data-ttu-id="a5804-194">Hidden 成员是公开的，但不会出现在 `Get-Member` 的输出中，除非添加 `-Force` 参数。</span><span class="sxs-lookup"><span data-stu-id="a5804-194">Hidden members are public, but do not appear in the output of `Get-Member` unless the `-Force` parameter is added.</span></span> <span data-ttu-id="a5804-195">当选项卡完成或使用 Intellisense 时，除非完成发生在定义 Hidden 成员的类中，否则不包括 Hidden 成员。</span><span class="sxs-lookup"><span data-stu-id="a5804-195">Hidden members are not included when tab completing or using Intellisense unless the completion occurs in the class defining the hidden member.</span></span>

<span data-ttu-id="a5804-196">已添加新的属性  System.Management.Automation.HiddenAttribute，以便 C\# 代码可以在 PowerShell 中具有相同的语义。</span><span class="sxs-lookup"><span data-stu-id="a5804-196">A new attribute, **System.Management.Automation.HiddenAttribute** has been added so that C\# code can have the same semantics within PowerShell.</span></span>

### <a name="return-types"></a><span data-ttu-id="a5804-197">返回类型</span><span class="sxs-lookup"><span data-stu-id="a5804-197">Return types</span></span>

<span data-ttu-id="a5804-198">返回类型是一种构造。</span><span class="sxs-lookup"><span data-stu-id="a5804-198">Return type is a contract.</span></span> <span data-ttu-id="a5804-199">返回值将被转换为预期类型。</span><span class="sxs-lookup"><span data-stu-id="a5804-199">The return value is converted to the expected type.</span></span> <span data-ttu-id="a5804-200">如果没有指定返回类型，则返回类型为 void  。</span><span class="sxs-lookup"><span data-stu-id="a5804-200">If no return type is specified, the return type is **void**.</span></span> <span data-ttu-id="a5804-201">没有对象流。</span><span class="sxs-lookup"><span data-stu-id="a5804-201">There is no streaming of objects.</span></span> <span data-ttu-id="a5804-202">对象无法写入到工作流中，不论是有意还是无意。</span><span class="sxs-lookup"><span data-stu-id="a5804-202">Objects cannot be written to the pipeline either intentionally or by accident.</span></span>

### <a name="attributes"></a><span data-ttu-id="a5804-203">属性</span><span class="sxs-lookup"><span data-stu-id="a5804-203">Attributes</span></span>

<span data-ttu-id="a5804-204">添加了 **DscResource** 和 **DscProperty** 这两个新属性。</span><span class="sxs-lookup"><span data-stu-id="a5804-204">Two new attributes, **DscResource** and **DscProperty** have been added.</span></span>

### <a name="lexical-scoping-of-variables"></a><span data-ttu-id="a5804-205">变量的词法作用域</span><span class="sxs-lookup"><span data-stu-id="a5804-205">Lexical scoping of variables</span></span>

<span data-ttu-id="a5804-206">下例介绍了词法作用域在此版本中的工作原理。</span><span class="sxs-lookup"><span data-stu-id="a5804-206">The following shows an example of how lexical scoping works in this release.</span></span>

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

## <a name="end-to-end-example"></a><span data-ttu-id="a5804-207">端到端示例</span><span class="sxs-lookup"><span data-stu-id="a5804-207">End-to-End Example</span></span>

<span data-ttu-id="a5804-208">下面的示例创建了一些自定义类来实现 HTML 动态样式表语言 (DSL)。</span><span class="sxs-lookup"><span data-stu-id="a5804-208">The following example creates some custom classes to implement an HTML dynamic style sheet language (DSL).</span></span> <span data-ttu-id="a5804-209">然后，由于不能在模块的范围之外使用类型，因此，该示例还添加了帮助程序函数来创建特定的元素类型作为元素类的一部分（如标题样式和表）。</span><span class="sxs-lookup"><span data-stu-id="a5804-209">Then, the example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

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
# These are required because types aren't visible outside of the module.
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
        TR (-join $Properties.Foreach{ TD ($row.$_) } )
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
