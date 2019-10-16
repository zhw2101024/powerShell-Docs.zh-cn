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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360686"
---
# <a name="how-to-write-a-powershell-script-module"></a>如何编写 PowerShell 脚本模块

脚本模块实质上是保存在 hbase-runner.psm1 扩展中的任何有效 PowerShell 脚本。 此扩展允许 PowerShell 引擎对文件使用许多规则和 cmdlet。 其中的大多数功能都可帮助你在其他系统上安装代码，以及管理范围。 你还可以使用模块清单文件，该文件可以描述更复杂的安装和解决方案。

## <a name="writing-a-powershell-script-module"></a>编写 PowerShell 脚本模块

您可以通过将有效的 PowerShell 脚本保存到 hbase-runner.psm1 文件，然后将该文件保存在 PowerShell 可以找到它的目录中来创建脚本模块。 在该文件夹中，还可以放置运行脚本所需的任何资源，以及描述模块工作方式的清单文件。

#### <a name="to-create-a-basic-powershell-module"></a>创建基本 PowerShell 模块

1. 获取现有的 PowerShell 脚本，并使用扩展名 hbase-runner.psm1 保存该脚本。

   保存带有. hbase-runner.psm1 扩展名的脚本意味着可以使用模块 cmdlet （如[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)）。 这些 cmdlet 主要是为了使你能够轻松地将代码导入或导出到其他用户的系统上。 （另一种解决方案是在其他系统上加载代码，然后将代码点置于活动内存中，这不是一个特别可扩展的解决方案。）有关详细信息，请参阅[Windows PowerShell 模块](./understanding-a-windows-powershell-module.md)中的**模块 cmdlet 和变量**部分。请注意，默认情况下，导入 hbase-runner.psm1 文件的用户可以访问脚本中的所有函数，但不会显示属性。

   本主题末尾提供了一个名为 `Show-Calendar` 的示例 PowerShell 脚本。

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

2. 若要控制用户对某些函数或属性的访问，请在脚本末尾调用[export-modulemember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) 。

   页面底部的示例代码只有一个函数，该函数在默认情况下会公开。 但是，建议显式调用要公开的函数，如以下代码所述：

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   你还可以使用模块清单来限制导入的内容。 有关详细信息，请参阅[导入 Powershell 模块](./importing-a-powershell-module.md)和[如何编写 powershell 模块清单](./how-to-write-a-powershell-module-manifest.md)。

3. 如果你有自己的模块需要加载的模块，则可以在你自己的模块顶部对 `Import-Module` 进行调用。

   `Import-Module` 是一个将目标模块导入系统的 cmdlet。 同样，也可以在稍后的步骤中使用它来安装您自己的模块。 此页底部的示例代码不使用任何导入模块。 但是，如果确实如此，则会在文件顶部列出，如以下代码所述：

   ```powershell
   Import-Module GenericModule
   ```

4. 若要将模块描述到 PowerShell 帮助系统，可以在文件中使用标准帮助注释，也可以创建其他帮助文件。

   本主题底部的代码示例包含注释中的帮助信息。 你还可以编写包含其他帮助内容的扩展 XML 文件。 有关详细信息，请参阅[编写 Windows PowerShell 模块的帮助](./writing-help-for-windows-powershell-modules.md)。

5. 如果要将其他模块、XML 文件或其他内容与模块一起打包，则可以使用模块清单来实现此目的。

   模块清单是一个文件，其中包含其他模块的名称、目录布局、版本控制编号、作者数据和其他信息片段。 PowerShell 使用模块清单文件来组织和部署解决方案。 但是，由于本示例相对简单，因此不需要清单文件。 有关详细信息，请参阅[模块清单](./how-to-write-a-powershell-module-manifest.md)。

6. 若要安装并运行模块，请将模块保存到相应的 PowerShell 路径之一，并调用 `Import-Module`。

   可以在其中安装模块的路径位于 `$env:PSModulePath` 全局变量中。 例如，在系统上保存模块的通用路径将为 `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`。 请确保为模块创建一个文件夹，使其在中存在，即使它只是一个 hbase-runner.psm1 文件。 如果未将模块保存到其中一个路径，则必须在调用时将模块的位置传入 `Import-Module`。 （否则，PowerShell 将无法找到它。）从 PowerShell 3.0 开始，如果你已将模块放置在一个 PowerShell 模块路径中，则无需显式导入它。 当用户调用函数时，将自动加载模块。
   有关模块路径的详细信息，请参阅[导入 PowerShell 模块](./importing-a-powershell-module.md)和[PSModulePath 环境变量](./modifying-the-psmodulepath-installation-path.md)。

7. 若要从活动服务中删除模块，请调用[remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module)。

   请注意， [Remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module)从活动内存中删除模块，实际上不会将模块文件从保存到的位置删除。

### <a name="show-calendar-code-example"></a>显示日历代码示例

下面的示例是一个简单的脚本模块，其中包含一个名为 `Show-Calendar` 的函数。
此函数显示日历的直观表示形式。 此外，该示例还包含用于摘要、说明、参数值和示例的 PowerShell 帮助字符串。 请注意，最后一行代码确保在导入模块时，将 `Show-Calendar` 函数作为模块成员导出。

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
