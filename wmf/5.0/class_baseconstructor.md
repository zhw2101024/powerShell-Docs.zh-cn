---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,安装程序"
ms.openlocfilehash: 403a79e17b832b5c58fd21a138fcebb8adb76d40
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="call-base-class-constructor"></a><span data-ttu-id="b90c0-102">调用基类构造函数</span><span class="sxs-lookup"><span data-stu-id="b90c0-102">Call Base Class Constructor</span></span>

<span data-ttu-id="b90c0-103">若要从子类调用基类构造函数，请使用关键字 **base**：</span><span class="sxs-lookup"><span data-stu-id="b90c0-103">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

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

<span data-ttu-id="b90c0-104">如果一个基类具有一个默认（无参数）构造函数，则可以省略显式构造函数的调用：</span><span class="sxs-lookup"><span data-stu-id="b90c0-104">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```PowerShell
class C : B
{
    C([int]$c) {}
}
```

