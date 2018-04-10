---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 43b26426a76b6503a83e35ae0c02a0af69902ed6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="declare-base-class"></a><span data-ttu-id="d0ebe-102">声明基类</span><span class="sxs-lookup"><span data-stu-id="d0ebe-102">Declare Base Class</span></span>
<span data-ttu-id="d0ebe-103">可以将 Windows PowerShell 类声明为另一个 Windows PowerShell 类的基类型。</span><span class="sxs-lookup"><span data-stu-id="d0ebe-103">You can declare a Windows PowerShell class as a base type for another Windows PowerShell class.</span></span>

```powershell
class bar
{
   [int]foo()
       {
           return 100500
       }
}

class baz : bar {}

[baz]::new().foo() # return 100500
```

<span data-ttu-id="d0ebe-104">此外，还可以使用现有的.NET Framework 类型作为基类：</span><span class="sxs-lookup"><span data-stu-id="d0ebe-104">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```