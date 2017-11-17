---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "从管道中删除对象 (Where Object)"
ms.assetid: 01df8b22-2d22-4e2c-a18d-c004cd3cc284
ms.openlocfilehash: 4140c4c3ebb26223d03ca139992fedf6e184a38b
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2017
---
# <a name="removing-objects-from-the-pipeline-where-object"></a><span data-ttu-id="314d8-103">从管道中删除对象 (Where-Object)</span><span class="sxs-lookup"><span data-stu-id="314d8-103">Removing Objects from the Pipeline (Where-Object)</span></span>
<span data-ttu-id="314d8-104">在 Windows PowerShell 中，你通常会生成和传递比预期更多的对象到管道中。</span><span class="sxs-lookup"><span data-stu-id="314d8-104">In Windows PowerShell, you often generate and pass along more objects to a pipeline than you want.</span></span> <span data-ttu-id="314d8-105">可以通过使用 **Format** cmdlet 指定特定对象的属性进行显示，但是这对从显示中删除整个对象的问题没有任何帮助。</span><span class="sxs-lookup"><span data-stu-id="314d8-105">You can specify the properties of particular objects to display by using the **Format** cmdlets, but this does not help with the problem of removing entire objects from the display.</span></span> <span data-ttu-id="314d8-106">你可能希望在管道末尾之前筛选对象，以便你可以只对初始生成对象的子集执行操作。</span><span class="sxs-lookup"><span data-stu-id="314d8-106">You may want to filter objects before the end of a pipeline, so you can perform actions on only a subset of the initially-generated objects.</span></span>

<span data-ttu-id="314d8-107">Windows PowerShell 包括 **Where-Object** cmdlet，它可让你在管道中测试每个对象，并且仅沿管道传递满足特定测试条件的对象。</span><span class="sxs-lookup"><span data-stu-id="314d8-107">Windows PowerShell includes a **Where-Object** cmdlet that allows you to test each object in the pipeline and only pass it along the pipeline if it meets a particular test condition.</span></span> <span data-ttu-id="314d8-108">将从管道中删除未通过测试的对象。</span><span class="sxs-lookup"><span data-stu-id="314d8-108">Objects that do not pass the test are removed from the pipeline.</span></span> <span data-ttu-id="314d8-109">提供测试条件作为 **Where-ObjectFilterScript** 参数的值。</span><span class="sxs-lookup"><span data-stu-id="314d8-109">You supply the test condition as the value of the **Where-ObjectFilterScript** parameter.</span></span>

### <a name="performing-simple-tests-with-where-object"></a><span data-ttu-id="314d8-110">使用 Where-Object 执行简单测试</span><span class="sxs-lookup"><span data-stu-id="314d8-110">Performing Simple Tests with Where-Object</span></span>
<span data-ttu-id="314d8-111">**FilterScript** 的值是一个*脚本块* - 由大括号 {} 括起来的一个或多个 Windows PowerShell 命令，其计算结果为 True 或 False。</span><span class="sxs-lookup"><span data-stu-id="314d8-111">The value of **FilterScript** is a *script block* -  one or more Windows PowerShell commands surrounded by braces {} - that evaluates to true or false.</span></span> <span data-ttu-id="314d8-112">这些脚本块可能非常简单，但是创建它们需要了解有关 Windows PowerShell 的另一个概念，即比较运算符。</span><span class="sxs-lookup"><span data-stu-id="314d8-112">These script blocks can be very simple, but creating them requires knowing about another Windows PowerShell concept, comparison operators.</span></span> <span data-ttu-id="314d8-113">比较运算符比较其每一侧显示的项。</span><span class="sxs-lookup"><span data-stu-id="314d8-113">A comparison operator compares the items that appear on each side of it.</span></span> <span data-ttu-id="314d8-114">比较运算符以“-”字符开头，后跟名称。</span><span class="sxs-lookup"><span data-stu-id="314d8-114">Comparison operators begin with a '-' character and are followed by a name.</span></span> <span data-ttu-id="314d8-115">基本比较运算符适用于几乎任何类型的对象。</span><span class="sxs-lookup"><span data-stu-id="314d8-115">Basic comparison operators work on almost any kind of object.</span></span> <span data-ttu-id="314d8-116">更高级的比较运算符可能仅适用于文本或数组。</span><span class="sxs-lookup"><span data-stu-id="314d8-116">The more advanced comparison operators might only work on text or arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="314d8-117">默认情况下，在处理文本时，Windows PowerShell 比较运算符不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="314d8-117">By default, when working with text, Windows PowerShell comparison operators are case-insensitive.</span></span>

