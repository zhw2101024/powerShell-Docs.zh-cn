---
ms.date: 10/22/2019
keywords: powershell,cmdlet
title: 使用格式命令更改输出视图
ms.openlocfilehash: 9d9854362b5150a99bdd0c02518599840c1fd42d
ms.sourcegitcommit: 36e4c79afda2ce11febd93951e143687245f0b50
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/02/2019
ms.locfileid: "73444427"
---
# <a name="using-format-commands-to-change-output-view"></a><span data-ttu-id="5e9ff-103">使用格式命令更改输出视图</span><span class="sxs-lookup"><span data-stu-id="5e9ff-103">Using Format Commands to Change Output View</span></span>

<span data-ttu-id="5e9ff-104">PowerShell 具有一组 cmdlet，可让你控制特定对象的属性的显示方式。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-104">PowerShell has a set of cmdlets that allow you to control how properties are displayed for particular objects.</span></span> <span data-ttu-id="5e9ff-105">所有 cmdlet 的名称都以谓词 `Format` 开头。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-105">The names of all the cmdlets begin with the verb `Format`.</span></span> <span data-ttu-id="5e9ff-106">它们使你可以选择要显示的属性。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-106">They let you select which properties you want to show.</span></span>

```powershell
Get-Command -Verb Format -Module Microsoft.PowerShell.Utility
```

```Output
CommandType     Name               Version    Source
-----------     ----               -------    ------
Cmdlet          Format-Custom      6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Hex         6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-List        6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Table       6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Wide        6.1.0.0    Microsoft.PowerShell.Utility
```

<span data-ttu-id="5e9ff-107">本文介绍 `Format-Wide`、`Format-List` 和 `Format-Table` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-107">This article describes the `Format-Wide`, `Format-List`, and `Format-Table` cmdlets.</span></span>

<span data-ttu-id="5e9ff-108">PowerShell 中的每个对象类型都具有未指定要显示的属性时使用的默认属性。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-108">Each object type in PowerShell has default properties that are used when you don't specify which properties to display.</span></span> <span data-ttu-id="5e9ff-109">各 cmdlet 也使用相同的 Property 参数，来指定要显示的属性  。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-109">Each cmdlet also uses the same **Property** parameter to specify which properties you want to display.</span></span> <span data-ttu-id="5e9ff-110">因为 `Format-Wide` 只显示单个属性，其 Property 参数仅采用单个值，但 `Format-List` 和 `Format-Table` 的属性参数接受一系列属性名称  。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-110">Because `Format-Wide` only shows a single property, its **Property** parameter only takes a single value, but the property parameters of `Format-List` and `Format-Table` accept a list of property names.</span></span>

<span data-ttu-id="5e9ff-111">在此示例中，`Get-Process` cmdlet 的默认输出显示，我们有两个正在运行的 Internet Explorer 实例。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-111">In this example, the default output of `Get-Process` cmdlet shows that we have two instances of Internet Explorer running.</span></span>

```powershell
Get-Process -Name iexplore
```

<span data-ttu-id="5e9ff-112">Process 对象的默认格式显示如下属性  ：</span><span class="sxs-lookup"><span data-stu-id="5e9ff-112">The default format for **Process** objects displays the properties shown here:</span></span>

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     32    25.52      10.25      13.11   12808   1 iexplore
     52    11.46      26.46       3.55   21748   1 iexplore
```

## <a name="using-format-wide-for-single-item-output"></a><span data-ttu-id="5e9ff-113">将 Format-Wide 用于 Single-Item 输出</span><span class="sxs-lookup"><span data-stu-id="5e9ff-113">Using Format-Wide for Single-Item Output</span></span>

<span data-ttu-id="5e9ff-114">默认情况下，`Format-Wide` cmdlet 只显示对象的默认属性。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-114">The `Format-Wide` cmdlet, by default, displays only the default property of an object.</span></span> <span data-ttu-id="5e9ff-115">与每个对象关联的信息将显示在单个列中：</span><span class="sxs-lookup"><span data-stu-id="5e9ff-115">The information associated with each object is displayed in a single column:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide
```

```Output
Format-Custom          Format-Hex
Format-List            Format-Table
Format-Wide
```

