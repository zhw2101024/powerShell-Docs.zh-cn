---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 使用文件、文件夹和注册表项
ms.assetid: e6cf87aa-b5f8-48d5-a75a-7cb7ecb482dc
ms.openlocfilehash: a09b127d4ba37d33cb4c0f0ce0819e645fd4b137
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="working-with-files-folders-and-registry-keys"></a><span data-ttu-id="28250-103">使用文件、文件夹和注册表项</span><span class="sxs-lookup"><span data-stu-id="28250-103">Working With Files, Folders and Registry Keys</span></span>

<span data-ttu-id="28250-104">Windows PowerShell 使用名词 **Item** 来引用在 Windows PowerShell 驱动器上找到的项。</span><span class="sxs-lookup"><span data-stu-id="28250-104">Windows PowerShell uses the noun **Item** to refer to items found on a Windows PowerShell drive.</span></span> <span data-ttu-id="28250-105">处理 Windows PowerShell FileSystem 提供程序时，**Item** 可能是文件、文件夹或 Windows PowerShell 驱动器。</span><span class="sxs-lookup"><span data-stu-id="28250-105">When dealing with the Windows PowerShell FileSystem provider, an **Item** might be a file, a folder, or the Windows PowerShell drive.</span></span> <span data-ttu-id="28250-106">列出并使用这些项是大部分管理设置中的关键基本任务，因此我们想要详细讨论这些任务。</span><span class="sxs-lookup"><span data-stu-id="28250-106">Listing and working with these items is a critical basic task in most administrative settings, so we want to discuss these tasks in detail.</span></span>

### <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a><span data-ttu-id="28250-107">枚举文件、文件夹和注册表项 (Get-ChildItem)</span><span class="sxs-lookup"><span data-stu-id="28250-107">Enumerating Files, Folders, and Registry Keys (Get-ChildItem)</span></span>

<span data-ttu-id="28250-108">由于从特定位置获取项的集合是很常见的任务，因此 **Get-ChildItem** cmdlet 专门用于返回在容器（例如某个文件夹）中找到的所有项。</span><span class="sxs-lookup"><span data-stu-id="28250-108">Since getting a collection of items from a particular location is such a common task, the **Get-ChildItem** cmdlet is designed specifically to return all items found within a container such as a folder.</span></span>

<span data-ttu-id="28250-109">如果你希望返回直接包含在文件夹 C:\\Windows 内的所有文件和文件夹，请键入：</span><span class="sxs-lookup"><span data-stu-id="28250-109">If you want to return all files and folders that are contained directly within the folder C:\\Windows, type:</span></span>

```
PS> Get-ChildItem -Path C:\Windows
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-16   8:10 AM          0 0.log
-a---        2005-11-29   3:16 PM         97 acc1.txt
-a---        2005-10-23  11:21 PM       3848 actsetup.log
...
```

<span data-ttu-id="28250-110">列出操作看起来和你在 **Cmd.exe** 中输入 **dir** 命令或在 UNIX 命令 shell 中输入 **ls** 命令时类似。</span><span class="sxs-lookup"><span data-stu-id="28250-110">The listing looks similar to what you would see when you enter the **dir** command in **Cmd.exe**, or the **ls** command in a UNIX command shell.</span></span>

<span data-ttu-id="28250-111">你可以通过使用 **Get-ChildItem** cmdlet 的参数来执行非常复杂的列出操作。</span><span class="sxs-lookup"><span data-stu-id="28250-111">You can perform very complex listings by using parameters of the **Get-ChildItem** cmdlet.</span></span> <span data-ttu-id="28250-112">接下来，我们将介绍一些方案。</span><span class="sxs-lookup"><span data-stu-id="28250-112">We will look at a few scenarios next.</span></span> <span data-ttu-id="28250-113">你可以通过键入以下内容来查看 **Get-ChildItem** cmdlet 的语法：</span><span class="sxs-lookup"><span data-stu-id="28250-113">You can see the syntax the **Get-ChildItem** cmdlet by typing:</span></span>

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

