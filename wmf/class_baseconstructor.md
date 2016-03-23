# 调用基类构造函数

若要从子类调用基类构造函数，请使用关键字 **base**：

```PowerShell
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

如果一个基类具有一个默认（无参数）构造函数，则可以省略显式构造函数的调用：

```PowerShell
class C : B
{
    C([int]$c) {}
}
```<!--HONumber=Mar16_HO2-->