<span data-ttu-id="5e9ff-116">你还可以指定非默认属性：</span><span class="sxs-lookup"><span data-stu-id="5e9ff-116">You can also specify a non-default property:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun
```

```Output
Custom                 Hex
List                   Table
Wide
```

### <a name="controlling-format-wide-display-with-column"></a><span data-ttu-id="5e9ff-117">使用列控制 Format-Wide 显示</span><span class="sxs-lookup"><span data-stu-id="5e9ff-117">Controlling Format-Wide Display with Column</span></span>

<span data-ttu-id="5e9ff-118">使用 `Format-Wide` cmdlet 时，每次只能显示一个属性。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-118">With the `Format-Wide` cmdlet, you can only display a single property at a time.</span></span> <span data-ttu-id="5e9ff-119">这可用于在多个列中显示大型列表。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-119">This makes it useful for displaying large lists in multiple columns.</span></span>

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 3
```

```Output
Custom                 Hex                  List
Table                  Wide

```

## <a name="using-format-list-for-a-list-view"></a><span data-ttu-id="5e9ff-120">将 Format-List 用于列表视图</span><span class="sxs-lookup"><span data-stu-id="5e9ff-120">Using Format-List for a List View</span></span>

<span data-ttu-id="5e9ff-121">`Format-List` cmdlet 以列表的形式显示对象，同时标记每个属性并在单独的行上显示：</span><span class="sxs-lookup"><span data-stu-id="5e9ff-121">The `Format-List` cmdlet displays an object in the form of a listing, with each property labeled and displayed on a separate line:</span></span>

```powershell
Get-Process -Name iexplore | Format-List
```

```Output
Id      : 12808
Handles : 578
CPU     : 13.140625
SI      : 1
Name    : iexplore

Id      : 21748
Handles : 641
CPU     : 3.59375
SI      : 1
Name    : iexplore
```

<span data-ttu-id="5e9ff-122">你可以指定所需数目的属性：</span><span class="sxs-lookup"><span data-stu-id="5e9ff-122">You can specify as many properties as you want:</span></span>

```powershell
Get-Process -Name iexplore | Format-List -Property ProcessName,FileVersion,StartTime,Id
```

```Output
ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:58 AM
Id          : 12808

ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:57 AM
Id          : 21748
```

### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a><span data-ttu-id="5e9ff-123">通过将 Format-List 与通配符搭配使用获取详细信息</span><span class="sxs-lookup"><span data-stu-id="5e9ff-123">Getting Detailed Information by Using Format-List with Wildcards</span></span>

<span data-ttu-id="5e9ff-124">`Format-List` cmdlet 使你可以将通配符用作其 Property 参数的值  。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-124">The `Format-List` cmdlet lets you use a wildcard as the value of its **Property** parameter.</span></span> <span data-ttu-id="5e9ff-125">这样便可以显示详细信息。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-125">This lets you display detailed information.</span></span> <span data-ttu-id="5e9ff-126">通常情况下，对象包含的信息比你需要的多，这就是默认情况下 PowerShell 不显示所有属性值的原因。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-126">Often, objects include more information than you need, which is why PowerShell doesn't show all property values by default.</span></span> <span data-ttu-id="5e9ff-127">若要显示对象的全部属性，则使用 **Format-List-Property \&#42;** 命令。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-127">To show all of properties of an object, use the **Format-List -Property \&#42;** command.</span></span> <span data-ttu-id="5e9ff-128">下面的命令针对单个进程生成超过 60 行的输出：</span><span class="sxs-lookup"><span data-stu-id="5e9ff-128">The following command generates over 60 lines of output for a single process:</span></span>

```powershell
Get-Process -Name iexplore | Format-List -Property *
```

<span data-ttu-id="5e9ff-129">虽然 `Format-List` 命令对显示详细信息很有用，但如果你想要包括多个项目的输出的概述，更常用的是一个更简单的表格视图。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-129">Although the `Format-List` command is useful for showing detail, if you want an overview of output that includes many items, a simpler tabular view is often more useful.</span></span>

## <a name="using-format-table-for-tabular-output"></a><span data-ttu-id="5e9ff-130">将 Format-Table 用于表格输出</span><span class="sxs-lookup"><span data-stu-id="5e9ff-130">Using Format-Table for Tabular Output</span></span>

