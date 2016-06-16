---
title:  ISEOptions 对象
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  75e2a76f-f3d1-490b-ad5d-e3829946aabb
---

# ISEOptions 对象
  **ISEOptions** 对象代表 Windows PowerShell ISE 的各种设置。 它是 **Microsoft.PowerShell.Host.ISE.ISEOptions** 类的实例。

 **ISEOptions** 对象提供以下方法和属性。

 **方法**

-   [RestoreDefaultConsoleTokenColors()](#rdctc)

-   [RestoreDefaults()](#rd)

-   [RestoreDefaultTokenColors()](#rdtc)

-   [RestoreDefaultXmlTokenColors()](#rdxtc)

 **“属性”**

-   [AutoSaveMinuteInterval](#asmi)

-   [CommandPaneBackgroundColor](#cpbc)

-   [CommandPaneUp](#cpu)

-   [CommandPaneBackgroundColor](#conpbc)

-   [ConsolePaneForegroundColor](#conpfc)

-   [ConsolePaneTextBackgroundColor](#conptbc)

-   [ConsoleTokenColors](#contc)

-   [DebugBackgroundColor](#dbc)

-   [DebugForegroundColor](#dfc)

-   [DefaultOptions](#do)

-   [ErrorBackgroundColor](#ebc)

-   [ErrorForegroundColor](#efc)

-   [FontName](#fn)

-   [FontSize](#fs)

-   [IntellisenseTimeoutInSeconds](#itis)

-   [MruCount](#mc)

-   [OutputPaneBackgroundColor](#opbc)

-   [OutputPaneTextForegroundColor](#optfc)

-   [OutputPaneTextBackgroundColor](#optbc)

-   [ScriptPaneBackgroundColor](#spbc)

-   [ScriptPaneForegroundColor](#spfc)

-   [SelectedScriptPaneState](#ssps)

-   [ShowDefaultSnippets](#sds)

-   [ShowIntellisenseInConsolePane](#siicp)

-   [ShowIntellisenseInScriptPane](#siisp)

-   [ShowLineNumbers](#sln)

-   [ShowOutlining](#so)

-   [ShowToolBar](#stb)

-   [ShowWarningBeforeSavingOnRun](#swbsor)

-   [ShowWarningForDuplicateFiles](#swfdf)

-   [TokenColors](#tc)

-   [UseEnterToSelectInConsolePaneIntellisense](#uetsicpi)

-   [UseEnterToSelectInScriptPaneIntellisense](#uetsispi)

-   [UseLocalHelp](#ulh)

-   [VerboseBackgroundColor](#vbc)

-   [VerboseForegroundColor](#vfc)

-   [WarningBackgroundColor](#wbc)

-   [WarningForegroundColor](#wfc)

-   [XmlTokenColors](#xtc)

-   [缩放](#z)

## 方法

###  <a name="rdctc"></a> RestoreDefaultConsoleTokenColors\(\)
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

 还原“控制台”窗格中的标记颜色的默认值。

```
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = "red"
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

###  <a name="rd"></a> RestoreDefaults\(\)
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。

 还原“控制台”窗格中的所有选项设置的默认值。 此外，它还重置提供标准复选框以防止再次显示消息的各种警告消息的行为。

```
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = "orange"
$psISE.Options.RestoreDefaults()
```

###  <a name="rdtc"></a> RestoreDefaultTokenColors\(\)
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。

 还原“脚本”窗格中的标记颜色的默认值。

```
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultTokenColors()
```

###  <a name="rdxtc"></a> RestoreDefaultXmlTokenColors\(\)
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

 还原 Windows PowerShell ISE 中显示的 XML 元素的标记颜色的默认值。 另请参阅 [XmlTokenColors](#xtc)。

```
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## “属性”

###  <a name="asmi"></a> AutoSaveMinuteInterval
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

 通过 Windows PowerShell ISE 指定文件自动保存操作之间的分钟数。 默认值为 2 分钟。 该值是一个整数。

```
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

###  <a name="cpbc"></a> CommandPaneBackgroundColor
  此功能存在于 Windows PowerShell ISE 2.0 中，但已在更高版本的 ISE 中删除或重命名。  对于更高版本，请参阅 [ConsolePaneBackgroundColor](#conpbc)。

 指定“命令”窗格的背景色。 它是 **System.Windows.Media.Color** 类的实例。

```
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = "orange"
```

###  <a name="cpu"></a> CommandPaneUp
  此功能存在于 Windows PowerShell ISE 2.0 中，但已在更高版本的 ISE 中删除或重命名。

 指定“命令”窗格是否位于“输出”窗格上方。

```
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true

```

###  <a name="conpbc"></a> CommandPaneBackgroundColor
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

 指定“控制台”窗格的背景色。 它是 **System.Windows.Media.Color** 类的实例。

```
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = "red"
```

###  <a name="conpfc"></a> ConsolePaneForegroundColor
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

 指定“控制台”窗格中文本的前景色。

```
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = "yellow"

```

###  <a name="conptbc"></a> ConsolePaneTextBackgroundColor
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

 指定“控制台”窗格中文本的背景色。

```
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = "pink"
```

###  <a name="contc"></a> ConsoleTokenColors
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

 指定 Windows PowerShell ISE“控制台”窗格中 IntelliSense 标记的颜色。 此属性是一个包含标记类型的名称值对和“控制台”窗格颜色的字典对象。 若要更改“脚本”窗格中 IntelliSense 标记的颜色，请参阅 [TokenColors](#tc)。 若要将颜色重置为默认值，请参阅 [RestoreDefaultConsoleTokenColors()](#rdctc)。 可以针对以下项设置标记颜色：Attribute、Command、CommandArgument、CommandParameter、Comment、GroupEnd、GroupStart、Keyword、LineContinuation、LoopLabel、Member、NewLine、Number、Operator、Position、StatementSeparator、String、Type、Unknown、Variable。

```
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = "magenta"

```

###  <a name="dbc"></a> DebugBackgroundColor
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。

 指定“控制台”窗格中显示的调试文本的背景色。 它是 **System.Windows.Media.Color** 类的实例。

```
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor ='#0000FF'
```

###  <a name="dfc"></a> DebugForegroundColor
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。

 指定“控制台”窗格中显示的调试文本的前景色。 它是 **System.Windows.Media.Color** 类的实例。

```
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor ="yellow"
```

###  <a name="do"></a> DefaultOptions
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。

 指定使用重置方法时要使用的默认值的属性集合。

```
# Displays the name of the default options. This example is from ISE 4.0.
$psISE.Options.DefaultOptions

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

###  <a name="ebc"></a> ErrorBackgroundColor
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。

 指定“控制台”窗格中显示的错误文本的背景色。 它是 **System.Windows.Media.Color** 类的实例。

```
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor="black"
```

###  <a name="efc"></a> ErrorForegroundColor
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。

 指定“控制台”窗格中显示的错误文本的前景色。 它是 **System.Windows.Media.Color** 类的实例。

```
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor ="green"
```

###  <a name="fn"></a> FontName
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。

 指定“脚本”窗格和“控制台”窗格中当前使用的字体名称。

```
# Changes the font used in both panes.
$psISE.Options.FontName = "courier new"
```

###  <a name="fs"></a> FontSize
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。

 以整数形式指定字体大小。 在“脚本”窗格、“命令”窗格以及“输出”窗格中使用。 值的有效范围是 8 至 32。

```
# Changes the font size in all panes.
$psISE.Options.FontSize = 20

```

###  <a name="itis"></a> IntellisenseTimeoutInSeconds
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

 指定 IntelliSense 用来尝试解决当前所键入文本的秒数。 该秒数之后，IntelliSense 将会超时，并使你能够继续键入。 默认值是 3 秒。 该值是一个整数。

```
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

###  <a name="mc"></a> MruCount
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

 指定 Windows PowerShell ISE 跟踪并在**“文件打开”**菜单底部显示的最近打开的文件数。 默认值为 10。 该值是一个整数。

```
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

###  <a name="opbc"></a> OutputPaneBackgroundColor
  此功能存在于 Windows PowerShell ISE 2.0 中，但已在更高版本的 ISE 中删除或重命名。  对于更高版本，请参阅 [ConsolePaneBackgroundColor](#conpbc)。

 读写属性，可获取或设置“输出”窗格本身的背景色。 它是 **System.Windows.Media.Color** 类的实例。

```
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = "gold"

```

###  <a name="optfc"></a> OutputPaneTextForegroundColor
  此功能存在于 Windows PowerShell ISE 2.0 中，但已在更高版本的 ISE 中删除或重命名。  对于更高版本，请参阅 [ConsolePaneForegroundColor](#conpfc)。

 读写属性，可更改 Windows PowerShell ISE 2.0 中“输出”窗格中的文本前景色。

```
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = "blue"

```

###  <a name="optbc"></a> OutputPaneTextBackgroundColor
  此功能存在于 Windows PowerShell ISE 2.0 中，但已在更高版本的 ISE 中删除或重命名。  对于更高版本，请参阅 [ConsolePaneTextBackgroundColor](#conptbc)。

 读写属性，可更改“输出”窗格中的文本背景色。

```
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = "pink"
```

###  <a name="spbc"></a> ScriptPaneBackgroundColor
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。

 读写属性，可获取或设置文件的背景色。 它是 **System.Windows.Media.Color** 类的实例。

```

# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = ”yellow”

```

###  <a name="spfc"></a> ScriptPaneForegroundColor
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。

 读写属性，可获取或设置“脚本”窗格中非脚本文件的前景色。
若要设置脚本文件的前景色，请使用 [TokenColors](The-ISEOptions-Object.md#tc) 属性。

```
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = "green"

```

###  <a name="ssps"></a> SelectedScriptPaneState
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。

 读写属性，可获取或设置“脚本”窗格在显示屏上的位置。 字符串可以是“最大化”、“顶部”或“右侧”。

```
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = "Top"
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = "Right"
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = "Maximized"

```

###  <a name="sds"></a> ShowDefaultSnippets
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

 指定代码段的 **CTRL + J** 列表是否包括Windows PowerShell 中包含的初学者套件。 当设置为 **$false** 时，只有用户定义的代码段显示在 **CTRL + J** 列表中。 默认值为 **$true**。

```
# Hide the default snippets from the CTRL+J list.
$psISe.Options.ShowDefaultSnippets = $false
```

###  <a name="siicp"></a> ShowIntellisenseInConsolePane
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

 指定 IntelliSense 是否在“控制台”窗格中提供语法、参数和值建议。 默认值为 **$true**。

```
# Turn off IntelliSense in the console pane.
$psISe.Options.ShowIntellisenseInConsolePane = $false
```

###  <a name="siisp"></a> ShowIntellisenseInScriptPane
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

 指定 IntelliSense 是否在“脚本”窗格中提供语法、参数和值建议。 默认值为 **$true**。

```
# Turn off IntelliSense in the Script pane.
$psISe.Options.ShowIntellisenseInScriptPane = $false
```

###  <a name="sln"></a> ShowLineNumbers
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

 指定“脚本”窗格是否在左边空白处显示行号。 默认值为 **$true**。

```
# Turn off line numbers in the Script pane.
$psISe.Options.ShowLineNumbers = $false
```

###  <a name="so"></a> ShowOutlining
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

 指定“脚本”窗格中是否在左边空白处代码段的旁边显示可展开和折叠的括号。 如果显示，你可以单击文本块旁边的减号 \(\-\) 图标将其折叠起来，或单击加号 \(\+\) 图标展开文本块。 默认值为 **$true**。

```
# Turn off outlining in the Script pane.
$psISe.Options.ShowOutlining = $false
```

###  <a name="stb"></a> ShowToolBar
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。

 指定 ISE 工具栏是否显示在 Windows PowerShell ISE 窗口的顶部。 默认值为 **$true**。

```
# Show the toolbar.
$psISe.Options.ShowToolBar = $true
```

###  <a name="swbsor"></a> ShowWarningBeforeSavingOnRun
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。

 指定在运行脚本之前自动保存该脚本是否显示警告消息。 默认值为 **$true**。

```
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun=$true

```

###  <a name="swfdf"></a> ShowWarningForDuplicateFiles
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。

 指定在不同 PowerShell 选项卡中打开同一个文件时是否显示警告消息。 如果设置为 **$true**，在多个选项卡打开同一个文件将显示此消息：“已在另一个 Windows PowerShell 选项卡中打开此文件的副本。 对此文件所做的更改将影响所有打开的副本。” 默认值为 **$true**。

```
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true

```

###  <a name="tc"></a> TokenColors
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。

 指定 Windows PowerShell ISE“脚本”窗格中 IntelliSense 标记的颜色。 此属性是一个包含标记类型的名称值对和“脚本”窗格颜色的字典对象。 若要更改“脚本”窗格中 IntelliSense 标记的颜色，请参阅 [ConsoleTokenColors](#contc)。 若要将颜色重置为默认值，请参阅 [RestoreDefaultTokenColors()](#rdtc)。 可以针对以下项设置标记颜色：Attribute、Command、CommandArgument、CommandParameter、Comment、GroupEnd、GroupStart、Keyword、LineContinuation、LoopLabel、Member、NewLine、Number、Operator、Position、StatementSeparator、String、Type、Unknown、Variable。

```
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"

```

###  <a name="uetsicpi"></a> UseEnterToSelectInConsolePaneIntellisense
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

 指定是否可以使用 Enter 键选择 IntelliSense 在“控制台”窗格中提供的选项。 默认值为 **$true**。

```
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$false

```

###  <a name="uetsispi"></a> UseEnterToSelectInScriptPaneIntellisense
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

 指定是否可以使用 Enter 键选择 IntelliSense 在“脚本”窗格中提供的选项。 默认值为 **$true**。

```
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$true

```

###  <a name="ulh"></a> UseLocalHelp
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

 指定将光标置于关键字中并按 F1 时是显示本地安装的帮助还是联机 TechNet 库帮助。 如果设置为 **$true**，那么弹出窗口会显示本地安装的帮助中的内容。 可以通过运行 `Update-Help` 命令安装帮助文件。 如果设置为 **$false**，则你的浏览器会在 TechNet 库中打开一个页面。

```
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp=$false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp=$true

```

###  <a name="vbc"></a> VerboseBackgroundColor
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。

 指定“控制台”窗格中显示的详细文本的背景色。 它是 **System.Windows.Media.Color** 对象。

```
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

###  <a name="vfc"></a> VerboseForegroundColor
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。

 指定“控制台”窗格中显示的详细文本的前景色。 它是 **System.Windows.Media.Color** 对象。

```
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor =”yellow”
```

###  <a name="wbc"></a> WarningBackgroundColor
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。

 指定“控制台”窗格中显示的警告文本的背景色。 它是 **System.Windows.Media.Color** 对象。

```
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor ='#0000FF'
```

###  <a name="wfc"></a> WarningForegroundColor
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。

 指定“输出”窗格中显示的警告文本的前景色。 它是 **System.Windows.Media.Color** 对象。

```
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor =”yellow”
```

###  <a name="xtc"></a> XmlTokenColors
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

 指定包含标记类型的名称值对以及 Windows PowerShell ISE 中显示的 XML 内容颜色的字典对象。 可以针对以下项设置标记颜色：Attribute、Command、CommandArgument、CommandParameter、Comment、GroupEnd、GroupStart、Keyword、LineContinuation、LoopLabel、Member、NewLine、Number、Operator、Position、StatementSeparator、String、Type、Unknown、Variable。 另请参阅 [RestoreDefaultXmlTokenColors()](#rdxtc)。

```
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = "green"
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = "magenta"

```

###  <a name="z"></a> 缩放
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

 在“控制台”和“脚本”窗格中指定文本的相对大小。 默认值为 100。 较小的值会导致 Windows PowerShell ISE 中的文本显示得较小，数字越大会导致文本显示得越大。 该值为一个整数，范围为 20 到 400。

```
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## 另请参阅
 [Windows PowerShell ISE 脚本对象模型](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
 [Windows PowerShell ISE 对象模型参考](Windows-PowerShell-ISE-Object-Model-Reference.md)



<!--HONumber=May16_HO2-->


