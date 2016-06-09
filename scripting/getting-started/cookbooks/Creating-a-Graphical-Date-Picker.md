---
title:  创建图形日期选取器
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  c1cb722c-41e9-4baa-be83-59b4653222e9
---

# 创建图形日期选取器
使用 Windows PowerShell 3.0 和更高版本创建一个带有日历式图形控件的窗体，该控件使用户可以选择本月的某一天。

## 创建图形日期选取器控件
复制以下内容并将其粘贴到 Windows PowerShell ISE 中，然后将其另存为 Windows PowerShell 脚本 (.ps1)。

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form 

$form.Text = "Select a Date" 
$form.Size = New-Object Drawing.Size @(243,230) 
$form.StartPosition = "CenterScreen"

$calendar = New-Object System.Windows.Forms.MonthCalendar 
$calendar.ShowTodayCircle = $False
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar) 

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$form.Topmost = $True

$result = $form.ShowDialog() 

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

该脚本首先加载两个 .NET Framework 类：**System.Drawing** 和 **System.Windows.Forms**。 然后，启动 .NET Framework 类 **Windows.Forms.Form** 的新实例；它提供一个可以开始添加控件的空白窗体或窗口。

```
$form = New-Object Windows.Forms.Form
```

在创建 Form 类的实例后，为此类的三个属性赋值。

-   **Text。** 这将成为该窗口的标题。

-   **Size。** 这是窗体的大小（以像素为单位）。 上述脚本创建的窗体大小为宽 243 像素、高 230 像素。

-   **StartingPosition。** 在上述脚本中，此可选属性将设置为 **CenterScreen**。 如果未添加此属性，Windows 将在窗体打开时选择一个位置。 通过将 **StartingPosition** 设置为 **CenterScreen**，可使窗体在每次加载时都自动显示在屏幕中间。

```
$form.Text = "Select a Date" 
$form.Size = New-Object Drawing.Size @(243,230) 
$form.StartPosition = "CenterScreen"
```

接下来，在窗体中创建并添加一个日历控件。 在此示例中，当前日期未突出显示或带圆圈。 用户一次只可以在日历上选择一天。

```
$calendar = New-Object System.Windows.Forms.MonthCalendar 
$calendar.ShowTodayCircle = $False
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

接下来，为窗体创建“确定”按钮。 指定“确定”按钮的大小和行为。 在此示例中，按钮位置为距窗体上边缘 165 像素，距左边缘 38 像素。 按钮高度为 23 像素，按钮长度为 75 像素。 此脚本使用预定义的 Windows 窗体类型确定按钮行为。

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

采用相同方式创建“取消”按钮。 “取消”按钮距窗口上边缘 165 像素，但距左边缘 113 像素。

```
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

将 **Topmost** 属性设置为 **$True** 以强制该窗口在其他打开的窗口和对话框之上打开。

```
$form.Topmost = $True
```

添加以下代码行以在 Windows 中显示该窗体。

```
$result = $form.ShowDialog()
```

最后，**If** 块内的代码指示在用户在日历上选择某一天，然后单击“确定”按钮或按“Enter”键后，Windows 应如何处理该窗体。 Windows PowerShell 向用户显示选定的日期。

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## 另请参阅
[Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?（Hey Scripting Guy 博客：为什么这些 PowerShell GUI 示例不起作用？）](http://go.microsoft.com/fwlink/?LinkId=506644)
[GitHub: Dave Wyatt's WinFormsExampleUpdates（GitHub：Dave Wyatt 的 WinFormsExampleUpdates）](https://github.com/dlwyatt/WinFormsExampleUpdates)
[Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker（Windows PowerShell 每周提示：创建图形日期选取器）](http://technet.microsoft.com/library/ff730942.aspx)



<!--HONumber=May16_HO2-->


