---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 188ede0c558210a746ad0f6c6cef6f571b280878
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="declare-base-class"></a><span data-ttu-id="89216-102">声明基类</span><span class="sxs-lookup"><span data-stu-id="89216-102">Declare Base Class</span></span>
<span data-ttu-id="89216-103">可以将 Windows PowerShell 类声明为另一个 Windows PowerShell 类的基类型。</span><span class="sxs-lookup"><span data-stu-id="89216-103">You can declare a Windows PowerShell class as a base type for another Windows PowerShell class.</span></span>

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

<span data-ttu-id="89216-104">此外，还可以使用现有的.NET Framework 类型作为基类：</span><span class="sxs-lookup"><span data-stu-id="89216-104">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```
