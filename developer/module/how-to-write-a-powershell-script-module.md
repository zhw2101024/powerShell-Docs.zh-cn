---
title: 如何编写 PowerShell 脚本模块 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed7645ea-5e52-4a45-81a7-aa3c2d605cde
caps.latest.revision: 16
ms.openlocfilehash: b2a929a1724f77f0516ad24cfd90f6d6053ed19e
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470799"
---
# <a name="how-to-write-a-powershell-script-module"></a><span data-ttu-id="4d053-102">如何编写 PowerShell 脚本模块</span><span class="sxs-lookup"><span data-stu-id="4d053-102">How to Write a PowerShell Script Module</span></span>

<span data-ttu-id="4d053-103">脚本模块是实质上是任何有效的 PowerShell 脚本保存在扩展名为.psm1。</span><span class="sxs-lookup"><span data-stu-id="4d053-103">A script module is essentially any valid PowerShell script saved in a .psm1 extension.</span></span> <span data-ttu-id="4d053-104">该扩展允许 PowerShell 引擎将在你的文件上使用多种规则和 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4d053-104">This extension allows the PowerShell engine to use a number of rules and cmdlets on your file.</span></span> <span data-ttu-id="4d053-105">大多数这些功能是为了帮助你还可以管理作用域在其他系统上安装你的代码。</span><span class="sxs-lookup"><span data-stu-id="4d053-105">Most of these capabilities are there to help you install your code on other systems, as well as manage scoping.</span></span> <span data-ttu-id="4d053-106">此外可以使用模块清单文件，可以描述变得更加复杂的安装和解决方案。</span><span class="sxs-lookup"><span data-stu-id="4d053-106">You can also use a module manifest file, which can describe even more complex installations and solutions.</span></span>

## <a name="writing-a-powershell-script-module"></a><span data-ttu-id="4d053-107">编写 PowerShell 脚本模块</span><span class="sxs-lookup"><span data-stu-id="4d053-107">Writing a PowerShell Script Module</span></span>

<span data-ttu-id="4d053-108">通过将有效的 PowerShell 脚本保存到.psm1 文件中，然后将该文件保存在位于 PowerShell 可在其中找到一个目录中创建的脚本模块。</span><span class="sxs-lookup"><span data-stu-id="4d053-108">You create a script module by saving a valid PowerShell script to a .psm1 file, and then saving that file in a directory located where PowerShell can find it.</span></span> <span data-ttu-id="4d053-109">在该文件夹中还可以将任何所需的资源以运行您的脚本，以及一个清单文件用于描述到 PowerShell 模块的工作原理。</span><span class="sxs-lookup"><span data-stu-id="4d053-109">In that folder you can also place any resources you need to run your script, as well as a manifest file that describes to PowerShell how your module works.</span></span>

#### <a name="to-create-a-basic-powershell-module"></a><span data-ttu-id="4d053-110">若要创建基本的 PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="4d053-110">To create a basic PowerShell Module</span></span>

