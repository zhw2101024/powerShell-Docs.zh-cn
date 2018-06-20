---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: d7aec1a2ba8964e877ddd7406609fe135b1eb462
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219736"
---
# <a name="call-base-class-method"></a><span data-ttu-id="715e2-102">调用基类方法</span><span class="sxs-lookup"><span data-stu-id="715e2-102">Call Base Class Method</span></span>

<span data-ttu-id="715e2-103">你可以重写子类中的现有方法。</span><span class="sxs-lookup"><span data-stu-id="715e2-103">You can override existing methods in subclasses.</span></span> <span data-ttu-id="715e2-104">若要执行此操作，请使用相同的名称和签名声明方法：</span><span class="sxs-lookup"><span data-stu-id="715e2-104">To do this, declare methods by using the same name and signature:</span></span>

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

<span data-ttu-id="715e2-105">若要从重写实现中调用基类方法，请在调用时强制转换为基类 ([baseClass]$this)：</span><span class="sxs-lookup"><span data-stu-id="715e2-105">To call base class methods from overridden implementations, cast to the base class ([baseClass]$this) on invocation:</span></span>

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

<span data-ttu-id="715e2-106">所有 PowerShell 方法都是虚拟的。</span><span class="sxs-lookup"><span data-stu-id="715e2-106">All PowerShell methods are virtual.</span></span> <span data-ttu-id="715e2-107">你可以像重写时那样使用相同的语法隐藏子类中的非虚拟 .NET 方法：只需使用相同的名称和签名声明方法。</span><span class="sxs-lookup"><span data-stu-id="715e2-107">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override: just declare methods with same name and signature.</span></span>

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