<span data-ttu-id="28250-114">可以混合并匹配这些参数以获取高度自定义的输出。</span><span class="sxs-lookup"><span data-stu-id="28250-114">These parameters can be mixed and matched to get highly customized output.</span></span>

#### <a name="listing-all-contained-items--recurse"></a><span data-ttu-id="28250-115">列出所有包含的项 (-Recurse)</span><span class="sxs-lookup"><span data-stu-id="28250-115">Listing all Contained Items (-Recurse)</span></span>

<span data-ttu-id="28250-116">若要查看 Windows 文件夹内的项和子文件夹内包含的任何项，请使用 **Get-ChildItem** 的 **Recurse** 参数。</span><span class="sxs-lookup"><span data-stu-id="28250-116">To see both the items inside a Windows folder and any items that are contained within the subfolders, use the **Recurse** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="28250-117">此列出操作显示 Windows 文件夹内的所有内容及其子文件夹中的项。</span><span class="sxs-lookup"><span data-stu-id="28250-117">The listing displays everything within the Windows folder and the items in its subfolders.</span></span> <span data-ttu-id="28250-118">例如：</span><span class="sxs-lookup"><span data-stu-id="28250-118">For example:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

#### <a name="filtering-items-by-name--name"></a><span data-ttu-id="28250-119">按名称筛选项 (-Name)</span><span class="sxs-lookup"><span data-stu-id="28250-119">Filtering Items by Name (-Name)</span></span>

<span data-ttu-id="28250-120">若要仅显示项的名称，请使用 **Get-Childitem** 的 **Name** 参数：</span><span class="sxs-lookup"><span data-stu-id="28250-120">To display only the names of items, use the **Name** parameter of **Get-Childitem**:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

#### <a name="forcibly-listing-hidden-items--force"></a><span data-ttu-id="28250-121">强制列出隐藏的项 (-Force)</span><span class="sxs-lookup"><span data-stu-id="28250-121">Forcibly Listing Hidden Items (-Force)</span></span>

<span data-ttu-id="28250-122">正常情况下在文件资源管理器或 Cmd.exe 中不可见的项不会在 **Get-ChildItem** 命令的输出中显示。</span><span class="sxs-lookup"><span data-stu-id="28250-122">Items that are normally invisible in File Explorer or Cmd.exe are not displayed in the output of a **Get-ChildItem** command.</span></span> <span data-ttu-id="28250-123">若要显示隐藏的项，请使用 **Get-ChildItem** 的 **Force** 参数。</span><span class="sxs-lookup"><span data-stu-id="28250-123">To display hidden items, use the **Force** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="28250-124">例如：</span><span class="sxs-lookup"><span data-stu-id="28250-124">For example:</span></span>

```powershell
Get-ChildItem -Path C:\Windows -Force
```

<span data-ttu-id="28250-125">此参数的名称为 Force，因为你可以强制替代 **Get-ChildItem** 命令的正常行为。</span><span class="sxs-lookup"><span data-stu-id="28250-125">This parameter is named Force because you can forcibly override the normal behavior of the **Get-ChildItem** command.</span></span> <span data-ttu-id="28250-126">Force 是一个广泛使用的参数，此参数可强制执行 cmdlet 通常不会执行的操作，尽管它不会执行任何危害系统安全的操作。</span><span class="sxs-lookup"><span data-stu-id="28250-126">Force is a widely used parameter that forces an action that a cmdlet would not normally perform, although it will not perform any action that compromises the security of the system.</span></span>

#### <a name="matching-item-names-with-wildcards"></a><span data-ttu-id="28250-127">使用通配符匹配项名称</span><span class="sxs-lookup"><span data-stu-id="28250-127">Matching Item Names with Wildcards</span></span>

<span data-ttu-id="28250-128">**Get-ChildItem** 命令支持要列出的项路径中的通配符。</span><span class="sxs-lookup"><span data-stu-id="28250-128">**The Get-ChildItem** command accepts wildcards in the path of the items to list.</span></span>