1. <span data-ttu-id="4d053-111">选取现有的 PowerShell 脚本，并具有.psm1 扩展名保存脚本。</span><span class="sxs-lookup"><span data-stu-id="4d053-111">Take an existing PowerShell script, and save the script with a .psm1 extension.</span></span>

   <span data-ttu-id="4d053-112">保存具有.psm1 的脚本扩展意味着，您可以使用模块 cmdlet，如[导入模块](/powershell/module/Microsoft.PowerShell.Core/Import-Module)，其上。</span><span class="sxs-lookup"><span data-stu-id="4d053-112">Saving a script with the .psm1 extension means that you can use the module cmdlets, such as [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), on it.</span></span> <span data-ttu-id="4d053-113">这些 cmdlet 存在主要，以便您可以轻松地导入和导出到其他用户的系统上您的代码。</span><span class="sxs-lookup"><span data-stu-id="4d053-113">These cmdlets exist primarily so that you can easily import and export your code onto other user's systems.</span></span> <span data-ttu-id="4d053-114">（替代解决方案是在其他系统，然后使用点获取来源代码将其加载到活动内存中，这并不特别是可缩放的解决方案。）有关详细信息请参阅**模块 Cmdlet 和变量**主题中[Windows PowerShell 模块](./understanding-a-windows-powershell-module.md)请注意，默认情况下，在脚本中的所有函数都都用户导入.psm1 文件，都可以访问但不是属性。</span><span class="sxs-lookup"><span data-stu-id="4d053-114">(The alternate solution would be to load up your code on other systems and then dot-source it into active memory, which isn't a particularly scalable solution.) For more information see the **Module Cmdlets and Variables** section in [Windows PowerShell Modules](./understanding-a-windows-powershell-module.md) Note that, by default, all functions in your script are accessible to users who import your .psm1 file, but properties are not.</span></span>

   <span data-ttu-id="4d053-115">示例 PowerShell 脚本，标题为`Show-Calendar`，可在本主题末尾。</span><span class="sxs-lookup"><span data-stu-id="4d053-115">An example PowerShell script, entitled `Show-Calendar`, is available at the end of this topic.</span></span>

   ```powershell
   function Show-Calendar {
   param(
       [DateTime] $start = [DateTime]::Today,
       [DateTime] $end = $start,
       $firstDayOfWeek,
       [int[]] $highlightDay,
       [string[]] $highlightDate = [DateTime]::Today.ToString()
       )

       #actual code for the function goes here see the end of the topic for the complete code sample
   }
   ```

