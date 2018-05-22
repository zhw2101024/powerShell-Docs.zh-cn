---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 116f79a95126d0a1c579a95ec99eb5d8b75cc1e0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="716f2-102">声明已实现的接口</span><span class="sxs-lookup"><span data-stu-id="716f2-102">Declare Implemented Interface</span></span>

<span data-ttu-id="716f2-103">如果未指定任何基类型，则可以在基类型或冒号 (:) 之后立即声明已实现的接口。</span><span class="sxs-lookup"><span data-stu-id="716f2-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="716f2-104">使用逗号分隔所有类型名称。</span><span class="sxs-lookup"><span data-stu-id="716f2-104">Separate all type names by using commas.</span></span> <span data-ttu-id="716f2-105">这与 C# 语法极其相似。</span><span class="sxs-lookup"><span data-stu-id="716f2-105">It’s very similar to C# syntax.</span></span>

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
