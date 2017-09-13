---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISEOptions 对象"
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
ms.openlocfilehash: 5e04adeebacfb9214bf39d9ec9c5f0e01f5729ee
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/08/2017
---
# <a name="the-iseoptions-object"></a><span data-ttu-id="af894-103">ISEOptions 对象</span><span class="sxs-lookup"><span data-stu-id="af894-103">The ISEOptions Object</span></span>
  <span data-ttu-id="af894-104">**ISEOptions** 对象代表 Windows PowerShell ISE 的各种设置。</span><span class="sxs-lookup"><span data-stu-id="af894-104">The **ISEOptions** object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="af894-105">它是 **Microsoft.PowerShell.Host.ISE.ISEOptions** 类的实例。</span><span class="sxs-lookup"><span data-stu-id="af894-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEOptions** class.</span></span>

 <span data-ttu-id="af894-106">**ISEOptions** 对象提供以下方法和属性。</span><span class="sxs-lookup"><span data-stu-id="af894-106">The **ISEOptions** object provides the following methods and properties.</span></span>

## <a name="methods"></a><span data-ttu-id="af894-107">方法</span><span class="sxs-lookup"><span data-stu-id="af894-107">Methods</span></span>

### <a name="restoredefaultconsoletokencolors"></a><span data-ttu-id="af894-108">RestoreDefaultConsoleTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="af894-108">RestoreDefaultConsoleTokenColors\(\)</span></span>
  <span data-ttu-id="af894-109">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="af894-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="af894-110">还原“控制台”窗格中的标记颜色的默认值。</span><span class="sxs-lookup"><span data-stu-id="af894-110">Restores the default values of the token colors in the Console pane.</span></span>

```
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = "red"
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a><span data-ttu-id="af894-111">RestoreDefaults\(\)</span><span class="sxs-lookup"><span data-stu-id="af894-111">RestoreDefaults\(\)</span></span>
  <span data-ttu-id="af894-112">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="af894-112">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="af894-113">还原“控制台”窗格中的所有选项设置的默认值。</span><span class="sxs-lookup"><span data-stu-id="af894-113">Restores the default values of all options settings in the Console pane.</span></span> <span data-ttu-id="af894-114">此外，它还重置提供标准复选框以防止再次显示消息的各种警告消息的行为。</span><span class="sxs-lookup"><span data-stu-id="af894-114">It also resets the behavior of various warning messages that provide the standard check box to prevent the message from being shown again.</span></span>

```
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = "orange"
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a><span data-ttu-id="af894-115">RestoreDefaultTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="af894-115">RestoreDefaultTokenColors\(\)</span></span>
  <span data-ttu-id="af894-116">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="af894-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="af894-117">还原“脚本”窗格中的标记颜色的默认值。</span><span class="sxs-lookup"><span data-stu-id="af894-117">Restores the default values of the token colors in the Script pane.</span></span>

```
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a><span data-ttu-id="af894-118">RestoreDefaultXmlTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="af894-118">RestoreDefaultXmlTokenColors\(\)</span></span>
  <span data-ttu-id="af894-119">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="af894-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="af894-120">还原 Windows PowerShell ISE 中显示的 XML 元素的标记颜色的默认值。</span><span class="sxs-lookup"><span data-stu-id="af894-120">Restores the default values of the token colors for XML elements that are displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="af894-121">另请参阅 [XmlTokenColors](#xmltokencolors)。</span><span class="sxs-lookup"><span data-stu-id="af894-121">Also see [XmlTokenColors](#xmltokencolors).</span></span>

```
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a><span data-ttu-id="af894-122">“属性”</span><span class="sxs-lookup"><span data-stu-id="af894-122">Properties</span></span>

### <a name="autosaveminuteinterval"></a><span data-ttu-id="af894-123">AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="af894-123">AutoSaveMinuteInterval</span></span>
  <span data-ttu-id="af894-124">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="af894-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="af894-125">通过 Windows PowerShell ISE 指定文件自动保存操作之间的分钟数。</span><span class="sxs-lookup"><span data-stu-id="af894-125">Specifies the number of minutes between automatic save operations of your files by Windows PowerShell ISE.</span></span> <span data-ttu-id="af894-126">默认值为 2 分钟。</span><span class="sxs-lookup"><span data-stu-id="af894-126">The default value is 2 minutes.</span></span> <span data-ttu-id="af894-127">该值是一个整数。</span><span class="sxs-lookup"><span data-stu-id="af894-127">The value is an integer.</span></span>

