---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 424e0b7a4d62fc35e5040a7e425950e887021d7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085875"
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