<span data-ttu-id="28250-129">由于通配符匹配由 Windows PowerShell 引擎处理，因此接受通配符的所有 cmdlet 使用相同的表示法，并具有相同的匹配行为。</span><span class="sxs-lookup"><span data-stu-id="28250-129">Because wildcard matching is handled by the Windows PowerShell engine, all cmdlets that accepts wildcards use the same notation and have the same matching behavior.</span></span> <span data-ttu-id="28250-130">Windows PowerShell 通配符表示法包括：</span><span class="sxs-lookup"><span data-stu-id="28250-130">The Windows PowerShell wildcard notation includes:</span></span>

- <span data-ttu-id="28250-131">星号 (\*) 匹配零个或多个出现的任何字符。</span><span class="sxs-lookup"><span data-stu-id="28250-131">Asterisk (\*)matches zero or more occurrences of any character.</span></span>

- <span data-ttu-id="28250-132">问号 (?) 完全匹配一个字符。</span><span class="sxs-lookup"><span data-stu-id="28250-132">Question mark (?) matches exactly one character.</span></span>

- <span data-ttu-id="28250-133">左括号 (\[) 字符和右括号 (]) 字符括起一组要匹配的字符。</span><span class="sxs-lookup"><span data-stu-id="28250-133">Left bracket (\[) character and right bracket (]) character surround a set of characters to be matched.</span></span>

<span data-ttu-id="28250-134">下面是一些通配符规则工作原理的示例。</span><span class="sxs-lookup"><span data-stu-id="28250-134">Here are some examples of how wildcard specification works.</span></span>

<span data-ttu-id="28250-135">若要在 Windows 目录中查找带有后缀 **.log** 并且基名称中正好有五个字符的所有文件，请输入以下命令：</span><span class="sxs-lookup"><span data-stu-id="28250-135">To find all files in the Windows directory with the suffix **.log** and exactly five characters in the base name, enter the following command:</span></span>

```
PS> Get-ChildItem -Path C:\Windows\?????.log

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
...
-a---        2006-05-11   6:31 PM     204276 ocgen.log
-a---        2006-05-11   6:31 PM      22365 ocmsn.log
...
-a---        2005-11-11   4:55 AM         64 setup.log
-a---        2005-12-15   2:24 PM      17719 VxSDM.log
...
```

<span data-ttu-id="28250-136">若要在 Windows 目录中查找以字母 **x** 开头的所有文件，请键入：</span><span class="sxs-lookup"><span data-stu-id="28250-136">To find all files that begin with the letter **x** in the Windows directory, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\x*
```

<span data-ttu-id="28250-137">若要查找名称以 **x** 或 **z** 开头的所有文件，请键入：</span><span class="sxs-lookup"><span data-stu-id="28250-137">To find all files whose names begin with **x** or **z**, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

#### <a name="excluding-items--exclude"></a><span data-ttu-id="28250-138">排除项 (-Exclude)</span><span class="sxs-lookup"><span data-stu-id="28250-138">Excluding Items (-Exclude)</span></span>

<span data-ttu-id="28250-139">你可以通过使用 Get-ChildItem 的 **Exclude** 参数来排除特定项。</span><span class="sxs-lookup"><span data-stu-id="28250-139">You can exclude specific items by using the **Exclude** parameter of Get-ChildItem.</span></span> <span data-ttu-id="28250-140">这可让你在单个声明中执行复杂的筛选。</span><span class="sxs-lookup"><span data-stu-id="28250-140">This lets you perform complex filtering in a single statement.</span></span>

<span data-ttu-id="28250-141">例如，假设你正尝试在 System32 文件夹中查找 Windows Time Service DLL，但是你只记得 DLL 名称以“W”开头并且其中有“32”。</span><span class="sxs-lookup"><span data-stu-id="28250-141">For example, suppose you are trying to find the Windows Time Service DLL in the System32 folder, and all you can remember about the DLL name is that it begins with "W" and has "32" in it.</span></span>

<span data-ttu-id="28250-142">类似于 **w\&#42;32\&#42;.dll** 的表达式将找到满足条件的所有 DLL，但它也可能返回名称中包含“95”或“16”的 Windows 95 和 16 位 Windows 兼容性 DLL。</span><span class="sxs-lookup"><span data-stu-id="28250-142">An expression like **w\&#42;32\&#42;.dll** will find all DLLs that satisfy the conditions, but it may also return the Windows 95 and 16-bit Windows compatibility DLLs that include "95" or "16" in their names.</span></span> <span data-ttu-id="28250-143">你可以通过将 **Exclude** 参数与模式 **\&#42;\[9516]\&#42;** 一起使用来忽略名称中含有任意这些数字的文件：</span><span class="sxs-lookup"><span data-stu-id="28250-143">You can omit files that have any of these numbers in their names by using the **Exclude** parameter with the pattern **\&#42;\[9516]\&#42;**:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS\System32\w*32*.dll -Exclude *[9516]*

Directory: Microsoft.PowerShell.Core\FileSystem::C:\WINDOWS\System32
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     174592 w32time.dll
-a---        2004-08-04   8:00 AM      22016 w32topl.dll
-a---        2004-08-04   8:00 AM     101888 win32spl.dll
-a---        2004-08-04   8:00 AM     172032 wldap32.dll
-a---        2004-08-04   8:00 AM     264192 wow32.dll
-a---        2004-08-04   8:00 AM      82944 ws2_32.dll
-a---        2004-08-04   8:00 AM      42496 wsnmp32.dll
-a---        2004-08-04   8:00 AM      22528 wsock32.dll
-a---        2004-08-04   8:00 AM      18432 wtsapi32.dll
```