2. <span data-ttu-id="4d053-116">若要控制用户对特定函数或属性访问，请调用[Export-modulemember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember)您的脚本结尾处。</span><span class="sxs-lookup"><span data-stu-id="4d053-116">To control user access to certain functions or properties, call [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) at the end of your script.</span></span>

   <span data-ttu-id="4d053-117">在页面底部的示例代码具有只有一个函数，它默认情况下会公开。</span><span class="sxs-lookup"><span data-stu-id="4d053-117">The example code at the bottom of the page has only one function, which by default would be exposed.</span></span> <span data-ttu-id="4d053-118">但是，建议你明确指出希望公开，如下面的代码中所述的函数：</span><span class="sxs-lookup"><span data-stu-id="4d053-118">However, it is recommended that you explicitly call out which functions you wish to expose, as described in the following code:</span></span>

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   <span data-ttu-id="4d053-119">你还可以限制什么使用模块清单导入。</span><span class="sxs-lookup"><span data-stu-id="4d053-119">You can also restrict what is imported using a module manifest.</span></span> <span data-ttu-id="4d053-120">有关详细信息，请参阅[导入 PowerShell 模块](./importing-a-powershell-module.md)并[如何编写 PowerShell 模块清单](./how-to-write-a-powershell-module-manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="4d053-120">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [How to Write a PowerShell Module Manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

3. <span data-ttu-id="4d053-121">如果你有自己的模块需要已加载的模块，你可以使用这些通过调用`Import-Module`，在你自己的模块的顶部。</span><span class="sxs-lookup"><span data-stu-id="4d053-121">If you have modules that your own module needs to have loaded, you can use them with a call to `Import-Module`, at the top of your own module.</span></span>

   <span data-ttu-id="4d053-122">`Import-Module` 是一个导入到系统上的目标的模块的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4d053-122">`Import-Module` is a cmdlet that imports a targeted module onto a system.</span></span> <span data-ttu-id="4d053-123">在这种情况下，它还用于在以后过程中安装你自己的模块。</span><span class="sxs-lookup"><span data-stu-id="4d053-123">As such, it is also used at a later point in the procedure to install your own module as well.</span></span> <span data-ttu-id="4d053-124">在此页底部的示例代码不使用任何导入模块。</span><span class="sxs-lookup"><span data-stu-id="4d053-124">The sample code at the bottom of this page does not use any import modules.</span></span> <span data-ttu-id="4d053-125">如果有的话，但是，它们会列出顶部的文件，如下面的代码中所述：</span><span class="sxs-lookup"><span data-stu-id="4d053-125">If it did, however, they would be listed at the top of the file, as described in the following code:</span></span>

   ```powershell
   Import-Module GenericModule
   ```

4. <span data-ttu-id="4d053-126">若要描述你对 PowerShell 帮助系统的模块，可以使用该文件中的标准帮助注释或创建一个额外的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="4d053-126">To describe your module to the PowerShell Help system, you can either use standard help comments inside the file, or create an additional Help file.</span></span>

   <span data-ttu-id="4d053-127">本主题底部的代码示例在注释中包含的帮助信息。</span><span class="sxs-lookup"><span data-stu-id="4d053-127">The code sample at the bottom of this topic includes the help information in the comments.</span></span> <span data-ttu-id="4d053-128">您也可以编写展开的 XML 文件包含更多帮助内容。</span><span class="sxs-lookup"><span data-stu-id="4d053-128">You could also write expanded XML files that contain additional help content.</span></span> <span data-ttu-id="4d053-129">有关详细信息，请参阅[编写为 Windows PowerShell 模块帮助](./writing-help-for-windows-powershell-modules.md)。</span><span class="sxs-lookup"><span data-stu-id="4d053-129">For more information, see [Writing Help for Windows PowerShell Modules](./writing-help-for-windows-powershell-modules.md).</span></span>

5. <span data-ttu-id="4d053-130">如果你有更多的模块、 XML 文件或想要打包对模块的使用其他内容，就可以做到与模块清单。</span><span class="sxs-lookup"><span data-stu-id="4d053-130">If you have additional modules, XML files, or other content you want to package up with your module, you can do so with a module manifest.</span></span>

   <span data-ttu-id="4d053-131">模块清单是包含其他模块、 目录布局、 版本控制编号、 作者数据和其他信息片段的名称的文件。</span><span class="sxs-lookup"><span data-stu-id="4d053-131">A module manifest is a file that contains the names of other modules, directory layouts, versioning numbers, author data, and other pieces of information.</span></span> <span data-ttu-id="4d053-132">PowerShell 使用模块清单文件来组织和部署你的解决方案。</span><span class="sxs-lookup"><span data-stu-id="4d053-132">PowerShell uses the module manifest file to organize and deploy your solution.</span></span> <span data-ttu-id="4d053-133">但是，由于此示例中的相对简单特性，不需要清单文件。</span><span class="sxs-lookup"><span data-stu-id="4d053-133">However, due to the relatively simple nature of this example, a manifest file was not needed.</span></span> <span data-ttu-id="4d053-134">有关详细信息，请参阅[模块清单](./how-to-write-a-powershell-module-manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="4d053-134">For more information, see [Module Manifests](./how-to-write-a-powershell-module-manifest.md).</span></span>

6. <span data-ttu-id="4d053-135">若要安装和运行你的模块，将模块保存到一个相应的 PowerShell 路径，并调用`Import-Module`。</span><span class="sxs-lookup"><span data-stu-id="4d053-135">To install and run your module, save the module to one of the appropriate PowerShell paths, and make a call to `Import-Module`.</span></span>

   <span data-ttu-id="4d053-136">您可以在其中安装你的模块的路径位于`$env:PSModulePath`全局变量。</span><span class="sxs-lookup"><span data-stu-id="4d053-136">The paths where you can install your module are located in the `$env:PSModulePath` global variable.</span></span> <span data-ttu-id="4d053-137">例如，若要将模块保存在系统上的公共路径将`%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`。</span><span class="sxs-lookup"><span data-stu-id="4d053-137">For example, a common path to save a module on a system would be `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`.</span></span> <span data-ttu-id="4d053-138">请务必创建你的模块中，存在一个文件夹，即使它是单个.psm1 文件。</span><span class="sxs-lookup"><span data-stu-id="4d053-138">Be sure to create a folder for your module to exist in, even if it is only a single .psm1 file.</span></span> <span data-ttu-id="4d053-139">如果不保存你的模块对两个路径，必须在调用中模块的位置传递`Import-Module`。</span><span class="sxs-lookup"><span data-stu-id="4d053-139">If you did not save your module to one of these paths, you would have to pass in the location of your module in the call to `Import-Module`.</span></span> <span data-ttu-id="4d053-140">（否则，PowerShell 将不能找到它。）如果有一个 PowerShell 模块路径中放置您的模块，从与 PowerShell 3.0 开始，你不需要显式将其导入。</span><span class="sxs-lookup"><span data-stu-id="4d053-140">(Otherwise, PowerShell would not be able to find it.) Starting with PowerShell 3.0, if you have placed your module in one of the PowerShell module paths, you do not need to explicitly import it.</span></span> <span data-ttu-id="4d053-141">当用户调用函数时，会自动加载你的模块。</span><span class="sxs-lookup"><span data-stu-id="4d053-141">You module is automatically loaded when a user calls your function.</span></span>
   <span data-ttu-id="4d053-142">模块路径的详细信息，请参阅[导入 PowerShell 模块](./importing-a-powershell-module.md)并[PSModulePath 环境变量](./modifying-the-psmodulepath-installation-path.md)。</span><span class="sxs-lookup"><span data-stu-id="4d053-142">For more information on the module path, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [PSModulePath Environment Variable](./modifying-the-psmodulepath-installation-path.md).</span></span>

7. <span data-ttu-id="4d053-143">若要从活动服务中删除模块，请调用[Remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module)。</span><span class="sxs-lookup"><span data-stu-id="4d053-143">To remove a module from active service, make a call to [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span></span>

   <span data-ttu-id="4d053-144">请注意， [Remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module)删除你的模块从活动内存-它不会实际删除它从保存的模块文件的位置。</span><span class="sxs-lookup"><span data-stu-id="4d053-144">Note that [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) removes your module from active memory - it does not actually delete it from where you saved the module files.</span></span>

### <a name="show-calendar-code-example"></a><span data-ttu-id="4d053-145">显示日历的代码示例</span><span class="sxs-lookup"><span data-stu-id="4d053-145">Show-Calendar code example</span></span>

<span data-ttu-id="4d053-146">下面的示例是一个简单的脚本模块，包含一个名为的单个函数`Show-Calendar`。</span><span class="sxs-lookup"><span data-stu-id="4d053-146">The following example is a simple script module that contains a single function named `Show-Calendar`.</span></span>
<span data-ttu-id="4d053-147">此函数显示日历的可视表示形式。</span><span class="sxs-lookup"><span data-stu-id="4d053-147">This function displays a visual representation of a calendar.</span></span> <span data-ttu-id="4d053-148">此外，该示例包含有关摘要、 说明、 参数值和示例的 PowerShell 帮助字符串。</span><span class="sxs-lookup"><span data-stu-id="4d053-148">In addition, the sample contains the PowerShell Help strings for the synopsis, description, parameter values, and example.</span></span> <span data-ttu-id="4d053-149">请注意，最后一行代码可确保`Show-Calendar`函数将被导出为模块成员导入模块。</span><span class="sxs-lookup"><span data-stu-id="4d053-149">Note that the last line of code ensures that the `Show-Calendar` function is exported as a module member when the module is imported.</span></span>

```powershell
<#
 .Synopsis
  Displays a visual representation of a calendar.

 .Description
  Displays a visual representation of a calendar. This function supports multiple months
  and lets you highlight specific date ranges or days.

 .Parameter Start
  The first month to display.

 .Parameter End
  The last month to display.

 .Parameter FirstDayOfWeek
  The day of the month on which the week begins.

 .Parameter HighlightDay
  Specific days (numbered) to highlight. Used for date ranges like (25..31).
  Date ranges are specified by the Windows PowerShell range syntax. These dates are
  enclosed in square brackets.

 .Parameter HighlightDate
  Specific days (named) to highlight. These dates are surrounded by asterisks.

 .Example
   # Show a default display of this month.
   Show-Calendar

 .Example
   # Display a date range.
   Show-Calendar -Start "March, 2010" -End "May, 2010"

 .Example
   # Highlight a range of days.
   Show-Calendar -HighlightDay (1..10 + 22) -HighlightDate "December 25, 2008"
#>
function Show-Calendar {
param(
    [DateTime] $start = [DateTime]::Today,
    [DateTime] $end = $start,
    $firstDayOfWeek,
    [int[]] $highlightDay,
    [string[]] $highlightDate = [DateTime]::Today.ToString()
    )

## Determine the first day of the start and end months.
$start = New-Object DateTime $start.Year,$start.Month,1
$end = New-Object DateTime $end.Year,$end.Month,1

## Convert the highlighted dates into real dates.
[DateTime[]] $highlightDate = [DateTime[]] $highlightDate

## Retrieve the DateTimeFormat information so that the
## calendar can be manipulated.
$dateTimeFormat  = (Get-Culture).DateTimeFormat
if($firstDayOfWeek)
{
    $dateTimeFormat.FirstDayOfWeek = $firstDayOfWeek
}

$currentDay = $start

## Process the requested months.
while($start -le $end)
{
    ## Return to an earlier point in the function if the first day of the month
    ## is in the middle of the week.
    while($currentDay.DayOfWeek -ne $dateTimeFormat.FirstDayOfWeek)
    {
        $currentDay = $currentDay.AddDays(-1)
    }

    ## Prepare to store information about this date range.
    $currentWeek = New-Object PsObject
    $dayNames = @()
    $weeks = @()

    ## Continue processing dates until the function reaches the end of the month.
    ## The function continues until the week is completed with
    ## days from the next month.
    while(($currentDay -lt $start.AddMonths(1)) -or
        ($currentDay.DayOfWeek -ne $dateTimeFormat.FirstDayOfWeek))
    {
        ## Determine the day names to use to label the columns.
        $dayName = "{0:ddd}" -f $currentDay
        if($dayNames -notcontains $dayName)
        {
            $dayNames += $dayName
        }

        ## Pad the day number for display, highlighting if necessary.
        $displayDay = " {0,2} " -f $currentDay.Day

        ## Determine whether to highlight a specific date.
        if($highlightDate)
        {
            $compareDate = New-Object DateTime $currentDay.Year,
                $currentDay.Month,$currentDay.Day
            if($highlightDate -contains $compareDate)
            {
                $displayDay = "*" + ("{0,2}" -f $currentDay.Day) + "*"
            }
        }

        ## Otherwise, highlight as part of a date range.
        if($highlightDay -and ($highlightDay[0] -eq $currentDay.Day))
        {
            $displayDay = "[" + ("{0,2}" -f $currentDay.Day) + "]"
            $null,$highlightDay = $highlightDay
        }

        ## Add the day of the week and the day of the month as note properties.
        $currentWeek | Add-Member NoteProperty $dayName $displayDay

        ## Move to the next day of the month.
        $currentDay = $currentDay.AddDays(1)

        ## If the function reaches the next week, store the current week
        ## in the week list and continue.
        if($currentDay.DayOfWeek -eq $dateTimeFormat.FirstDayOfWeek)
        {
            $weeks += $currentWeek
            $currentWeek = New-Object PsObject
        }
    }

    ## Format the weeks as a table.
    $calendar = $weeks | Format-Table $dayNames -AutoSize | Out-String

    ## Add a centered header.
    $width = ($calendar.Split("`n") | Measure-Object -Maximum Length).Maximum
    $header = "{0:MMMM yyyy}" -f $start
    $padding = " " * (($width - $header.Length) / 2)
    $displayCalendar = " `n" + $padding + $header + "`n " + $calendar
    $displayCalendar.TrimEnd()

    ## Move to the next month.
    $start = $start.AddMonths(1)

}
}
Export-ModuleMember -Function Show-Calendar
```
