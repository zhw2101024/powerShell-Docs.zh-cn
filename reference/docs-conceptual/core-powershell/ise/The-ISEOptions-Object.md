---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISEOptions 对象"
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
ms.openlocfilehash: 56bdd5999b46b6e29e762c2d9a2060cebe3a1299
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2017
---
# <a name="the-iseoptions-object"></a><span data-ttu-id="1af16-103">ISEOptions 对象</span><span class="sxs-lookup"><span data-stu-id="1af16-103">The ISEOptions Object</span></span>
  <span data-ttu-id="1af16-104">**ISEOptions** 对象代表 Windows PowerShell ISE 的各种设置。</span><span class="sxs-lookup"><span data-stu-id="1af16-104">The **ISEOptions** object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="1af16-105">它是 **Microsoft.PowerShell.Host.ISE.ISEOptions** 类的实例。</span><span class="sxs-lookup"><span data-stu-id="1af16-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEOptions** class.</span></span>

 <span data-ttu-id="1af16-106">**ISEOptions** 对象提供以下方法和属性。</span><span class="sxs-lookup"><span data-stu-id="1af16-106">The **ISEOptions** object provides the following methods and properties.</span></span>

 <span data-ttu-id="1af16-107">**方法**</span><span class="sxs-lookup"><span data-stu-id="1af16-107">**Methods**</span></span>