<span data-ttu-id="314d8-118">出于分析考虑，<、> 和 = 等符号不用作比较运算符。</span><span class="sxs-lookup"><span data-stu-id="314d8-118">Due to parsing considerations, symbols such as <,>, and = are not used as comparison operators.</span></span> <span data-ttu-id="314d8-119">相反，比较运算符由字母组成。</span><span class="sxs-lookup"><span data-stu-id="314d8-119">Instead, comparison operators are comprised of letters.</span></span> <span data-ttu-id="314d8-120">下表中列出了基本比较运算符。</span><span class="sxs-lookup"><span data-stu-id="314d8-120">The basic comparison operators are listed in the following table.</span></span>

|<span data-ttu-id="314d8-121">比较运算符</span><span class="sxs-lookup"><span data-stu-id="314d8-121">Comparison Operator</span></span>|<span data-ttu-id="314d8-122">含义</span><span class="sxs-lookup"><span data-stu-id="314d8-122">Meaning</span></span>|<span data-ttu-id="314d8-123">示例（返回 True）</span><span class="sxs-lookup"><span data-stu-id="314d8-123">Example (returns true)</span></span>|
|-----------------------|-----------|--------------------------|
|<span data-ttu-id="314d8-124">-eq</span><span class="sxs-lookup"><span data-stu-id="314d8-124">-eq</span></span>|<span data-ttu-id="314d8-125">等于</span><span class="sxs-lookup"><span data-stu-id="314d8-125">is equal to</span></span>|<span data-ttu-id="314d8-126">1 -eq 1</span><span class="sxs-lookup"><span data-stu-id="314d8-126">1 -eq 1</span></span>|
|<span data-ttu-id="314d8-127">-ne</span><span class="sxs-lookup"><span data-stu-id="314d8-127">-ne</span></span>|<span data-ttu-id="314d8-128">不等于</span><span class="sxs-lookup"><span data-stu-id="314d8-128">Is not equal to</span></span>|<span data-ttu-id="314d8-129">1 -ne 2</span><span class="sxs-lookup"><span data-stu-id="314d8-129">1 -ne 2</span></span>|
|<span data-ttu-id="314d8-130">-lt</span><span class="sxs-lookup"><span data-stu-id="314d8-130">-lt</span></span>|<span data-ttu-id="314d8-131">小于</span><span class="sxs-lookup"><span data-stu-id="314d8-131">Is less than</span></span>|<span data-ttu-id="314d8-132">1 -lt 2</span><span class="sxs-lookup"><span data-stu-id="314d8-132">1 -lt 2</span></span>|
|<span data-ttu-id="314d8-133">-le</span><span class="sxs-lookup"><span data-stu-id="314d8-133">-le</span></span>|<span data-ttu-id="314d8-134">小于或等于</span><span class="sxs-lookup"><span data-stu-id="314d8-134">Is less than or equal to</span></span>|<span data-ttu-id="314d8-135">1 -le 2</span><span class="sxs-lookup"><span data-stu-id="314d8-135">1 -le 2</span></span>|
|<span data-ttu-id="314d8-136">-gt</span><span class="sxs-lookup"><span data-stu-id="314d8-136">-gt</span></span>|<span data-ttu-id="314d8-137">大于</span><span class="sxs-lookup"><span data-stu-id="314d8-137">Is greater than</span></span>|<span data-ttu-id="314d8-138">2 -gt 1</span><span class="sxs-lookup"><span data-stu-id="314d8-138">2 -gt 1</span></span>|
|<span data-ttu-id="314d8-139">-ge</span><span class="sxs-lookup"><span data-stu-id="314d8-139">-ge</span></span>|<span data-ttu-id="314d8-140">大于或等于</span><span class="sxs-lookup"><span data-stu-id="314d8-140">Is greater than or equal to</span></span>|<span data-ttu-id="314d8-141">2 -ge 1</span><span class="sxs-lookup"><span data-stu-id="314d8-141">2 -ge 1</span></span>|
|<span data-ttu-id="314d8-142">-like</span><span class="sxs-lookup"><span data-stu-id="314d8-142">-like</span></span>|<span data-ttu-id="314d8-143">相似（文本的通配符比较）</span><span class="sxs-lookup"><span data-stu-id="314d8-143">Is like (wildcard comparison for text)</span></span>|<span data-ttu-id="314d8-144">"file.doc" -like "f\*.do?"</span><span class="sxs-lookup"><span data-stu-id="314d8-144">"file.doc" -like "f\*.do?"</span></span>|
|<span data-ttu-id="314d8-145">-notlike</span><span class="sxs-lookup"><span data-stu-id="314d8-145">-notlike</span></span>|<span data-ttu-id="314d8-146">不相似（文本的通配符比较）</span><span class="sxs-lookup"><span data-stu-id="314d8-146">Is not like (wildcard comparison for text)</span></span>|<span data-ttu-id="314d8-147">"file.doc" -notlike "p\*.doc"</span><span class="sxs-lookup"><span data-stu-id="314d8-147">"file.doc" -notlike "p\*.doc"</span></span>|
|<span data-ttu-id="314d8-148">-contains</span><span class="sxs-lookup"><span data-stu-id="314d8-148">-contains</span></span>|<span data-ttu-id="314d8-149">包含</span><span class="sxs-lookup"><span data-stu-id="314d8-149">Contains</span></span>|<span data-ttu-id="314d8-150">1,2,3 -contains 1</span><span class="sxs-lookup"><span data-stu-id="314d8-150">1,2,3 -contains 1</span></span>|
|<span data-ttu-id="314d8-151">-notcontains</span><span class="sxs-lookup"><span data-stu-id="314d8-151">-notcontains</span></span>|<span data-ttu-id="314d8-152">不包含</span><span class="sxs-lookup"><span data-stu-id="314d8-152">Does not contain</span></span>|<span data-ttu-id="314d8-153">1,2,3 -notcontains 4</span><span class="sxs-lookup"><span data-stu-id="314d8-153">1,2,3 -notcontains 4</span></span>|

