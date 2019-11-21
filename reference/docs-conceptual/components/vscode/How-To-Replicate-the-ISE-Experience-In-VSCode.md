---
title: 如何复制 Visual Studio Code 中的 ISE 体验
description: 如何复制 Visual Studio Code 中的 ISE 体验
ms.date: 08/06/2018
ms.openlocfilehash: d5542e9a3a48b1ae64356309be669418edf6c79e
ms.sourcegitcommit: a6e54a305fdeb6482321c77da8066d2f991c93e1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2019
ms.locfileid: "74117473"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="f8bbe-103">如何复制 Visual Studio Code 中的 ISE 体验</span><span class="sxs-lookup"><span data-stu-id="f8bbe-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="f8bbe-104">虽然适用于 VSCode 的 PowerShell 扩展并不寻求与 PowerShell ISE 的完全功能奇偶一致性，但有些功能可以让 ISE 用户更自然地体验 VSCode。</span><span class="sxs-lookup"><span data-stu-id="f8bbe-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="f8bbe-105">本文档尝试列出可以在 VSCode 中配置的设置，以使用户获得与 ISE 相比更熟悉的体验。</span><span class="sxs-lookup"><span data-stu-id="f8bbe-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="f8bbe-106">键绑定</span><span class="sxs-lookup"><span data-stu-id="f8bbe-106">Key bindings</span></span>

| <span data-ttu-id="f8bbe-107">功能</span><span class="sxs-lookup"><span data-stu-id="f8bbe-107">Function</span></span>                              | <span data-ttu-id="f8bbe-108">ISE 绑定</span><span class="sxs-lookup"><span data-stu-id="f8bbe-108">ISE Binding</span></span>                  | <span data-ttu-id="f8bbe-109">VSCode 绑定</span><span class="sxs-lookup"><span data-stu-id="f8bbe-109">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="f8bbe-110">干扰并中断调试器</span><span class="sxs-lookup"><span data-stu-id="f8bbe-110">Interrupt and break debugger</span></span>          | <span data-ttu-id="f8bbe-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="f8bbe-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="f8bbe-112"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="f8bbe-112"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="f8bbe-113">执行当前行/突出显示的文本</span><span class="sxs-lookup"><span data-stu-id="f8bbe-113">Execute current line/highlighted text</span></span> | <span data-ttu-id="f8bbe-114"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="f8bbe-114"><kbd>F8</kbd></span></span>                | <span data-ttu-id="f8bbe-115"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="f8bbe-115"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="f8bbe-116">列出可用代码片段</span><span class="sxs-lookup"><span data-stu-id="f8bbe-116">List available snippets</span></span>               | <span data-ttu-id="f8bbe-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="f8bbe-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="f8bbe-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="f8bbe-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="f8bbe-119">自定义键绑定</span><span class="sxs-lookup"><span data-stu-id="f8bbe-119">Custom Key bindings</span></span>

<span data-ttu-id="f8bbe-120">也可以在 VSCode 中[配置自己的键绑定](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)。</span><span class="sxs-lookup"><span data-stu-id="f8bbe-120">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="simplified-ise-like-ui"></a><span data-ttu-id="f8bbe-121">简化的类似 ISE 的 UI</span><span class="sxs-lookup"><span data-stu-id="f8bbe-121">Simplified ISE-like UI</span></span>

<span data-ttu-id="f8bbe-122">如果希望简化 Visual Studio Code UI，以便看起来更接近 ISE 的 UI，请应用以下两个设置：</span><span class="sxs-lookup"><span data-stu-id="f8bbe-122">If you're looking to simplify the Visual Studio Code UI to look more closely to the UI of the ISE, apply these two settings:</span></span>

```json
"workbench.activityBar.visible": false,
"debug.openDebug": "neverOpen",
```

<span data-ttu-id="f8bbe-123">这会在红色框内隐藏下面的“活动栏”和“调试侧边栏”部分：</span><span class="sxs-lookup"><span data-stu-id="f8bbe-123">This will hide the "Activity Bar" and the "Debug Side Bar" sections below inside of the red box:</span></span>

