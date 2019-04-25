---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 4b593e9a1eca43ee7ad85fc921ae3c1d62722db9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085846"
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="e2b89-102">声明已实现的接口</span><span class="sxs-lookup"><span data-stu-id="e2b89-102">Declare Implemented Interface</span></span>

<span data-ttu-id="e2b89-103">如果未指定任何基类型，则可以在基类型或冒号 (:) 之后立即声明已实现的接口。</span><span class="sxs-lookup"><span data-stu-id="e2b89-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="e2b89-104">使用逗号分隔所有类型名称。</span><span class="sxs-lookup"><span data-stu-id="e2b89-104">Separate all type names by using commas.</span></span> <span data-ttu-id="e2b89-105">这与 C# 语法极其相似。</span><span class="sxs-lookup"><span data-stu-id="e2b89-105">It’s very similar to C# syntax.</span></span>

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
