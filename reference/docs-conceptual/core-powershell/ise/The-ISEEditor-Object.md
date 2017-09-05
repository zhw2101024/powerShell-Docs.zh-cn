---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISEEditor 对象"
ms.assetid: 0101daf8-4e31-4e4c-ab89-01d95dcb8f46
ms.openlocfilehash: e2ddb0de1089c832f130e1f5c7c8dcb199aca2fa
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2017
---
# <a name="the-iseeditor-object"></a><span data-ttu-id="b087a-103">ISEEditor 对象</span><span class="sxs-lookup"><span data-stu-id="b087a-103">The ISEEditor Object</span></span>
  <span data-ttu-id="b087a-104">**ISEEditor** 对象是 Microsoft.PowerShell.Host.ISE.ISEEditor 类的实例。</span><span class="sxs-lookup"><span data-stu-id="b087a-104">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="b087a-105">控制台窗格是 **ISEEditor** 对象。</span><span class="sxs-lookup"><span data-stu-id="b087a-105">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="b087a-106">每个 [ISEFile](The-ISEFile-Object.md) 对象都有一个关联的 **ISEEditor** 对象。</span><span class="sxs-lookup"><span data-stu-id="b087a-106">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="b087a-107">以下各节列出了 **ISEEditor** 对象的方法和属性。</span><span class="sxs-lookup"><span data-stu-id="b087a-107">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="b087a-108">方法</span><span class="sxs-lookup"><span data-stu-id="b087a-108">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="b087a-109">Clear\(\)</span><span class="sxs-lookup"><span data-stu-id="b087a-109">Clear\(\)</span></span>
  <span data-ttu-id="b087a-110">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="b087a-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b087a-111">清除编辑器中的文本。</span><span class="sxs-lookup"><span data-stu-id="b087a-111">Clears the text in the editor.</span></span>

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="b087a-112">EnsureVisible\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="b087a-112">EnsureVisible\(int lineNumber\)</span></span>
  <span data-ttu-id="b087a-113">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="b087a-113">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b087a-114">滚动编辑器以使对应于指定 **lineNumber** 参数值的行可见。</span><span class="sxs-lookup"><span data-stu-id="b087a-114">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="b087a-115">如果指定的行号超出范围 1，即用于定义有效行号的最后一个行号，则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="b087a-115">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

 <span data-ttu-id="b087a-116">**lineNumber** 要使其可见的行号。</span><span class="sxs-lookup"><span data-stu-id="b087a-116">**lineNumber** The number of the line that is to be made visible.</span></span>

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view. 
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="b087a-117">Focus\(\)</span><span class="sxs-lookup"><span data-stu-id="b087a-117">Focus\(\)</span></span>
  <span data-ttu-id="b087a-118">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="b087a-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b087a-119">将焦点设置到编辑器。</span><span class="sxs-lookup"><span data-stu-id="b087a-119">Sets the focus to the editor.</span></span>

```powershell
# Sets focus to the Console pane. 
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="b087a-120">GetLineLength\(int lineNumber \)</span><span class="sxs-lookup"><span data-stu-id="b087a-120">GetLineLength\(int lineNumber \)</span></span>
  <span data-ttu-id="b087a-121">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="b087a-121">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b087a-122">获取按行号指定的行的长度（整数形式）。</span><span class="sxs-lookup"><span data-stu-id="b087a-122">Gets the line length as an integer for the line that is specified by the line number.</span></span>

 <span data-ttu-id="b087a-123">**lineNumber** 要获取长度的行号。</span><span class="sxs-lookup"><span data-stu-id="b087a-123">**lineNumber** The number of the line of which to get the length.</span></span>

 <span data-ttu-id="b087a-124">**Returns** 所指定行号的行的长度。</span><span class="sxs-lookup"><span data-stu-id="b087a-124">**Returns** The line length for the line at the specified line number.</span></span>

```powershell
# Gets the length of the first line in the text of the Command pane. 
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="b087a-125">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="b087a-125">GoToMatch\(\)</span></span>
  <span data-ttu-id="b087a-126">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="b087a-126">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="b087a-127">如果编辑器对象的 **CanGoToMatch** 属性是 **$true**，当脱字号直接位于左括号、中括号或大括号 - \(、\[、{ - 或直接位于右括号、中括号或大括号 - \)、\]、}。</span><span class="sxs-lookup"><span data-stu-id="b087a-127">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is **$true**, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - \(,\[,{ - or immediately after a closing parenthesis, bracket, or brace - \),\],}.</span></span>  <span data-ttu-id="b087a-128">脱字号位于开始字符之前或结束字符之后。</span><span class="sxs-lookup"><span data-stu-id="b087a-128">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="b087a-129">如果 **CanGoToMatch** 属性是 **$false**，则此方法不执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="b087a-129">If the **CanGoToMatch** property is **$false**, then this method does nothing.</span></span> <span data-ttu-id="b087a-130">请参阅 [CanGoToMatch]()。</span><span class="sxs-lookup"><span data-stu-id="b087a-130">See [CanGoToMatch]().</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace.
