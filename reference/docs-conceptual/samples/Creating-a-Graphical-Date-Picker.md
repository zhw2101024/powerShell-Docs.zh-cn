---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 创建图形日期选取器
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: d3b24af935e781a8a36fc346a6108baaed37b6db
ms.sourcegitcommit: 3f6002e7109373eda31cc65fc84d2600447cb7e9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59506795"
---
# <a name="creating-a-graphical-date-picker"></a><span data-ttu-id="4ead4-103">创建图形日期选取器</span><span class="sxs-lookup"><span data-stu-id="4ead4-103">Creating a Graphical Date Picker</span></span>

<span data-ttu-id="4ead4-104">使用 Windows PowerShell 3.0 和更高版本创建一个带有日历式图形控件的窗体，该控件使用户可以选择本月的某一天。</span><span class="sxs-lookup"><span data-stu-id="4ead4-104">Use Windows PowerShell 3.0 and later releases to create a form with a graphical, calendar-style control that lets users select a day of the month.</span></span>

## <a name="create-a-graphical-date-picker-control"></a><span data-ttu-id="4ead4-105">创建图形日期选取器控件</span><span class="sxs-lookup"><span data-stu-id="4ead4-105">Create a graphical date-picker control</span></span>

<span data-ttu-id="4ead4-106">复制以下内容并将其粘贴到 Windows PowerShell ISE 中，然后将其另存为 Windows PowerShell 脚本 (.ps1)。</span><span class="sxs-lookup"><span data-stu-id="4ead4-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

