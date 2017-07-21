---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,安装程序"
ms.openlocfilehash: 28da6d12d3f7a59777425e1cc4531a609a793ddb
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="call-base-class-method"></a><span data-ttu-id="a519d-102">调用基类方法</span><span class="sxs-lookup"><span data-stu-id="a519d-102">Call Base Class Method</span></span>

<span data-ttu-id="a519d-103">你可以重写子类中的现有方法。</span><span class="sxs-lookup"><span data-stu-id="a519d-103">You can override existing methods in subclasses.</span></span> <span data-ttu-id="a519d-104">若要执行此操作，请使用相同的名称和签名声明方法：</span><span class="sxs-lookup"><span data-stu-id="a519d-104">To do this, declare methods by using the same name and signature:</span></span>

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

<span data-ttu-id="a519d-105">若要从重写实现中调用基类方法，请在调用时强制转换为基类 ([baseClass]$this)：</span><span class="sxs-lookup"><span data-stu-id="a519d-105">To call base class methods from overridden implementations, cast to the base class ([baseClass]$this) on invocation:</span></span>

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

<span data-ttu-id="a519d-106">所有 PowerShell 方法都是虚拟的。</span><span class="sxs-lookup"><span data-stu-id="a519d-106">All PowerShell methods are virtual.</span></span> <span data-ttu-id="a519d-107">你可以像重写时那样使用相同的语法隐藏子类中的非虚拟 .NET 方法：只需使用相同的名称和签名声明方法。</span><span class="sxs-lookup"><span data-stu-id="a519d-107">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override: just declare methods with same name and signature.</span></span>

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
```

