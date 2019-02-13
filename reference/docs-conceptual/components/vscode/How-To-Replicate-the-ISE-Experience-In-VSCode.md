---
title: 如何复制 Visual Studio Code 中的 ISE 体验
description: 如何复制 Visual Studio Code 中的 ISE 体验
ms.date: 08/06/2018
ms.openlocfilehash: 983da850c13d72bcdc7b2d33970c6e9e06b3d869
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "55677304"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="288cb-103">如何复制 Visual Studio Code 中的 ISE 体验</span><span class="sxs-lookup"><span data-stu-id="288cb-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="288cb-104">适用于 VSCode 的 PowerShell 扩展不会查找在 PowerShell ISE 的完整功能奇偶一致性，而有功能到位，才能使 VSCode 体验更自然的 ISE 的用户。</span><span class="sxs-lookup"><span data-stu-id="288cb-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="288cb-105">本文档会尝试将在 VSCode 以使用户体验更熟悉相比在 ISE 中可配置的列表设置。</span><span class="sxs-lookup"><span data-stu-id="288cb-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="288cb-106">键绑定</span><span class="sxs-lookup"><span data-stu-id="288cb-106">Key bindings</span></span>

| <span data-ttu-id="288cb-107">功能</span><span class="sxs-lookup"><span data-stu-id="288cb-107">Function</span></span>                              | <span data-ttu-id="288cb-108">ISE 绑定</span><span class="sxs-lookup"><span data-stu-id="288cb-108">ISE Binding</span></span>                  | <span data-ttu-id="288cb-109">VSCode 绑定</span><span class="sxs-lookup"><span data-stu-id="288cb-109">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="288cb-110">中断并中断调试器</span><span class="sxs-lookup"><span data-stu-id="288cb-110">Interrupt and break debugger</span></span>          | <span data-ttu-id="288cb-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="288cb-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="288cb-112"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="288cb-112"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="288cb-113">执行当前突出显示行/文本</span><span class="sxs-lookup"><span data-stu-id="288cb-113">Execute current line/highlighted text</span></span> | <span data-ttu-id="288cb-114"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="288cb-114"><kbd>F8</kbd></span></span>                | <span data-ttu-id="288cb-115"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="288cb-115"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="288cb-116">列表可用代码段</span><span class="sxs-lookup"><span data-stu-id="288cb-116">List available snippets</span></span>               | <span data-ttu-id="288cb-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="288cb-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="288cb-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="288cb-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="288cb-119">自定义键绑定</span><span class="sxs-lookup"><span data-stu-id="288cb-119">Custom Key bindings</span></span>

<span data-ttu-id="288cb-120">你可以[配置你自己的键绑定](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)也 VSCode 中。</span><span class="sxs-lookup"><span data-stu-id="288cb-120">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="tab-completion"></a><span data-ttu-id="288cb-121">Tab 自动补全</span><span class="sxs-lookup"><span data-stu-id="288cb-121">Tab completion</span></span>

<span data-ttu-id="288cb-122">若要启用更类似于 ISE 的 tab 自动补全，请添加此设置：</span><span class="sxs-lookup"><span data-stu-id="288cb-122">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> <span data-ttu-id="288cb-123">此设置已添加到 VSCode 直接 （而不是扩展中）。</span><span class="sxs-lookup"><span data-stu-id="288cb-123">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="288cb-124">其行为由 VSCode 直接确定，无法更改的扩展插件。</span><span class="sxs-lookup"><span data-stu-id="288cb-124">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="288cb-125">在控制台上执行时没有焦点</span><span class="sxs-lookup"><span data-stu-id="288cb-125">No focus on console when executing</span></span>

<span data-ttu-id="288cb-126">若要在使用执行时，在编辑器中保持焦点<kbd>F8</kbd>:</span><span class="sxs-lookup"><span data-stu-id="288cb-126">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

<span data-ttu-id="288cb-127">默认值是`true`用于可访问性目的。</span><span class="sxs-lookup"><span data-stu-id="288cb-127">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="288cb-128">不要在启动时开始集成的控制台</span><span class="sxs-lookup"><span data-stu-id="288cb-128">Don't start integrated console on startup</span></span>