<span data-ttu-id="5e9ff-131">如果你在没有指定属性名称的情况下使用 `Format-Table` cmdlet 来格式化 `Get-Process` 命令的输出，你所得到的输出会和未使用 `Format` cmdlet 执行任何格式设置时得到的完全一样。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-131">If you use the `Format-Table` cmdlet with no property names specified to format the output of the `Get-Process` command, you get exactly the same output as you do without a `Format` cmdlet.</span></span> <span data-ttu-id="5e9ff-132">默认情况下，PowerShell 以表格格式显示 Process 对象  。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-132">By default, PowerShell displays **Process** objects in a tabular format.</span></span>

```powershell
Get-Service -Name win* | Format-Table
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  WinHttpAutoProx... WinHTTP Web Proxy Auto-Discovery Se...
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Manag...
```

### <a name="improving-format-table-output-autosize"></a><span data-ttu-id="5e9ff-133">改进 Format-Table 输出（自动调整大小）</span><span class="sxs-lookup"><span data-stu-id="5e9ff-133">Improving Format-Table Output (AutoSize)</span></span>

<span data-ttu-id="5e9ff-134">尽管表格视图对显示大量信息很有用，但如果显示区域对于数据来说太窄，则可能导致数据难以理解。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-134">Although a tabular view is useful for displaying lots of information, it may be difficult to interpret if the display is too narrow for the data.</span></span> <span data-ttu-id="5e9ff-135">在上面的示例中，输出被截断。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-135">In the previous example, the output is truncated.</span></span> <span data-ttu-id="5e9ff-136">当你运行 `Format-Table` 命令时，如果你指定 AutoSize  参数，PowerShell 会根据显示的实际数据来计算列宽。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-136">If you specify the **AutoSize** parameter when you run the `Format-Table` command, PowerShell calculates column widths based on the actual data displayed.</span></span> <span data-ttu-id="5e9ff-137">这使得列可读。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-137">This makes the columns readable.</span></span>

```powershell
Get-Service -Name win* | Format-Table -AutoSize
```

```Output
Status  Name                DisplayName
------  ----                -----------
Running WinDefend           Windows Defender Antivirus Service
Running WinHttpAutoProxySvc WinHTTP Web Proxy Auto-Discovery Service
Running Winmgmt             Windows Management Instrumentation
Running WinRM               Windows Remote Management (WS-Management)
```

<span data-ttu-id="5e9ff-138">`Format-Table` cmdlet 仍可能会截断数据，但仅会在屏幕的末尾处进行截断。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-138">The `Format-Table` cmdlet might still truncate data, but it only truncates at the end of the screen.</span></span> <span data-ttu-id="5e9ff-139">除最后一个显示的属性外，会让所有属性获得各自所需的大小，以使最长的数据元素得以正确显示。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-139">Properties, other than the last one displayed, are given as much size as they need for their longest data element to display correctly.</span></span>

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -AutoSize
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc, iphl…
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms, TPHKLO…
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

<span data-ttu-id="5e9ff-140">`Format-Table` 命令假设按重要性顺序列出属性。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-140">The `Format-Table` command assumes that properties are listed in order of importance.</span></span> <span data-ttu-id="5e9ff-141">因此，它会尝试完整显示离列表开头最近的那些属性。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-141">So it attempts to fully display the properties nearest the beginning.</span></span> <span data-ttu-id="5e9ff-142">如果 `Format-Table` 命令无法显示所有属性，则会从显示中删除某些列。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-142">If the `Format-Table` command can't display all the properties, it removes some columns from the display.</span></span> <span data-ttu-id="5e9ff-143">可以在 DependentServices 属性前一个示例中查看此行为  。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-143">You can see this behavior in the **DependentServices** property previous example.</span></span>

### <a name="wrapping-format-table-output-in-columns-wrap"></a><span data-ttu-id="5e9ff-144">让列中的 Format-Table 输出自动换行 (Wrap)</span><span class="sxs-lookup"><span data-stu-id="5e9ff-144">Wrapping Format-Table Output in Columns (Wrap)</span></span>

