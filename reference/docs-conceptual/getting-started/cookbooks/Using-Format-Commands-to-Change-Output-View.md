---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "使用格式命令更改输出视图"
ms.assetid: 63515a06-a6f7-4175-a45e-a0537f4f6d05
ms.openlocfilehash: 0163fcb21d586fc98902d9bdcfab6fe4eb97c225
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2017
---
# <a name="using-format-commands-to-change-output-view"></a><span data-ttu-id="ebad6-103">使用格式命令更改输出视图</span><span class="sxs-lookup"><span data-stu-id="ebad6-103">Using Format Commands to Change Output View</span></span>
<span data-ttu-id="ebad6-104">Windows PowerShell 具有一组 cmdlet，可让你控制要显示的特定对象的属性。</span><span class="sxs-lookup"><span data-stu-id="ebad6-104">Windows PowerShell has a set of cmdlets that allow you to control which properties are displayed for particular objects.</span></span> <span data-ttu-id="ebad6-105">所有 cmdlet 的名称都以谓词 **Format** 开头。</span><span class="sxs-lookup"><span data-stu-id="ebad6-105">The names of all the cmdlets begin with the verb **Format**.</span></span> <span data-ttu-id="ebad6-106">它们使你可以选择要显示的一个或多个属性。</span><span class="sxs-lookup"><span data-stu-id="ebad6-106">They let you select one or more properties to show.</span></span>

<span data-ttu-id="ebad6-107">**Format** cmdlet 包括 **Format-Wide**、**Format-List**、**Format-Table** 和 **Format-Custom**。</span><span class="sxs-lookup"><span data-stu-id="ebad6-107">The **Format** cmdlets are **Format-Wide**, **Format-List**, **Format-Table**, and **Format-Custom**.</span></span> <span data-ttu-id="ebad6-108">在本用户指南中，我们将只介绍 **Format-Wide**、**Format-List** 和 **Format-Table** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ebad6-108">We will only describe the **Format-Wide**, **Format-List**, and **Format-Table** cmdlets in this user's guide.</span></span>

<span data-ttu-id="ebad6-109">如果不指定要显示的特定属性，则每个 format cmdlet 都具有要使用的默认属性。</span><span class="sxs-lookup"><span data-stu-id="ebad6-109">Each format cmdlet has default properties that will be used if you do not specify specific properties to display.</span></span> <span data-ttu-id="ebad6-110">各 cmdlet 也使用相同的参数名称，**Property**，来指定要显示的属性。</span><span class="sxs-lookup"><span data-stu-id="ebad6-110">Each cmdlet also uses the same parameter name, **Property**, to specify which properties you want to display.</span></span> <span data-ttu-id="ebad6-111">因为 **Format-Wide** 只显示单个属性，其 **Property** 参数仅采用单个值，但 **Format-List** 和 **Format-Table** 的属性参数接受一系列属性名称。</span><span class="sxs-lookup"><span data-stu-id="ebad6-111">Because **Format-Wide** only shows a single property, its **Property** parameter only takes a single value, but the property parameters of **Format-List** and **Format-Table** will accept a list of property names.</span></span>

<span data-ttu-id="ebad6-112">如果你将命令 **Get-Process-Name powershell** 与 Windows PowerShell 运行的两个实例搭配使用，你将得到如下所示的输出：</span><span class="sxs-lookup"><span data-stu-id="ebad6-112">If you use the command **Get-Process -Name powershell** with two instances of Windows PowerShell running, you get output that looks like this:</span></span>

