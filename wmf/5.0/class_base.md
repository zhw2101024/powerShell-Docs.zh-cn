---
ms.date: 2017-06-12T00:00:00.000Z
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,安装程序"
ms.openlocfilehash: 5dbaa126cf9ae3917c3a8787ffc5ef5ac77b19c1
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2017
---
# <a name="declare-base-class"></a>声明基类
可以将 Windows PowerShell 类声明为另一个 Windows PowerShell 类的基类型。

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

此外，还可以使用现有的.NET Framework 类型作为基类：

```powershell
class MyIntList : system.collections.generic.list[int]
{
    
}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

