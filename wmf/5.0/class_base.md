---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 8b3ebd22e03bf9bdd5f26965137a1b1ce9f47c3e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058771"
---
# <a name="declare-base-class"></a><span data-ttu-id="87c56-102">声明基类</span><span class="sxs-lookup"><span data-stu-id="87c56-102">Declare Base Class</span></span>
<span data-ttu-id="87c56-103">可以将 Windows PowerShell 类声明为另一个 Windows PowerShell 类的基类型。</span><span class="sxs-lookup"><span data-stu-id="87c56-103">You can declare a Windows PowerShell class as a base type for another Windows PowerShell class.</span></span>

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

<span data-ttu-id="87c56-104">此外，还可以使用现有的.NET Framework 类型作为基类：</span><span class="sxs-lookup"><span data-stu-id="87c56-104">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```