```
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

<span data-ttu-id="ebad6-113">在本部分接下来的内容中，我们将探究如何使用 **Format** cmdlet 更改此命令的输出的显示方式。</span><span class="sxs-lookup"><span data-stu-id="ebad6-113">In the rest of this section, we will explore how to use **Format** cmdlets to change the way the output of this command is displayed.</span></span>

### <a name="using-format-wide-for-single-item-output"></a><span data-ttu-id="ebad6-114">将 Format-Wide 用于 Single-Item 输出</span><span class="sxs-lookup"><span data-stu-id="ebad6-114">Using Format-Wide for Single-Item Output</span></span>
<span data-ttu-id="ebad6-115">默认情况下，**Format-Wide** 只显示对象的默认属性。</span><span class="sxs-lookup"><span data-stu-id="ebad6-115">The **Format-Wide** cmdlet, by default, displays only the default property of an object.</span></span> <span data-ttu-id="ebad6-116">与每个对象关联的信息将显示在单个列中：</span><span class="sxs-lookup"><span data-stu-id="ebad6-116">The information associated with each object is displayed in a single column:</span></span>

```
PS> Get-Process -Name powershell | Format-Wide

powershell                              powershell
```

<span data-ttu-id="ebad6-117">你还可以指定非默认属性：</span><span class="sxs-lookup"><span data-stu-id="ebad6-117">You can also specify a non-default property:</span></span>

```
PS> Get-Process -Name powershell | Format-Wide -Property Id

2760                                    3448
```

#### <a name="controlling-format-wide-display-with-column"></a><span data-ttu-id="ebad6-118">使用列控制 Format-Wide 显示</span><span class="sxs-lookup"><span data-stu-id="ebad6-118">Controlling Format-Wide Display with Column</span></span>
<span data-ttu-id="ebad6-119">使用 **Format-Wide** cmdlet，每次只能显示一个属性。</span><span class="sxs-lookup"><span data-stu-id="ebad6-119">With the **Format-Wide** cmdlet, you can only display a single property at a time.</span></span> <span data-ttu-id="ebad6-120">这对于显示每行只显示一个元素的简单列表很有用。</span><span class="sxs-lookup"><span data-stu-id="ebad6-120">This makes it useful for displaying simple lists that show only one element per line.</span></span> <span data-ttu-id="ebad6-121">若要获取简单列表，通过键入以下内容将 **Column** 参数的值设为 1：</span><span class="sxs-lookup"><span data-stu-id="ebad6-121">To get a simple listing, set the value of the **Column** parameter to 1 by typing:</span></span>

```
Get-Command Format-Wide -Property Name -Column 1
```

### <a name="using-format-list-for-a-list-view"></a><span data-ttu-id="ebad6-122">将 Format-List 用于列表视图</span><span class="sxs-lookup"><span data-stu-id="ebad6-122">Using Format-List for a List View</span></span>
<span data-ttu-id="ebad6-123">**Format-List** cmdlet 以列表的形式显示对象，同时标记每个属性并在单独的行上显示：</span><span class="sxs-lookup"><span data-stu-id="ebad6-123">The **Format-List** cmdlet displays an object in the form of a listing, with each property labeled and displayed on a separate line:</span></span>

```
PS> Get-Process -Name powershell | Format-List

Id      : 2760
Handles : 1242
CPU     : 3.03125
Name    : powershell

