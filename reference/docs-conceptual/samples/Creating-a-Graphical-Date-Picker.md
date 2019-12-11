---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 创建图形日期选取器
ms.openlocfilehash: d05445963b41af61a61aa29a425e638d43fb5d9d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030251"
---
# <a name="creating-a-graphical-date-picker"></a>创建图形日期选取器

使用 Windows PowerShell 3.0 和更高版本创建一个带有日历式图形控件的窗体，该控件使用户可以选择本月的某一天。

## <a name="create-a-graphical-date-picker-control"></a>创建图形日期选取器控件

复制以下内容并将其粘贴到 Windows PowerShell ISE 中，然后将其另存为 Windows PowerShell 脚本 (.ps1)。

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}

$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)

$OKButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$result = $form.ShowDialog()

if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

该脚本首先加载两个 .NET Framework 类：System.Drawing 和 System.Windows.Forms   。
然后，启动 .NET Framework 类 **Windows.Forms.Form** 的新实例；它提供一个可以开始添加控件的空白窗体或窗口。

```powershell
$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}
```

此示例使用 Property 属性和 hashtable 将值分配给此类的四个属性  。

1. **StartPosition**：如果未添加此属性，Windows 将在窗体打开时选择一个位置。
   通过将此属性设置为 CenterScreen  ，可使窗体在每次加载时都自动显示在屏幕中间。

2. **Size**：这是窗体的大小（以像素为单位）。
   上述脚本创建的窗体大小为宽 243 像素、高 230 像素。

3. **Text**：这将成为该窗口的标题。

4. **Topmost**：通过将此属性设置为 `$true`，可以强制此窗口在其他已打开的窗口和对话框之上打开。

接下来，在窗体中创建并添加一个日历控件。
在此示例中，当前日期未突出显示或带圆圈。
用户一次只可以在日历上选择一天。

```powershell
$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)
```

接下来，为窗体创建“确定”按钮。 
指定“确定”按钮的大小和行为。 
在此示例中，按钮位置为距窗体上边缘 165 像素，距左边缘 38 像素。
按钮高度为 23 像素，按钮长度为 75 像素。
此脚本使用预定义的 Windows 窗体类型确定按钮行为。

```powershell
$OKButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

采用相同方式创建“取消”按钮。 
“取消”按钮距窗口上边缘 165 像素，但距左边缘 113 像素。 

```powershell
$CancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

添加以下代码行以在 Windows 中显示该窗体。

```powershell
$result = $form.ShowDialog()
```

最后，`if` 块内的代码指示在用户在日历上选择某一天，然后单击“确定”按钮或按“Enter”键后，Windows 应如何处理该窗体   。
Windows PowerShell 向用户显示选定的日期。

```powershell
if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a>另请参阅

- [你好，脚本专家：为什么这些 PowerShell GUI 示例不起作用呢？](https://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub：Dave Wyatt 的 WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [本周 Windows PowerShell 提示：创建图形日期选取器](https://technet.microsoft.com/library/ff730942.aspx)
