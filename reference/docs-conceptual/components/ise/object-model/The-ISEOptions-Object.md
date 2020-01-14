---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: ISEOptions 对象
ms.openlocfilehash: 9caa78a70cb837c755b2eff9af6ce0aa5dbb7452
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736941"
---
# <a name="the-iseoptions-object"></a>ISEOptions 对象

**ISEOptions** 对象代表 Windows PowerShell ISE 的各种设置。 它是 **Microsoft.PowerShell.Host.ISE.ISEOptions** 类的实例。

**ISEOptions** 对象提供以下方法和属性。

## <a name="methods"></a>方法

### <a name="restoredefaultconsoletokencolors"></a>RestoreDefaultConsoleTokenColors\(\)

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

还原“控制台”窗格中的标记颜色的默认值。

```powershell
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = 'red'
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a>RestoreDefaults\(\)

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

还原“控制台”窗格中的所有选项设置的默认值。 此外，它还重置提供标准复选框以防止再次显示消息的各种警告消息的行为。

```powershell
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = 'orange'
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a>RestoreDefaultTokenColors\(\)

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

还原“脚本”窗格中的标记颜色的默认值。

```powershell
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a>RestoreDefaultXmlTokenColors\(\)

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

还原 Windows PowerShell ISE 中显示的 XML 元素的标记颜色的默认值。 另请参阅 [XmlTokenColors](#xmltokencolors)。

```powershell
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a>属性

### <a name="autosaveminuteinterval"></a>AutoSaveMinuteInterval

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

通过 Windows PowerShell ISE 指定文件自动保存操作之间的分钟数。 默认值为 2 分钟。 该值是一个整数。