![突出显示的部分包括“活动栏”和“调试侧边栏”](images/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

<span data-ttu-id="f8bbe-125">最终结果如下所示：</span><span class="sxs-lookup"><span data-stu-id="f8bbe-125">The end result looks like this:</span></span>

![简化的 VS Code 视图](images/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

## <a name="tab-completion"></a><span data-ttu-id="f8bbe-127">Tab 自动补全</span><span class="sxs-lookup"><span data-stu-id="f8bbe-127">Tab completion</span></span>

<span data-ttu-id="f8bbe-128">若要启用更类似于 ISE 的 Tab 自动补全，请添加以下设置：</span><span class="sxs-lookup"><span data-stu-id="f8bbe-128">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on",
```

> [!NOTE]
> <span data-ttu-id="f8bbe-129">此设置已直接添加到 VSCode（而不是扩展中）。</span><span class="sxs-lookup"><span data-stu-id="f8bbe-129">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="f8bbe-130">其行为由 VSCode 直接决定，并且不能由扩展更改。</span><span class="sxs-lookup"><span data-stu-id="f8bbe-130">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="f8bbe-131">执行时控制台上无焦点</span><span class="sxs-lookup"><span data-stu-id="f8bbe-131">No focus on console when executing</span></span>

<span data-ttu-id="f8bbe-132">使用 <kbd>F8</kbd> 执行时，要在编辑器中保持焦点：</span><span class="sxs-lookup"><span data-stu-id="f8bbe-132">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

<span data-ttu-id="f8bbe-133">出于辅助功能目的，默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="f8bbe-133">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="f8bbe-134">启动时不要启动集成控制台</span><span class="sxs-lookup"><span data-stu-id="f8bbe-134">Don't start integrated console on startup</span></span>

<span data-ttu-id="f8bbe-135">若要在启动时停止集成控制台，请设置：</span><span class="sxs-lookup"><span data-stu-id="f8bbe-135">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="f8bbe-136">后台 PowerShell 进程仍将启动，因为它提供 IntelliSense、脚本分析、符号导航等。但控制台不会显示。</span><span class="sxs-lookup"><span data-stu-id="f8bbe-136">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="f8bbe-137">假设默认情况下文件是 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f8bbe-137">Assume files are PowerShell by default</span></span>

<span data-ttu-id="f8bbe-138">若要创建新/无标题文件，请默认注册为 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="f8bbe-138">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell",
```

## <a name="color-scheme"></a><span data-ttu-id="f8bbe-139">配色方案</span><span class="sxs-lookup"><span data-stu-id="f8bbe-139">Color scheme</span></span>

<span data-ttu-id="f8bbe-140">有许多可供 VSCode 使用的 ISE 主题，从而使编辑器看起来更像 ISE。</span><span class="sxs-lookup"><span data-stu-id="f8bbe-140">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="f8bbe-141">在[命令面板]中，键入 `theme` 以获得 `Preferences: Color Theme`，并按 <kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="f8bbe-141">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="f8bbe-142">从下拉列表中选择 `PowerShell ISE`。</span><span class="sxs-lookup"><span data-stu-id="f8bbe-142">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="f8bbe-143">可以通过以下工具在设置中设置该主题：</span><span class="sxs-lookup"><span data-stu-id="f8bbe-143">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE",
```

## <a name="powershell-command-explorer"></a><span data-ttu-id="f8bbe-144">PowerShell 命令资源管理器</span><span class="sxs-lookup"><span data-stu-id="f8bbe-144">PowerShell Command Explorer</span></span>

<span data-ttu-id="f8bbe-145">感谢 [@corbob](https://github.com/corbob) 的工作，PowerShell 扩展开始有其自己的命令资源管理器。</span><span class="sxs-lookup"><span data-stu-id="f8bbe-145">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="f8bbe-146">在[命令面板]中，键入 `PowerShell Command Explorer` 并按 <kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="f8bbe-146">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="f8bbe-147">在 ISE 中打开</span><span class="sxs-lookup"><span data-stu-id="f8bbe-147">Open in the ISE</span></span>

<span data-ttu-id="f8bbe-148">如果最终仍想要在 ISE 中打开一个文件，可以使用 <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>。</span><span class="sxs-lookup"><span data-stu-id="f8bbe-148">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="f8bbe-149">其他资源</span><span class="sxs-lookup"><span data-stu-id="f8bbe-149">Other resources</span></span>

- <span data-ttu-id="f8bbe-150">4sysops 上有[一篇有关如何将 VSCode 配置得更像 ISE 的精彩文章](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/)。</span><span class="sxs-lookup"><span data-stu-id="f8bbe-150">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="f8bbe-151">Mike F Robbins 撰写了一篇关于如何设置 VSCode 的[出色文章](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/)。</span><span class="sxs-lookup"><span data-stu-id="f8bbe-151">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="f8bbe-152">Learn PowerShell 上有一篇关于为 PowerShell 设置 VSCode 的[优秀文章](https://www.learnpwsh.com/setup-vs-code-for-powershell/)。</span><span class="sxs-lookup"><span data-stu-id="f8bbe-152">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="f8bbe-153">更多设置</span><span class="sxs-lookup"><span data-stu-id="f8bbe-153">More settings</span></span>

<span data-ttu-id="f8bbe-154">如果知道更多让 ISE 用户更熟悉 VSCode 的方法，请参与编写本文档。如果正在寻找兼容性配置，但找不到任何方法来启用它，则[提出问题](https://github.com/PowerShell/vscode-powershell/issues/new/choose)，然后询问！</span><span class="sxs-lookup"><span data-stu-id="f8bbe-154">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="f8bbe-155">此外，我们始终乐于接受 PR 并欢迎投稿！</span><span class="sxs-lookup"><span data-stu-id="f8bbe-155">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="f8bbe-156">VSCode 提示</span><span class="sxs-lookup"><span data-stu-id="f8bbe-156">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="f8bbe-157">命令面板</span><span class="sxs-lookup"><span data-stu-id="f8bbe-157">Command Palette</span></span>

<span data-ttu-id="f8bbe-158"><kbd>F1</kbd> 或 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>（macOS 上为 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>）</span><span class="sxs-lookup"><span data-stu-id="f8bbe-158"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="f8bbe-159">在 VSCode 中执行命令的简便方法。</span><span class="sxs-lookup"><span data-stu-id="f8bbe-159">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="f8bbe-160">有关详细信息，请参阅 [VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette)。</span><span class="sxs-lookup"><span data-stu-id="f8bbe-160">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[命令面板]: #command-palette
[Command Palette]: #command-palette