<span data-ttu-id="288cb-129">若要在启动时停止集成的控制台，请设置：</span><span class="sxs-lookup"><span data-stu-id="288cb-129">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="288cb-130">后台 PowerShell 进程仍将启动，因为它提供 IntelliSense，脚本分析、 符号导航，等等。但不会显示在控制台中。</span><span class="sxs-lookup"><span data-stu-id="288cb-130">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="288cb-131">假设文件默认情况下是 PowerShell</span><span class="sxs-lookup"><span data-stu-id="288cb-131">Assume files are PowerShell by default</span></span>

<span data-ttu-id="288cb-132">若要使新/无标题文件，因为 PowerShell 默认情况下注册：</span><span class="sxs-lookup"><span data-stu-id="288cb-132">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a><span data-ttu-id="288cb-133">配色方案</span><span class="sxs-lookup"><span data-stu-id="288cb-133">Color scheme</span></span>

<span data-ttu-id="288cb-134">有大量 ISE 主题适用于 VSCode 将看起来更像 ISE 编辑器。</span><span class="sxs-lookup"><span data-stu-id="288cb-134">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="288cb-135">在中[命令面板]类型`theme`若要获取`Preferences: Color Theme`然后按<kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="288cb-135">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="288cb-136">在下拉列表中，选择`PowerShell ISE`。</span><span class="sxs-lookup"><span data-stu-id="288cb-136">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="288cb-137">可以使用在设置中设置此主题：</span><span class="sxs-lookup"><span data-stu-id="288cb-137">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a><span data-ttu-id="288cb-138">PowerShell 命令资源管理器</span><span class="sxs-lookup"><span data-stu-id="288cb-138">PowerShell Command Explorer</span></span>

<span data-ttu-id="288cb-139">衷心感谢的工作成果[ @corbob ](https://github.com/corbob)，PowerShell 扩展具有其自己命令资源管理器的开始部分。</span><span class="sxs-lookup"><span data-stu-id="288cb-139">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="288cb-140">在中[命令面板]，输入`PowerShell Command Explorer`然后按<kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="288cb-140">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="288cb-141">在 ISE 中打开</span><span class="sxs-lookup"><span data-stu-id="288cb-141">Open in the ISE</span></span>

<span data-ttu-id="288cb-142">如果您会得到想是否仍要在 ISE 中打开一个文件，则可以使用<kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>。</span><span class="sxs-lookup"><span data-stu-id="288cb-142">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="288cb-143">其他资源</span><span class="sxs-lookup"><span data-stu-id="288cb-143">Other resources</span></span>

- <span data-ttu-id="288cb-144">具有 4sysops[优秀文章](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/)配置 VSCode 是更像是在 ISE。</span><span class="sxs-lookup"><span data-stu-id="288cb-144">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="288cb-145">具有 Mike F Robbins[优秀文章](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/)设置 VSCode。</span><span class="sxs-lookup"><span data-stu-id="288cb-145">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="288cb-146">了解 PowerShell 具有[出色写入](https://www.learnpwsh.com/setup-vs-code-for-powershell/)获取 VSCode 的 PowerShell 安装程序。</span><span class="sxs-lookup"><span data-stu-id="288cb-146">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="288cb-147">更多设置</span><span class="sxs-lookup"><span data-stu-id="288cb-147">More settings</span></span>

<span data-ttu-id="288cb-148">如果您知道的更多方式进行 VSCode 感觉更熟悉的 ISE 用户，参与此文档。如果要查找的兼容性配置但找不到任何方式来启用它，请[提出问题](https://github.com/PowerShell/vscode-powershell/issues/new/choose)并提出你的问题 ！</span><span class="sxs-lookup"><span data-stu-id="288cb-148">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="288cb-149">我们始终乐于接受 Pr 和贡献也 ！</span><span class="sxs-lookup"><span data-stu-id="288cb-149">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="288cb-150">VSCode 提示</span><span class="sxs-lookup"><span data-stu-id="288cb-150">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="288cb-151">命令面板</span><span class="sxs-lookup"><span data-stu-id="288cb-151">Command Palette</span></span>

<span data-ttu-id="288cb-152"><kbd>F1</kbd>或者<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd>移位</kbd>+<kbd>P</kbd>在 macOS 上)</span><span class="sxs-lookup"><span data-stu-id="288cb-152"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="288cb-153">在 VSCode 中执行命令的简便方法。</span><span class="sxs-lookup"><span data-stu-id="288cb-153">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="288cb-154">有关详细信息，请参阅[VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette)。</span><span class="sxs-lookup"><span data-stu-id="288cb-154">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[命令面板]: #command-palette
[Command Palette]: #command-palette