-   [<span data-ttu-id="1af16-108">RestoreDefaultConsoleTokenColors()</span><span class="sxs-lookup"><span data-stu-id="1af16-108">RestoreDefaultConsoleTokenColors()</span></span>](#rdctc)

-   [<span data-ttu-id="1af16-109">RestoreDefaults()</span><span class="sxs-lookup"><span data-stu-id="1af16-109">RestoreDefaults()</span></span>](#rd)

-   [<span data-ttu-id="1af16-110">RestoreDefaultTokenColors()</span><span class="sxs-lookup"><span data-stu-id="1af16-110">RestoreDefaultTokenColors()</span></span>](#rdtc)

-   [<span data-ttu-id="1af16-111">RestoreDefaultXmlTokenColors()</span><span class="sxs-lookup"><span data-stu-id="1af16-111">RestoreDefaultXmlTokenColors()</span></span>](#rdxtc)

 <span data-ttu-id="1af16-112">**属性**</span><span class="sxs-lookup"><span data-stu-id="1af16-112">**Properties**</span></span>

-   [<span data-ttu-id="1af16-113">AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="1af16-113">AutoSaveMinuteInterval</span></span>](#asmi)

-   [<span data-ttu-id="1af16-114">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-114">CommandPaneBackgroundColor</span></span>](#cpbc)

-   [<span data-ttu-id="1af16-115">CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="1af16-115">CommandPaneUp</span></span>](#cpu)

-   [<span data-ttu-id="1af16-116">ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-116">ConsolePaneBackgroundColor</span></span>](#conpbc)

-   [<span data-ttu-id="1af16-117">ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-117">ConsolePaneForegroundColor</span></span>](#conpfc)

-   [<span data-ttu-id="1af16-118">ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-118">ConsolePaneTextBackgroundColor</span></span>](#conptbc)

-   [<span data-ttu-id="1af16-119">ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="1af16-119">ConsoleTokenColors</span></span>](#contc)

-   [<span data-ttu-id="1af16-120">DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-120">DebugBackgroundColor</span></span>](#dbc)

-   [<span data-ttu-id="1af16-121">DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-121">DebugForegroundColor</span></span>](#dfc)

-   [<span data-ttu-id="1af16-122">DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="1af16-122">DefaultOptions</span></span>](#do)

-   [<span data-ttu-id="1af16-123">ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-123">ErrorBackgroundColor</span></span>](#ebc)

-   [<span data-ttu-id="1af16-124">ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-124">ErrorForegroundColor</span></span>](#efc)

-   [<span data-ttu-id="1af16-125">FontName</span><span class="sxs-lookup"><span data-stu-id="1af16-125">FontName</span></span>](#fn)

-   [<span data-ttu-id="1af16-126">FontSize</span><span class="sxs-lookup"><span data-stu-id="1af16-126">FontSize</span></span>](#fs)

-   [<span data-ttu-id="1af16-127">IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="1af16-127">IntellisenseTimeoutInSeconds</span></span>](#itis)

-   [<span data-ttu-id="1af16-128">MruCount</span><span class="sxs-lookup"><span data-stu-id="1af16-128">MruCount</span></span>](#mc)

-   [<span data-ttu-id="1af16-129">OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-129">OutputPaneBackgroundColor</span></span>](#opbc)

-   [<span data-ttu-id="1af16-130">OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-130">OutputPaneTextForegroundColor</span></span>](#optfc)

-   [<span data-ttu-id="1af16-131">OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-131">OutputPaneTextBackgroundColor</span></span>](#optbc)

-   [<span data-ttu-id="1af16-132">ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-132">ScriptPaneBackgroundColor</span></span>](#spbc)

-   [<span data-ttu-id="1af16-133">ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-133">ScriptPaneForegroundColor</span></span>](#spfc)

-   [<span data-ttu-id="1af16-134">SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="1af16-134">SelectedScriptPaneState</span></span>](#ssps)

-   [<span data-ttu-id="1af16-135">ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="1af16-135">ShowDefaultSnippets</span></span>](#sds)

-   [<span data-ttu-id="1af16-136">ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="1af16-136">ShowIntellisenseInConsolePane</span></span>](#siicp)

-   [<span data-ttu-id="1af16-137">ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="1af16-137">ShowIntellisenseInScriptPane</span></span>](#siisp)

-   [<span data-ttu-id="1af16-138">ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="1af16-138">ShowLineNumbers</span></span>](#sln)

-   [<span data-ttu-id="1af16-139">ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="1af16-139">ShowOutlining</span></span>](#so)

-   [<span data-ttu-id="1af16-140">ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="1af16-140">ShowToolBar</span></span>](#stb)

-   [<span data-ttu-id="1af16-141">ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="1af16-141">ShowWarningBeforeSavingOnRun</span></span>](#swbsor)

-   [<span data-ttu-id="1af16-142">ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="1af16-142">ShowWarningForDuplicateFiles</span></span>](#swfdf)

-   [<span data-ttu-id="1af16-143">TokenColors</span><span class="sxs-lookup"><span data-stu-id="1af16-143">TokenColors</span></span>](#tc)

-   [<span data-ttu-id="1af16-144">UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="1af16-144">UseEnterToSelectInConsolePaneIntellisense</span></span>](#uetsicpi)

-   [<span data-ttu-id="1af16-145">UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="1af16-145">UseEnterToSelectInScriptPaneIntellisense</span></span>](#uetsispi)

-   [<span data-ttu-id="1af16-146">UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="1af16-146">UseLocalHelp</span></span>](#ulh)

-   [<span data-ttu-id="1af16-147">VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-147">VerboseBackgroundColor</span></span>](#vbc)

-   [<span data-ttu-id="1af16-148">VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-148">VerboseForegroundColor</span></span>](#vfc)

-   [<span data-ttu-id="1af16-149">WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-149">WarningBackgroundColor</span></span>](#wbc)

-   [<span data-ttu-id="1af16-150">WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-150">WarningForegroundColor</span></span>](#wfc)

-   [<span data-ttu-id="1af16-151">XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="1af16-151">XmlTokenColors</span></span>](#xtc)

-   [<span data-ttu-id="1af16-152">缩放</span><span class="sxs-lookup"><span data-stu-id="1af16-152">Zoom</span></span>](#z)

## <a name="methods"></a><span data-ttu-id="1af16-153">方法</span><span class="sxs-lookup"><span data-stu-id="1af16-153">Methods</span></span>

###  <span data-ttu-id="1af16-154"><a name="rdctc"></a> RestoreDefaultConsoleTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="1af16-154"><a name="rdctc"></a> RestoreDefaultConsoleTokenColors\(\)</span></span>
  <span data-ttu-id="1af16-155">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="1af16-155">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1af16-156">还原“控制台”窗格中的标记颜色的默认值。</span><span class="sxs-lookup"><span data-stu-id="1af16-156">Restores the default values of the token colors in the Console pane.</span></span>

```
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = "red"
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

###  <span data-ttu-id="1af16-157"><a name="rd"></a> RestoreDefaults\(\)</span><span class="sxs-lookup"><span data-stu-id="1af16-157"><a name="rd"></a> RestoreDefaults\(\)</span></span>
  <span data-ttu-id="1af16-158">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="1af16-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1af16-159">还原“控制台”窗格中的所有选项设置的默认值。</span><span class="sxs-lookup"><span data-stu-id="1af16-159">Restores the default values of all options settings in the Console pane.</span></span> <span data-ttu-id="1af16-160">此外，它还重置提供标准复选框以防止再次显示消息的各种警告消息的行为。</span><span class="sxs-lookup"><span data-stu-id="1af16-160">It also resets the behavior of various warning messages that provide the standard check box to prevent the message from being shown again.</span></span>

```
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = "orange"
$psISE.Options.RestoreDefaults()
```

###  <span data-ttu-id="1af16-161"><a name="rdtc"></a> RestoreDefaultTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="1af16-161"><a name="rdtc"></a> RestoreDefaultTokenColors\(\)</span></span>
  <span data-ttu-id="1af16-162">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="1af16-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1af16-163">还原“脚本”窗格中的标记颜色的默认值。</span><span class="sxs-lookup"><span data-stu-id="1af16-163">Restores the default values of the token colors in the Script pane.</span></span>

```
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultTokenColors()
```

###  <span data-ttu-id="1af16-164"><a name="rdxtc"></a> RestoreDefaultXmlTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="1af16-164"><a name="rdxtc"></a> RestoreDefaultXmlTokenColors\(\)</span></span>
  <span data-ttu-id="1af16-165">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="1af16-165">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1af16-166">还原 Windows PowerShell ISE 中显示的 XML 元素的标记颜色的默认值。</span><span class="sxs-lookup"><span data-stu-id="1af16-166">Restores the default values of the token colors for XML elements that are displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="1af16-167">另请参阅 [XmlTokenColors](#xtc)。</span><span class="sxs-lookup"><span data-stu-id="1af16-167">Also see [XmlTokenColors](#xtc).</span></span>

```
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a><span data-ttu-id="1af16-168">“属性”</span><span class="sxs-lookup"><span data-stu-id="1af16-168">Properties</span></span>

###  <span data-ttu-id="1af16-169"><a name="asmi"></a> AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="1af16-169"><a name="asmi"></a> AutoSaveMinuteInterval</span></span>
  <span data-ttu-id="1af16-170">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="1af16-170">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1af16-171">通过 Windows PowerShell ISE 指定文件自动保存操作之间的分钟数。</span><span class="sxs-lookup"><span data-stu-id="1af16-171">Specifies the number of minutes between automatic save operations of your files by Windows PowerShell ISE.</span></span> <span data-ttu-id="1af16-172">默认值为 2 分钟。</span><span class="sxs-lookup"><span data-stu-id="1af16-172">The default value is 2 minutes.</span></span> <span data-ttu-id="1af16-173">该值是一个整数。</span><span class="sxs-lookup"><span data-stu-id="1af16-173">The value is an integer.</span></span>

```
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

###  <span data-ttu-id="1af16-174"><a name="cpbc"></a> CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-174"><a name="cpbc"></a> CommandPaneBackgroundColor</span></span>
  <span data-ttu-id="1af16-175">此功能存在于 Windows PowerShell ISE 2.0 中，但已在更高版本的 ISE 中删除或重命名。</span><span class="sxs-lookup"><span data-stu-id="1af16-175">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="1af16-176">对于更高版本，请参阅 [ConsolePaneBackgroundColor](#conpbc)。</span><span class="sxs-lookup"><span data-stu-id="1af16-176">For later versions, see [ConsolePaneBackgroundColor](#conpbc).</span></span>

 <span data-ttu-id="1af16-177">指定“命令”窗格的背景色。</span><span class="sxs-lookup"><span data-stu-id="1af16-177">Specifies the background color for the Command pane.</span></span> <span data-ttu-id="1af16-178">它是 **System.Windows.Media.Color** 类的实例。</span><span class="sxs-lookup"><span data-stu-id="1af16-178">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = "orange"
```

###  <span data-ttu-id="1af16-179"><a name="cpu"></a> CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="1af16-179"><a name="cpu"></a> CommandPaneUp</span></span>
  <span data-ttu-id="1af16-180">此功能存在于 Windows PowerShell ISE 2.0 中，但已在更高版本的 ISE 中删除或重命名。</span><span class="sxs-lookup"><span data-stu-id="1af16-180">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>

 <span data-ttu-id="1af16-181">指定“命令”窗格是否位于“输出”窗格上方。</span><span class="sxs-lookup"><span data-stu-id="1af16-181">Specifies whether the Command pane is located above the Output pane.</span></span>

```
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true

```

###  <span data-ttu-id="1af16-182"><a name="conpbc"></a> ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-182"><a name="conpbc"></a> ConsolePaneBackgroundColor</span></span>
  <span data-ttu-id="1af16-183">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="1af16-183">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1af16-184">指定“控制台”窗格的背景色。</span><span class="sxs-lookup"><span data-stu-id="1af16-184">Specifies the background color for the Console pane.</span></span> <span data-ttu-id="1af16-185">它是 **System.Windows.Media.Color** 类的实例。</span><span class="sxs-lookup"><span data-stu-id="1af16-185">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = "red"
```

###  <span data-ttu-id="1af16-186"><a name="conpfc"></a> ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-186"><a name="conpfc"></a> ConsolePaneForegroundColor</span></span>
  <span data-ttu-id="1af16-187">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="1af16-187">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1af16-188">指定“控制台”窗格中文本的前景色。</span><span class="sxs-lookup"><span data-stu-id="1af16-188">Specifies the foreground color of the text in the Console pane.</span></span>

```
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = "yellow"

```

###  <span data-ttu-id="1af16-189"><a name="conptbc"></a> ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-189"><a name="conptbc"></a> ConsolePaneTextBackgroundColor</span></span>
  <span data-ttu-id="1af16-190">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="1af16-190">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1af16-191">指定“控制台”窗格中文本的背景色。</span><span class="sxs-lookup"><span data-stu-id="1af16-191">Specifies the background color of the text in the Console pane.</span></span>

```
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = "pink"
```

###  <span data-ttu-id="1af16-192"><a name="contc"></a> ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="1af16-192"><a name="contc"></a> ConsoleTokenColors</span></span>
  <span data-ttu-id="1af16-193">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="1af16-193">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1af16-194">指定 Windows PowerShell ISE“控制台”窗格中 IntelliSense 标记的颜色。</span><span class="sxs-lookup"><span data-stu-id="1af16-194">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Console pane.</span></span> <span data-ttu-id="1af16-195">此属性是一个包含标记类型的名称/值对和“控制台”窗格颜色的字典对象。</span><span class="sxs-lookup"><span data-stu-id="1af16-195">This property is a dictionary object that contains name/value pairs of token types and colors for the Console pane.</span></span> <span data-ttu-id="1af16-196">若要更改“脚本”窗格中 IntelliSense 标记的颜色，请参阅 [TokenColors](#tc)。</span><span class="sxs-lookup"><span data-stu-id="1af16-196">To change the colors of the IntelliSense tokens in the Script pane, see [TokenColors](#tc).</span></span> <span data-ttu-id="1af16-197">若要将颜色重置为默认值，请参阅 [RestoreDefaultConsoleTokenColors()](#rdctc)。</span><span class="sxs-lookup"><span data-stu-id="1af16-197">To reset the colors to the default values, see [RestoreDefaultConsoleTokenColors()](#rdctc).</span></span> <span data-ttu-id="1af16-198">可以针对以下项设置标记颜色：Attribute、Command、CommandArgument、CommandParameter、Comment、GroupEnd、GroupStart、Keyword、LineContinuation、LoopLabel、Member、NewLine、Number、Operator、Position、StatementSeparator、String、Type、Unknown、Variable。</span><span class="sxs-lookup"><span data-stu-id="1af16-198">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = "magenta"

```

###  <span data-ttu-id="1af16-199"><a name="dbc"></a> DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-199"><a name="dbc"></a> DebugBackgroundColor</span></span>
  <span data-ttu-id="1af16-200">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="1af16-200">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1af16-201">指定“控制台”窗格中显示的调试文本的背景色。</span><span class="sxs-lookup"><span data-stu-id="1af16-201">Specifies the background color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="1af16-202">它是 **System.Windows.Media.Color** 类的实例。</span><span class="sxs-lookup"><span data-stu-id="1af16-202">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor ='#0000FF'
```

###  <span data-ttu-id="1af16-203"><a name="dfc"></a> DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-203"><a name="dfc"></a> DebugForegroundColor</span></span>
  <span data-ttu-id="1af16-204">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="1af16-204">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1af16-205">指定“控制台”窗格中显示的调试文本的前景色。</span><span class="sxs-lookup"><span data-stu-id="1af16-205">Specifies the foreground color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="1af16-206">它是 **System.Windows.Media.Color** 类的实例。</span><span class="sxs-lookup"><span data-stu-id="1af16-206">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor ="yellow"
```

###  <span data-ttu-id="1af16-207"><a name="do"></a> DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="1af16-207"><a name="do"></a> DefaultOptions</span></span>
  <span data-ttu-id="1af16-208">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="1af16-208">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1af16-209">指定使用重置方法时要使用的默认值的属性集合。</span><span class="sxs-lookup"><span data-stu-id="1af16-209">A collection of properties that specify the default values to be used when the Reset methods are used.</span></span>

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

###  <span data-ttu-id="1af16-210"><a name="ebc"></a> ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-210"><a name="ebc"></a> ErrorBackgroundColor</span></span>
  <span data-ttu-id="1af16-211">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="1af16-211">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1af16-212">指定“控制台”窗格中显示的错误文本的背景色。</span><span class="sxs-lookup"><span data-stu-id="1af16-212">Specifies the background color for error text that appears in the Console pane.</span></span> <span data-ttu-id="1af16-213">它是 **System.Windows.Media.Color** 类的实例。</span><span class="sxs-lookup"><span data-stu-id="1af16-213">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor="black"
```

###  <span data-ttu-id="1af16-214"><a name="efc"></a> ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-214"><a name="efc"></a> ErrorForegroundColor</span></span>
  <span data-ttu-id="1af16-215">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="1af16-215">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1af16-216">指定“控制台”窗格中显示的错误文本的前景色。</span><span class="sxs-lookup"><span data-stu-id="1af16-216">Specifies the foreground color for error text that appears in the Console pane.</span></span> <span data-ttu-id="1af16-217">它是 **System.Windows.Media.Color** 类的实例。</span><span class="sxs-lookup"><span data-stu-id="1af16-217">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor ="green"
```

###  <span data-ttu-id="1af16-218"><a name="fn"></a> FontName</span><span class="sxs-lookup"><span data-stu-id="1af16-218"><a name="fn"></a> FontName</span></span>
  <span data-ttu-id="1af16-219">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="1af16-219">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1af16-220">指定“脚本”窗格和“控制台”窗格中当前使用的字体名称。</span><span class="sxs-lookup"><span data-stu-id="1af16-220">Specifies the font name currently in use in both the Script pane and the Console pane.</span></span>

```
# Changes the font used in both panes.
$psISE.Options.FontName = "courier new"
```

###  <span data-ttu-id="1af16-221"><a name="fs"></a> FontSize</span><span class="sxs-lookup"><span data-stu-id="1af16-221"><a name="fs"></a> FontSize</span></span>
  <span data-ttu-id="1af16-222">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="1af16-222">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1af16-223">以整数形式指定字体大小。</span><span class="sxs-lookup"><span data-stu-id="1af16-223">Specifies the font size as an integer.</span></span> <span data-ttu-id="1af16-224">在“脚本”窗格、“命令”窗格以及“输出”窗格中使用。</span><span class="sxs-lookup"><span data-stu-id="1af16-224">It is used in the Script pane, the Command pane, and the Output pane.</span></span> <span data-ttu-id="1af16-225">值的有效范围是 8 至 32。</span><span class="sxs-lookup"><span data-stu-id="1af16-225">The valid range of values is 8 through 32.</span></span>

```
# Changes the font size in all panes.
$psISE.Options.FontSize = 20

```

###  <span data-ttu-id="1af16-226"><a name="itis"></a> IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="1af16-226"><a name="itis"></a> IntellisenseTimeoutInSeconds</span></span>
  <span data-ttu-id="1af16-227">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="1af16-227">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1af16-228">指定 IntelliSense 用来尝试解决当前所键入文本的秒数。</span><span class="sxs-lookup"><span data-stu-id="1af16-228">Specifies the number of seconds that IntelliSense uses to try to resolve the currently typed text.</span></span> <span data-ttu-id="1af16-229">该秒数之后，IntelliSense 将会超时，并使你能够继续键入。</span><span class="sxs-lookup"><span data-stu-id="1af16-229">After this number of seconds, IntelliSense times out and enables you to continue typing.</span></span> <span data-ttu-id="1af16-230">默认值是 3 秒。</span><span class="sxs-lookup"><span data-stu-id="1af16-230">The default value is 3 seconds.</span></span> <span data-ttu-id="1af16-231">该值是一个整数。</span><span class="sxs-lookup"><span data-stu-id="1af16-231">The value is an integer.</span></span>

```
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

###  <span data-ttu-id="1af16-232"><a name="mc"></a> MruCount</span><span class="sxs-lookup"><span data-stu-id="1af16-232"><a name="mc"></a> MruCount</span></span>
  <span data-ttu-id="1af16-233">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="1af16-233">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1af16-234">指定 Windows PowerShell ISE 跟踪并在**“文件打开”**菜单底部显示的最近打开的文件数。</span><span class="sxs-lookup"><span data-stu-id="1af16-234">Specifies the number of recently opened files that Windows PowerShell ISE tracks and displays at the bottom of the **File Open** menu.</span></span> <span data-ttu-id="1af16-235">默认值为 10。</span><span class="sxs-lookup"><span data-stu-id="1af16-235">The default value is 10.</span></span> <span data-ttu-id="1af16-236">该值是一个整数。</span><span class="sxs-lookup"><span data-stu-id="1af16-236">The value is an integer.</span></span>

```
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

###  <span data-ttu-id="1af16-237"><a name="opbc"></a> OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-237"><a name="opbc"></a> OutputPaneBackgroundColor</span></span>
  <span data-ttu-id="1af16-238">此功能存在于 Windows PowerShell ISE 2.0 中，但已在更高版本的 ISE 中删除或重命名。</span><span class="sxs-lookup"><span data-stu-id="1af16-238">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="1af16-239">对于更高版本，请参阅 [ConsolePaneBackgroundColor](#conpbc)。</span><span class="sxs-lookup"><span data-stu-id="1af16-239">For later versions, see [ConsolePaneBackgroundColor](#conpbc).</span></span>

 <span data-ttu-id="1af16-240">读/写属性，可获取或设置“输出”窗格本身的背景色。</span><span class="sxs-lookup"><span data-stu-id="1af16-240">The read/write property that gets or sets the background color for the Output pane itself.</span></span> <span data-ttu-id="1af16-241">它是 **System.Windows.Media.Color** 类的实例。</span><span class="sxs-lookup"><span data-stu-id="1af16-241">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = "gold"

```

###  <span data-ttu-id="1af16-242"><a name="optfc"></a> OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-242"><a name="optfc"></a> OutputPaneTextForegroundColor</span></span>
  <span data-ttu-id="1af16-243">此功能存在于 Windows PowerShell ISE 2.0 中，但已在更高版本的 ISE 中删除或重命名。</span><span class="sxs-lookup"><span data-stu-id="1af16-243">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="1af16-244">对于更高版本，请参阅 [ConsolePaneForegroundColor](#conpfc)。</span><span class="sxs-lookup"><span data-stu-id="1af16-244">For later versions, see [ConsolePaneForegroundColor](#conpfc).</span></span>

 <span data-ttu-id="1af16-245">读/写属性，可更改 Windows PowerShell ISE 2.0 中“输出”窗格中的文本前景色。</span><span class="sxs-lookup"><span data-stu-id="1af16-245">The read/write property that changes the foreground color of the text in the Output pane in Windows PowerShell ISE 2.0.</span></span>

```
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = "blue"

```

###  <span data-ttu-id="1af16-246"><a name="optbc"></a> OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-246"><a name="optbc"></a> OutputPaneTextBackgroundColor</span></span>
  <span data-ttu-id="1af16-247">此功能存在于 Windows PowerShell ISE 2.0 中，但已在更高版本的 ISE 中删除或重命名。</span><span class="sxs-lookup"><span data-stu-id="1af16-247">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="1af16-248">对于更高版本，请参阅 [ConsolePaneTextBackgroundColor](#conptbc)。</span><span class="sxs-lookup"><span data-stu-id="1af16-248">For later versions, see [ConsolePaneTextBackgroundColor](#conptbc).</span></span>

 <span data-ttu-id="1af16-249">读/写属性，可更改“输出”窗格中的文本背景色。</span><span class="sxs-lookup"><span data-stu-id="1af16-249">The read/write property that changes the background color of the text in the Output pane.</span></span>

```
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = "pink"
```

###  <span data-ttu-id="1af16-250"><a name="spbc"></a> ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-250"><a name="spbc"></a> ScriptPaneBackgroundColor</span></span>
  <span data-ttu-id="1af16-251">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="1af16-251">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1af16-252">读/写属性，可获取或设置文件的背景色。</span><span class="sxs-lookup"><span data-stu-id="1af16-252">The read/write property that gets or sets the background color for files.</span></span> <span data-ttu-id="1af16-253">它是 **System.Windows.Media.Color** 类的实例。</span><span class="sxs-lookup"><span data-stu-id="1af16-253">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```

# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = ”yellow”

```

###  <span data-ttu-id="1af16-254"><a name="spfc"></a> ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-254"><a name="spfc"></a> ScriptPaneForegroundColor</span></span>
  <span data-ttu-id="1af16-255">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="1af16-255">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1af16-256">读/写属性，可获取或设置“脚本”窗格中非脚本文件的前景色。</span><span class="sxs-lookup"><span data-stu-id="1af16-256">The read/write property that gets or sets the foreground color for non-script files in the Script pane.</span></span>
<span data-ttu-id="1af16-257">若要设置脚本文件的前景色，请使用 [TokenColors](The-ISEOptions-Object.md#tc) 属性。</span><span class="sxs-lookup"><span data-stu-id="1af16-257">To set the foreground color for script files, use the [TokenColors](The-ISEOptions-Object.md#tc) property.</span></span>

```
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = "green"

```

###  <span data-ttu-id="1af16-258"><a name="ssps"></a> SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="1af16-258"><a name="ssps"></a> SelectedScriptPaneState</span></span>
  <span data-ttu-id="1af16-259">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="1af16-259">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1af16-260">读/写属性，可获取或设置“脚本”窗格在显示屏上的位置。</span><span class="sxs-lookup"><span data-stu-id="1af16-260">The read/write property that gets or sets the position of the Script pane on the display.</span></span> <span data-ttu-id="1af16-261">字符串可以是“最大化”、“顶部”或“右侧”。</span><span class="sxs-lookup"><span data-stu-id="1af16-261">The string can be either "Maximized", "Top", or "Right".</span></span>

```
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = "Top"
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = "Right"
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = "Maximized"

```

###  <span data-ttu-id="1af16-262"><a name="sds"></a> ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="1af16-262"><a name="sds"></a> ShowDefaultSnippets</span></span>
  <span data-ttu-id="1af16-263">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="1af16-263">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1af16-264">指定代码段的 **CTRL + J** 列表是否包括Windows PowerShell 中包含的初学者套件。</span><span class="sxs-lookup"><span data-stu-id="1af16-264">Specifies whether the **CTRL+J** list of snippets includes the starter set that is included in Windows PowerShell.</span></span> <span data-ttu-id="1af16-265">当设置为 **$false** 时，只有用户定义的代码段显示在 **CTRL + J** 列表中。</span><span class="sxs-lookup"><span data-stu-id="1af16-265">When set to **$false**, only user-defined snippets appear in the **CTRL+J** list.</span></span> <span data-ttu-id="1af16-266">默认值为 **$true**。</span><span class="sxs-lookup"><span data-stu-id="1af16-266">The default value is **$true**.</span></span>

```
# Hide the default snippets from the CTRL+J list.
$psISe.Options.ShowDefaultSnippets = $false
```

###  <span data-ttu-id="1af16-267"><a name="siicp"></a> ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="1af16-267"><a name="siicp"></a> ShowIntellisenseInConsolePane</span></span>
  <span data-ttu-id="1af16-268">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="1af16-268">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1af16-269">指定 IntelliSense 是否在“控制台”窗格中提供语法、参数和值建议。</span><span class="sxs-lookup"><span data-stu-id="1af16-269">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Console pane.</span></span> <span data-ttu-id="1af16-270">默认值为 **$true**。</span><span class="sxs-lookup"><span data-stu-id="1af16-270">The default value is **$true**.</span></span>

```
# Turn off IntelliSense in the console pane.
$psISe.Options.ShowIntellisenseInConsolePane = $false
```

###  <span data-ttu-id="1af16-271"><a name="siisp"></a> ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="1af16-271"><a name="siisp"></a> ShowIntellisenseInScriptPane</span></span>
  <span data-ttu-id="1af16-272">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="1af16-272">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1af16-273">指定 IntelliSense 是否在“脚本”窗格中提供语法、参数和值建议。</span><span class="sxs-lookup"><span data-stu-id="1af16-273">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Script pane.</span></span> <span data-ttu-id="1af16-274">默认值为 **$true**。</span><span class="sxs-lookup"><span data-stu-id="1af16-274">The default value is **$true**.</span></span>

```
# Turn off IntelliSense in the Script pane.
$psISe.Options.ShowIntellisenseInScriptPane = $false
```

###  <span data-ttu-id="1af16-275"><a name="sln"></a> ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="1af16-275"><a name="sln"></a> ShowLineNumbers</span></span>
  <span data-ttu-id="1af16-276">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="1af16-276">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1af16-277">指定“脚本”窗格是否在左边空白处显示行号。</span><span class="sxs-lookup"><span data-stu-id="1af16-277">Specifies whether the Script pane displays line numbers in the left margin.</span></span> <span data-ttu-id="1af16-278">默认值为 **$true**。</span><span class="sxs-lookup"><span data-stu-id="1af16-278">The default value is **$true**.</span></span>

```
# Turn off line numbers in the Script pane.
$psISe.Options.ShowLineNumbers = $false
```

###  <span data-ttu-id="1af16-279"><a name="so"></a> ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="1af16-279"><a name="so"></a> ShowOutlining</span></span>
  <span data-ttu-id="1af16-280">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="1af16-280">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1af16-281">指定“脚本”窗格中是否在左边空白处代码段的旁边显示可展开和折叠的括号。</span><span class="sxs-lookup"><span data-stu-id="1af16-281">Specifies whether the Script pane displays expandable and collapsible brackets next to sections of code in the left margin.</span></span> <span data-ttu-id="1af16-282">如果显示，你可以单击文本块旁边的减号 \(-\) 图标将其折叠起来，或单击加号 \(+\) 图标展开文本块。</span><span class="sxs-lookup"><span data-stu-id="1af16-282">When they are displayed, you can click the minus \(-\) icons next to a block of text to collapse it or click the plus \(+\) icon to expand a block of text.</span></span> <span data-ttu-id="1af16-283">默认值为 **$true**。</span><span class="sxs-lookup"><span data-stu-id="1af16-283">The default value is **$true**.</span></span>

```
# Turn off outlining in the Script pane.
$psISe.Options.ShowOutlining = $false
```

###  <span data-ttu-id="1af16-284"><a name="stb"></a> ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="1af16-284"><a name="stb"></a> ShowToolBar</span></span>
  <span data-ttu-id="1af16-285">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="1af16-285">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1af16-286">指定 ISE 工具栏是否显示在 Windows PowerShell ISE 窗口的顶部。</span><span class="sxs-lookup"><span data-stu-id="1af16-286">Specifies whether the ISE toolbar appears at the top of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="1af16-287">默认值为 **$true**。</span><span class="sxs-lookup"><span data-stu-id="1af16-287">The default value is **$true**.</span></span>

```
# Show the toolbar.
$psISe.Options.ShowToolBar = $true
```

###  <span data-ttu-id="1af16-288"><a name="swbsor"></a> ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="1af16-288"><a name="swbsor"></a> ShowWarningBeforeSavingOnRun</span></span>
  <span data-ttu-id="1af16-289">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="1af16-289">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1af16-290">指定在运行脚本之前自动保存该脚本是否显示警告消息。</span><span class="sxs-lookup"><span data-stu-id="1af16-290">Specifies whether a warning message appears when a script is saved automatically before it is run.</span></span> <span data-ttu-id="1af16-291">默认值为 **$true**。</span><span class="sxs-lookup"><span data-stu-id="1af16-291">The default value is **$true**.</span></span>

```
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun=$true

```

###  <span data-ttu-id="1af16-292"><a name="swfdf"></a> ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="1af16-292"><a name="swfdf"></a> ShowWarningForDuplicateFiles</span></span>
  <span data-ttu-id="1af16-293">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="1af16-293">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1af16-294">指定在不同 PowerShell 选项卡中打开同一个文件时是否显示警告消息。</span><span class="sxs-lookup"><span data-stu-id="1af16-294">Specifies whether a warning message appears when the same file is opened in different PowerShell tabs.</span></span> <span data-ttu-id="1af16-295">如果设置为 **$true**，在多个选项卡打开同一个文件将显示此消息：“已在另一个 Windows PowerShell 选项卡中打开此文件的副本。</span><span class="sxs-lookup"><span data-stu-id="1af16-295">If set to **$true**, to open the same file in multiple tabs displays this message: "A copy of this file is open in another Windows PowerShell tab.</span></span> <span data-ttu-id="1af16-296">对此文件所做的更改将影响所有打开的副本。”</span><span class="sxs-lookup"><span data-stu-id="1af16-296">Changes made to this file will affect all open copies."</span></span> <span data-ttu-id="1af16-297">默认值为 **$true**。</span><span class="sxs-lookup"><span data-stu-id="1af16-297">The default value is **$true**.</span></span>

```
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true

```

###  <span data-ttu-id="1af16-298"><a name="tc"></a> TokenColors</span><span class="sxs-lookup"><span data-stu-id="1af16-298"><a name="tc"></a> TokenColors</span></span>
  <span data-ttu-id="1af16-299">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="1af16-299">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1af16-300">指定 Windows PowerShell ISE“脚本”窗格中 IntelliSense 标记的颜色。</span><span class="sxs-lookup"><span data-stu-id="1af16-300">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Script pane.</span></span> <span data-ttu-id="1af16-301">此属性是一个包含标记类型的名称/值对和“脚本”窗格颜色的字典对象。</span><span class="sxs-lookup"><span data-stu-id="1af16-301">This property is a dictionary object that contains name/value pairs of token types and colors for the Script pane.</span></span> <span data-ttu-id="1af16-302">若要更改“脚本”窗格中 IntelliSense 标记的颜色，请参阅 [ConsoleTokenColors](#contc)。</span><span class="sxs-lookup"><span data-stu-id="1af16-302">To change the colors of the IntelliSense tokens in the Console pane, see [ConsoleTokenColors](#contc).</span></span> <span data-ttu-id="1af16-303">若要将颜色重置为默认值，请参阅 [RestoreDefaultTokenColors()](#rdtc)。</span><span class="sxs-lookup"><span data-stu-id="1af16-303">To reset the colors to the default values, see [RestoreDefaultTokenColors()](#rdtc).</span></span> <span data-ttu-id="1af16-304">可以针对以下项设置标记颜色：Attribute、Command、CommandArgument、CommandParameter、Comment、GroupEnd、GroupStart、Keyword、LineContinuation、LoopLabel、Member、NewLine、Number、Operator、Position、StatementSeparator、String、Type、Unknown、Variable。</span><span class="sxs-lookup"><span data-stu-id="1af16-304">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"

```

###  <span data-ttu-id="1af16-305"><a name="uetsicpi"></a> UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="1af16-305"><a name="uetsicpi"></a> UseEnterToSelectInConsolePaneIntellisense</span></span>
  <span data-ttu-id="1af16-306">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="1af16-306">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1af16-307">指定是否可以使用 Enter 键选择 IntelliSense 在“控制台”窗格中提供的选项。</span><span class="sxs-lookup"><span data-stu-id="1af16-307">Specifies whether you can use the Enter key to select an IntelliSense provided option in the Console pane.</span></span> <span data-ttu-id="1af16-308">默认值为 **$true**。</span><span class="sxs-lookup"><span data-stu-id="1af16-308">The default value is **$true**.</span></span>

```
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$false

```

###  <span data-ttu-id="1af16-309"><a name="uetsispi"></a> UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="1af16-309"><a name="uetsispi"></a> UseEnterToSelectInScriptPaneIntellisense</span></span>
  <span data-ttu-id="1af16-310">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="1af16-310">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1af16-311">指定是否可以使用 Enter 键选择 IntelliSense 在“脚本”窗格中提供的选项。</span><span class="sxs-lookup"><span data-stu-id="1af16-311">Specifies whether you can use the Enter key to select an IntelliSense-provided option in the Script pane.</span></span> <span data-ttu-id="1af16-312">默认值为 **$true**。</span><span class="sxs-lookup"><span data-stu-id="1af16-312">The default value is **$true**.</span></span>

```
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$true

```

###  <span data-ttu-id="1af16-313"><a name="ulh"></a> UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="1af16-313"><a name="ulh"></a> UseLocalHelp</span></span>
  <span data-ttu-id="1af16-314">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="1af16-314">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1af16-315">指定将光标置于关键字中并按 F1 时是显示本地安装的帮助还是联机 TechNet 库帮助。</span><span class="sxs-lookup"><span data-stu-id="1af16-315">Specifies whether the locally installed Help or the online TechNet Library Help appears when you press F1 with the cursor positioned in a keyword.</span></span> <span data-ttu-id="1af16-316">如果设置为 **$true**，那么弹出窗口会显示本地安装的帮助中的内容。</span><span class="sxs-lookup"><span data-stu-id="1af16-316">If set to **$true**, then a pop-up window shows content from the locally installed Help.</span></span> <span data-ttu-id="1af16-317">可以通过运行 `Update-Help` 命令安装帮助文件。</span><span class="sxs-lookup"><span data-stu-id="1af16-317">You can install the Help files by running the `Update-Help` command.</span></span> <span data-ttu-id="1af16-318">如果设置为 **$false**，则你的浏览器会在 TechNet 库中打开一个页面。</span><span class="sxs-lookup"><span data-stu-id="1af16-318">If set to **$false**, then your browser opens to a page in the TechNet Library.</span></span>

```
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp=$false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp=$true

```

###  <span data-ttu-id="1af16-319"><a name="vbc"></a> VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-319"><a name="vbc"></a> VerboseBackgroundColor</span></span>
  <span data-ttu-id="1af16-320">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="1af16-320">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1af16-321">指定“控制台”窗格中显示的详细文本的背景色。</span><span class="sxs-lookup"><span data-stu-id="1af16-321">Specifies the background color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="1af16-322">它是 **System.Windows.Media.Color** 对象。</span><span class="sxs-lookup"><span data-stu-id="1af16-322">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

###  <span data-ttu-id="1af16-323"><a name="vfc"></a> VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-323"><a name="vfc"></a> VerboseForegroundColor</span></span>
  <span data-ttu-id="1af16-324">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="1af16-324">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1af16-325">指定“控制台”窗格中显示的详细文本的前景色。</span><span class="sxs-lookup"><span data-stu-id="1af16-325">Specifies the foreground color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="1af16-326">它是 **System.Windows.Media.Color** 对象。</span><span class="sxs-lookup"><span data-stu-id="1af16-326">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor =”yellow”
```

###  <span data-ttu-id="1af16-327"><a name="wbc"></a> WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-327"><a name="wbc"></a> WarningBackgroundColor</span></span>
  <span data-ttu-id="1af16-328">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="1af16-328">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1af16-329">指定“控制台”窗格中显示的警告文本的背景色。</span><span class="sxs-lookup"><span data-stu-id="1af16-329">Specifies the background color for warning text that appears in the Console pane.</span></span> <span data-ttu-id="1af16-330">它是 **System.Windows.Media.Color** 对象。</span><span class="sxs-lookup"><span data-stu-id="1af16-330">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor ='#0000FF'
```

###  <span data-ttu-id="1af16-331"><a name="wfc"></a> WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="1af16-331"><a name="wfc"></a> WarningForegroundColor</span></span>
  <span data-ttu-id="1af16-332">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="1af16-332">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="1af16-333">指定“输出”窗格中显示的警告文本的前景色。</span><span class="sxs-lookup"><span data-stu-id="1af16-333">Specifies the foreground color for warning text that appears in the Output pane.</span></span> <span data-ttu-id="1af16-334">它是 **System.Windows.Media.Color** 对象。</span><span class="sxs-lookup"><span data-stu-id="1af16-334">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor =”yellow”
```

###  <span data-ttu-id="1af16-335"><a name="xtc"></a> XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="1af16-335"><a name="xtc"></a> XmlTokenColors</span></span>
  <span data-ttu-id="1af16-336">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="1af16-336">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1af16-337">指定包含标记类型的名称/值对以及 Windows PowerShell ISE 中显示的 XML 内容颜色的字典对象。</span><span class="sxs-lookup"><span data-stu-id="1af16-337">Specifies a dictionary object that contains name/value pairs of token types and colors for XML content that is displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="1af16-338">可以针对以下项设置标记颜色：Attribute、Command、CommandArgument、CommandParameter、Comment、GroupEnd、GroupStart、Keyword、LineContinuation、LoopLabel、Member、NewLine、Number、Operator、Position、StatementSeparator、String、Type、Unknown、Variable。</span><span class="sxs-lookup"><span data-stu-id="1af16-338">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span> <span data-ttu-id="1af16-339">另请参阅 [RestoreDefaultXmlTokenColors()](#rdxtc)。</span><span class="sxs-lookup"><span data-stu-id="1af16-339">Also see [RestoreDefaultXmlTokenColors()](#rdxtc).</span></span>

```
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = "green"
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = "magenta"

```

###  <span data-ttu-id="1af16-340"><a name="z"></a>缩放</span><span class="sxs-lookup"><span data-stu-id="1af16-340"><a name="z"></a> Zoom</span></span>
  <span data-ttu-id="1af16-341">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="1af16-341">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="1af16-342">在“控制台”和“脚本”窗格中指定文本的相对大小。</span><span class="sxs-lookup"><span data-stu-id="1af16-342">Specifies the relative size of text in both the Console and Script panes.</span></span> <span data-ttu-id="1af16-343">默认值为 100。</span><span class="sxs-lookup"><span data-stu-id="1af16-343">The default value is 100.</span></span> <span data-ttu-id="1af16-344">较小的值会导致 Windows PowerShell ISE 中的文本显示得较小，数字越大会导致文本显示得越大。</span><span class="sxs-lookup"><span data-stu-id="1af16-344">Smaller values cause the text in Windows PowerShell ISE to appear smaller while larger numbers cause text to appear larger.</span></span> <span data-ttu-id="1af16-345">该值为一个整数，范围为 20 到 400。</span><span class="sxs-lookup"><span data-stu-id="1af16-345">The value is an integer that ranges from 20 to 400.</span></span>

```
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a><span data-ttu-id="1af16-346">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1af16-346">See Also</span></span>
- [<span data-ttu-id="1af16-347">Windows PowerShell ISE 脚本对象模型</span><span class="sxs-lookup"><span data-stu-id="1af16-347">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="1af16-348">Windows PowerShell ISE 对象模型参考</span><span class="sxs-lookup"><span data-stu-id="1af16-348">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)