<span data-ttu-id="314d8-154">Where-Object 脚本块使用特殊变量“$_”来指代管道中的当前对象。</span><span class="sxs-lookup"><span data-stu-id="314d8-154">Where-Object script blocks use the special variable '$_' to refer to the current object in the pipeline.</span></span> <span data-ttu-id="314d8-155">以下是其工作原理示例。</span><span class="sxs-lookup"><span data-stu-id="314d8-155">Here is an example of how it works.</span></span> <span data-ttu-id="314d8-156">如果你有一个数字列表，且希望仅返回小于 3 的数字，则可使用 Where-Object 通过键入以下内容来筛选数字：</span><span class="sxs-lookup"><span data-stu-id="314d8-156">If you have a list of numbers, and only want to return the ones that are less than 3, you can use Where-Object to filter the numbers by typing:</span></span>

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

### <a name="filtering-based-on-object-properties"></a><span data-ttu-id="314d8-157">基于对象属性进行筛选</span><span class="sxs-lookup"><span data-stu-id="314d8-157">Filtering Based on Object Properties</span></span>
<span data-ttu-id="314d8-158">既然 $_ 指代当前管道对象，我们就可以访问其属性以进行测试。</span><span class="sxs-lookup"><span data-stu-id="314d8-158">Since $_ refers to the current pipeline object, we can access its properties for our tests.</span></span>

<span data-ttu-id="314d8-159">例如，我们可以看看 WMI 中的 Win32_SystemDriver 类。</span><span class="sxs-lookup"><span data-stu-id="314d8-159">As an example, we can look at the Win32_SystemDriver class in WMI.</span></span> <span data-ttu-id="314d8-160">一个特定的系统上可能有数百个系统驱动程序，但是你可能只对特定一些系统驱动程序感兴趣，例如那些当前正在运行的程序。</span><span class="sxs-lookup"><span data-stu-id="314d8-160">There might be hundreds of system drivers on a particular system, but you might only be interested in a particular set of the system drivers, such as those which are currently running.</span></span> <span data-ttu-id="314d8-161">如果你使用 Get-Member 查看 Win32_SystemDriver 成员（**Get-WmiObject -Class Win32_SystemDriver | Get-Member -MemberType 属性**），你将发现相关属性为 State，并且在驱动程序运行时，它的值为“Running”。</span><span class="sxs-lookup"><span data-stu-id="314d8-161">If you use Get-Member to view Win32_SystemDriver members (**Get-WmiObject -Class Win32_SystemDriver | Get-Member -MemberType Property**) you will see that the relevant property is State, and that it has a value of "Running" when the driver is running.</span></span> <span data-ttu-id="314d8-162">你可以筛选系统驱动程序，通过键入以下内容仅选择正在运行的驱动程序：</span><span class="sxs-lookup"><span data-stu-id="314d8-162">You can filter the system drivers, selecting only the running ones by typing:</span></span>

```
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"}
```

<span data-ttu-id="314d8-163">这仍会生成一个较长的列表。</span><span class="sxs-lookup"><span data-stu-id="314d8-163">This still produces a long list.</span></span> <span data-ttu-id="314d8-164">你可能还希望进行筛选，以通过测试 StartMode 值仅选择自动启动的驱动程序集：</span><span class="sxs-lookup"><span data-stu-id="314d8-164">You may want to filter to only select the drivers set to start automatically by testing the StartMode value as well:</span></span>

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Auto"}

