---
title: 如何编写 PowerShell 脚本模块 |Microsoft Docs
ms.custom: ''
ms.date: 11/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed7645ea-5e52-4a45-81a7-aa3c2d605cde
caps.latest.revision: 16
ms.openlocfilehash: 7742eedd67283535b9e5898adc74d0d48faf68fe
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416263"
---
# <a name="how-to-write-a-powershell-script-module"></a><span data-ttu-id="19644-102">如何编写 PowerShell 脚本模块</span><span class="sxs-lookup"><span data-stu-id="19644-102">How to Write a PowerShell Script Module</span></span>

<span data-ttu-id="19644-103">脚本模块是任何保存在 `.psm1` 扩展中的有效 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="19644-103">A script module is any valid PowerShell script saved in a `.psm1` extension.</span></span> <span data-ttu-id="19644-104">此扩展允许 PowerShell 引擎对文件使用规则和模块 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="19644-104">This extension allows the PowerShell engine to use rules and module cmdlets on your file.</span></span> <span data-ttu-id="19644-105">其中的大多数功能都可帮助你在其他系统上安装代码，以及管理范围。</span><span class="sxs-lookup"><span data-stu-id="19644-105">Most of these capabilities are there to help you install your code on other systems, as well as manage scoping.</span></span> <span data-ttu-id="19644-106">你还可以使用模块清单文件，其中介绍了更复杂的安装和解决方案。</span><span class="sxs-lookup"><span data-stu-id="19644-106">You can also use a module manifest file, which describes more complex installations and solutions.</span></span>

## <a name="writing-a-powershell-script-module"></a><span data-ttu-id="19644-107">编写 PowerShell 脚本模块</span><span class="sxs-lookup"><span data-stu-id="19644-107">Writing a PowerShell script module</span></span>

<span data-ttu-id="19644-108">若要创建脚本模块，请将有效的 PowerShell 脚本保存到 `.psm1` 文件中。</span><span class="sxs-lookup"><span data-stu-id="19644-108">To create a script module, save a valid PowerShell script to a `.psm1` file.</span></span> <span data-ttu-id="19644-109">脚本及其存储位置的目录必须使用相同的名称。</span><span class="sxs-lookup"><span data-stu-id="19644-109">The script and the directory where it's stored must use the same name.</span></span> <span data-ttu-id="19644-110">例如，名为 `MyPsScript.psm1` 的脚本存储在名为 `MyPsScript`的目录中。</span><span class="sxs-lookup"><span data-stu-id="19644-110">For example, a script named `MyPsScript.psm1` is stored in a directory named `MyPsScript`.</span></span>

<span data-ttu-id="19644-111">模块的目录必须位于 `$env:PSModulePath`中指定的路径中。</span><span class="sxs-lookup"><span data-stu-id="19644-111">The module's directory needs to be in a path specified in `$env:PSModulePath`.</span></span> <span data-ttu-id="19644-112">模块的目录可以包含运行脚本所需的任何资源，还可以包含模块清单文件，用于描述模块的工作方式。</span><span class="sxs-lookup"><span data-stu-id="19644-112">The module's directory can contain any resources that are needed to run the script, and a module manifest file that describes to PowerShell how your module works.</span></span>

## <a name="create-a-basic-powershell-module"></a><span data-ttu-id="19644-113">创建基本 PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="19644-113">Create a basic PowerShell module</span></span>

<span data-ttu-id="19644-114">以下步骤介绍了如何创建 PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="19644-114">The following steps describe how to create a PowerShell module.</span></span>