```powershell
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a>CommandPaneBackgroundColor

此功能存在于 Windows PowerShell ISE 2.0 中，但已在更高版本的 ISE 中删除或重命名。 对于更高版本，请参阅 [ConsolePaneBackgroundColor](#consolepanebackgroundcolor)。

指定“命令”窗格的背景色。 它是 **System.Windows.Media.Color** 类的实例。

```powershell
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = 'orange'
```

### <a name="commandpaneup"></a>CommandPaneUp

此功能存在于 Windows PowerShell ISE 2.0 中，但已在更高版本的 ISE 中删除或重命名。

指定“命令”窗格是否位于“输出”窗格上方。

```powershell
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true
```

### <a name="consolepanebackgroundcolor"></a>CommandPaneBackgroundColor

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

指定“控制台”窗格的背景色。 它是 **System.Windows.Media.Color** 类的实例。

```powershell
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = 'red'
```

### <a name="consolepaneforegroundcolor"></a>ConsolePaneForegroundColor

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

指定“控制台”窗格中文本的前景色。

```powershell
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = 'yellow'
```

### <a name="consolepanetextbackgroundcolor"></a>ConsolePaneTextBackgroundColor

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

指定“控制台”窗格中文本的背景色。

```powershell
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = 'pink'
```

### <a name="consoletokencolors"></a>ConsoleTokenColors

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

指定 Windows PowerShell ISE“控制台”窗格中 IntelliSense 标记的颜色。 此属性是一个包含标记类型的名称/值对和“控制台”窗格颜色的字典对象。 若要更改“脚本”窗格中 IntelliSense 标记的颜色，请参阅 [TokenColors](#tokencolors)。
要将颜色重置为默认值，请参阅 [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors)。
可以针对以下项设置令牌颜色：Attribute、Command、CommandArgument、CommandParameter、Comment、GroupEnd、GroupStart、Keyword、LineContinuation、LoopLabel、Member、NewLine、Number、Operator、Position、StatementSeparator、String、Type、Unknown、Variable。

```powershell
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = 'green'
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = 'magenta'
```

### <a name="debugbackgroundcolor"></a>DebugBackgroundColor

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

指定“控制台”窗格中显示的调试文本的背景色。 它是 **System.Windows.Media.Color** 类的实例。

```powershell
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor = '#0000FF'
```

### <a name="debugforegroundcolor"></a>DebugForegroundColor

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

指定“控制台”窗格中显示的调试文本的前景色。 它是 **System.Windows.Media.Color** 类的实例。

```powershell
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor = 'yellow'
```

### <a name="defaultoptions"></a>DefaultOptions

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

指定使用重置方法时要使用的默认值的属性集合。

```powershell
# Displays the name of the default options. This example is from ISE 4.0.
$psISE.Options.DefaultOptions
```

```Output
SelectedScriptPaneState                   : Top
ShowDefaultSnippets                       : True
ShowToolBar                               : True
ShowOutlining                             : True
ShowLineNumbers                           : True
TokenColors                               : {[Attribute, #FF00BFFF], [Command, #FF0000FF], [CommandArgument, #FF8A2BE2], [CommandParameter, #FF000080]...}
ConsoleTokenColors                        : {[Attribute, #FFB0C4DE], [Command, #FFE0FFFF], [CommandArgument, #FFEE82EE], [CommandParameter, #FFFFE4B5]...}
XmlTokenColors                            : {[Comment, #FF006400], [CommentDelimiter, #FF008000], [ElementName, #FF8B0000], [MarkupExtension, #FFFF8C00]...}
DefaultOptions                            : Microsoft.PowerShell.Host.ISE.ISEOptions
FontSize                                  : 9
Zoom                                      : 100
FontName                                  : Lucida Console
ErrorForegroundColor                      : #FFFF0000
ErrorBackgroundColor                      : #00FFFFFF
WarningForegroundColor                    : #FFFF8C00
WarningBackgroundColor                    : #00FFFFFF
VerboseForegroundColor                    : #FF00FFFF
VerboseBackgroundColor                    : #00FFFFFF
DebugForegroundColor                      : #FF00FFFF
DebugBackgroundColor                      : #00FFFFFF
ConsolePaneBackgroundColor                : #FF012456
ConsolePaneTextBackgroundColor            : #FF012456
ConsolePaneForegroundColor                : #FFF5F5F5
ScriptPaneBackgroundColor                 : #FFFFFFFF
ScriptPaneForegroundColor                 : #FF000000
ShowWarningForDuplicateFiles              : True
ShowWarningBeforeSavingOnRun              : True
UseLocalHelp                              : True
AutoSaveMinuteInterval                    : 2
MruCount                                  : 10
ShowIntellisenseInConsolePane             : True
ShowIntellisenseInScriptPane              : True
UseEnterToSelectInConsolePaneIntellisense : True
UseEnterToSelectInScriptPaneIntellisense  : True
IntellisenseTimeoutInSeconds              : 3
```

### <a name="errorbackgroundcolor"></a>ErrorBackgroundColor

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

指定“控制台”窗格中显示的错误文本的背景色。 它是 **System.Windows.Media.Color** 类的实例。

```powershell
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor = 'black'
```

### <a name="errorforegroundcolor"></a>ErrorForegroundColor

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

指定“控制台”窗格中显示的错误文本的前景色。 它是 **System.Windows.Media.Color** 类的实例。

```powershell
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor = 'green'
```

### <a name="fontname"></a>FontName

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

指定“脚本”窗格和“控制台”窗格中当前使用的字体名称。

```powershell
# Changes the font used in both panes.
$psISE.Options.FontName = 'Courier New'
```

### <a name="fontsize"></a>FontSize

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

以整数形式指定字体大小。 在“脚本”窗格、“命令”窗格以及“输出”窗格中使用。 值的有效范围是 8 至 32。

```powershell
# Changes the font size in all panes.
$psISE.Options.FontSize = 20
```

### <a name="intellisensetimeoutinseconds"></a>IntellisenseTimeoutInSeconds

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

指定 IntelliSense 用来尝试解决当前所键入文本的秒数。
该秒数之后，IntelliSense 将会超时，并使你能够继续键入。 默认值是 3 秒。 该值是一个整数。

```powershell
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a>MruCount

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

指定 Windows PowerShell ISE 跟踪并在 **“文件打开”** 菜单底部显示的最近打开的文件数。 默认值为 10。 该值是一个整数。

```powershell
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a>OutputPaneBackgroundColor

此功能存在于 Windows PowerShell ISE 2.0 中，但已在更高版本的 ISE 中删除或重命名。 对于更高版本，请参阅 [ConsolePaneBackgroundColor](#consolepanebackgroundcolor)。

读/写属性，可获取或设置“输出”窗格本身的背景色。 它是 **System.Windows.Media.Color** 类的实例。

```powershell
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = 'gold'
```

### <a name="outputpanetextforegroundcolor"></a>OutputPaneTextForegroundColor

此功能存在于 Windows PowerShell ISE 2.0 中，但已在更高版本的 ISE 中删除或重命名。 对于更高版本，请参阅 [ConsolePaneForegroundColor](#consolepaneforegroundcolor)。

读/写属性，可更改 Windows PowerShell ISE 2.0 中“输出”窗格中的文本前景色。

```powershell
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = 'blue'
```

### <a name="outputpanetextbackgroundcolor"></a>OutputPaneTextBackgroundColor

此功能存在于 Windows PowerShell ISE 2.0 中，但已在更高版本的 ISE 中删除或重命名。 对于更高版本，请参阅 [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor)。

读/写属性，可更改“输出”窗格中的文本背景色。

```powershell
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = 'pink'
```

### <a name="scriptpanebackgroundcolor"></a>ScriptPaneBackgroundColor

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

读/写属性，可获取或设置文件的背景色。 它是 **System.Windows.Media.Color** 类的实例。

```powershell
# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'
```

### <a name="scriptpaneforegroundcolor"></a>ScriptPaneForegroundColor

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

读/写属性，可获取或设置“脚本”窗格中非脚本文件的前景色。
要设置脚本文件的前景色，请使用 [TokenColors](#tokencolors)。

```powershell
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = 'green'
```

### <a name="selectedscriptpanestate"></a>SelectedScriptPaneState

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

读/写属性，可获取或设置“脚本”窗格在显示屏上的位置。 字符串可以是“Maximized”、“Top”或“Right”。

```powershell
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = 'Top'
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = 'Right'
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = 'Maximized'
```

### <a name="showdefaultsnippets"></a>ShowDefaultSnippets

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

指定代码段的 <kbd>CTRL</kbd>+<kbd>J</kbd> 列表是否包括Windows PowerShell 中包含的初学者套件。 当设置为 `$false` 时，只有用户定义的代码段显示在 <kbd>CTRL</kbd>+<kbd>J</kbd> 列表中。
默认值是 `$true`。

```powershell
# Hide the default snippets from the CTRL+J list.
$psISE.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a>ShowIntellisenseInConsolePane

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

指定 IntelliSense 是否在“控制台”窗格中提供语法、参数和值建议。
默认值是 `$true`。

```powershell
# Turn off IntelliSense in the console pane.
$psISE.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a>ShowIntellisenseInScriptPane

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

指定 IntelliSense 是否在“脚本”窗格中提供语法、参数和值建议。
默认值是 `$true`。

```powershell
# Turn off IntelliSense in the Script pane.
$psISE.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a>ShowLineNumbers

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

指定“脚本”窗格是否在左边空白处显示行号。 默认值是 `$true`。

```powershell
# Turn off line numbers in the Script pane.
$psISE.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a>ShowOutlining

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

指定“脚本”窗格中是否在左边空白处代码段的旁边显示可展开和折叠的括号。 如果显示，你可以单击文本块旁边的减号 `-` 图标将其折叠起来，或单击加号 `+` 图标展开文本块。 默认值是 `$true`。

```powershell
# Turn off outlining in the Script pane.
$psISE.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a>ShowToolBar

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

指定 ISE 工具栏是否显示在 Windows PowerShell ISE 窗口的顶部。 默认值是 `$true`。

```powershell
# Show the toolbar.
$psISE.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a>ShowWarningBeforeSavingOnRun

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

指定在运行脚本之前自动保存该脚本是否显示警告消息。
默认值是 `$true`。

```powershell
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun = $true
```

### <a name="showwarningforduplicatefiles"></a>ShowWarningForDuplicateFiles

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

指定在不同 PowerShell 选项卡中打开同一个文件时是否显示警告消息。 如果设置为“`$true`”，则在多个选项卡中打开同一个文件会显示以下消息："已在其他 Windows PowerShell 选项卡中打开此文件的副本。对此文件所做的更改将影响所有打开的副本。” 默认值是 `$true`。

```powershell
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true
```

### <a name="tokencolors"></a>TokenColors

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

指定 Windows PowerShell ISE“脚本”窗格中 IntelliSense 标记的颜色。 此属性是一个包含标记类型的名称/值对和“脚本”窗格颜色的字典对象。 若要更改“脚本”窗格中 IntelliSense 标记的颜色，请参阅 [ConsoleTokenColors](#consoletokencolors)。
要将颜色重置为默认值，请参阅 [RestoreDefaultTokenColors](#restoredefaulttokencolors)。
可以针对以下项设置令牌颜色：Attribute、Command、CommandArgument、CommandParameter、Comment、GroupEnd、GroupStart、Keyword、LineContinuation、LoopLabel、Member、NewLine、Number、Operator、Position、StatementSeparator、String、Type、Unknown、Variable。

```powershell
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"
```

### <a name="useentertoselectinconsolepaneintellisense"></a>UseEnterToSelectInConsolePaneIntellisense

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

指定是否可以使用 Enter 键选择 IntelliSense 在“控制台”窗格中提供的选项。 默认值是 `$true`。

```powershell
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $false
```

### <a name="useentertoselectinscriptpaneintellisense"></a>UseEnterToSelectInScriptPaneIntellisense

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

指定是否可以使用 Enter 键选择 IntelliSense 在“脚本”窗格中提供的选项。 默认值是 `$true`。

```powershell
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $true
```

### <a name="uselocalhelp"></a>UseLocalHelp

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

指定将光标置于关键字中并按 <kbd>F1</kbd> 时是显示本地安装的帮助还是联机 TechNet 库帮助。 如果设置为 `$true`，那么弹出窗口会显示本地安装的帮助中的内容。 可以通过运行 `Update-Help` 命令安装帮助文件。 如果设置为 `$false`，则你的浏览器会在 TechNet 库中打开一个页面。

```powershell
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp = $false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp = $true
```

### <a name="verbosebackgroundcolor"></a>VerboseBackgroundColor

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

指定“控制台”窗格中显示的详细文本的背景色。 它是 **System.Windows.Media.Color** 对象。

```powershell
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a>VerboseForegroundColor

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

指定“控制台”窗格中显示的详细文本的前景色。 它是 **System.Windows.Media.Color** 对象。

```powershell
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor = 'yellow'
```

### <a name="warningbackgroundcolor"></a>WarningBackgroundColor

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

指定“控制台”窗格中显示的警告文本的背景色。 它是 **System.Windows.Media.Color** 对象。

```powershell
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor = '#0000FF'
```

### <a name="warningforegroundcolor"></a>WarningForegroundColor

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

指定“输出”窗格中显示的警告文本的前景色。 它是 **System.Windows.Media.Color** 对象。

```powershell
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor = 'yellow'
```

### <a name="xmltokencolors"></a>XmlTokenColors

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

指定包含标记类型的名称/值对以及 Windows PowerShell ISE 中显示的 XML 内容颜色的字典对象。 可以针对以下项设置令牌颜色：Attribute、Command、CommandArgument、CommandParameter、Comment、GroupEnd、GroupStart、Keyword、LineContinuation、LoopLabel、Member、NewLine、Number、Operator、Position、StatementSeparator、String、Type、Unknown、Variable。 另请参阅 [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors)。

```powershell
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = 'green'
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = 'magenta'
```

### <a name="zoom"></a>Zoom

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

在“控制台”和“脚本”窗格中指定文本的相对大小。 默认值为 100。
较小的值会导致 Windows PowerShell ISE 中的文本显示得较小，数字越大会导致文本显示得越大。 该值为一个整数，范围为 20 到 400。

```powershell
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a>另请参阅

- [Windows PowerShell ISE 脚本对象模型的用途](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE 对象模型层次结构](The-ISE-Object-Model-Hierarchy.md)
