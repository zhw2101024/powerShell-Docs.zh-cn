---
title:  多选列表框
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  f74cd5d9-da57-4802-b614-0b194a7bc8f8
---

# 多选列表框
使用 Windows PowerShell 3.0 和更高版本在自定义 Windows 窗体中创建多选列表框控件。

## 创建允许进行多选的列表框控件
复制以下内容并将其粘贴到 Windows PowerShell ISE 中，然后将其另存为 Windows PowerShell 脚本 (.ps1)。

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form 
$form.Text = "Data Entry Form"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please make a selection from the list below:"
$form.Controls.Add($label) 

$listBox = New-Object System.Windows.Forms.Listbox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20) 

$listBox.SelectionMode = "MultiExtended"

[void] $listBox.Items.Add("Item 1")
[void] $listBox.Items.Add("Item 2")
[void] $listBox.Items.Add("Item 3")
[void] $listBox.Items.Add("Item 4")
[void] $listBox.Items.Add("Item 5")

$listBox.Height = 70
$form.Controls.Add($listBox) 
$form.Topmost = $True

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

该脚本首先加载两个 .NET Framework 类：**System.Drawing** 和 **System.Windows.Forms**。 然后，启动 .NET Framework 类 **System.Windows.Forms.Form** 的新实例；它提供一个可以开始添加控件的空白窗体或窗口。

```
$form = New-Object System.Windows.Forms.Form
```

在创建 Form 类的实例后，为此类的三个属性赋值。

-   **Text。** 这将成为该窗口的标题。

-   **Size。** 这是窗体的大小（以像素为单位）。 上述脚本创建的窗体大小为宽 300 像素、高 200 像素。

-   **StartingPosition。** 在上述脚本中，此可选属性将设置为 **CenterScreen**。 如果未添加此属性，Windows 将在窗体打开时选择一个位置。 通过将 **StartingPosition** 设置为 **CenterScreen**，可使窗体在每次加载时都自动显示在屏幕中间。

```
$form.Text = "Data Entry Form"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"
```

接下来，为窗体创建“确定”按钮。 指定“确定”按钮的大小和行为。 在此示例中，按钮位置为距窗体上边缘 120 像素，距左边缘 75 像素。 按钮高度为 23 像素，按钮长度为 75 像素。 此脚本使用预定义的 Windows 窗体类型确定按钮行为。

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Size(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

采用相同方式创建“取消”按钮。 “取消”按钮距窗口上边缘 120 像素，但距左边缘 150 像素。

```
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

接下来，在窗口上提供标签文本，用于描述你希望用户提供的信息。

```
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please make a selection from the list below:"
$form.Controls.Add($label)
```

添加控件（在本例中为列表框），从而让用户提供你在标签文本中描述的信息。 除了文本框，你还可以应用许多其他控件；有关更多控件，请参阅 MSDN 上的 [System.Windows.Forms 命名空间](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx)。

```
$listBox = New-Object System.Windows.Forms.Listbox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20)
```

下面介绍如何指定你希望允许用户从列表中选择多个值。

```
$listBox.SelectionMode = "MultiExtended"
```

在下一部分中，你可以指定希望列表框向用户显示的值。

```
[void] $listBox.Items.Add("Item 1")
[void] $listBox.Items.Add("Item 2")
[void] $listBox.Items.Add("Item 3")
[void] $listBox.Items.Add("Item 4")
[void] $listBox.Items.Add("Item 5")
```

指定列表框控件的最大高度。

```
$listBox.Height = 70
```

将列表框控件添加到窗体中，并指示 Windows 在打开该窗体时，在其他窗口和对话框之上打开它。

```
$form.Controls.Add($listBox) 
$form.Topmost = $True
```

添加以下代码行以在 Windows 中显示该窗体。

```
$result = $form.ShowDialog()
```

最后，**If** 块内的代码指示在用户从列表框中选择一个或多个选项，然后单击“确定”按钮或按“Enter”键后，Windows 应如何处理该窗体。

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

## 另请参阅
[Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?（Hey Scripting Guy 博客：为什么这些 PowerShell GUI 示例不起作用？）](http://go.microsoft.com/fwlink/?LinkId=506644)
[GitHub: Dave Wyatt's WinFormsExampleUpdates（GitHub：Dave Wyatt 的 WinFormsExampleUpdates）](https://github.com/dlwyatt/WinFormsExampleUpdates)
[Windows PowerShell Tip of the Week:  Multi-Select List Boxes – And More!（Windows PowerShell 每周提示：多选列表框 - 还有更多！）](http://technet.microsoft.com/library/ff730950.aspx)



<!--HONumber=May16_HO2-->


