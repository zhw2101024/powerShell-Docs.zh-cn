---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 对对象进行排序
ms.openlocfilehash: ed78e7e333f3468781c9cd96df2194fbdfebe753
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030784"
---
# <a name="sorting-objects"></a>对对象进行排序

可以通过使用 `Sort-Object` cmdlet 组织已显示的数据，使其更易于扫描。 `Sort-Object` 依据一个或多个属性的名称进行排序，并返回按这些属性的值进行排序的数据。

## <a name="basic-sorting"></a>基本排序

请考虑列出当前目录中的子目录和文件的问题。
如果想要依次按 LastWriteTime 和 Name 进行排序，可键入：

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

也可通过指定 Descending 开关参数按相反顺序对对象进行排序。

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

可以使用数组中的哈希表按不同顺序对不同属性进行排序。
每个哈希表使用 Expression 键将属性名称指定为字符串，并使用 Ascending 或 Descending 键按 `$true` 或 `$false` 指定排序顺序。
Expression 键是必需的。
Ascending 或 Descending 键是可选的。

下面的示例按 LastWriteTime 降序和 Name 升序对对象进行排序。

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

还可以将 scriptblock 设置为 Expression 键。
运行 `Sort-Object` cmdlet 时，将执行 scriptblock 并使用结果进行排序。

下面的示例按 CreationTime 和 LastWriteTime 之间的时间跨度以降序对对象进行排序。

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

可以省略 Property 参数名称，如下所示：

```powershell
Sort-Object LastWriteTime, Name
```

此外，可以通过其内置别名 `sort` 来引用 `Sort-Object`：

```powershell
sort LastWriteTime, Name
```

用于排序的哈希表中的键可以缩写为：

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

在此示例中，e 代表 Expression，d 代表 Descending，a 代表 Ascending。

为了提高可读性，可以将哈希表置于一个单独的变量中：

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```
