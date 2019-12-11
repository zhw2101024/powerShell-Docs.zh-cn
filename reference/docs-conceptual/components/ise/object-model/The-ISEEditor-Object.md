---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: ISEEditor 对象
ms.openlocfilehash: 2d4c3d941035384c591ca57e809c0e3a9b852f5c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "62086759"
---
# <a name="the-iseeditor-object"></a><span data-ttu-id="d3e96-103">ISEEditor 对象</span><span class="sxs-lookup"><span data-stu-id="d3e96-103">The ISEEditor Object</span></span>

<span data-ttu-id="d3e96-104">**ISEEditor** 对象是 Microsoft.PowerShell.Host.ISE.ISEEditor 类的实例。</span><span class="sxs-lookup"><span data-stu-id="d3e96-104">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="d3e96-105">控制台窗格是 **ISEEditor** 对象。</span><span class="sxs-lookup"><span data-stu-id="d3e96-105">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="d3e96-106">每个 [ISEFile](The-ISEFile-Object.md) 对象都有一个关联的 **ISEEditor** 对象。</span><span class="sxs-lookup"><span data-stu-id="d3e96-106">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="d3e96-107">以下各节列出了 **ISEEditor** 对象的方法和属性。</span><span class="sxs-lookup"><span data-stu-id="d3e96-107">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="d3e96-108">方法</span><span class="sxs-lookup"><span data-stu-id="d3e96-108">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="d3e96-109">Clear\(\)</span><span class="sxs-lookup"><span data-stu-id="d3e96-109">Clear\(\)</span></span>

<span data-ttu-id="d3e96-110">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="d3e96-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d3e96-111">清除编辑器中的文本。</span><span class="sxs-lookup"><span data-stu-id="d3e96-111">Clears the text in the editor.</span></span>

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="d3e96-112">EnsureVisible\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="d3e96-112">EnsureVisible\(int lineNumber\)</span></span>

<span data-ttu-id="d3e96-113">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="d3e96-113">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d3e96-114">滚动编辑器以使对应于指定 **lineNumber** 参数值的行可见。</span><span class="sxs-lookup"><span data-stu-id="d3e96-114">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="d3e96-115">如果指定的行号超出范围 1，即用于定义有效行号的最后一个行号，则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="d3e96-115">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

<span data-ttu-id="d3e96-116">**lineNumber** 要使其可见的行号。</span><span class="sxs-lookup"><span data-stu-id="d3e96-116">**lineNumber** The number of the line that is to be made visible.</span></span>

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="d3e96-117">Focus\(\)</span><span class="sxs-lookup"><span data-stu-id="d3e96-117">Focus\(\)</span></span>

<span data-ttu-id="d3e96-118">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="d3e96-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d3e96-119">将焦点设置到编辑器。</span><span class="sxs-lookup"><span data-stu-id="d3e96-119">Sets the focus to the editor.</span></span>

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="d3e96-120">GetLineLength\(int lineNumber \)</span><span class="sxs-lookup"><span data-stu-id="d3e96-120">GetLineLength\(int lineNumber \)</span></span>

<span data-ttu-id="d3e96-121">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="d3e96-121">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d3e96-122">获取按行号指定的行的长度（整数形式）。</span><span class="sxs-lookup"><span data-stu-id="d3e96-122">Gets the line length as an integer for the line that is specified by the line number.</span></span>

<span data-ttu-id="d3e96-123">**lineNumber** 要获取长度的行号。</span><span class="sxs-lookup"><span data-stu-id="d3e96-123">**lineNumber** The number of the line of which to get the length.</span></span>

<span data-ttu-id="d3e96-124">**Returns** 所指定行号的行的长度。</span><span class="sxs-lookup"><span data-stu-id="d3e96-124">**Returns** The line length for the line at the specified line number.</span></span>

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="d3e96-125">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="d3e96-125">GoToMatch\(\)</span></span>

<span data-ttu-id="d3e96-126">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="d3e96-126">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="d3e96-127">如果编辑器对象的 **CanGoToMatch** 属性是 **$true**，当脱字号直接位于左括号、中括号或大括号 - \(、\[、{ - 或直接位于右括号、中括号或大括号 - \)、\]、}。</span><span class="sxs-lookup"><span data-stu-id="d3e96-127">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is **$true**, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - \(,\[,{ - or immediately after a closing parenthesis, bracket, or brace - \),\],}.</span></span>  <span data-ttu-id="d3e96-128">脱字号位于开始字符之前或结束字符之后。</span><span class="sxs-lookup"><span data-stu-id="d3e96-128">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="d3e96-129">如果 **CanGoToMatch** 属性是 **$false**，则此方法不执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="d3e96-129">If the **CanGoToMatch** property is **$false**, then this method does nothing.</span></span>

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a><span data-ttu-id="d3e96-130">InsertText\( text \)</span><span class="sxs-lookup"><span data-stu-id="d3e96-130">InsertText\( text \)</span></span>

