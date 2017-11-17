---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,安装程序"
ms.openlocfilehash: 968e78beb8df77588a08a9ce8732e4abcadde4d0
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2017
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="a2fe5-102">声明已实现的接口</span><span class="sxs-lookup"><span data-stu-id="a2fe5-102">Declare Implemented Interface</span></span>

<span data-ttu-id="a2fe5-103">如果未指定任何基类型，则可以在基类型或冒号 (:) 之后立即声明已实现的接口。</span><span class="sxs-lookup"><span data-stu-id="a2fe5-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="a2fe5-104">使用逗号分隔所有类型名称。</span><span class="sxs-lookup"><span data-stu-id="a2fe5-104">Separate all type names by using commas.</span></span> <span data-ttu-id="a2fe5-105">这与 C# 语法极其相似。</span><span class="sxs-lookup"><span data-stu-id="a2fe5-105">It’s very similar to C# syntax.</span></span>

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

