---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 3269c8cc871f22488b64fb072dac72698983f360
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="call-base-class-constructor"></a><span data-ttu-id="c459d-102">调用基类构造函数</span><span class="sxs-lookup"><span data-stu-id="c459d-102">Call Base Class Constructor</span></span>

<span data-ttu-id="c459d-103">若要从子类调用基类构造函数，请使用关键字 **base**：</span><span class="sxs-lookup"><span data-stu-id="c459d-103">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

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

<span data-ttu-id="c459d-104">如果一个基类具有一个默认（无参数）构造函数，则可以省略显式构造函数的调用：</span><span class="sxs-lookup"><span data-stu-id="c459d-104">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```