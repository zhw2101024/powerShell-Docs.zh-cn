# PowerShell 5.0 中的新语言功能 

PowerShell 5.0 引入了以下 Windows PowerShell 中的新语言元素：

## Class 关键字

**class** 关键字定义了一个新类。 这是真正的 .NET Framework 类型。 
Class 成员是公开的，但仅在模块作用域内公开。
不能引用类型名称作为字符串（例如，`New-Object` 不起作用），并且在此版本中，也不能在该类定义的脚本/模块外部使用类型文本（例如，`[MyClass]`）。

```powershell
class MyClass
{
    ...
}
```

## Enum 关键字和枚举

已添加对 **enum** 关键字的支持，它使用换行符作为分隔符。
当前局限：不能就枚举器本身定义枚举器，但可以根据另一个枚举初始化某个枚举，如下面的示例中所示。
此外，当前不能指定基类型；它始终是 [int]。

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

枚举器值必须是分析时间常量；不能将其设置为调用命令的结果。

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

枚举支持算术运算，如下面的示例中所示。

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

## Import-DscResource

**Import-DscResource** 现在是一个真正的动态关键字。
PowerShell 用于分析指定的模块的根模块，搜索包含 **DscResource** 属性的类。

## ImplementingAssembly

已将新字段 **ImplementingAssembly** 添加到了 ModuleInfo。 如果脚本模块定义类，或者二进制模块的加载程序集，则会将此字段设置为为脚本模块创建的动态程序集。 当 ModuleType = Manifest 时，不会对该字段进行设置。 

**ImplementingAssembly** 字段上的反射可发现模块中的资源。 这意味着你可以发现用 PowerShell 或其他托管语言编写的资源。

具有初始值设定项的字段：      

```powershell
[int] $i = 5
```

支持静态；其工作原理类似属性，类型约束也是如此，因此它可以按任意顺序指定。

```powershell
static [int] $count = 0
```

可选类型。

```powershell
$s = "hello"
```

所有成员都是公开的。 

## 构造函数和实例化

Windows PowerShell 类具有很多构造函数。它们具有与其类相同的名称。 这些构造函数可进行重载。 支持静态构造函数。 在运行构造函数中的任何代码之前，将初始化具有初始化表达式的属性。 静态属性在静态构造函数的主体之前进行初始化，而实例属性则在非静态构造函数的主体之前进行初始化。 目前，没有用于从另一个构造函数中调用某个构造函数的语法（例如，C\# 语法“: this()”）。 解决方法是定义一种常用的 Init 方法。 

下面是此版本中的实例化类的方法。

使用默认构造函数实例化。 请注意，此版本不支持 New-Object。

```powershell
$a = [MyClass]::new()
```

调用带参数的构造函数

```powershell
$b = [MyClass]::new(42)
```

将数组传递给带多个参数的构造函数
```powershell
$c = [MyClass]::new(@(42,43,44), "Hello")
```

在此版本中，New-Object 不适用于 Windows PowerShell 中定义的类。 此外对于此版本，类型名称只在词法上可见，意思是在定义类的模块或脚本外部不可见。 函数可以返回 Windows PowerShell 中定义的类的实例，并且实例在模块或脚本外部也同样有效。

`Get-Member -Static` 列出了构造函数，以便你可以像任何其他方法一样查看重载。 此语法的性能比 New-Object 快得多。

名为 **new** 的伪静态方法适用于 .NET 类型，如下面的示例中所示。

```powershell
[hashtable]::new()
```

你现在可以使用 Get-member 查看构造函数重载，或如此示例所示：

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

## 方法

Windows PowerShell 类方法被实现为仅有一个结束块的 ScriptBlock。 所有方法都是公开的。 下面介绍了定义一个名为 **DoSomething** 的方法的示例。

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

方法调用：

```powershell
$b = [MyClass]::new()
$b.DoSomething(42) 
```

还支持重载方法（即，那些与现有方法命名相同，但由其指定的值进行区分的方法）。

## “属性” 

所有属性都是公开的。 属性要求使用换行符或分号。 如果未指定任何对象类型，则该属性类型是对象。

使用验证属性或参数转换属性的属性（例如 `[ValidateSet("aaa")]`）按预期方式运行。

## Hidden

已添加新的关键字 **Hidden**。 **Hidden** 可应用于属性和方法（包括构造函数）。

Hidden 成员是公开的，除非添加了 -Force 参数，否则不出现在 Get-member 的输出中。

当选项卡完成或使用 Intellisense 时，除非完成发生在定义 Hidden 成员的类中，否则不包括 Hidden 成员。

已添加新的属性 **System.Management.Automation.HiddenAttribute**，以便 C# 代码可以在 Windows PowerShell 中具有相同的语义。

## 返回类型

返回类型是一种构造；返回值将被转换为预期类型。 如果没有指定返回类型，则返回类型为 void。 没有对象流；不能有意或无意将对象写入管道。

## 属性

已添加四个新属性：**DscResource**、**DscResourceKey**、**DscResourceMandatory** 和 **DscResourceOut**。

## 变量的词法作用域

下例介绍了词法作用域在此版本中的工作原理。

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

## 端到端示例

下面的示例创建了几个新的自定义类来实现 HTML 动态样式表语言 (DSL)。 
然后，由于不能在模块的范围之外使用类型，因此，该示例还添加了帮助程序函数来创建特定的元素类型作为元素类的一部分（如标题样式和表）。

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
```<!--HONumber=Mar16_HO2-->
