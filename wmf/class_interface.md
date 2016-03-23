# 声明已实现的接口

如果未指定任何基类型，则可以在基类型或冒号 (:) 之后立即声明已实现的接口。 使用逗号分隔所有类型名称。 这与 C# 语法极其相似。

```PowerShell
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
```<!--HONumber=Mar16_HO2-->
