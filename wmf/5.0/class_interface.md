---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 2c007321789ae22b4a2e048d2d64162b065f9a75
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="39e0b-102">声明已实现的接口</span><span class="sxs-lookup"><span data-stu-id="39e0b-102">Declare Implemented Interface</span></span>

<span data-ttu-id="39e0b-103">如果未指定任何基类型，则可以在基类型或冒号 (:) 之后立即声明已实现的接口。</span><span class="sxs-lookup"><span data-stu-id="39e0b-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="39e0b-104">使用逗号分隔所有类型名称。</span><span class="sxs-lookup"><span data-stu-id="39e0b-104">Separate all type names by using commas.</span></span> <span data-ttu-id="39e0b-105">这与 C# 语法极其相似。</span><span class="sxs-lookup"><span data-stu-id="39e0b-105">It’s very similar to C# syntax.</span></span>

```powershell
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
```