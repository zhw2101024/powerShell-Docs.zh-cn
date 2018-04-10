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
# <a name="call-base-class-constructor"></a>调用基类构造函数

若要从子类调用基类构造函数，请使用关键字 **base**：

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

如果一个基类具有一个默认（无参数）构造函数，则可以省略显式构造函数的调用：

```powershell
class C : B
{
    C([int]$c) {}
}
```