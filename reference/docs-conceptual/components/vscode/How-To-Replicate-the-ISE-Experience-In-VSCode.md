---
title: 如何复制 Visual Studio Code 中的 ISE 体验
description: 如何复制 Visual Studio Code 中的 ISE 体验
ms.date: 08/06/2018
ms.openlocfilehash: 193243dc2e3e921b22a6ee068370200ae84ce4ac
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279228"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="066d4-103">如何复制 Visual Studio Code 中的 ISE 体验</span><span class="sxs-lookup"><span data-stu-id="066d4-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="066d4-104">虽然适用于 VSCode 的 PowerShell 扩展并不寻求与 PowerShell ISE 的完全功能奇偶一致性，但有些功能可以让 ISE 用户更自然地体验 VSCode。</span><span class="sxs-lookup"><span data-stu-id="066d4-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="066d4-105">本文档尝试列出可以在 VSCode 中配置的设置，以使用户获得与 ISE 相比更熟悉的体验。</span><span class="sxs-lookup"><span data-stu-id="066d4-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="ise-mode"></a><span data-ttu-id="066d4-106">ISE 模式</span><span class="sxs-lookup"><span data-stu-id="066d4-106">ISE Mode</span></span>

> [!NOTE]
> <span data-ttu-id="066d4-107">此功能自版本 2019.12.0 起在 PowerShell 预览版扩展中可用，自版本 2020.3.0 起在 PowerShell 扩展中可用。</span><span class="sxs-lookup"><span data-stu-id="066d4-107">This feature is available in the PowerShell Preview extension since version 2019.12.0 and in the PowerShell extension since version 2020.3.0.</span></span>

<span data-ttu-id="066d4-108">在 Visual Studio Code 中复制 ISE 体验的最简单方法是打开“ISE 模式”。</span><span class="sxs-lookup"><span data-stu-id="066d4-108">The easiest way to replicate the ISE experience in Visual Studio Code is by turning on "ISE Mode".</span></span>
<span data-ttu-id="066d4-109">为此，请打开命令托盘（<kbd>F1</kbd> 或 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>，在 macOS 上为 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>），然后键入“ISE 模式”。</span><span class="sxs-lookup"><span data-stu-id="066d4-109">To do this, open the command pallet (<kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> OR <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS) and type in "ISE Mode".</span></span>
<span data-ttu-id="066d4-110">从列表中选择“PowerShell:启用 ISE 模式”。</span><span class="sxs-lookup"><span data-stu-id="066d4-110">Select "PowerShell: Enable ISE Mode" from the list.</span></span>

<span data-ttu-id="066d4-111">此命令将自动应用本文档中找到的大量设置。</span><span class="sxs-lookup"><span data-stu-id="066d4-111">This command will apply a lot of the settings found in this document automatically.</span></span>
<span data-ttu-id="066d4-112">结果类似以下形式：</span><span class="sxs-lookup"><span data-stu-id="066d4-112">The result looks like this:</span></span>

![ISE 模式](media/How-To-Replicate-the-ISE-Experience-In-VSCode/3-ise-mode.png)

<span data-ttu-id="066d4-114">本文的其余部分包含有关 ISE 模式下的设置和其他一些设置的更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="066d4-114">The rest of this article includes more detailed information on settings in ISE Mode and some additional settings.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="066d4-115">键绑定</span><span class="sxs-lookup"><span data-stu-id="066d4-115">Key bindings</span></span>

| <span data-ttu-id="066d4-116">函数</span><span class="sxs-lookup"><span data-stu-id="066d4-116">Function</span></span>                              | <span data-ttu-id="066d4-117">ISE 绑定</span><span class="sxs-lookup"><span data-stu-id="066d4-117">ISE Binding</span></span>                  | <span data-ttu-id="066d4-118">VSCode 绑定</span><span class="sxs-lookup"><span data-stu-id="066d4-118">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="066d4-119">干扰并中断调试器</span><span class="sxs-lookup"><span data-stu-id="066d4-119">Interrupt and break debugger</span></span>          | <span data-ttu-id="066d4-120"><kbd>Ctrl</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="066d4-120"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="066d4-121"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="066d4-121"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="066d4-122">执行当前行/突出显示的文本</span><span class="sxs-lookup"><span data-stu-id="066d4-122">Execute current line/highlighted text</span></span> | <span data-ttu-id="066d4-123"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="066d4-123"><kbd>F8</kbd></span></span>                | <span data-ttu-id="066d4-124"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="066d4-124"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="066d4-125">列出可用代码片段</span><span class="sxs-lookup"><span data-stu-id="066d4-125">List available snippets</span></span>               | <span data-ttu-id="066d4-126"><kbd>Ctrl</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="066d4-126"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="066d4-127"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="066d4-127"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="066d4-128">自定义键绑定</span><span class="sxs-lookup"><span data-stu-id="066d4-128">Custom Key bindings</span></span>

