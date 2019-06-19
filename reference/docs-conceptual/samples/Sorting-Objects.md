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
# <a name="sorting-objects"></a><span data-ttu-id="ef5f2-103">对对象进行排序</span><span class="sxs-lookup"><span data-stu-id="ef5f2-103">Sorting Objects</span></span>

<span data-ttu-id="ef5f2-104">可以通过使用 `Sort-Object` cmdlet 组织已显示的数据，使其更易于扫描。</span><span class="sxs-lookup"><span data-stu-id="ef5f2-104">We can organize displayed data to make it easier to scan by using the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="ef5f2-105">`Sort-Object` 依据一个或多个属性的名称进行排序，并返回按这些属性的值进行排序的数据。</span><span class="sxs-lookup"><span data-stu-id="ef5f2-105">`Sort-Object` takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

## <a name="basic-sorting"></a><span data-ttu-id="ef5f2-106">基本排序</span><span class="sxs-lookup"><span data-stu-id="ef5f2-106">Basic sorting</span></span>

<span data-ttu-id="ef5f2-107">请考虑列出当前目录中的子目录和文件的问题。</span><span class="sxs-lookup"><span data-stu-id="ef5f2-107">Consider the problem of listing subdirectories and files in the current directory.</span></span>
<span data-ttu-id="ef5f2-108">如果想要依次按 LastWriteTime 和 Name 进行排序，可键入：</span><span class="sxs-lookup"><span data-stu-id="ef5f2-108">If we want to sort by **LastWriteTime** and then by **Name**, we can do it by typing:</span></span>

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

<span data-ttu-id="ef5f2-109">也可通过指定 Descending 开关参数按相反顺序对对象进行排序。</span><span class="sxs-lookup"><span data-stu-id="ef5f2-109">You can also sort the objects in reverse order by specifying the **Descending** switch parameter.</span></span>

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

## <a name="using-hash-tables"></a><span data-ttu-id="ef5f2-110">使用哈希表</span><span class="sxs-lookup"><span data-stu-id="ef5f2-110">Using hash tables</span></span>

<span data-ttu-id="ef5f2-111">可以使用数组中的哈希表按不同顺序对不同属性进行排序。</span><span class="sxs-lookup"><span data-stu-id="ef5f2-111">You can sort different properties in different orders by using hash tables in an array.</span></span>
<span data-ttu-id="ef5f2-112">每个哈希表使用 Expression 键将属性名称指定为字符串，并使用 Ascending 或 Descending 键按 `$true` 或 `$false` 指定排序顺序。</span><span class="sxs-lookup"><span data-stu-id="ef5f2-112">Each hash table uses an **Expression** key to specify the property name as string and an **Ascending** or **Descending** key to specify the sort order by `$true` or `$false`.</span></span>
<span data-ttu-id="ef5f2-113">Expression 键是必需的。</span><span class="sxs-lookup"><span data-stu-id="ef5f2-113">The **Expression** key is mandatory.</span></span>
<span data-ttu-id="ef5f2-114">Ascending 或 Descending 键是可选的。</span><span class="sxs-lookup"><span data-stu-id="ef5f2-114">The **Ascending** or **Descending** key is optional.</span></span>

<span data-ttu-id="ef5f2-115">下面的示例按 LastWriteTime 降序和 Name 升序对对象进行排序。</span><span class="sxs-lookup"><span data-stu-id="ef5f2-115">The following example sorts objects in descending **LastWriteTime** order and ascending **Name** order.</span></span>

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

<span data-ttu-id="ef5f2-116">还可以将 scriptblock 设置为 Expression 键。</span><span class="sxs-lookup"><span data-stu-id="ef5f2-116">You can also set a scriptblock to the **Expression** key.</span></span>
<span data-ttu-id="ef5f2-117">运行 `Sort-Object` cmdlet 时，将执行 scriptblock 并使用结果进行排序。</span><span class="sxs-lookup"><span data-stu-id="ef5f2-117">When running the `Sort-Object` cmdlet, the scriptblock is executed and the result is used for sorting.</span></span>

<span data-ttu-id="ef5f2-118">下面的示例按 CreationTime 和 LastWriteTime 之间的时间跨度以降序对对象进行排序。</span><span class="sxs-lookup"><span data-stu-id="ef5f2-118">The following example sorts objects in descending order by the time span between **CreationTime** and **LastWriteTime**.</span></span>

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

## <a name="tips"></a><span data-ttu-id="ef5f2-119">提示</span><span class="sxs-lookup"><span data-stu-id="ef5f2-119">Tips</span></span>

<span data-ttu-id="ef5f2-120">可以省略 Property 参数名称，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ef5f2-120">You can omit the **Property** parameter name as following:</span></span>

```powershell
Sort-Object LastWriteTime, Name
```

<span data-ttu-id="ef5f2-121">此外，可以通过其内置别名 `sort` 来引用 `Sort-Object`：</span><span class="sxs-lookup"><span data-stu-id="ef5f2-121">Besides, you can refer to `Sort-Object` by its built-in alias, `sort`:</span></span>

```powershell
sort LastWriteTime, Name
```

<span data-ttu-id="ef5f2-122">用于排序的哈希表中的键可以缩写为：</span><span class="sxs-lookup"><span data-stu-id="ef5f2-122">The keys in the hash tables for sorting can be abbreviated as following:</span></span>

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

<span data-ttu-id="ef5f2-123">在此示例中，e 代表 Expression，d 代表 Descending，a 代表 Ascending。</span><span class="sxs-lookup"><span data-stu-id="ef5f2-123">In this example, the **e** stands for **Expression**, the **d** stands for **Descending**, and the **a** stands for **Ascending**.</span></span>

<span data-ttu-id="ef5f2-124">为了提高可读性，可以将哈希表置于一个单独的变量中：</span><span class="sxs-lookup"><span data-stu-id="ef5f2-124">To improve readability, you can place the hash tables into a separate variable:</span></span>

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```