Id      : 3448
Handles : 328
CPU     : 1.0625
Name    : powershell
```

<span data-ttu-id="ebad6-124">你可以指定所需数目的属性：</span><span class="sxs-lookup"><span data-stu-id="ebad6-124">You can specify as many properties as you want:</span></span>

```
PS> Get-Process -Name powershell | Format-List -Property ProcessName,FileVersion
,StartTime,Id

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:42:00
Id          : 2760

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:54:28
Id          : 3448
```

#### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a><span data-ttu-id="ebad6-125">通过将 Format-List 与通配符搭配使用获取详细信息</span><span class="sxs-lookup"><span data-stu-id="ebad6-125">Getting Detailed Information by Using Format-List with Wildcards</span></span>
<span data-ttu-id="ebad6-126">**Format-List** cmdlet 使你可以将通配符用作其 **Property** 参数的值。</span><span class="sxs-lookup"><span data-stu-id="ebad6-126">The **Format-List** cmdlet lets you use a wildcard as the value of its **Property** parameter.</span></span> <span data-ttu-id="ebad6-127">这样便可以显示详细信息。</span><span class="sxs-lookup"><span data-stu-id="ebad6-127">This lets you display detailed information.</span></span> <span data-ttu-id="ebad6-128">通常情况下，对象包含的信息比你需要的多，这就是默认情况下 Windows PowerShell 不显示所有属性值的原因。</span><span class="sxs-lookup"><span data-stu-id="ebad6-128">Often, objects include more information than you need, which is why Windows PowerShell does not show all property values by default.</span></span> <span data-ttu-id="ebad6-129">若要显示对象的全部属性，则使用 **Format-List-Property \&#42;**命令。</span><span class="sxs-lookup"><span data-stu-id="ebad6-129">To show all of properties of an object, use the **Format-List -Property \&#42;** command.</span></span> <span data-ttu-id="ebad6-130">下面的命令针对单个进程生成超过 60 行的输出：</span><span class="sxs-lookup"><span data-stu-id="ebad6-130">The following command generates over 60 lines of output for a single process:</span></span>

```
Get-Process -Name powershell | Format-List -Property *
```

<span data-ttu-id="ebad6-131">虽然 **Format-List** 命令对显示详细信息很有用，但如果你想要包括多个项目的输出的概述，更常用的是一个更简单的表格视图。</span><span class="sxs-lookup"><span data-stu-id="ebad6-131">Although the **Format-List** command is useful for showing detail, if you want an overview of output that includes many items, a simpler tabular view is often more useful.</span></span>

### <a name="using-format-table-for-tabular-output"></a><span data-ttu-id="ebad6-132">将 Format-Table 用于表格输出</span><span class="sxs-lookup"><span data-stu-id="ebad6-132">Using Format-Table for Tabular Output</span></span>
<span data-ttu-id="ebad6-133">如果你在没有指定属性名称的情况下使用 **Format-Table** cmdlet 来格式化 **Get-Process** 命令的输出，你所得到的输出会和未执行任何格式设置时得到的完全一样。</span><span class="sxs-lookup"><span data-stu-id="ebad6-133">If you use the **Format-Table** cmdlet with no property names specified to format the output of the **Get-Process** command, you get exactly the same output as you do without performing any formatting.</span></span> <span data-ttu-id="ebad6-134">原因是进程通常以表格格式显示，和大多数 Windows PowerShell 对象一样。</span><span class="sxs-lookup"><span data-stu-id="ebad6-134">The reason is that processes are usually displayed in a tabular format, as are most Windows PowerShell objects.</span></span>

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

#### <a name="improving-format-table-output-autosize"></a><span data-ttu-id="ebad6-135">改进 Format-Table 输出（自动调整大小）</span><span class="sxs-lookup"><span data-stu-id="ebad6-135">Improving Format-Table Output (AutoSize)</span></span>
<span data-ttu-id="ebad6-136">尽管表格视图对显示大量可比较的信息很有用，但如果显示区域对于数据来说太窄，则可能导致数据难以理解。</span><span class="sxs-lookup"><span data-stu-id="ebad6-136">Although a tabular view is useful for displaying a lot of comparable information, it may be difficult to interpret if the display is too narrow for the data.</span></span> <span data-ttu-id="ebad6-137">例如，如果你尝试显示进程路径、ID、名称和公司，你获得的却是进程路径和公司列的截断了的输出：</span><span class="sxs-lookup"><span data-stu-id="ebad6-137">For example, if you try to display process path, ID, name, and company, you get truncated output for the process path and the company column:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

<span data-ttu-id="ebad6-138">当你运行 **Format-Table** 命令时，如果你指定 **AutoSize** 参数，Windows PowerShell 会根据你要显示的实际数据来计算列宽。</span><span class="sxs-lookup"><span data-stu-id="ebad6-138">If you specify the **AutoSize** parameter when you run the **Format-Table** command, Windows PowerShell will calculate column widths based on the actual data you are going to display.</span></span> <span data-ttu-id="ebad6-139">这使得**路径**列可读，但公司列将仍保持截断状态：</span><span class="sxs-lookup"><span data-stu-id="ebad6-139">This makes the **Path** column readable, but the company column remains truncated:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

<span data-ttu-id="ebad6-140">**Format-Table** cmdlet 仍可能会截断数据，但仅会在屏幕的末尾处进行截断。</span><span class="sxs-lookup"><span data-stu-id="ebad6-140">The **Format-Table** cmdlet might still truncate data, but it will only do so at the end of the screen.</span></span> <span data-ttu-id="ebad6-141">除最后一个显示的属性外，会让所有属性获得各自所需的大小，以使最长的数据元素得以正确显示。</span><span class="sxs-lookup"><span data-stu-id="ebad6-141">Properties, other than the last one displayed, are given as much size as they need for their longest data element to display correctly.</span></span> <span data-ttu-id="ebad6-142">如果你交换**属性**值列表中**路径**和**公司**的位置，你会发现公司名称是可见的，但路径则被截断：</span><span class="sxs-lookup"><span data-stu-id="ebad6-142">You can see that company name is visible but path is truncated if you swap the locations of **Path** and **Company** in the **Property** value list:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

<span data-ttu-id="ebad6-143">**Format-Table** 命令假定属性距离属性列表的开头越近，则该属性越重要。</span><span class="sxs-lookup"><span data-stu-id="ebad6-143">The **Format-Table** command assumes that the nearer a property is to the beginning of the property list, the more important it is.</span></span> <span data-ttu-id="ebad6-144">因此，它会尝试完整显示离列表开头最近的那些属性。</span><span class="sxs-lookup"><span data-stu-id="ebad6-144">So it attempts to display the properties nearest the beginning completely.</span></span> <span data-ttu-id="ebad6-145">如果 **Format-Table** 命令无法显示所有属性，它将从显示中删除某些列，并发出警告。</span><span class="sxs-lookup"><span data-stu-id="ebad6-145">If the **Format-Table** command cannot display all the properties, it will remove some columns from the display and provide a warning.</span></span> <span data-ttu-id="ebad6-146">如果你使**名称**变成列表中的最后一个属性，便可以看到这一行为：</span><span class="sxs-lookup"><span data-stu-id="ebad6-146">You can see this behavior if you make **Name** the last property in the list:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

<span data-ttu-id="ebad6-147">在上面的输出中，将截断 ID 列以使其适合列表，并叠加列标题。</span><span class="sxs-lookup"><span data-stu-id="ebad6-147">In the output above, the ID column is truncated to make it fit into the listing, and the column headings are stacked up.</span></span> <span data-ttu-id="ebad6-148">自动调整列大小不会始终执行所需的操作。</span><span class="sxs-lookup"><span data-stu-id="ebad6-148">Automatically resizing the columns does not always do what you want.</span></span>

#### <a name="wrapping-format-table-output-in-columns-wrap"></a><span data-ttu-id="ebad6-149">让列中的 Format-Table 输出自动换行 (Wrap)</span><span class="sxs-lookup"><span data-stu-id="ebad6-149">Wrapping Format-Table Output in Columns (Wrap)</span></span>
<span data-ttu-id="ebad6-150">你可以通过使用 **Wrap** 参数让较长的 **Format-Table** 数据在其显示列中自动换行。</span><span class="sxs-lookup"><span data-stu-id="ebad6-150">You can force lengthy **Format-Table** data to wrap within its display column by using the **Wrap** parameter.</span></span> <span data-ttu-id="ebad6-151">仅使用 **Wrap** 参数不一定会实现所需的操作，因为如果你不同时指定 **AutoSize**，它会使用默认设置：</span><span class="sxs-lookup"><span data-stu-id="ebad6-151">Using the **Wrap** parameter alone will not necessarily do what you expect, since it uses default settings if you do not also specify **AutoSize**:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

<span data-ttu-id="ebad6-152">使用 **Wrap** 参数的一个优点是基本不会减慢进程速度。</span><span class="sxs-lookup"><span data-stu-id="ebad6-152">An advantage of using the **Wrap** parameter by itself is that it does not slow down processing very much.</span></span> <span data-ttu-id="ebad6-153">如果你对大型目录系统执行递归文件列表，那么如果你使用 **AutoSize**，可能得耗用大量时间和内存，才能显示第一批输出项。</span><span class="sxs-lookup"><span data-stu-id="ebad6-153">If you perform a recursive file listing of a large directory system, it might take a very long time and use a lot of memory before displaying the first output items if you use **AutoSize**.</span></span>

<span data-ttu-id="ebad6-154">如果你并不关心系统负载，那么结合使用 **AutoSize** 和 **Wrap** 参数则会获得良好的效果。</span><span class="sxs-lookup"><span data-stu-id="ebad6-154">If you are not concerned about system load, then **AutoSize** works well with the **Wrap** parameter.</span></span> <span data-ttu-id="ebad6-155">会始终向初始列分配其所需的宽度以使其中的项显示在一行上，就和你指定 **AutoSize** 而不使用 **Wrap** 参数的效果一样。</span><span class="sxs-lookup"><span data-stu-id="ebad6-155">The initial columns are always allotted as much width as they need to display items on one line, just as when you specify **AutoSize** without the **Wrap** parameter.</span></span> <span data-ttu-id="ebad6-156">唯一的不同是最后一列将自动换行（如有必要的话）：</span><span class="sxs-lookup"><span data-stu-id="ebad6-156">The only difference is that the final column will be wrapped if necessary:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

<span data-ttu-id="ebad6-157">如果你先指定最宽的列，则某些列可能无法显示，因此最安全的做法是先指定最小的数据元素。</span><span class="sxs-lookup"><span data-stu-id="ebad6-157">Some columns might not be displayed if you specify the widest columns first, so it is safest to specify the smallest data elements first.</span></span> <span data-ttu-id="ebad6-158">在下面的示例中，我们首先指定特别宽的路径元素，甚至使用自动换行，但仍丢失了最后的**名称**列：</span><span class="sxs-lookup"><span data-stu-id="ebad6-158">In the following example, we specify the extremely wide path element first, and even with wrapping, we still lose the final **Name** column:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

#### <a name="organizing-table-output--groupby"></a><span data-ttu-id="ebad6-159">组织选项卡输出 (-GroupBy)</span><span class="sxs-lookup"><span data-stu-id="ebad6-159">Organizing Table Output (-GroupBy)</span></span>
<span data-ttu-id="ebad6-160">用于表格输出控制的另一个有用参数是 **GroupBy**。</span><span class="sxs-lookup"><span data-stu-id="ebad6-160">Another useful parameter for tabular output control is **GroupBy**.</span></span> <span data-ttu-id="ebad6-161">较长的列表可能尤其难以进行比较。</span><span class="sxs-lookup"><span data-stu-id="ebad6-161">Longer tabular listings in particular may be hard to compare.</span></span> <span data-ttu-id="ebad6-162">**GroupBy** 参数基于属性值对输出进行分组</span><span class="sxs-lookup"><span data-stu-id="ebad6-162">The **GroupBy** parameter groups output based on a property value.</span></span> <span data-ttu-id="ebad6-163">例如，我们可以按公司对进程分组以便于检查，同时从属性列表中省略公司的值：</span><span class="sxs-lookup"><span data-stu-id="ebad6-163">For example, we can group processes by company for easier inspection, omitting the company value from the property listing:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```