```
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a><span data-ttu-id="af894-128">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="af894-128">CommandPaneBackgroundColor</span></span>
  <span data-ttu-id="af894-129">此功能存在于 Windows PowerShell ISE 2.0 中，但已在更高版本的 ISE 中删除或重命名。</span><span class="sxs-lookup"><span data-stu-id="af894-129">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="af894-130">对于更高版本，请参阅 [ConsolePaneBackgroundColor](#consolepanebackgroundcolor)。</span><span class="sxs-lookup"><span data-stu-id="af894-130">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

 <span data-ttu-id="af894-131">指定“命令”窗格的背景色。</span><span class="sxs-lookup"><span data-stu-id="af894-131">Specifies the background color for the Command pane.</span></span> <span data-ttu-id="af894-132">它是 **System.Windows.Media.Color** 类的实例。</span><span class="sxs-lookup"><span data-stu-id="af894-132">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = "orange"
```

### <a name="commandpaneup"></a><span data-ttu-id="af894-133">CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="af894-133">CommandPaneUp</span></span>
  <span data-ttu-id="af894-134">此功能存在于 Windows PowerShell ISE 2.0 中，但已在更高版本的 ISE 中删除或重命名。</span><span class="sxs-lookup"><span data-stu-id="af894-134">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>

 <span data-ttu-id="af894-135">指定“命令”窗格是否位于“输出”窗格上方。</span><span class="sxs-lookup"><span data-stu-id="af894-135">Specifies whether the Command pane is located above the Output pane.</span></span>

```
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true

```

### <a name="consolepanebackgroundcolor"></a><span data-ttu-id="af894-136">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="af894-136">ConsolePaneBackgroundColor</span></span>
  <span data-ttu-id="af894-137">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="af894-137">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="af894-138">指定“控制台”窗格的背景色。</span><span class="sxs-lookup"><span data-stu-id="af894-138">Specifies the background color for the Console pane.</span></span> <span data-ttu-id="af894-139">它是 **System.Windows.Media.Color** 类的实例。</span><span class="sxs-lookup"><span data-stu-id="af894-139">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = "red"
```

### <a name="consolepaneforegroundcolor"></a><span data-ttu-id="af894-140">ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="af894-140">ConsolePaneForegroundColor</span></span>
  <span data-ttu-id="af894-141">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="af894-141">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="af894-142">指定“控制台”窗格中文本的前景色。</span><span class="sxs-lookup"><span data-stu-id="af894-142">Specifies the foreground color of the text in the Console pane.</span></span>

```
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = "yellow"

```

### <a name="consolepanetextbackgroundcolor"></a><span data-ttu-id="af894-143">ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="af894-143">ConsolePaneTextBackgroundColor</span></span>
  <span data-ttu-id="af894-144">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="af894-144">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="af894-145">指定“控制台”窗格中文本的背景色。</span><span class="sxs-lookup"><span data-stu-id="af894-145">Specifies the background color of the text in the Console pane.</span></span>

```
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = "pink"
```

### <a name="consoletokencolors"></a><span data-ttu-id="af894-146">ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="af894-146">ConsoleTokenColors</span></span>
  <span data-ttu-id="af894-147">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="af894-147">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="af894-148">指定 Windows PowerShell ISE“控制台”窗格中 IntelliSense 标记的颜色。</span><span class="sxs-lookup"><span data-stu-id="af894-148">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Console pane.</span></span> <span data-ttu-id="af894-149">此属性是一个包含标记类型的名称/值对和“控制台”窗格颜色的字典对象。</span><span class="sxs-lookup"><span data-stu-id="af894-149">This property is a dictionary object that contains name/value pairs of token types and colors for the Console pane.</span></span> <span data-ttu-id="af894-150">若要更改“脚本”窗格中 IntelliSense 标记的颜色，请参阅 [TokenColors](#tokencolors)。</span><span class="sxs-lookup"><span data-stu-id="af894-150">To change the colors of the IntelliSense tokens in the Script pane, see [TokenColors](#tokencolors).</span></span> <span data-ttu-id="af894-151">要将颜色重置为默认值，请参阅 [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors)。</span><span class="sxs-lookup"><span data-stu-id="af894-151">To reset the colors to the default values, see [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span></span> <span data-ttu-id="af894-152">可以针对以下项设置标记颜色：Attribute、Command、CommandArgument、CommandParameter、Comment、GroupEnd、GroupStart、Keyword、LineContinuation、LoopLabel、Member、NewLine、Number、Operator、Position、StatementSeparator、String、Type、Unknown、Variable。</span><span class="sxs-lookup"><span data-stu-id="af894-152">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = "magenta"

```

