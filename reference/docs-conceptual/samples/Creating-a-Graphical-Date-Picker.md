---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 创建图形日期选取器
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: 6dd43a3b1f4c67633ad1755de3db88eb8c6772c8
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400365"
---
# <a name="creating-a-graphical-date-picker"></a><span data-ttu-id="310df-103">创建图形日期选取器</span><span class="sxs-lookup"><span data-stu-id="310df-103">Creating a Graphical Date Picker</span></span>

<span data-ttu-id="310df-104">使用 Windows PowerShell 3.0 和更高版本创建一个带有日历式图形控件的窗体，该控件使用户可以选择本月的某一天。</span><span class="sxs-lookup"><span data-stu-id="310df-104">Use Windows PowerShell 3.0 and later releases to create a form with a graphical, calendar-style control that lets users select a day of the month.</span></span>

## <a name="create-a-graphical-date-picker-control"></a><span data-ttu-id="310df-105">创建图形日期选取器控件</span><span class="sxs-lookup"><span data-stu-id="310df-105">Create a graphical date-picker control</span></span>

<span data-ttu-id="310df-106">复制以下内容并将其粘贴到 Windows PowerShell ISE 中，然后将其另存为 Windows PowerShell 脚本 (.ps1)。</span><span class="sxs-lookup"><span data-stu-id="310df-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form

$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'

$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

<span data-ttu-id="310df-107">该脚本首先加载两个 .NET Framework 类：System.Drawing 和 System.Windows.Forms。</span><span class="sxs-lookup"><span data-stu-id="310df-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="310df-108">然后，启动 .NET Framework 类 **Windows.Forms.Form** 的新实例；它提供一个可以开始添加控件的空白窗体或窗口。</span><span class="sxs-lookup"><span data-stu-id="310df-108">You then start a new instance of the .NET Framework class **Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object Windows.Forms.Form
```

<span data-ttu-id="310df-109">在创建 Form 类的实例后，为此类的三个属性赋值。</span><span class="sxs-lookup"><span data-stu-id="310df-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="310df-110">**文本。**</span><span class="sxs-lookup"><span data-stu-id="310df-110">**Text.**</span></span> <span data-ttu-id="310df-111">这将成为该窗口的标题。</span><span class="sxs-lookup"><span data-stu-id="310df-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="310df-112">**大小。**</span><span class="sxs-lookup"><span data-stu-id="310df-112">**Size.**</span></span> <span data-ttu-id="310df-113">这是窗体的大小（以像素为单位）。</span><span class="sxs-lookup"><span data-stu-id="310df-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="310df-114">上述脚本创建的窗体大小为宽 243 像素、高 230 像素。</span><span class="sxs-lookup"><span data-stu-id="310df-114">The preceding script creates a form that’s 243 pixels wide by 230 pixels tall.</span></span>

- <span data-ttu-id="310df-115">**StartingPosition。**</span><span class="sxs-lookup"><span data-stu-id="310df-115">**StartingPosition.**</span></span> <span data-ttu-id="310df-116">在上述脚本中，此可选属性将设置为 **CenterScreen**。</span><span class="sxs-lookup"><span data-stu-id="310df-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="310df-117">如果未添加此属性，Windows 将在窗体打开时选择一个位置。</span><span class="sxs-lookup"><span data-stu-id="310df-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="310df-118">通过将 **StartingPosition** 设置为 **CenterScreen**，可使窗体在每次加载时都自动显示在屏幕中间。</span><span class="sxs-lookup"><span data-stu-id="310df-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="310df-119">接下来，在窗体中创建并添加一个日历控件。</span><span class="sxs-lookup"><span data-stu-id="310df-119">Next, create and then add a calendar control in your form.</span></span> <span data-ttu-id="310df-120">在此示例中，当前日期未突出显示或带圆圈。</span><span class="sxs-lookup"><span data-stu-id="310df-120">In this example, the current day is not highlighted or circled.</span></span> <span data-ttu-id="310df-121">用户一次只可以在日历上选择一天。</span><span class="sxs-lookup"><span data-stu-id="310df-121">Users can select only one day on the calendar at one time.</span></span>

```powershell
$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

<span data-ttu-id="310df-122">接下来，为窗体创建“确定”按钮。</span><span class="sxs-lookup"><span data-stu-id="310df-122">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="310df-123">指定“确定”按钮的大小和行为。</span><span class="sxs-lookup"><span data-stu-id="310df-123">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="310df-124">在此示例中，按钮位置为距窗体上边缘 165 像素，距左边缘 38 像素。</span><span class="sxs-lookup"><span data-stu-id="310df-124">In this example, the button position is 165 pixels from the form’s top edge, and 38 pixels from the left edge.</span></span> <span data-ttu-id="310df-125">按钮高度为 23 像素，按钮长度为 75 像素。</span><span class="sxs-lookup"><span data-stu-id="310df-125">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="310df-126">此脚本使用预定义的 Windows 窗体类型确定按钮行为。</span><span class="sxs-lookup"><span data-stu-id="310df-126">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="310df-127">采用相同方式创建“取消”按钮。</span><span class="sxs-lookup"><span data-stu-id="310df-127">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="310df-128">“取消”按钮距窗口上边缘 165 像素，但距左边缘 113 像素。</span><span class="sxs-lookup"><span data-stu-id="310df-128">The **Cancel** button is 165 pixels from the top, but 113 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="310df-129">将 Topmost 属性设置为 $True，以强制此窗口在其他已打开的窗口和对话框之上打开。</span><span class="sxs-lookup"><span data-stu-id="310df-129">Set the **Topmost** property to **$true** to force the window to open atop other open windows and dialog boxes.</span></span>

```powershell
$form.Topmost = $true
```

<span data-ttu-id="310df-130">添加以下代码行以在 Windows 中显示该窗体。</span><span class="sxs-lookup"><span data-stu-id="310df-130">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="310df-131">最后，**If** 块内的代码指示在用户在日历上选择某一天，然后单击“确定”按钮或按“Enter”键后，Windows 应如何处理该窗体。</span><span class="sxs-lookup"><span data-stu-id="310df-131">Finally, the code inside the **If** block instructs Windows what to do with the form after users select a day on the calendar, and then click the **OK** button or press the **Enter** key.</span></span> <span data-ttu-id="310df-132">Windows PowerShell 向用户显示选定的日期。</span><span class="sxs-lookup"><span data-stu-id="310df-132">Windows PowerShell displays the selected date to users.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a><span data-ttu-id="310df-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="310df-133">See Also</span></span>

- [<span data-ttu-id="310df-134">脚本编写人员，你好：为什么这些 PowerShell GUI 示例不起作用呢？</span><span class="sxs-lookup"><span data-stu-id="310df-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](https://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="310df-135">GitHub：Dave Wyatt 的 WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="310df-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="310df-136">Windows PowerShell 每周提示：创建图形日期选取器</span><span class="sxs-lookup"><span data-stu-id="310df-136">Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker</span></span>](https://technet.microsoft.com/library/ff730942.aspx)