<span data-ttu-id="5e9ff-145">可以通过使用 Wrap 参数让较长的 `Format-Table` 数据在其显示列中自动换行  。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-145">You can force lengthy `Format-Table` data to wrap within its display column by using the **Wrap** parameter.</span></span> <span data-ttu-id="5e9ff-146">使用 Wrap 参数可能不会实现所需的操作，因为如果你不同时指定 AutoSize，它会使用默认设置   ：</span><span class="sxs-lookup"><span data-stu-id="5e9ff-146">Using the **Wrap** parameter may not do what you expect, since it uses default settings if you don't also specify **AutoSize**:</span></span>

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -Wrap
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc,
                                                                                iphlpsvc}
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms,
                                                                                TPHKLOAD,
                                                                                SUService,
                                                                                smstsmgr…}
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

<span data-ttu-id="5e9ff-147">使用 Wrap 参数基本不会减慢进程速度  。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-147">Using the **Wrap** parameter by itself doesn't slow down processing very much.</span></span> <span data-ttu-id="5e9ff-148">但是，使用 AutoSize 格式化大型目录结构的递归文件列表可能得耗用大量时间和内存，才能显示第一批输出项  。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-148">However, using **AutoSize** to format a recursive file listing of a large directory structure can take a long time and use lots of memory before displaying the first output items.</span></span>

<span data-ttu-id="5e9ff-149">如果你并不关心系统负载，那么结合使用 AutoSize 和 Wrap 参数则会获得良好的效果   。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-149">If you aren't concerned about system load, then **AutoSize** works well with the **Wrap** parameter.</span></span>
<span data-ttu-id="5e9ff-150">初始列仍根据需要最大限度地使用宽度来在一行上显示项，但在必要时将最后一列换行。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-150">The initial columns still use as much width as needed to display items on one line, but the final column is wrapped, if necessary.</span></span>

> [!NOTE]
> <span data-ttu-id="5e9ff-151">当你首先指定最宽的列时，可能不会显示某些列。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-151">Some columns may not be displayed when you specify the widest columns first.</span></span> <span data-ttu-id="5e9ff-152">为了获得最佳结果，请先指定最小的数据元素。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-152">For best results, specify the smallest data elements first.</span></span>

<span data-ttu-id="5e9ff-153">在下面的示例中，我们首先指定最宽的属性。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-153">In the following example, we specify the widest properties first.</span></span>

```powershell
Get-Process -Name iexplore | Format-Table -Wrap -AutoSize -Property FileVersion,Path,Name,Id
```

<span data-ttu-id="5e9ff-154">即使进行了换行，也会省略最后 ID 列  ：</span><span class="sxs-lookup"><span data-stu-id="5e9ff-154">Even with wrapping, the final **Id** column is omitted:</span></span>

```Output
FileVersion                          Path                                                  Nam
                                                                                           e
-----------                          ----                                                  ---
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files (x86)\Internet Explorer\IEXPLORE.EXE iex
                                                                                           plo
                                                                                           re
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files\Internet Explorer\iexplore.exe       iex
                                                                                           plo
                                                                                           re
```

### <a name="organizing-table-output--groupby"></a><span data-ttu-id="5e9ff-155">组织选项卡输出 (-GroupBy)</span><span class="sxs-lookup"><span data-stu-id="5e9ff-155">Organizing Table Output (-GroupBy)</span></span>

<span data-ttu-id="5e9ff-156">用于表格输出控制的另一个有用参数是 **GroupBy**。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-156">Another useful parameter for tabular output control is **GroupBy**.</span></span> <span data-ttu-id="5e9ff-157">较长的列表可能尤其难以进行比较。</span><span class="sxs-lookup"><span data-stu-id="5e9ff-157">Longer tabular listings in particular may be hard to compare.</span></span> <span data-ttu-id="5e9ff-158">**GroupBy** 参数基于属性值对输出进行分组</span><span class="sxs-lookup"><span data-stu-id="5e9ff-158">The **GroupBy** parameter groups output based on a property value.</span></span> <span data-ttu-id="5e9ff-159">例如，我们可以按 StartType 对服务分组以便于检查，同时从属性列表中省略 StartType 值   ：</span><span class="sxs-lookup"><span data-stu-id="5e9ff-159">For example, we can group services by **StartType** for easier inspection, omitting the **StartType** value from the property listing:</span></span>

```powershell
Get-Service -Name win* | Sort-Object StartType | Format-Table -GroupBy StartType
```

```Output
   StartType: Automatic
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Managem…

   StartType: Manual
Status   Name               DisplayName
------   ----               -----------
Running  WinHttpAutoProxyS… WinHTTP Web Proxy Auto-Discovery Serv…
```