```

### <a name="inserttext-text-"></a><span data-ttu-id="b087a-131">InsertText\( text \)</span><span class="sxs-lookup"><span data-stu-id="b087a-131">InsertText\( text \)</span></span>
  <span data-ttu-id="b087a-132">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="b087a-132">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b087a-133">将所选内容替换为文本或在当前脱字号位置插入文本。</span><span class="sxs-lookup"><span data-stu-id="b087a-133">Replaces the selection with text or inserts text at the current caret position.</span></span>

 <span data-ttu-id="b087a-134">**text** - String 要插入的文本。</span><span class="sxs-lookup"><span data-stu-id="b087a-134">**text** - String The text to insert.</span></span>

 <span data-ttu-id="b087a-135">请参阅本主题稍后介绍的[脚本示例]()。</span><span class="sxs-lookup"><span data-stu-id="b087a-135">See the [Scripting Example]() later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="b087a-136">Select\( startLine, startColumn, endLine, endColumn \)</span><span class="sxs-lookup"><span data-stu-id="b087a-136">Select\( startLine, startColumn, endLine, endColumn \)</span></span>
  <span data-ttu-id="b087a-137">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="b087a-137">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b087a-138">从 **startLine**、**startColumn**、**endLine** 和 **endColumn** 参数中选择文本。</span><span class="sxs-lookup"><span data-stu-id="b087a-138">Selects the text from the **startLine**, **startColumn**, **endLine**, and **endColumn** parameters.</span></span>

 <span data-ttu-id="b087a-139">**startLine** - Integer 所选内容的起始行。</span><span class="sxs-lookup"><span data-stu-id="b087a-139">**startLine** - Integer The line where the selection starts.</span></span>

 <span data-ttu-id="b087a-140">**startColumn** - Integer 所选内容的起始行中的列。</span><span class="sxs-lookup"><span data-stu-id="b087a-140">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

 <span data-ttu-id="b087a-141">**endLine** - Integer 所选内容的结束行。</span><span class="sxs-lookup"><span data-stu-id="b087a-141">**endLine** - Integer The line where the selection ends.</span></span>

 <span data-ttu-id="b087a-142">**endColumn** - Integer 所选内容的结束行中的列。</span><span class="sxs-lookup"><span data-stu-id="b087a-142">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

 <span data-ttu-id="b087a-143">请参阅本主题稍后介绍的[脚本示例]()。</span><span class="sxs-lookup"><span data-stu-id="b087a-143">See the  [Scripting Example]() later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="b087a-144">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="b087a-144">SelectCaretLine\(\)</span></span>
  <span data-ttu-id="b087a-145">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="b087a-145">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b087a-146">选择当前包含脱字号的整个文本行。</span><span class="sxs-lookup"><span data-stu-id="b087a-146">Selects the entire line of text that currently contains the caret.</span></span>

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1) 
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="b087a-147">SetCaretPosition\( lineNumber, columnNumber \)</span><span class="sxs-lookup"><span data-stu-id="b087a-147">SetCaretPosition\( lineNumber, columnNumber \)</span></span>
  <span data-ttu-id="b087a-148">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="b087a-148">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b087a-149">在行号和列号处设置脱字号位置。</span><span class="sxs-lookup"><span data-stu-id="b087a-149">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="b087a-150">如果脱字号行号或脱字号列号不在其各自的有效范围内，会引发异常。</span><span class="sxs-lookup"><span data-stu-id="b087a-150">It throws an exception if either the caret line number  or the caret column number  are out of their respective valid ranges.</span></span>

 <span data-ttu-id="b087a-151">**lineNumber** - Integer 脱字号行号。</span><span class="sxs-lookup"><span data-stu-id="b087a-151">**lineNumber** - Integer The caret line number.</span></span>

 <span data-ttu-id="b087a-152">**columnNumber** - Integer 脱字号列号。</span><span class="sxs-lookup"><span data-stu-id="b087a-152">**columnNumber** - Integer The caret column number.</span></span>

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="b087a-153">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="b087a-153">ToggleOutliningExpansion\(\)</span></span>
  <span data-ttu-id="b087a-154">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="b087a-154">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="b087a-155">使所有大纲部分展开或折叠。</span><span class="sxs-lookup"><span data-stu-id="b087a-155">Causes all the outline sections to expand or collapse.</span></span>

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="b087a-156">“属性”</span><span class="sxs-lookup"><span data-stu-id="b087a-156">Properties</span></span>

###  <span data-ttu-id="b087a-157"><a name="CanGoToMatch"></a> CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="b087a-157"><a name="CanGoToMatch"></a> CanGoToMatch</span></span>
  <span data-ttu-id="b087a-158">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="b087a-158">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="b087a-159">只读布尔值属性，可指示将脱字号插入小括号、中括号还是大括号（即 \(\)、\[\]、{}）旁边。</span><span class="sxs-lookup"><span data-stu-id="b087a-159">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - \(\), \[\], {}.</span></span> <span data-ttu-id="b087a-160">如果脱字号直接位于开始字符之前或直接位于结束字符之后，则此属性值是 **$true**。</span><span class="sxs-lookup"><span data-stu-id="b087a-160">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is **$true**.</span></span> <span data-ttu-id="b087a-161">否则，是**$false**。</span><span class="sxs-lookup"><span data-stu-id="b087a-161">Otherwise, it is **$false**.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

###  <span data-ttu-id="b087a-162"><a name="CaretColumn"></a> CaretColumn</span><span class="sxs-lookup"><span data-stu-id="b087a-162"><a name="CaretColumn"></a> CaretColumn</span></span>
  <span data-ttu-id="b087a-163">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="b087a-163">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b087a-164">只读属性，可获取对应于脱字号位置的列号。</span><span class="sxs-lookup"><span data-stu-id="b087a-164">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

###  <span data-ttu-id="b087a-165"><a name="CaretLine"></a> CaretLine</span><span class="sxs-lookup"><span data-stu-id="b087a-165"><a name="CaretLine"></a> CaretLine</span></span>
  <span data-ttu-id="b087a-166">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="b087a-166">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b087a-167">只读属性，可获取包含脱字号的行号。</span><span class="sxs-lookup"><span data-stu-id="b087a-167">The read-only property that gets the number of the line that contains the caret.</span></span>

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

###  <span data-ttu-id="b087a-168"><a name="CaretLineText"></a> CaretLineText</span><span class="sxs-lookup"><span data-stu-id="b087a-168"><a name="CaretLineText"></a> CaretLineText</span></span>
  <span data-ttu-id="b087a-169">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="b087a-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b087a-170">只读属性，可获取包含脱字号的完整文本行。</span><span class="sxs-lookup"><span data-stu-id="b087a-170">The read-only property that gets the complete line of text that contains the caret.</span></span>

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

###  <span data-ttu-id="b087a-171"><a name="LineCount"></a> LineCount</span><span class="sxs-lookup"><span data-stu-id="b087a-171"><a name="LineCount"></a> LineCount</span></span>
  <span data-ttu-id="b087a-172">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="b087a-172">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b087a-173">只读属性，可获取编辑器中的行计数。</span><span class="sxs-lookup"><span data-stu-id="b087a-173">The read-only property that gets the line count from the editor.</span></span>

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

###  <span data-ttu-id="b087a-174"><a name="SelectedText"></a> SelectedText</span><span class="sxs-lookup"><span data-stu-id="b087a-174"><a name="SelectedText"></a> SelectedText</span></span>
  <span data-ttu-id="b087a-175">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="b087a-175">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b087a-176">只读属性，可获取编辑器中的所选文本。</span><span class="sxs-lookup"><span data-stu-id="b087a-176">The read-only property that gets the selected text from the editor.</span></span>

 <span data-ttu-id="b087a-177">请参阅本主题稍后介绍的[脚本示例]()。</span><span class="sxs-lookup"><span data-stu-id="b087a-177">See the  [Scripting Example]() later in this topic.</span></span>

###  <span data-ttu-id="b087a-178"><a name="Text"></a>文本</span><span class="sxs-lookup"><span data-stu-id="b087a-178"><a name="Text"></a> Text</span></span>
  <span data-ttu-id="b087a-179">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="b087a-179">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b087a-180">读写属性，可获取或设置编辑器中的文本。</span><span class="sxs-lookup"><span data-stu-id="b087a-180">The read/write property that gets or sets the text in the editor.</span></span>

 <span data-ttu-id="b087a-181">请参阅本主题稍后介绍的[脚本示例]()。</span><span class="sxs-lookup"><span data-stu-id="b087a-181">See the [Scripting Example]() later in this topic.</span></span>

##  <span data-ttu-id="b087a-182"><a name="example"></a>脚本示例</span><span class="sxs-lookup"><span data-stu-id="b087a-182"><a name="example"></a> Scripting Example</span></span>

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
$endColumn= $myEditor.GetLineLength(3)
# Select the text in the first three lines.
$myEditor.Select(1,1,3,$endColumn + 1)
$selection = $myEditor.SelectedText
# Clear all the text in the editor.
$myEditor.Clear()
# Add the selected text back, but in lower case.
$myEditor.InsertText($selection.ToLower())
```

## <a name="see-also"></a><span data-ttu-id="b087a-183">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b087a-183">See Also</span></span>
- [<span data-ttu-id="b087a-184">ISEFile 对象</span><span class="sxs-lookup"><span data-stu-id="b087a-184">The ISEFile Object</span></span>](The-ISEFile-Object.md) 
- [<span data-ttu-id="b087a-185">PowerShellTab 对象</span><span class="sxs-lookup"><span data-stu-id="b087a-185">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md) 
- [<span data-ttu-id="b087a-186">Windows PowerShell ISE 脚本对象模型</span><span class="sxs-lookup"><span data-stu-id="b087a-186">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="b087a-187">Windows PowerShell ISE 对象模型参考</span><span class="sxs-lookup"><span data-stu-id="b087a-187">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="b087a-188">ISE 对象模型层次结构</span><span class="sxs-lookup"><span data-stu-id="b087a-188">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
