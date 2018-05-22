---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 9486fdbaeca66c83551564c76ce47482f77c36b9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="call-base-class-constructor"></a><span data-ttu-id="3b2b4-102">调用基类构造函数</span><span class="sxs-lookup"><span data-stu-id="3b2b4-102">Call Base Class Constructor</span></span>

<span data-ttu-id="3b2b4-103">若要从子类调用基类构造函数，请使用关键字 **base**：</span><span class="sxs-lookup"><span data-stu-id="3b2b4-103">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

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

<span data-ttu-id="3b2b4-104">如果一个基类具有一个默认（无参数）构造函数，则可以省略显式构造函数的调用：</span><span class="sxs-lookup"><span data-stu-id="3b2b4-104">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```