<span data-ttu-id="4ead4-107">该脚本首先加载两个 .NET Framework 类：System.Drawing 和 System.Windows.Forms。</span><span class="sxs-lookup"><span data-stu-id="4ead4-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span>
<span data-ttu-id="4ead4-108">然后，启动 .NET Framework 类 **Windows.Forms.Form** 的新实例；它提供一个可以开始添加控件的空白窗体或窗口。</span><span class="sxs-lookup"><span data-stu-id="4ead4-108">You then start a new instance of the .NET Framework class **Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}
```

<span data-ttu-id="4ead4-109">此示例使用 Property 属性和 hashtable 将值分配给此类的四个属性。</span><span class="sxs-lookup"><span data-stu-id="4ead4-109">This example assigns values to four properties of this class by using the **Property** property and hashtable.</span></span>

1. <span data-ttu-id="4ead4-110">**StartPosition**：如果未添加此属性，Windows 将在窗体打开时选择一个位置。</span><span class="sxs-lookup"><span data-stu-id="4ead4-110">**StartPosition**: If you don’t add this property, Windows selects a location when the form is opened.</span></span>
   <span data-ttu-id="4ead4-111">通过将此属性设置为 CenterScreen，可使窗体在每次加载时都自动显示在屏幕中间。</span><span class="sxs-lookup"><span data-stu-id="4ead4-111">By setting this property to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

2. <span data-ttu-id="4ead4-112">**Size**：这是窗体的大小（以像素为单位）。</span><span class="sxs-lookup"><span data-stu-id="4ead4-112">**Size**: This is the size of the form, in pixels.</span></span>
   <span data-ttu-id="4ead4-113">上述脚本创建的窗体大小为宽 243 像素、高 230 像素。</span><span class="sxs-lookup"><span data-stu-id="4ead4-113">The preceding script creates a form that’s 243 pixels wide by 230 pixels tall.</span></span>

3. <span data-ttu-id="4ead4-114">**Text**：这将成为该窗口的标题。</span><span class="sxs-lookup"><span data-stu-id="4ead4-114">**Text**: This becomes the title of the window.</span></span>

4. <span data-ttu-id="4ead4-115">**Topmost**：通过将此属性设置为 `$true`，可以强制此窗口在其他已打开的窗口和对话框之上打开。</span><span class="sxs-lookup"><span data-stu-id="4ead4-115">**Topmost**: By setting this property to `$true`, you can force the window to open atop other open windows and dialog boxes.</span></span>

<span data-ttu-id="4ead4-116">接下来，在窗体中创建并添加一个日历控件。</span><span class="sxs-lookup"><span data-stu-id="4ead4-116">Next, create and then add a calendar control in your form.</span></span>
<span data-ttu-id="4ead4-117">在此示例中，当前日期未突出显示或带圆圈。</span><span class="sxs-lookup"><span data-stu-id="4ead4-117">In this example, the current day is not highlighted or circled.</span></span>
<span data-ttu-id="4ead4-118">用户一次只可以在日历上选择一天。</span><span class="sxs-lookup"><span data-stu-id="4ead4-118">Users can select only one day on the calendar at one time.</span></span>

```powershell
$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)
```

<span data-ttu-id="4ead4-119">接下来，为窗体创建“确定”按钮。</span><span class="sxs-lookup"><span data-stu-id="4ead4-119">Next, create an **OK** button for your form.</span></span>
<span data-ttu-id="4ead4-120">指定“确定”按钮的大小和行为。</span><span class="sxs-lookup"><span data-stu-id="4ead4-120">Specify the size and behavior of the **OK** button.</span></span>
<span data-ttu-id="4ead4-121">在此示例中，按钮位置为距窗体上边缘 165 像素，距左边缘 38 像素。</span><span class="sxs-lookup"><span data-stu-id="4ead4-121">In this example, the button position is 165 pixels from the form’s top edge, and 38 pixels from the left edge.</span></span>
<span data-ttu-id="4ead4-122">按钮高度为 23 像素，按钮长度为 75 像素。</span><span class="sxs-lookup"><span data-stu-id="4ead4-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span>
<span data-ttu-id="4ead4-123">此脚本使用预定义的 Windows 窗体类型确定按钮行为。</span><span class="sxs-lookup"><span data-stu-id="4ead4-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

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

<span data-ttu-id="4ead4-124">采用相同方式创建“取消”按钮。</span><span class="sxs-lookup"><span data-stu-id="4ead4-124">Similarly, you create a **Cancel** button.</span></span>
<span data-ttu-id="4ead4-125">“取消”按钮距窗口上边缘 165 像素，但距左边缘 113 像素。</span><span class="sxs-lookup"><span data-stu-id="4ead4-125">The **Cancel** button is 165 pixels from the top, but 113 pixels from the left edge of the window.</span></span>

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

<span data-ttu-id="4ead4-126">添加以下代码行以在 Windows 中显示该窗体。</span><span class="sxs-lookup"><span data-stu-id="4ead4-126">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="4ead4-127">最后，`if` 块内的代码指示在用户在日历上选择某一天，然后单击“确定”按钮或按“Enter”键后，Windows 应如何处理该窗体。</span><span class="sxs-lookup"><span data-stu-id="4ead4-127">Finally, the code inside the `if` block instructs Windows what to do with the form after users select a day on the calendar, and then click the **OK** button or press the **Enter** key.</span></span>
<span data-ttu-id="4ead4-128">Windows PowerShell 向用户显示选定的日期。</span><span class="sxs-lookup"><span data-stu-id="4ead4-128">Windows PowerShell displays the selected date to users.</span></span>

```powershell
if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a><span data-ttu-id="4ead4-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4ead4-129">See Also</span></span>

- [<span data-ttu-id="4ead4-130">脚本编写人员，你好：为什么这些 PowerShell GUI 示例不起作用呢？</span><span class="sxs-lookup"><span data-stu-id="4ead4-130">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](https://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="4ead4-131">GitHub：Dave Wyatt 的 WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="4ead4-131">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="4ead4-132">本周 Windows PowerShell 提示：创建图形日期选取器</span><span class="sxs-lookup"><span data-stu-id="4ead4-132">Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker</span></span>](https://technet.microsoft.com/library/ff730942.aspx)