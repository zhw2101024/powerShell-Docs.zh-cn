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
ms.openlocfilehash: e8b7151538235cdf7183b78aa8df7e596d6bcfd9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859003"
---
# <a name="how-to-write-a-powershell-script-module"></a>如何编写 PowerShell 脚本模块

脚本模块是实质上是任何有效的 PowerShell 脚本保存在扩展名为.psm1。 该扩展允许 PowerShell 引擎将在你的文件上使用多种规则和 cmdlet。 大多数这些功能是为了帮助你还可以管理作用域在其他系统上安装你的代码。 此外可以使用模块清单文件，可以描述变得更加复杂的安装和解决方案。

## <a name="writing-a-powershell-script-module"></a>编写 PowerShell 脚本模块

通过将有效的 PowerShell 脚本保存到.psm1 文件中，然后将该文件保存在位于 PowerShell 可在其中找到一个目录中创建的脚本模块。 在该文件夹中还可以将任何所需的资源以运行您的脚本，以及一个清单文件用于描述到 PowerShell 模块的工作原理。

#### <a name="to-create-a-basic-powershell-module"></a>若要创建基本的 PowerShell 模块

1. 选取现有的 PowerShell 脚本，并具有.psm1 扩展名保存脚本。

   保存具有.psm1 的脚本扩展意味着，您可以使用模块 cmdlet，如[导入模块](/powershell/module/Microsoft.PowerShell.Core/Import-Module)，其上。 这些 cmdlet 存在主要，以便您可以轻松地导入和导出到其他用户的系统上您的代码。 （替代解决方案是在其他系统，然后使用点获取来源代码将其加载到活动内存中，这并不特别是可缩放的解决方案。）有关详细信息请参阅**模块 Cmdlet 和变量**主题中[Windows PowerShell 模块](./understanding-a-windows-powershell-module.md)请注意，默认情况下，您的脚本中的所有函数都可供导入你.psm1 的用户文件，但属性将不会。

   在本主题末尾提供了示例 PowerShell 脚本，标题为显示日历。

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

2. 如果你想要控制用户对特定函数或属性访问，则调用[Export-modulemember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember)您的脚本结尾处。

   在页面底部的示例代码具有只有一个函数，它默认情况下会公开。 但是，建议你明确指出希望公开，如下面的代码中所述的函数：

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   你还可以限制什么使用模块清单导入。 有关详细信息，请参阅[导入 PowerShell 模块](./importing-a-powershell-module.md)并[如何编写 PowerShell 模块清单](./how-to-write-a-powershell-module-manifest.md)。

3. 如果你有自己的模块需要已加载的模块，你可以使用这些通过调用`Import-Module`，在你自己的模块的顶部。

   `Import-Module` 是一个导入到系统上的目标的模块的 cmdlet。 在这种情况下，它还用于在以后过程中安装你自己的模块。 在此页底部的示例代码不使用任何导入模块。 如果有的话，但是，它们会列出顶部的文件，如下面的代码中所述：

   ```powershell
   Import-Module GenericModule
   ```

4. 如果你想要描述你对 PowerShell 帮助系统的模块，就可以做到文件内的标准帮助注释或包含一个额外的帮助文件。

   本主题底部的代码示例在注释中包含的帮助信息。 如果这样选择，也可以编写展开的 XML 文件包含更多帮助内容。 有关详细信息，请参阅[编写为 Windows PowerShell 模块帮助](./writing-help-for-windows-powershell-modules.md)。

5. 如果你有更多的模块、 XML 文件或想要打包对模块的使用其他内容，就可以做到与模块清单。

   模块清单是包含其他模块、 目录布局、 版本控制编号、 作者数据和其他信息片段的名称的文件。 PowerShell 使用模块清单文件来组织和部署你的解决方案。 但是，由于此示例中的相对简单特性，不需要清单文件。 有关详细信息，请参阅[模块清单](./how-to-write-a-powershell-module-manifest.md)。

6. 若要安装和运行你的模块，将模块保存到一个相应的 PowerShell 路径，并调用`Import-Module`。

   您可以在其中安装你的模块的路径位于`$env:PSModulePath`全局变量。 例如，若要将模块保存在系统上的公共路径将`%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`。 请务必创建你的模块中，存在一个文件夹，即使它是单个.psm1 文件。 如果不保存你的模块对两个路径，必须在调用中模块的位置传递`Import-Module`。 （否则，PowerShell 将不能找到它。）与 PowerShell 3.0 中，从开始，如果有一个 PowerShell 模块路径上放置你的模块，你不需要显式将其导入： 只需让用户调用函数将自动加载它。 模块路径的详细信息，请参阅[导入 PowerShell 模块](./importing-a-powershell-module.md)并[PSModulePath 环境变量](./modifying-the-psmodulepath-installation-path.md)。

7. 若要从活动服务中删除模块，请调用[Remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module)。

请注意， [Remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module)删除你的模块从活动内存-它不会实际删除它从保存的模块文件的位置。

### <a name="show-calendar-code-example"></a>显示日历的代码示例

下面的示例是一个简单的脚本模块，其中包含一个名为显示日历的单个函数。 此函数显示日历的可视表示形式。 此外，该示例包含有关摘要、 说明、 参数值和示例的 PowerShell 帮助字符串。 请注意最后一行代码，指示导入模块时，显示日历函数，导出为模块成员。

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
    $width = ($calendar.Split("'n") | Measure-Object -Maximum Length).Maximum
    $header = "{0:MMMM yyyy}" -f $start
    $padding = " " * (($width - $header.Length) / 2)
    $displayCalendar = " 'n" + $padding + $header + "'n " + $calendar
    $displayCalendar.TrimEnd()

    ## Move to the next month.
    $start = $start.AddMonths(1)

}
}
Export-ModuleMember -Function Show-Calendar
```