### <a name="debugbackgroundcolor"></a><span data-ttu-id="af894-153">DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="af894-153">DebugBackgroundColor</span></span>
  <span data-ttu-id="af894-154">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="af894-154">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="af894-155">指定“控制台”窗格中显示的调试文本的背景色。</span><span class="sxs-lookup"><span data-stu-id="af894-155">Specifies the background color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="af894-156">它是 **System.Windows.Media.Color** 类的实例。</span><span class="sxs-lookup"><span data-stu-id="af894-156">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor ='#0000FF'
```

### <a name="debugforegroundcolor"></a><span data-ttu-id="af894-157">DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="af894-157">DebugForegroundColor</span></span>
  <span data-ttu-id="af894-158">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="af894-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="af894-159">指定“控制台”窗格中显示的调试文本的前景色。</span><span class="sxs-lookup"><span data-stu-id="af894-159">Specifies the foreground color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="af894-160">它是 **System.Windows.Media.Color** 类的实例。</span><span class="sxs-lookup"><span data-stu-id="af894-160">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor ="yellow"
```

### <a name="defaultoptions"></a><span data-ttu-id="af894-161">DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="af894-161">DefaultOptions</span></span>
  <span data-ttu-id="af894-162">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="af894-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="af894-163">指定使用重置方法时要使用的默认值的属性集合。</span><span class="sxs-lookup"><span data-stu-id="af894-163">A collection of properties that specify the default values to be used when the Reset methods are used.</span></span>

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

### <a name="errorbackgroundcolor"></a><span data-ttu-id="af894-164">ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="af894-164">ErrorBackgroundColor</span></span>
  <span data-ttu-id="af894-165">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="af894-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="af894-166">指定“控制台”窗格中显示的错误文本的背景色。</span><span class="sxs-lookup"><span data-stu-id="af894-166">Specifies the background color for error text that appears in the Console pane.</span></span> <span data-ttu-id="af894-167">它是 **System.Windows.Media.Color** 类的实例。</span><span class="sxs-lookup"><span data-stu-id="af894-167">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor="black"
```

### <a name="errorforegroundcolor"></a><span data-ttu-id="af894-168">ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="af894-168">ErrorForegroundColor</span></span>
  <span data-ttu-id="af894-169">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="af894-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="af894-170">指定“控制台”窗格中显示的错误文本的前景色。</span><span class="sxs-lookup"><span data-stu-id="af894-170">Specifies the foreground color for error text that appears in the Console pane.</span></span> <span data-ttu-id="af894-171">它是 **System.Windows.Media.Color** 类的实例。</span><span class="sxs-lookup"><span data-stu-id="af894-171">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor ="green"
```

### <a name="fontname"></a><span data-ttu-id="af894-172">FontName</span><span class="sxs-lookup"><span data-stu-id="af894-172">FontName</span></span>
  <span data-ttu-id="af894-173">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="af894-173">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="af894-174">指定“脚本”窗格和“控制台”窗格中当前使用的字体名称。</span><span class="sxs-lookup"><span data-stu-id="af894-174">Specifies the font name currently in use in both the Script pane and the Console pane.</span></span>

```
# Changes the font used in both panes.
$psISE.Options.FontName = "courier new"
```

### <a name="fontsize"></a><span data-ttu-id="af894-175">FontSize</span><span class="sxs-lookup"><span data-stu-id="af894-175">FontSize</span></span>
  <span data-ttu-id="af894-176">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="af894-176">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="af894-177">以整数形式指定字体大小。</span><span class="sxs-lookup"><span data-stu-id="af894-177">Specifies the font size as an integer.</span></span> <span data-ttu-id="af894-178">在“脚本”窗格、“命令”窗格以及“输出”窗格中使用。</span><span class="sxs-lookup"><span data-stu-id="af894-178">It is used in the Script pane, the Command pane, and the Output pane.</span></span> <span data-ttu-id="af894-179">值的有效范围是 8 至 32。</span><span class="sxs-lookup"><span data-stu-id="af894-179">The valid range of values is 8 through 32.</span></span>

```
# Changes the font size in all panes.
$psISE.Options.FontSize = 20

```

