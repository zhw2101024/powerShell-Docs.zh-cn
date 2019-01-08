---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 对对象进行排序
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 06aa15d89888f1ecbe60b8e1dfb4efebb1d73673
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400378"
---
# <a name="sorting-objects"></a>对对象进行排序

我们可以将组织显示的数据，使其更轻松地使用扫描`Sort-Object`cmdlet。 `Sort-Object` 将一个或多个要作为排序依据的属性的名称并返回按这些属性值进行排序的数据。

## <a name="basic-sorting"></a>基本排序

请考虑列出当前目录中子目录和文件的问题。
如果我们想要作为排序依据**LastWriteTime**然后按**名称**，我们可以通过键入操作即可：

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
11/6/2017 10:10:11 AM  .localization-config
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:15 AM  tests
6/6/2018 7:58:59 PM    CONTRIBUTING.md
6/6/2018 7:58:59 PM    README.md
...
```

您还可以进行排序的对象按相反的顺序通过指定**降序**开关参数。

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name -Descending |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  reference
12/1/2018 10:13:50 PM  dsc
...
6/6/2018 7:58:59 PM    README.md
6/6/2018 7:58:59 PM    CONTRIBUTING.md
11/6/2017 10:10:15 AM  tests
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  .localization-config
```

## <a name="using-hash-tables"></a>使用哈希表

可以通过使用哈希表数组中对不同属性进行不同的顺序进行排序。
每个哈希表使用**表达式**键属性名称指定为字符串和一个**Ascending**或**降序**键以指定排序顺序由`$true`或`$false`.
**表达式**键是必需的。
**升序**或**降序**关键字是可选的。

下面的示例对按降序对象进行排序**LastWriteTime**顺序和升序**名称**顺序。

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = 'LastWriteTime'; Descending = $true }, @{ Expression = 'Name'; Ascending = $true } |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  dsc
12/1/2018 10:13:50 PM  reference
11/29/2018 6:56:01 PM  .openpublishing.redirection.json
11/29/2018 6:56:01 PM  gallery
11/24/2018 10:33:22 AM developer
11/20/2018 7:22:19 PM  .markdownlint.json
...
```

您还可以设置为一个脚本块**表达式**密钥。
运行时`Sort-Object`cmdlet 执行脚本块，以及用于排序结果。

下面的示例对对象之间的时间跨度按降序进行排序**CreationTime**并**LastWriteTime**。

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = { $_.LastWriteTime - $_.CreationTime }; Descending = $true } |
  Format-Table -Property LastWriteTime, CreationTime
```

```output
LastWriteTime          CreationTime
-------------          ------------
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:15 AM
11/3/2018 9:58:17 AM   11/6/2017 10:10:11 AM
10/26/2018 4:50:21 PM  11/6/2017 10:10:11 AM
11/17/2018 1:10:57 PM  11/29/2017 5:48:30 PM
11/12/2018 6:29:53 PM  12/7/2017 7:57:07 PM
...
```

## <a name="tips"></a>提示

可以省略**属性**参数名称，如下所示：

```powershell
Sort-Object LastWriteTime, Name
```

此外，请参阅`Sort-Object`的内置别名， `sort`:

```powershell
sort LastWriteTime, Name
```

哈希表中进行排序的键可缩写如下所示：

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

在此示例中， **e**代表**表达式**，则**d**代表**降序**，并代表**升序**。

为了提高可读性，可以将哈希表放到一个单独的变量：

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```