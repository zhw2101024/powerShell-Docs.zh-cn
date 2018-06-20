---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: ISEEditor 对象
ms.openlocfilehash: 2d4c3d941035384c591ca57e809c0e3a9b852f5c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952607"
---
# <a name="the-iseeditor-object"></a>ISEEditor 对象

**ISEEditor** 对象是 Microsoft.PowerShell.Host.ISE.ISEEditor 类的实例。 控制台窗格是 **ISEEditor** 对象。 每个 [ISEFile](The-ISEFile-Object.md) 对象都有一个关联的 **ISEEditor** 对象。 以下各节列出了 **ISEEditor** 对象的方法和属性。

## <a name="methods"></a>方法

### <a name="clear"></a>Clear\(\)

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

清除编辑器中的文本。

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a>EnsureVisible\(int lineNumber\)

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

滚动编辑器以使对应于指定 **lineNumber** 参数值的行可见。 如果指定的行号超出范围 1，即用于定义有效行号的最后一个行号，则会引发异常。

**lineNumber** 要使其可见的行号。

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a>Focus\(\)

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

将焦点设置到编辑器。

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a>GetLineLength\(int lineNumber \)

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

获取按行号指定的行的长度（整数形式）。

**lineNumber** 要获取长度的行号。

**Returns** 所指定行号的行的长度。

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a>GoToMatch\(\)

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

如果编辑器对象的 **CanGoToMatch** 属性是 **$true**，当脱字号直接位于左括号、中括号或大括号 - \(、\[、{ - 或直接位于右括号、中括号或大括号 - \)、\]、}。  脱字号位于开始字符之前或结束字符之后。 如果 **CanGoToMatch** 属性是 **$false**，则此方法不执行任何操作。

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a>InsertText\( text \)

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

将所选内容替换为文本或在当前脱字号位置插入文本。

**text** - String 要插入的文本。

请参阅本主题稍后介绍的[脚本示例](#scripting-example)。

### <a name="select-startline-startcolumn-endline-endcolumn-"></a>Select\( startLine, startColumn, endLine, endColumn \)

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

从 **startLine**、**startColumn**、**endLine** 和 **endColumn** 参数中选择文本。

**startLine** - Integer 所选内容的起始行。

**startColumn** - Integer 所选内容的起始行中的列。

**endLine** - Integer 所选内容的结束行。

**endColumn** - Integer 所选内容的结束行中的列。

请参阅本主题稍后介绍的[脚本示例](#scripting-example)。

### <a name="selectcaretline"></a>SelectCaretLine\(\)

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

选择当前包含脱字号的整个文本行。

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a>SetCaretPosition\( lineNumber, columnNumber \)

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

在行号和列号处设置脱字号位置。 如果脱字号行号或脱字号列号不在其各自的有效范围内，会引发异常。

**lineNumber** - Integer 脱字号行号。

**columnNumber** - Integer 脱字号列号。

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a>ToggleOutliningExpansion\(\)

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

使所有大纲部分展开或折叠。

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a>“属性”

### <a name="cangotomatch"></a>CanGoToMatch

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

只读布尔值属性，可指示将脱字号插入小括号、中括号还是大括号（即 \(\)、\[\]、{}）旁边。 如果脱字号直接位于开始字符之前或直接位于结束字符之后，则此属性值是 **$true**。 否则，是 **$false**。

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a>CaretColumn

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

只读属性，可获取对应于脱字号位置的列号。

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a>CaretLine

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

只读属性，可获取包含脱字号的行号。

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a>CaretLineText

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

只读属性，可获取包含脱字号的完整文本行。

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a>LineCount

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

只读属性，可获取编辑器中的行计数。

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a>SelectedText

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

只读属性，可获取编辑器中的所选文本。

请参阅本主题稍后介绍的[脚本示例](#scripting-example)。

### <a name="text"></a>文本

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

读写属性，可获取或设置编辑器中的文本。

请参阅本主题稍后介绍的[脚本示例](#scripting-example)。

## <a name="scripting-example"></a>脚本示例

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

## <a name="see-also"></a>另请参阅

- [ISEFile 对象](The-ISEFile-Object.md)
- [PowerShellTab 对象](The-PowerShellTab-Object.md)
- [Windows PowerShell ISE 脚本对象模型的用途](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE 对象模型层次结构](The-ISE-Object-Model-Hierarchy.md)