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
# <a name="sorting-objects"></a><span data-ttu-id="6a653-103">对对象进行排序</span><span class="sxs-lookup"><span data-stu-id="6a653-103">Sorting Objects</span></span>

<span data-ttu-id="6a653-104">我们可以将组织显示的数据，使其更轻松地使用扫描`Sort-Object`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6a653-104">We can organize displayed data to make it easier to scan by using the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="6a653-105">`Sort-Object` 将一个或多个要作为排序依据的属性的名称并返回按这些属性值进行排序的数据。</span><span class="sxs-lookup"><span data-stu-id="6a653-105">`Sort-Object` takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

## <a name="basic-sorting"></a><span data-ttu-id="6a653-106">基本排序</span><span class="sxs-lookup"><span data-stu-id="6a653-106">Basic sorting</span></span>

<span data-ttu-id="6a653-107">请考虑列出当前目录中子目录和文件的问题。</span><span class="sxs-lookup"><span data-stu-id="6a653-107">Consider the problem of listing subdirectories and files in the current directory.</span></span>
<span data-ttu-id="6a653-108">如果我们想要作为排序依据**LastWriteTime**然后按**名称**，我们可以通过键入操作即可：</span><span class="sxs-lookup"><span data-stu-id="6a653-108">If we want to sort by **LastWriteTime** and then by **Name**, we can do it by typing:</span></span>

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

<span data-ttu-id="6a653-109">您还可以进行排序的对象按相反的顺序通过指定**降序**开关参数。</span><span class="sxs-lookup"><span data-stu-id="6a653-109">You can also sort the objects in reverse order by specifying the **Descending** switch parameter.</span></span>

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

## <a name="using-hash-tables"></a><span data-ttu-id="6a653-110">使用哈希表</span><span class="sxs-lookup"><span data-stu-id="6a653-110">Using hash tables</span></span>

<span data-ttu-id="6a653-111">可以通过使用哈希表数组中对不同属性进行不同的顺序进行排序。</span><span class="sxs-lookup"><span data-stu-id="6a653-111">You can sort different properties in different orders by using hash tables in an array.</span></span>
<span data-ttu-id="6a653-112">每个哈希表使用**表达式**键属性名称指定为字符串和一个**Ascending**或**降序**键以指定排序顺序由`$true`或`$false`.</span><span class="sxs-lookup"><span data-stu-id="6a653-112">Each hash table uses an **Expression** key to specify the property name as string and an **Ascending** or **Descending** key to specify the sort order by `$true` or `$false`.</span></span>
<span data-ttu-id="6a653-113">**表达式**键是必需的。</span><span class="sxs-lookup"><span data-stu-id="6a653-113">The **Expression** key is mandatory.</span></span>
<span data-ttu-id="6a653-114">**升序**或**降序**关键字是可选的。</span><span class="sxs-lookup"><span data-stu-id="6a653-114">The **Ascending** or **Descending** key is optional.</span></span>

<span data-ttu-id="6a653-115">下面的示例对按降序对象进行排序**LastWriteTime**顺序和升序**名称**顺序。</span><span class="sxs-lookup"><span data-stu-id="6a653-115">The following example sorts objects in descending **LastWriteTime** order and ascending **Name** order.</span></span>

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

<span data-ttu-id="6a653-116">您还可以设置为一个脚本块**表达式**密钥。</span><span class="sxs-lookup"><span data-stu-id="6a653-116">You can also set a scriptblock to the **Expression** key.</span></span>
<span data-ttu-id="6a653-117">运行时`Sort-Object`cmdlet 执行脚本块，以及用于排序结果。</span><span class="sxs-lookup"><span data-stu-id="6a653-117">When running the `Sort-Object` cmdlet, the scriptblock is executed and the result is used for sorting.</span></span>

<span data-ttu-id="6a653-118">下面的示例对对象之间的时间跨度按降序进行排序**CreationTime**并**LastWriteTime**。</span><span class="sxs-lookup"><span data-stu-id="6a653-118">The following example sorts objects in descending order by the time span between **CreationTime** and **LastWriteTime**.</span></span>

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

## <a name="tips"></a><span data-ttu-id="6a653-119">提示</span><span class="sxs-lookup"><span data-stu-id="6a653-119">Tips</span></span>

<span data-ttu-id="6a653-120">可以省略**属性**参数名称，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6a653-120">You can omit the **Property** parameter name as following:</span></span>

```powershell
Sort-Object LastWriteTime, Name
```

<span data-ttu-id="6a653-121">此外，请参阅`Sort-Object`的内置别名， `sort`:</span><span class="sxs-lookup"><span data-stu-id="6a653-121">Besides, you can refer to `Sort-Object` by its built-in alias, `sort`:</span></span>

```powershell
sort LastWriteTime, Name
```

<span data-ttu-id="6a653-122">哈希表中进行排序的键可缩写如下所示：</span><span class="sxs-lookup"><span data-stu-id="6a653-122">The keys in the hash tables for sorting can be abbreviated as following:</span></span>

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

<span data-ttu-id="6a653-123">在此示例中， **e**代表**表达式**，则**d**代表**降序**，并代表**升序**。</span><span class="sxs-lookup"><span data-stu-id="6a653-123">In this example, the **e** stands for **Expression**, the **d** stands for **Descending**, and the **a** stands for **Ascending**.</span></span>

<span data-ttu-id="6a653-124">为了提高可读性，可以将哈希表放到一个单独的变量：</span><span class="sxs-lookup"><span data-stu-id="6a653-124">To improve readability, you can place the hash tables into a separate variable:</span></span>

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```