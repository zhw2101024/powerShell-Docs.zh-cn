# 调用基类方法

你可以重写子类中的现有方法。 若要执行此操作，请使用相同的名称和签名声明方法：

```PowerShell
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

若要从重写实现中调用基类方法，请在调用时强制转换为基类 ([baseClass]$this)：

```PowerShell
class childClass2 : baseClass
{
    [int]foo()
    {
        return 3 * ([baseClass]$this).foo()
    }
}

[childClass2]::new().foo() # return 301500
```

所有 PowerShell 方法都是虚拟的。 你可以像重写时那样使用相同的语法隐藏子类中的非虚拟 .NET 方法：只需使用相同的名称和签名声明方法。

```PowerShell
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
```<!--HONumber=Mar16_HO2-->