<span data-ttu-id="066d4-129">也可以在 VSCode 中[配置自己的键绑定](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)。</span><span class="sxs-lookup"><span data-stu-id="066d4-129">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="simplified-ise-like-ui"></a><span data-ttu-id="066d4-130">简化的类似 ISE 的 UI</span><span class="sxs-lookup"><span data-stu-id="066d4-130">Simplified ISE-like UI</span></span>

<span data-ttu-id="066d4-131">如果希望简化 Visual Studio Code UI，以便看起来更接近 ISE 的 UI，请应用以下两个设置：</span><span class="sxs-lookup"><span data-stu-id="066d4-131">If you're looking to simplify the Visual Studio Code UI to look more closely to the UI of the ISE, apply these two settings:</span></span>

```json
"workbench.activityBar.visible": false,
"debug.openDebug": "neverOpen",
```

> [!NOTE]
> <span data-ttu-id="066d4-132">这些设置包含在[“ISE 模式”](#ise-mode)中。</span><span class="sxs-lookup"><span data-stu-id="066d4-132">These settings are included in ["ISE Mode"](#ise-mode).</span></span>

<span data-ttu-id="066d4-133">这会在红色框内隐藏下面的“活动栏”和“调试侧边栏”部分：</span><span class="sxs-lookup"><span data-stu-id="066d4-133">This will hide the "Activity Bar" and the "Debug Side Bar" sections below inside of the red box:</span></span>

![突出显示的部分包括“活动栏”和“调试侧边栏”](media/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

<span data-ttu-id="066d4-135">最终结果如下所示：</span><span class="sxs-lookup"><span data-stu-id="066d4-135">The end result looks like this:</span></span>

![简化的 VS Code 视图](media/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

## <a name="tab-completion"></a><span data-ttu-id="066d4-137">Tab 自动补全</span><span class="sxs-lookup"><span data-stu-id="066d4-137">Tab completion</span></span>

<span data-ttu-id="066d4-138">若要启用更类似于 ISE 的 Tab 自动补全，请添加以下设置：</span><span class="sxs-lookup"><span data-stu-id="066d4-138">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on",
```

> [!NOTE]
> <span data-ttu-id="066d4-139">此设置已直接添加到 VSCode（而不是扩展中）。</span><span class="sxs-lookup"><span data-stu-id="066d4-139">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="066d4-140">其行为由 VSCode 直接决定，并且不能由扩展更改。</span><span class="sxs-lookup"><span data-stu-id="066d4-140">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

> [!NOTE]
> <span data-ttu-id="066d4-141">此设置包含在[“ISE 模式”](#ise-mode)中。</span><span class="sxs-lookup"><span data-stu-id="066d4-141">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="066d4-142">执行时焦点无需置于控制台</span><span class="sxs-lookup"><span data-stu-id="066d4-142">No focus on console when executing</span></span>

<span data-ttu-id="066d4-143">使用 <kbd>F8</kbd> 执行时，要在编辑器中保持焦点：</span><span class="sxs-lookup"><span data-stu-id="066d4-143">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

> [!NOTE]
> <span data-ttu-id="066d4-144">此设置包含在[“ISE 模式”](#ise-mode)中。</span><span class="sxs-lookup"><span data-stu-id="066d4-144">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

<span data-ttu-id="066d4-145">访问性目的默认为 `true`。</span><span class="sxs-lookup"><span data-stu-id="066d4-145">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="066d4-146">启动时不要启动集成控制台</span><span class="sxs-lookup"><span data-stu-id="066d4-146">Don't start integrated console on startup</span></span>

<span data-ttu-id="066d4-147">若要在启动时停止集成控制台，请设置：</span><span class="sxs-lookup"><span data-stu-id="066d4-147">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="066d4-148">后台 PowerShell 进程仍将启动，因为它提供 IntelliSense、脚本分析、符号导航等。但控制台不会显示。</span><span class="sxs-lookup"><span data-stu-id="066d4-148">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="066d4-149">假设默认情况下文件是 PowerShell</span><span class="sxs-lookup"><span data-stu-id="066d4-149">Assume files are PowerShell by default</span></span>

<span data-ttu-id="066d4-150">若要创建新/无标题文件，请默认注册为 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="066d4-150">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell",
```

> [!NOTE]
> <span data-ttu-id="066d4-151">此设置包含在[“ISE 模式”](#ise-mode)中。</span><span class="sxs-lookup"><span data-stu-id="066d4-151">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

## <a name="color-scheme"></a><span data-ttu-id="066d4-152">配色方案</span><span class="sxs-lookup"><span data-stu-id="066d4-152">Color scheme</span></span>

<span data-ttu-id="066d4-153">有许多可供 VSCode 使用的 ISE 主题，从而使编辑器看起来更像 ISE。</span><span class="sxs-lookup"><span data-stu-id="066d4-153">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="066d4-154">在[命令面板]中，键入 `theme` 以获得 `Preferences: Color Theme`，并按 <kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="066d4-154">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="066d4-155">从下拉列表中选择 `PowerShell ISE`。</span><span class="sxs-lookup"><span data-stu-id="066d4-155">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="066d4-156">可以通过以下工具在设置中设置该主题：</span><span class="sxs-lookup"><span data-stu-id="066d4-156">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE",
```

> [!NOTE]
> <span data-ttu-id="066d4-157">此设置包含在[“ISE 模式”](#ise-mode)中。</span><span class="sxs-lookup"><span data-stu-id="066d4-157">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

## <a name="powershell-command-explorer"></a><span data-ttu-id="066d4-158">PowerShell 命令资源管理器</span><span class="sxs-lookup"><span data-stu-id="066d4-158">PowerShell Command Explorer</span></span>

<span data-ttu-id="066d4-159">感谢 [@corbob](https://github.com/corbob) 的工作，PowerShell 扩展开始有其自己的命令资源管理器。</span><span class="sxs-lookup"><span data-stu-id="066d4-159">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="066d4-160">在[命令面板]中，键入 `PowerShell Command Explorer` 并按 <kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="066d4-160">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

> [!NOTE]
> <span data-ttu-id="066d4-161">这会自动显示在[“ISE 模式”](#ise-mode)中。</span><span class="sxs-lookup"><span data-stu-id="066d4-161">This is shown automatically in ["ISE Mode"](#ise-mode).</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="066d4-162">在 ISE 中打开</span><span class="sxs-lookup"><span data-stu-id="066d4-162">Open in the ISE</span></span>

<span data-ttu-id="066d4-163">如果最终仍想要在 ISE 中打开一个文件，可以使用 <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>。</span><span class="sxs-lookup"><span data-stu-id="066d4-163">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="066d4-164">其他资源</span><span class="sxs-lookup"><span data-stu-id="066d4-164">Other resources</span></span>

- <span data-ttu-id="066d4-165">4sysops 上有[一篇有关如何将 VSCode 配置得更像 ISE 的精彩文章](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/)。</span><span class="sxs-lookup"><span data-stu-id="066d4-165">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="066d4-166">Mike F Robbins 撰写了一篇关于如何设置 VSCode 的[出色文章](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/)。</span><span class="sxs-lookup"><span data-stu-id="066d4-166">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="066d4-167">Learn PowerShell 上有一篇关于为 PowerShell 设置 VSCode 的[优秀文章](https://www.learnpwsh.com/setup-vs-code-for-powershell/)。</span><span class="sxs-lookup"><span data-stu-id="066d4-167">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="066d4-168">更多设置</span><span class="sxs-lookup"><span data-stu-id="066d4-168">More settings</span></span>

<span data-ttu-id="066d4-169">如果知道更多让 ISE 用户更熟悉 VSCode 的方法，请参与编写本文档。如果正在寻找兼容性配置，但找不到任何方法来启用它，则[提出问题](https://github.com/PowerShell/vscode-powershell/issues/new/choose)，然后询问！</span><span class="sxs-lookup"><span data-stu-id="066d4-169">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="066d4-170">此外，我们始终乐于接受 PR 并欢迎投稿！</span><span class="sxs-lookup"><span data-stu-id="066d4-170">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="066d4-171">VSCode 提示</span><span class="sxs-lookup"><span data-stu-id="066d4-171">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="066d4-172">命令面板</span><span class="sxs-lookup"><span data-stu-id="066d4-172">Command Palette</span></span>

<span data-ttu-id="066d4-173"><kbd>F1</kbd> 或 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>（macOS 上为 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>）</span><span class="sxs-lookup"><span data-stu-id="066d4-173"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="066d4-174">在 VSCode 中执行命令的简便方法。</span><span class="sxs-lookup"><span data-stu-id="066d4-174">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="066d4-175">有关详细信息，请参阅 [VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette)。</span><span class="sxs-lookup"><span data-stu-id="066d4-175">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[命令面板]: #command-palette
[Command Palette]: #command-palette