1. <span data-ttu-id="19644-115">使用 `.psm1` 扩展名保存 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="19644-115">Save a PowerShell script with a `.psm1` extension.</span></span> <span data-ttu-id="19644-116">为脚本和保存脚本的目录使用相同的名称。</span><span class="sxs-lookup"><span data-stu-id="19644-116">Use the same name for the script and the directory where the script is saved.</span></span>

   <span data-ttu-id="19644-117">使用 `.psm1` 扩展名保存脚本意味着可以使用 module cmdlet，如[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)。</span><span class="sxs-lookup"><span data-stu-id="19644-117">Saving a script with the `.psm1` extension means that you can use the module cmdlets, such as [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span> <span data-ttu-id="19644-118">模块 cmdlet 主要用于将代码导入和导出到其他用户的系统上。</span><span class="sxs-lookup"><span data-stu-id="19644-118">The module cmdlets exist primarily so that you can import and export your code onto other user's systems.</span></span> <span data-ttu-id="19644-119">另一种解决方案是在其他系统上加载代码，然后将代码点置于活动内存中，这不是一种可缩放的解决方案。</span><span class="sxs-lookup"><span data-stu-id="19644-119">The alternate solution would be to load your code on other systems and then dot-source it into active memory, which isn't a scalable solution.</span></span> <span data-ttu-id="19644-120">有关详细信息，请参阅[了解 Windows PowerShell 模块](./understanding-a-windows-powershell-module.md#module-cmdlets-and-variables)。</span><span class="sxs-lookup"><span data-stu-id="19644-120">For more information, see [Understanding a Windows PowerShell Module](./understanding-a-windows-powershell-module.md#module-cmdlets-and-variables).</span></span>
   <span data-ttu-id="19644-121">默认情况下，当用户导入 `.psm1` 文件时，脚本中的所有函数都是可访问的，但变量不能。</span><span class="sxs-lookup"><span data-stu-id="19644-121">By default, when users import your `.psm1` file, all functions in your script are accessible, but variables aren't.</span></span>

   <span data-ttu-id="19644-122">本文末尾提供了一个名为 `Show-Calendar`的示例 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="19644-122">An example PowerShell script, entitled `Show-Calendar`, is available at the end of this article.</span></span>

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

2. <span data-ttu-id="19644-123">若要控制用户对某些函数或变量的访问，请在脚本末尾调用[export-modulemember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) 。</span><span class="sxs-lookup"><span data-stu-id="19644-123">To control user access to certain functions or variables, call [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) at the end of your script.</span></span>

   <span data-ttu-id="19644-124">本文底部的示例代码只有一个函数，该函数在默认情况下会公开。</span><span class="sxs-lookup"><span data-stu-id="19644-124">The example code at the bottom of the article has only one function, which by default would be exposed.</span></span> <span data-ttu-id="19644-125">但是，建议您显式调用要公开的函数，如以下代码所述：</span><span class="sxs-lookup"><span data-stu-id="19644-125">However, it's recommended you explicitly call out which functions you wish to expose, as described in the following code:</span></span>

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   <span data-ttu-id="19644-126">您可以使用模块清单来限制导入的内容。</span><span class="sxs-lookup"><span data-stu-id="19644-126">You can restrict what's imported using a module manifest.</span></span> <span data-ttu-id="19644-127">有关详细信息，请参阅[导入 Powershell 模块](./importing-a-powershell-module.md)和[如何编写 powershell 模块清单](./how-to-write-a-powershell-module-manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="19644-127">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [How to Write a PowerShell Module Manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

3. <span data-ttu-id="19644-128">如果你有自己的模块需要加载的模块，则可以使用模块顶部 `Import-Module`。</span><span class="sxs-lookup"><span data-stu-id="19644-128">If you have modules that your own module needs to load, you can use `Import-Module`, at the top of your module.</span></span>

   <span data-ttu-id="19644-129">`Import-Module` cmdlet 将目标模块导入到系统中，并可在稍后的过程中用于安装您自己的模块。</span><span class="sxs-lookup"><span data-stu-id="19644-129">The `Import-Module` cmdlet imports a targeted module onto a system, and can be used at a later point in the procedure to install your own module.</span></span> <span data-ttu-id="19644-130">本文底部的示例代码不使用任何导入模块。</span><span class="sxs-lookup"><span data-stu-id="19644-130">The sample code at the bottom of this article doesn't use any import modules.</span></span> <span data-ttu-id="19644-131">但如果确实如此，则会在文件顶部列出，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="19644-131">But if it did, they would be listed at the top of the file, as shown in the following code:</span></span>

   ```powershell
   Import-Module GenericModule
   ```

4. <span data-ttu-id="19644-132">若要将模块描述到 PowerShell 帮助系统，可以在文件中使用标准帮助注释，也可以创建其他帮助文件。</span><span class="sxs-lookup"><span data-stu-id="19644-132">To describe your module to the PowerShell Help system, you can either use standard help comments inside the file, or create an additional Help file.</span></span>

   <span data-ttu-id="19644-133">本文底部的代码示例包含注释中的帮助信息。</span><span class="sxs-lookup"><span data-stu-id="19644-133">The code sample at the bottom of this article includes the help information in the comments.</span></span> <span data-ttu-id="19644-134">你还可以编写包含其他帮助内容的扩展 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="19644-134">You could also write expanded XML files that contain additional help content.</span></span> <span data-ttu-id="19644-135">有关详细信息，请参阅[编写 Windows PowerShell 模块的帮助](./writing-help-for-windows-powershell-modules.md)。</span><span class="sxs-lookup"><span data-stu-id="19644-135">For more information, see [Writing Help for Windows PowerShell Modules](./writing-help-for-windows-powershell-modules.md).</span></span>

5. <span data-ttu-id="19644-136">如果你有其他要随模块一起打包的模块、XML 文件或其他内容，则可以使用模块清单。</span><span class="sxs-lookup"><span data-stu-id="19644-136">If you have additional modules, XML files, or other content you want to package with your module, you can use a module manifest.</span></span>

   <span data-ttu-id="19644-137">模块清单是一个文件，其中包含其他模块的名称、目录布局、版本控制编号、作者数据和其他信息片段。</span><span class="sxs-lookup"><span data-stu-id="19644-137">A module manifest is a file that contains the names of other modules, directory layouts, versioning numbers, author data, and other pieces of information.</span></span> <span data-ttu-id="19644-138">PowerShell 使用模块清单文件来组织和部署解决方案。</span><span class="sxs-lookup"><span data-stu-id="19644-138">PowerShell uses the module manifest file to organize and deploy your solution.</span></span> <span data-ttu-id="19644-139">有关详细信息，请参阅[如何编写 PowerShell 模块清单](./how-to-write-a-powershell-module-manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="19644-139">For more information, see [How to write a PowerShell module manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

6. <span data-ttu-id="19644-140">若要安装并运行模块，请将模块保存到相应的 PowerShell 路径之一，并使用 `Import-Module`。</span><span class="sxs-lookup"><span data-stu-id="19644-140">To install and run your module, save the module to one of the appropriate PowerShell paths, and use `Import-Module`.</span></span>

   <span data-ttu-id="19644-141">您可以在其中安装模块的路径位于 `$env:PSModulePath` 全局变量中。</span><span class="sxs-lookup"><span data-stu-id="19644-141">The paths where you can install your module are located in the `$env:PSModulePath` global variable.</span></span> <span data-ttu-id="19644-142">例如，在系统上保存模块的通用路径将 `%SystemRoot%/users/<user>/Documents/PowerShell/Modules/<moduleName>`。</span><span class="sxs-lookup"><span data-stu-id="19644-142">For example, a common path to save a module on a system would be `%SystemRoot%/users/<user>/Documents/PowerShell/Modules/<moduleName>`.</span></span> <span data-ttu-id="19644-143">请确保为模块创建一个与脚本模块同名的目录，即使它只是一个 `.psm1` 文件也是如此。</span><span class="sxs-lookup"><span data-stu-id="19644-143">Be sure to create a directory for your module that uses the same name as the script module, even if it's only a single `.psm1` file.</span></span> <span data-ttu-id="19644-144">如果未将模块保存到其中一个路径，则必须在 `Import-Module` 命令中指定该模块的位置。</span><span class="sxs-lookup"><span data-stu-id="19644-144">If you didn't save your module to one of these paths, you would have to specify the module's location in the `Import-Module` command.</span></span> <span data-ttu-id="19644-145">否则，PowerShell 将找不到该模块。</span><span class="sxs-lookup"><span data-stu-id="19644-145">Otherwise, PowerShell wouldn't be able to find the module.</span></span>

   <span data-ttu-id="19644-146">从 PowerShell 3.0 开始，如果已将模块放置在一个 PowerShell 模块路径中，则无需显式导入它。</span><span class="sxs-lookup"><span data-stu-id="19644-146">Starting with PowerShell 3.0, if you've placed your module in one of the PowerShell module paths, you don't need to explicitly import it.</span></span> <span data-ttu-id="19644-147">当用户调用函数时，将自动加载模块。</span><span class="sxs-lookup"><span data-stu-id="19644-147">Your module is automatically loaded when a user calls your function.</span></span> <span data-ttu-id="19644-148">有关模块路径的详细信息，请参阅[导入 PowerShell 模块](./importing-a-powershell-module.md)和[修改 PSModulePath 安装路径](./modifying-the-psmodulepath-installation-path.md)。</span><span class="sxs-lookup"><span data-stu-id="19644-148">For more information about the module path, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [Modifying the PSModulePath Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

7. <span data-ttu-id="19644-149">若要从当前 PowerShell 会话中的活动服务中删除模块，请使用[remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module)。</span><span class="sxs-lookup"><span data-stu-id="19644-149">To remove a module from active service in the current PowerShell session, use [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span></span>

   > [!NOTE]
   > <span data-ttu-id="19644-150">`Remove-Module` 从当前 PowerShell 会话中删除模块，但不会卸载模块或删除模块的文件。</span><span class="sxs-lookup"><span data-stu-id="19644-150">`Remove-Module` removes a module from the current PowerShell session, but doesn't uninstall the module or delete the module's files.</span></span>

## <a name="show-calendar-code-example"></a><span data-ttu-id="19644-151">显示日历代码示例</span><span class="sxs-lookup"><span data-stu-id="19644-151">Show-Calendar code example</span></span>

<span data-ttu-id="19644-152">下面的示例是一个脚本模块，其中包含一个名为 `Show-Calendar`的函数。</span><span class="sxs-lookup"><span data-stu-id="19644-152">The following example is a script module that contains a single function named `Show-Calendar`.</span></span> <span data-ttu-id="19644-153">此函数显示日历的直观表示形式。</span><span class="sxs-lookup"><span data-stu-id="19644-153">This function displays a visual representation of a calendar.</span></span> <span data-ttu-id="19644-154">该示例包含用于摘要、说明、参数值和代码的 PowerShell 帮助字符串。</span><span class="sxs-lookup"><span data-stu-id="19644-154">The sample contains the PowerShell Help strings for the synopsis, description, parameter values, and code.</span></span> <span data-ttu-id="19644-155">导入模块后，`Export-ModuleMember` 命令将确保 `Show-Calendar` 函数作为模块成员导出。</span><span class="sxs-lookup"><span data-stu-id="19644-155">When the module is imported, the `Export-ModuleMember` command ensures that the `Show-Calendar` function is exported as a module member.</span></span>

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