#### <a name="mixing-get-childitem-parameters"></a><span data-ttu-id="28250-144">混合使用 Get-ChildItem 参数</span><span class="sxs-lookup"><span data-stu-id="28250-144">Mixing Get-ChildItem Parameters</span></span>

<span data-ttu-id="28250-145">你可以在同一命令中使用 **Get-ChildItem** cmdlet 的多个参数。</span><span class="sxs-lookup"><span data-stu-id="28250-145">You can use several of the parameters of the **Get-ChildItem** cmdlet in the same command.</span></span> <span data-ttu-id="28250-146">在混合使用参数之前，请确保你了解通配符匹配。</span><span class="sxs-lookup"><span data-stu-id="28250-146">Before you mix parameters, be sure that you understand wildcard matching.</span></span> <span data-ttu-id="28250-147">例如，以下命令不会返回任何结果：</span><span class="sxs-lookup"><span data-stu-id="28250-147">For example, the following command returns no results:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

<span data-ttu-id="28250-148">即使 Windows 文件夹中有两个以字母“z”开头的 DLL，也没有结果。</span><span class="sxs-lookup"><span data-stu-id="28250-148">There are no results, even though there are two DLLs that begin with the letter "z" in the Windows folder.</span></span>

<span data-ttu-id="28250-149">由于我们已将通配符指定为路径的一部分，因此未返回任何结果。</span><span class="sxs-lookup"><span data-stu-id="28250-149">No results were returned because we specified the wildcard as part of the path.</span></span> <span data-ttu-id="28250-150">即使命令是递归的，**Get-ChildItem** cmdlet 也会将项限制为 Windows 文件夹中名称以“.dll”结尾的项。</span><span class="sxs-lookup"><span data-stu-id="28250-150">Even though the command was recursive, the **Get-ChildItem** cmdlet restricted the items to those that are in the Windows folder with names ending with ".dll".</span></span>

<span data-ttu-id="28250-151">若要指定名称匹配特殊模式的文件的递归搜索，请使用 **-Include** 参数。</span><span class="sxs-lookup"><span data-stu-id="28250-151">To specify a recursive search for files whose names match a special pattern, use the **-Include** parameter.</span></span>

```
PS> Get-ChildItem -Path C:\Windows -Include *.dll -Recurse -Exclude [a-y]*.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32\Setup

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM       8261 zoneoc.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     337920 zipfldr.dll
```