DisplayName : RAS Asynchronous Media Driver
Name        : AsyncMac
State       : Running
Status      : OK
Started     : True

DisplayName : Audio Stub Driver
Name        : audstub
State       : Running
Status      : OK
Started     : True
```

<span data-ttu-id="314d8-165">这为我们提供了大量不再需要的信息，因为我们知道驱动程序正在运行。</span><span class="sxs-lookup"><span data-stu-id="314d8-165">This gives us a lot of information we no longer need because we know that the drivers are running.</span></span> <span data-ttu-id="314d8-166">事实上，此时我们可能需要的唯一信息就是名称和显示名。</span><span class="sxs-lookup"><span data-stu-id="314d8-166">In fact, the only information we probably need at this point are the name and the display name.</span></span> <span data-ttu-id="314d8-167">下面的命令仅包括这两种属性，从而使输出更简单：</span><span class="sxs-lookup"><span data-stu-id="314d8-167">The following command includes only those two properties, resulting in much simpler output:</span></span>

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Manual"} | Format-Table -Property Name,DisplayName

Name                                    DisplayName
----                                    -----------
AsyncMac                                RAS Asynchronous Media Driver
Fdc                                     Floppy Disk Controller Driver
Flpydisk                                Floppy Disk Driver
Gpc                                     Generic Packet Classifier
IpNat                                   IP Network Address Translator
mouhid                                  Mouse HID Driver
MRxDAV                                  WebDav Client Redirector
mssmbios                                Microsoft System Management BIOS Driver
```

<span data-ttu-id="314d8-168">上面的命令包含两个 Where-Object 元素，但是可以使用 -and 逻辑运算符将其表示为一个 Where-Object 元素，如下所示：</span><span class="sxs-lookup"><span data-stu-id="314d8-168">There are two Where-Object elements in the above command, but they can be expressed in a single Where-Object element by using the -and logical operator, like this:</span></span>

```
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq "Running") -and ($_.StartMode -eq "Manual") } | Format-Table -Property Name,DisplayName
```

<span data-ttu-id="314d8-169">下表中列出了标准逻辑运算符。</span><span class="sxs-lookup"><span data-stu-id="314d8-169">The standard logical operators are listed in the following table.</span></span>

|<span data-ttu-id="314d8-170">逻辑运算符</span><span class="sxs-lookup"><span data-stu-id="314d8-170">Logical Operator</span></span>|<span data-ttu-id="314d8-171">含义</span><span class="sxs-lookup"><span data-stu-id="314d8-171">Meaning</span></span>|<span data-ttu-id="314d8-172">示例（返回 True）</span><span class="sxs-lookup"><span data-stu-id="314d8-172">Example (returns true)</span></span>|
|--------------------|-----------|--------------------------|
|<span data-ttu-id="314d8-173">-and</span><span class="sxs-lookup"><span data-stu-id="314d8-173">-and</span></span>|<span data-ttu-id="314d8-174">Logical and；如果两侧都为 True，则返回 True</span><span class="sxs-lookup"><span data-stu-id="314d8-174">Logical and; true if both sides are true</span></span>|<span data-ttu-id="314d8-175">(1 -eq 1) -and (2 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="314d8-175">(1 -eq 1) -and (2 -eq 2)</span></span>|
|<span data-ttu-id="314d8-176">-or</span><span class="sxs-lookup"><span data-stu-id="314d8-176">-or</span></span>|<span data-ttu-id="314d8-177">Logical or；如果某一侧为 True，则返回 True</span><span class="sxs-lookup"><span data-stu-id="314d8-177">Logical or; true if either side is true</span></span>|<span data-ttu-id="314d8-178">(1 -eq 1) -or (1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="314d8-178">(1 -eq 1) -or (1 -eq 2)</span></span>|
|<span data-ttu-id="314d8-179">-not</span><span class="sxs-lookup"><span data-stu-id="314d8-179">-not</span></span>|<span data-ttu-id="314d8-180">Logical not；反转 True 和 False</span><span class="sxs-lookup"><span data-stu-id="314d8-180">Logical not; reverses true and false</span></span>|<span data-ttu-id="314d8-181">-not (1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="314d8-181">-not (1 -eq 2)</span></span>|
|\!|<span data-ttu-id="314d8-182">Logical not；反转 True 和 False</span><span class="sxs-lookup"><span data-stu-id="314d8-182">Logical not; reverses true and false</span></span>|<span data-ttu-id="314d8-183">\!(1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="314d8-183">\!(1 -eq 2)</span></span>|