<span data-ttu-id="d3e96-131">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="d3e96-131">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d3e96-132">将所选内容替换为文本或在当前脱字号位置插入文本。</span><span class="sxs-lookup"><span data-stu-id="d3e96-132">Replaces the selection with text or inserts text at the current caret position.</span></span>

<span data-ttu-id="d3e96-133">**text** - String 要插入的文本。</span><span class="sxs-lookup"><span data-stu-id="d3e96-133">**text** - String The text to insert.</span></span>

<span data-ttu-id="d3e96-134">请参阅本主题稍后介绍的[脚本示例](#scripting-example)。</span><span class="sxs-lookup"><span data-stu-id="d3e96-134">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="d3e96-135">Select\( startLine, startColumn, endLine, endColumn \)</span><span class="sxs-lookup"><span data-stu-id="d3e96-135">Select\( startLine, startColumn, endLine, endColumn \)</span></span>

<span data-ttu-id="d3e96-136">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="d3e96-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d3e96-137">从 **startLine**、**startColumn**、**endLine** 和 **endColumn** 参数中选择文本。</span><span class="sxs-lookup"><span data-stu-id="d3e96-137">Selects the text from the **startLine**, **startColumn**, **endLine**, and **endColumn** parameters.</span></span>

<span data-ttu-id="d3e96-138">**startLine** - Integer 所选内容的起始行。</span><span class="sxs-lookup"><span data-stu-id="d3e96-138">**startLine** - Integer The line where the selection starts.</span></span>

<span data-ttu-id="d3e96-139">**startColumn** - Integer 所选内容的起始行中的列。</span><span class="sxs-lookup"><span data-stu-id="d3e96-139">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

<span data-ttu-id="d3e96-140">**endLine** - Integer 所选内容的结束行。</span><span class="sxs-lookup"><span data-stu-id="d3e96-140">**endLine** - Integer The line where the selection ends.</span></span>

<span data-ttu-id="d3e96-141">**endColumn** - Integer 所选内容的结束行中的列。</span><span class="sxs-lookup"><span data-stu-id="d3e96-141">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

<span data-ttu-id="d3e96-142">请参阅本主题稍后介绍的[脚本示例](#scripting-example)。</span><span class="sxs-lookup"><span data-stu-id="d3e96-142">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="d3e96-143">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="d3e96-143">SelectCaretLine\(\)</span></span>

<span data-ttu-id="d3e96-144">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="d3e96-144">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d3e96-145">选择当前包含脱字号的整个文本行。</span><span class="sxs-lookup"><span data-stu-id="d3e96-145">Selects the entire line of text that currently contains the caret.</span></span>

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="d3e96-146">SetCaretPosition\( lineNumber, columnNumber \)</span><span class="sxs-lookup"><span data-stu-id="d3e96-146">SetCaretPosition\( lineNumber, columnNumber \)</span></span>

<span data-ttu-id="d3e96-147">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="d3e96-147">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d3e96-148">在行号和列号处设置脱字号位置。</span><span class="sxs-lookup"><span data-stu-id="d3e96-148">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="d3e96-149">如果脱字号行号或脱字号列号不在其各自的有效范围内，会引发异常。</span><span class="sxs-lookup"><span data-stu-id="d3e96-149">It throws an exception if either the caret line number  or the caret column number  are out of their respective valid ranges.</span></span>

<span data-ttu-id="d3e96-150">**lineNumber** - Integer 脱字号行号。</span><span class="sxs-lookup"><span data-stu-id="d3e96-150">**lineNumber** - Integer The caret line number.</span></span>

<span data-ttu-id="d3e96-151">**columnNumber** - Integer 脱字号列号。</span><span class="sxs-lookup"><span data-stu-id="d3e96-151">**columnNumber** - Integer The caret column number.</span></span>

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="d3e96-152">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="d3e96-152">ToggleOutliningExpansion\(\)</span></span>

<span data-ttu-id="d3e96-153">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="d3e96-153">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="d3e96-154">使所有大纲部分展开或折叠。</span><span class="sxs-lookup"><span data-stu-id="d3e96-154">Causes all the outline sections to expand or collapse.</span></span>

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="d3e96-155">“属性”</span><span class="sxs-lookup"><span data-stu-id="d3e96-155">Properties</span></span>

### <a name="cangotomatch"></a><span data-ttu-id="d3e96-156">CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="d3e96-156">CanGoToMatch</span></span>

<span data-ttu-id="d3e96-157">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="d3e96-157">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="d3e96-158">只读布尔值属性，指示脱字号是否位于小括号、中括号或大括号（即 \(\)、\[\]、{}）旁边。</span><span class="sxs-lookup"><span data-stu-id="d3e96-158">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - \(\), \[\], {}.</span></span> <span data-ttu-id="d3e96-159">如果脱字号直接位于开始字符之前或直接位于结束字符之后，则此属性值是 **$true**。</span><span class="sxs-lookup"><span data-stu-id="d3e96-159">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is **$true**.</span></span> <span data-ttu-id="d3e96-160">否则，是 **$false**。</span><span class="sxs-lookup"><span data-stu-id="d3e96-160">Otherwise, it is **$false**.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a><span data-ttu-id="d3e96-161">CaretColumn</span><span class="sxs-lookup"><span data-stu-id="d3e96-161">CaretColumn</span></span>

<span data-ttu-id="d3e96-162">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="d3e96-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d3e96-163">只读属性，可获取对应于脱字号位置的列号。</span><span class="sxs-lookup"><span data-stu-id="d3e96-163">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a><span data-ttu-id="d3e96-164">CaretLine</span><span class="sxs-lookup"><span data-stu-id="d3e96-164">CaretLine</span></span>

<span data-ttu-id="d3e96-165">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="d3e96-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d3e96-166">只读属性，可获取包含脱字号的行号。</span><span class="sxs-lookup"><span data-stu-id="d3e96-166">The read-only property that gets the number of the line that contains the caret.</span></span>

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a><span data-ttu-id="d3e96-167">CaretLineText</span><span class="sxs-lookup"><span data-stu-id="d3e96-167">CaretLineText</span></span>

<span data-ttu-id="d3e96-168">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="d3e96-168">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d3e96-169">只读属性，可获取包含脱字号的完整文本行。</span><span class="sxs-lookup"><span data-stu-id="d3e96-169">The read-only property that gets the complete line of text that contains the caret.</span></span>

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a><span data-ttu-id="d3e96-170">LineCount</span><span class="sxs-lookup"><span data-stu-id="d3e96-170">LineCount</span></span>

<span data-ttu-id="d3e96-171">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="d3e96-171">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d3e96-172">只读属性，可获取编辑器中的行计数。</span><span class="sxs-lookup"><span data-stu-id="d3e96-172">The read-only property that gets the line count from the editor.</span></span>

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a><span data-ttu-id="d3e96-173">SelectedText</span><span class="sxs-lookup"><span data-stu-id="d3e96-173">SelectedText</span></span>

<span data-ttu-id="d3e96-174">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="d3e96-174">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d3e96-175">只读属性，可获取编辑器中的所选文本。</span><span class="sxs-lookup"><span data-stu-id="d3e96-175">The read-only property that gets the selected text from the editor.</span></span>

<span data-ttu-id="d3e96-176">请参阅本主题稍后介绍的[脚本示例](#scripting-example)。</span><span class="sxs-lookup"><span data-stu-id="d3e96-176">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="text"></a><span data-ttu-id="d3e96-177">文本</span><span class="sxs-lookup"><span data-stu-id="d3e96-177">Text</span></span>

<span data-ttu-id="d3e96-178">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="d3e96-178">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d3e96-179">读写属性，可获取或设置编辑器中的文本。</span><span class="sxs-lookup"><span data-stu-id="d3e96-179">The read/write property that gets or sets the text in the editor.</span></span>

<span data-ttu-id="d3e96-180">请参阅本主题稍后介绍的[脚本示例](#scripting-example)。</span><span class="sxs-lookup"><span data-stu-id="d3e96-180">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

## <a name="scripting-example"></a><span data-ttu-id="d3e96-181">脚本示例</span><span class="sxs-lookup"><span data-stu-id="d3e96-181">Scripting Example</span></span>

```powershell
# This illustrates how you can use the length of a line to
# select the entire line and shows how you can make it lowercase.
# You must run this in the Console pane. It will not run in the Script pane.
# Begin by getting a variable that points to the editor.
$myEditor = $psISE.CurrentFile.Editor
# Clear the text in the current file editor.
$myEditor.Clear()

# Make sure the file has five lines of text.
$myEditor.InsertText("LINE1 `n")
$myEditor.InsertText("LINE2 `n")
$myEditor.InsertText("LINE3 `n")
$myEditor.InsertText("LINE4 `n")
$myEditor.InsertText("LINE5 `n")

# Use the GetLineLength method to get the length of the third line.
$endColumn = $myEditor.GetLineLength(3)
# Select the text in the first three lines.
$myEditor.Select(1, 1, 3, $endColumn + 1)
$selection = $myEditor.SelectedText
# Clear all the text in the editor.
$myEditor.Clear()
# Add the selected text back, but in lower case.
$myEditor.InsertText($selection.ToLower())
```

## <a name="see-also"></a><span data-ttu-id="d3e96-182">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d3e96-182">See Also</span></span>

- [<span data-ttu-id="d3e96-183">ISEFile 对象</span><span class="sxs-lookup"><span data-stu-id="d3e96-183">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="d3e96-184">PowerShellTab 对象</span><span class="sxs-lookup"><span data-stu-id="d3e96-184">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="d3e96-185">Windows PowerShell ISE 脚本对象模型的用途</span><span class="sxs-lookup"><span data-stu-id="d3e96-185">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="d3e96-186">ISE 对象模型层次结构</span><span class="sxs-lookup"><span data-stu-id="d3e96-186">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)