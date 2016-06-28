---
title: "从列表框中选择项"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 327c7cc5-21d0-4ace-b151-aa1491d1d3c2
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 7e8fd05cfedd500c51f2d7e4f6adbb7d1f27cb00

---

# 从列表框中选择项
使用 Windows PowerShell 3.0 和更高版本创建一个对话框，从而允许用户从列表框控件中选择项。

## 创建一个列表框控件，并从中选择项
复制以下内容并将其粘贴到 Windows PowerShell ISE 中，然后将其另存为 Windows PowerShell 脚本 (.ps1)。

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form 
$form.Text = "Select a Computer"
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
$label.Text = "Please select a computer:"
$form.Controls.Add($label) 

$listBox = New-Object System.Windows.Forms.ListBox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20) 
$listBox.Height = 80

[void] $listBox.Items.Add("atl-dc-001")
[void] $listBox.Items.Add("atl-dc-002")
[void] $listBox.Items.Add("atl-dc-003")
[void] $listBox.Items.Add("atl-dc-004")
[void] $listBox.Items.Add("atl-dc-005")
[void] $listBox.Items.Add("atl-dc-006")
[void] $listBox.Items.Add("atl-dc-007")

$form.Controls.Add($listBox) 

$form.Topmost = $True

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

该脚本首先加载两个 .NET Framework 类：**System.Drawing** 和 **System.Windows.Forms**。 然后，启动 .NET Framework 类 **System.Windows.Forms.Form** 的新实例；它提供一个可以开始添加控件的空白窗体或窗口。

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
```

在创建 Form 类的实例后，为此类的三个属性赋值。

-   **Text。** 这将成为该窗口的标题。

-   **Size。** 这是窗体的大小（以像素为单位）。 上述脚本创建的窗体大小为宽 300 像素、高 200 像素。

-   **StartingPosition。** 在上述脚本中，此可选属性将设置为 **CenterScreen**。 如果未添加此属性，Windows 将在窗体打开时选择一个位置。 通过将 **StartingPosition** 设置为 **CenterScreen**，可使窗体在每次加载时都自动显示在屏幕中间。

```
$form.Text = "Select a Computer"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"
```

接下来，为窗体创建“确定”按钮。   指定“确定”按钮的大小和行为。 在此示例中，按钮位置为距窗体上边缘 120 像素，距左边缘 75 像素。 按钮高度为 23 像素，按钮长度为 75 像素。 此脚本使用预定义的 Windows 窗体类型确定按钮行为。

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
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

接下来，在窗口上提供标签文本，用于描述你希望用户提供的信息。 在本例中，你希望用户选择一台计算机。

```
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please select a computer:"
$form.Controls.Add($label)
```

添加控件（在本例中为列表框），从而让用户提供你在标签文本中描述的信息。 除了文本框，你还可以应用许多其他控件；有关更多控件，请参阅 MSDN 上的 [System.Windows.Forms 命名空间](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx)。

```
$listBox = New-Object System.Windows.Forms.ListBox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20) 
$listBox.Height = 80
```

在下一部分中，你可以指定希望列表框向用户显示的值。

> [!NOTE]
> 此脚本创建的列表框只允许进行单选。 若要创建允许进行多选的列表框控件，请指定 **SelectionMode** 属性的值，类似于以下内容：`$listBox.SelectionMode = "MultiExtended"`。 有关详细信息，请参阅[多选列表框](Multiple-selection-List-Boxes.md)。

```
[void] $listBox.Items.Add("atl-dc-001")
[void] $listBox.Items.Add("atl-dc-002")
[void] $listBox.Items.Add("atl-dc-003")
[void] $listBox.Items.Add("atl-dc-004")
[void] $listBox.Items.Add("atl-dc-005")
[void] $listBox.Items.Add("atl-dc-006")
[void] $listBox.Items.Add("atl-dc-007")
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

最后，**If** 块内的代码指示在用户从列表框中选择某个选项，然后单击“确定”按钮或按“Enter”键后，Windows 应如何处理该窗体。

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

## 另请参阅
[Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?](http://go.microsoft.com/fwlink/?LinkId=506644)（Hey Scripting Guy 博客：为什么这些 PowerShell GUI 示例不起作用？）
[GitHub: Dave Wyatt's WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)（Dave Wyatt 的 WinFormsExampleUpdates）
[Windows PowerShell Tip of the Week:  Selecting Items from a List Box](http://technet.microsoft.com/library/ff730949.aspx)（Windows PowerShell 每周提示：从列表框选择项）




<!--HONumber=Jun16_HO4-->