### <a name="intellisensetimeoutinseconds"></a><span data-ttu-id="af894-180">IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="af894-180">IntellisenseTimeoutInSeconds</span></span>
  <span data-ttu-id="af894-181">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="af894-181">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="af894-182">指定 IntelliSense 用来尝试解决当前所键入文本的秒数。</span><span class="sxs-lookup"><span data-stu-id="af894-182">Specifies the number of seconds that IntelliSense uses to try to resolve the currently typed text.</span></span> <span data-ttu-id="af894-183">该秒数之后，IntelliSense 将会超时，并使你能够继续键入。</span><span class="sxs-lookup"><span data-stu-id="af894-183">After this number of seconds, IntelliSense times out and enables you to continue typing.</span></span> <span data-ttu-id="af894-184">默认值是 3 秒。</span><span class="sxs-lookup"><span data-stu-id="af894-184">The default value is 3 seconds.</span></span> <span data-ttu-id="af894-185">该值是一个整数。</span><span class="sxs-lookup"><span data-stu-id="af894-185">The value is an integer.</span></span>

```
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a><span data-ttu-id="af894-186">MruCount</span><span class="sxs-lookup"><span data-stu-id="af894-186">MruCount</span></span>
  <span data-ttu-id="af894-187">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="af894-187">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="af894-188">指定 Windows PowerShell ISE 跟踪并在**“文件打开”**菜单底部显示的最近打开的文件数。</span><span class="sxs-lookup"><span data-stu-id="af894-188">Specifies the number of recently opened files that Windows PowerShell ISE tracks and displays at the bottom of the **File Open** menu.</span></span> <span data-ttu-id="af894-189">默认值为 10。</span><span class="sxs-lookup"><span data-stu-id="af894-189">The default value is 10.</span></span> <span data-ttu-id="af894-190">该值是一个整数。</span><span class="sxs-lookup"><span data-stu-id="af894-190">The value is an integer.</span></span>

```
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a><span data-ttu-id="af894-191">OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="af894-191">OutputPaneBackgroundColor</span></span>
  <span data-ttu-id="af894-192">此功能存在于 Windows PowerShell ISE 2.0 中，但已在更高版本的 ISE 中删除或重命名。</span><span class="sxs-lookup"><span data-stu-id="af894-192">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="af894-193">对于更高版本，请参阅 [ConsolePaneBackgroundColor](#consolepanebackgroundcolor)。</span><span class="sxs-lookup"><span data-stu-id="af894-193">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

 <span data-ttu-id="af894-194">读/写属性，可获取或设置“输出”窗格本身的背景色。</span><span class="sxs-lookup"><span data-stu-id="af894-194">The read/write property that gets or sets the background color for the Output pane itself.</span></span> <span data-ttu-id="af894-195">它是 **System.Windows.Media.Color** 类的实例。</span><span class="sxs-lookup"><span data-stu-id="af894-195">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = "gold"

```

### <a name="outputpanetextforegroundcolor"></a><span data-ttu-id="af894-196">OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="af894-196">OutputPaneTextForegroundColor</span></span>
  <span data-ttu-id="af894-197">此功能存在于 Windows PowerShell ISE 2.0 中，但已在更高版本的 ISE 中删除或重命名。</span><span class="sxs-lookup"><span data-stu-id="af894-197">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="af894-198">对于更高版本，请参阅 [ConsolePaneForegroundColor](#consolepaneforegroundcolor)。</span><span class="sxs-lookup"><span data-stu-id="af894-198">For later versions, see [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span></span>

 <span data-ttu-id="af894-199">读/写属性，可更改 Windows PowerShell ISE 2.0 中“输出”窗格中的文本前景色。</span><span class="sxs-lookup"><span data-stu-id="af894-199">The read/write property that changes the foreground color of the text in the Output pane in Windows PowerShell ISE 2.0.</span></span>

```
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = "blue"

```

### <a name="outputpanetextbackgroundcolor"></a><span data-ttu-id="af894-200">OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="af894-200">OutputPaneTextBackgroundColor</span></span>
  <span data-ttu-id="af894-201">此功能存在于 Windows PowerShell ISE 2.0 中，但已在更高版本的 ISE 中删除或重命名。</span><span class="sxs-lookup"><span data-stu-id="af894-201">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="af894-202">对于更高版本，请参阅 [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor)。</span><span class="sxs-lookup"><span data-stu-id="af894-202">For later versions, see [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span></span>

 <span data-ttu-id="af894-203">读/写属性，可更改“输出”窗格中的文本背景色。</span><span class="sxs-lookup"><span data-stu-id="af894-203">The read/write property that changes the background color of the text in the Output pane.</span></span>

```
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = "pink"
```

### <a name="scriptpanebackgroundcolor"></a><span data-ttu-id="af894-204">ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="af894-204">ScriptPaneBackgroundColor</span></span>
  <span data-ttu-id="af894-205">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="af894-205">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="af894-206">读/写属性，可获取或设置文件的背景色。</span><span class="sxs-lookup"><span data-stu-id="af894-206">The read/write property that gets or sets the background color for files.</span></span> <span data-ttu-id="af894-207">它是 **System.Windows.Media.Color** 类的实例。</span><span class="sxs-lookup"><span data-stu-id="af894-207">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```

# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'

```

### <a name="scriptpaneforegroundcolor"></a><span data-ttu-id="af894-208">ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="af894-208">ScriptPaneForegroundColor</span></span>
  <span data-ttu-id="af894-209">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="af894-209">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="af894-210">读/写属性，可获取或设置“脚本”窗格中非脚本文件的前景色。</span><span class="sxs-lookup"><span data-stu-id="af894-210">The read/write property that gets or sets the foreground color for non-script files in the Script pane.</span></span>
<span data-ttu-id="af894-211">要设置脚本文件的前景色，请使用 [TokenColors](#tokencolors)。</span><span class="sxs-lookup"><span data-stu-id="af894-211">To set the foreground color for script files, use the [TokenColors](#tokencolors).</span></span>

```
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = "green"

```

### <a name="selectedscriptpanestate"></a><span data-ttu-id="af894-212">SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="af894-212">SelectedScriptPaneState</span></span>
  <span data-ttu-id="af894-213">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="af894-213">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="af894-214">读/写属性，可获取或设置“脚本”窗格在显示屏上的位置。</span><span class="sxs-lookup"><span data-stu-id="af894-214">The read/write property that gets or sets the position of the Script pane on the display.</span></span> <span data-ttu-id="af894-215">字符串可以是“最大化”、“顶部”或“右侧”。</span><span class="sxs-lookup"><span data-stu-id="af894-215">The string can be either "Maximized", "Top", or "Right".</span></span>

```
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = "Top"
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = "Right"
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = "Maximized"

```

### <a name="showdefaultsnippets"></a><span data-ttu-id="af894-216">ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="af894-216">ShowDefaultSnippets</span></span>
  <span data-ttu-id="af894-217">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="af894-217">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="af894-218">指定代码段的 **CTRL + J** 列表是否包括Windows PowerShell 中包含的初学者套件。</span><span class="sxs-lookup"><span data-stu-id="af894-218">Specifies whether the **CTRL+J** list of snippets includes the starter set that is included in Windows PowerShell.</span></span> <span data-ttu-id="af894-219">当设置为 **$false** 时，只有用户定义的代码段显示在 **CTRL + J** 列表中。</span><span class="sxs-lookup"><span data-stu-id="af894-219">When set to **$false**, only user-defined snippets appear in the **CTRL+J** list.</span></span> <span data-ttu-id="af894-220">默认值为 **$true**。</span><span class="sxs-lookup"><span data-stu-id="af894-220">The default value is **$true**.</span></span>

```
# Hide the default snippets from the CTRL+J list.
$psISe.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a><span data-ttu-id="af894-221">ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="af894-221">ShowIntellisenseInConsolePane</span></span>
  <span data-ttu-id="af894-222">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="af894-222">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="af894-223">指定 IntelliSense 是否在“控制台”窗格中提供语法、参数和值建议。</span><span class="sxs-lookup"><span data-stu-id="af894-223">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Console pane.</span></span> <span data-ttu-id="af894-224">默认值为 **$true**。</span><span class="sxs-lookup"><span data-stu-id="af894-224">The default value is **$true**.</span></span>

```
# Turn off IntelliSense in the console pane.
$psISe.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a><span data-ttu-id="af894-225">ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="af894-225">ShowIntellisenseInScriptPane</span></span>
  <span data-ttu-id="af894-226">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="af894-226">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="af894-227">指定 IntelliSense 是否在“脚本”窗格中提供语法、参数和值建议。</span><span class="sxs-lookup"><span data-stu-id="af894-227">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Script pane.</span></span> <span data-ttu-id="af894-228">默认值为 **$true**。</span><span class="sxs-lookup"><span data-stu-id="af894-228">The default value is **$true**.</span></span>

```
# Turn off IntelliSense in the Script pane.
$psISe.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a><span data-ttu-id="af894-229">ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="af894-229">ShowLineNumbers</span></span>
  <span data-ttu-id="af894-230">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="af894-230">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="af894-231">指定“脚本”窗格是否在左边空白处显示行号。</span><span class="sxs-lookup"><span data-stu-id="af894-231">Specifies whether the Script pane displays line numbers in the left margin.</span></span> <span data-ttu-id="af894-232">默认值为 **$true**。</span><span class="sxs-lookup"><span data-stu-id="af894-232">The default value is **$true**.</span></span>

```
# Turn off line numbers in the Script pane.
$psISe.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a><span data-ttu-id="af894-233">ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="af894-233">ShowOutlining</span></span>
  <span data-ttu-id="af894-234">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="af894-234">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="af894-235">指定“脚本”窗格中是否在左边空白处代码段的旁边显示可展开和折叠的括号。</span><span class="sxs-lookup"><span data-stu-id="af894-235">Specifies whether the Script pane displays expandable and collapsible brackets next to sections of code in the left margin.</span></span> <span data-ttu-id="af894-236">如果显示，你可以单击文本块旁边的减号 \(-\) 图标将其折叠起来，或单击加号 \(+\) 图标展开文本块。</span><span class="sxs-lookup"><span data-stu-id="af894-236">When they are displayed, you can click the minus \(-\) icons next to a block of text to collapse it or click the plus \(+\) icon to expand a block of text.</span></span> <span data-ttu-id="af894-237">默认值为 **$true**。</span><span class="sxs-lookup"><span data-stu-id="af894-237">The default value is **$true**.</span></span>

```
# Turn off outlining in the Script pane.
$psISe.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a><span data-ttu-id="af894-238">ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="af894-238">ShowToolBar</span></span>
  <span data-ttu-id="af894-239">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="af894-239">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="af894-240">指定 ISE 工具栏是否显示在 Windows PowerShell ISE 窗口的顶部。</span><span class="sxs-lookup"><span data-stu-id="af894-240">Specifies whether the ISE toolbar appears at the top of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="af894-241">默认值为 **$true**。</span><span class="sxs-lookup"><span data-stu-id="af894-241">The default value is **$true**.</span></span>

```
# Show the toolbar.
$psISe.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a><span data-ttu-id="af894-242">ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="af894-242">ShowWarningBeforeSavingOnRun</span></span>
  <span data-ttu-id="af894-243">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="af894-243">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="af894-244">指定在运行脚本之前自动保存该脚本是否显示警告消息。</span><span class="sxs-lookup"><span data-stu-id="af894-244">Specifies whether a warning message appears when a script is saved automatically before it is run.</span></span> <span data-ttu-id="af894-245">默认值为 **$true**。</span><span class="sxs-lookup"><span data-stu-id="af894-245">The default value is **$true**.</span></span>

```
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun=$true

```

### <a name="showwarningforduplicatefiles"></a><span data-ttu-id="af894-246">ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="af894-246">ShowWarningForDuplicateFiles</span></span>
  <span data-ttu-id="af894-247">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="af894-247">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="af894-248">指定在不同 PowerShell 选项卡中打开同一个文件时是否显示警告消息。</span><span class="sxs-lookup"><span data-stu-id="af894-248">Specifies whether a warning message appears when the same file is opened in different PowerShell tabs.</span></span> <span data-ttu-id="af894-249">如果设置为 **$true**，在多个选项卡打开同一个文件将显示此消息：“已在另一个 Windows PowerShell 选项卡中打开此文件的副本。对此文件所做的更改将影响所有打开的副本。”</span><span class="sxs-lookup"><span data-stu-id="af894-249">If set to **$true**, to open the same file in multiple tabs displays this message: "A copy of this file is open in another Windows PowerShell tab. Changes made to this file will affect all open copies."</span></span> <span data-ttu-id="af894-250">默认值为 **$true**。</span><span class="sxs-lookup"><span data-stu-id="af894-250">The default value is **$true**.</span></span>

```
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true

```

### <a name="tokencolors"></a><span data-ttu-id="af894-251">TokenColors</span><span class="sxs-lookup"><span data-stu-id="af894-251">TokenColors</span></span>
  <span data-ttu-id="af894-252">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="af894-252">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="af894-253">指定 Windows PowerShell ISE“脚本”窗格中 IntelliSense 标记的颜色。</span><span class="sxs-lookup"><span data-stu-id="af894-253">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Script pane.</span></span> <span data-ttu-id="af894-254">此属性是一个包含标记类型的名称/值对和“脚本”窗格颜色的字典对象。</span><span class="sxs-lookup"><span data-stu-id="af894-254">This property is a dictionary object that contains name/value pairs of token types and colors for the Script pane.</span></span> <span data-ttu-id="af894-255">若要更改“脚本”窗格中 IntelliSense 标记的颜色，请参阅 [ConsoleTokenColors](#consoletokencolors)。</span><span class="sxs-lookup"><span data-stu-id="af894-255">To change the colors of the IntelliSense tokens in the Console pane, see [ConsoleTokenColors](#consoletokencolors).</span></span> <span data-ttu-id="af894-256">要将颜色重置为默认值，请参阅 [RestoreDefaultTokenColors](#restoredefaulttokencolors)。</span><span class="sxs-lookup"><span data-stu-id="af894-256">To reset the colors to the default values, see [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span></span> <span data-ttu-id="af894-257">可以针对以下项设置标记颜色：Attribute、Command、CommandArgument、CommandParameter、Comment、GroupEnd、GroupStart、Keyword、LineContinuation、LoopLabel、Member、NewLine、Number、Operator、Position、StatementSeparator、String、Type、Unknown、Variable。</span><span class="sxs-lookup"><span data-stu-id="af894-257">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"

```

### <a name="useentertoselectinconsolepaneintellisense"></a><span data-ttu-id="af894-258">UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="af894-258">UseEnterToSelectInConsolePaneIntellisense</span></span>
  <span data-ttu-id="af894-259">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="af894-259">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="af894-260">指定是否可以使用 Enter 键选择 IntelliSense 在“控制台”窗格中提供的选项。</span><span class="sxs-lookup"><span data-stu-id="af894-260">Specifies whether you can use the Enter key to select an IntelliSense provided option in the Console pane.</span></span> <span data-ttu-id="af894-261">默认值为 **$true**。</span><span class="sxs-lookup"><span data-stu-id="af894-261">The default value is **$true**.</span></span>

```
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$false

```

### <a name="useentertoselectinscriptpaneintellisense"></a><span data-ttu-id="af894-262">UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="af894-262">UseEnterToSelectInScriptPaneIntellisense</span></span>
  <span data-ttu-id="af894-263">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="af894-263">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="af894-264">指定是否可以使用 Enter 键选择 IntelliSense 在“脚本”窗格中提供的选项。</span><span class="sxs-lookup"><span data-stu-id="af894-264">Specifies whether you can use the Enter key to select an IntelliSense-provided option in the Script pane.</span></span> <span data-ttu-id="af894-265">默认值为 **$true**。</span><span class="sxs-lookup"><span data-stu-id="af894-265">The default value is **$true**.</span></span>

```
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$true

```

### <a name="uselocalhelp"></a><span data-ttu-id="af894-266">UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="af894-266">UseLocalHelp</span></span>
  <span data-ttu-id="af894-267">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="af894-267">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="af894-268">指定将光标置于关键字中并按 F1 时是显示本地安装的帮助还是联机 TechNet 库帮助。</span><span class="sxs-lookup"><span data-stu-id="af894-268">Specifies whether the locally installed Help or the online TechNet Library Help appears when you press F1 with the cursor positioned in a keyword.</span></span> <span data-ttu-id="af894-269">如果设置为 **$true**，那么弹出窗口会显示本地安装的帮助中的内容。</span><span class="sxs-lookup"><span data-stu-id="af894-269">If set to **$true**, then a pop-up window shows content from the locally installed Help.</span></span> <span data-ttu-id="af894-270">可以通过运行 `Update-Help` 命令安装帮助文件。</span><span class="sxs-lookup"><span data-stu-id="af894-270">You can install the Help files by running the `Update-Help` command.</span></span> <span data-ttu-id="af894-271">如果设置为 **$false**，则你的浏览器会在 TechNet 库中打开一个页面。</span><span class="sxs-lookup"><span data-stu-id="af894-271">If set to **$false**, then your browser opens to a page in the TechNet Library.</span></span>

```
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp=$false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp=$true

```

### <a name="verbosebackgroundcolor"></a><span data-ttu-id="af894-272">VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="af894-272">VerboseBackgroundColor</span></span>
  <span data-ttu-id="af894-273">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="af894-273">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="af894-274">指定“控制台”窗格中显示的详细文本的背景色。</span><span class="sxs-lookup"><span data-stu-id="af894-274">Specifies the background color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="af894-275">它是 **System.Windows.Media.Color** 对象。</span><span class="sxs-lookup"><span data-stu-id="af894-275">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a><span data-ttu-id="af894-276">VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="af894-276">VerboseForegroundColor</span></span>
  <span data-ttu-id="af894-277">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="af894-277">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="af894-278">指定“控制台”窗格中显示的详细文本的前景色。</span><span class="sxs-lookup"><span data-stu-id="af894-278">Specifies the foreground color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="af894-279">它是 **System.Windows.Media.Color** 对象。</span><span class="sxs-lookup"><span data-stu-id="af894-279">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor ='yellow'
```

### <a name="warningbackgroundcolor"></a><span data-ttu-id="af894-280">WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="af894-280">WarningBackgroundColor</span></span>
  <span data-ttu-id="af894-281">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="af894-281">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="af894-282">指定“控制台”窗格中显示的警告文本的背景色。</span><span class="sxs-lookup"><span data-stu-id="af894-282">Specifies the background color for warning text that appears in the Console pane.</span></span> <span data-ttu-id="af894-283">它是 **System.Windows.Media.Color** 对象。</span><span class="sxs-lookup"><span data-stu-id="af894-283">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor ='#0000FF'
```

### <a name="warningforegroundcolor"></a><span data-ttu-id="af894-284">WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="af894-284">WarningForegroundColor</span></span>
  <span data-ttu-id="af894-285">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="af894-285">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="af894-286">指定“输出”窗格中显示的警告文本的前景色。</span><span class="sxs-lookup"><span data-stu-id="af894-286">Specifies the foreground color for warning text that appears in the Output pane.</span></span> <span data-ttu-id="af894-287">它是 **System.Windows.Media.Color** 对象。</span><span class="sxs-lookup"><span data-stu-id="af894-287">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor ='yellow'
```

### <a name="xmltokencolors"></a><span data-ttu-id="af894-288">XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="af894-288">XmlTokenColors</span></span>
  <span data-ttu-id="af894-289">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="af894-289">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="af894-290">指定包含标记类型的名称/值对以及 Windows PowerShell ISE 中显示的 XML 内容颜色的字典对象。</span><span class="sxs-lookup"><span data-stu-id="af894-290">Specifies a dictionary object that contains name/value pairs of token types and colors for XML content that is displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="af894-291">可以针对以下项设置标记颜色：Attribute、Command、CommandArgument、CommandParameter、Comment、GroupEnd、GroupStart、Keyword、LineContinuation、LoopLabel、Member、NewLine、Number、Operator、Position、StatementSeparator、String、Type、Unknown、Variable。</span><span class="sxs-lookup"><span data-stu-id="af894-291">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span> <span data-ttu-id="af894-292">另请参阅 [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors)。</span><span class="sxs-lookup"><span data-stu-id="af894-292">Also see [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span></span>

```
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = "green"
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = "magenta"

```

### <a name="zoom"></a><span data-ttu-id="af894-293">缩放</span><span class="sxs-lookup"><span data-stu-id="af894-293">Zoom</span></span>
  <span data-ttu-id="af894-294">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="af894-294">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="af894-295">在“控制台”和“脚本”窗格中指定文本的相对大小。</span><span class="sxs-lookup"><span data-stu-id="af894-295">Specifies the relative size of text in both the Console and Script panes.</span></span> <span data-ttu-id="af894-296">默认值为 100。</span><span class="sxs-lookup"><span data-stu-id="af894-296">The default value is 100.</span></span> <span data-ttu-id="af894-297">较小的值会导致 Windows PowerShell ISE 中的文本显示得较小，数字越大会导致文本显示得越大。</span><span class="sxs-lookup"><span data-stu-id="af894-297">Smaller values cause the text in Windows PowerShell ISE to appear smaller while larger numbers cause text to appear larger.</span></span> <span data-ttu-id="af894-298">该值为一个整数，范围为 20 到 400。</span><span class="sxs-lookup"><span data-stu-id="af894-298">The value is an integer that ranges from 20 to 400.</span></span>

```
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a><span data-ttu-id="af894-299">另请参阅</span><span class="sxs-lookup"><span data-stu-id="af894-299">See Also</span></span>
- [<span data-ttu-id="af894-300">Windows PowerShell ISE 脚本对象模型</span><span class="sxs-lookup"><span data-stu-id="af894-300">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="af894-301">Windows PowerShell ISE 对象模型参考</span><span class="sxs-lookup"><span data-stu-id="af894-301">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)

