---
title: 如何复制 Visual Studio Code 中的 ISE 体验
description: 如何复制 Visual Studio Code 中的 ISE 体验
ms.date: 08/06/2018
ms.openlocfilehash: 983da850c13d72bcdc7b2d33970c6e9e06b3d869
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058499"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="3d042-103">如何复制 Visual Studio Code 中的 ISE 体验</span><span class="sxs-lookup"><span data-stu-id="3d042-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="3d042-104">虽然适用于 VSCode 的 PowerShell 扩展并不寻求与 PowerShell ISE 的完全功能奇偶一致性，但有些功能可以让 ISE 用户更自然地体验 VSCode。</span><span class="sxs-lookup"><span data-stu-id="3d042-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="3d042-105">本文档尝试列出可以在 VSCode 中配置的设置，以使用户获得与 ISE 相比更熟悉的体验。</span><span class="sxs-lookup"><span data-stu-id="3d042-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="3d042-106">键绑定</span><span class="sxs-lookup"><span data-stu-id="3d042-106">Key bindings</span></span>

| <span data-ttu-id="3d042-107">功能</span><span class="sxs-lookup"><span data-stu-id="3d042-107">Function</span></span>                              | <span data-ttu-id="3d042-108">ISE 绑定</span><span class="sxs-lookup"><span data-stu-id="3d042-108">ISE Binding</span></span>                  | <span data-ttu-id="3d042-109">VSCode 绑定</span><span class="sxs-lookup"><span data-stu-id="3d042-109">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="3d042-110">干扰并中断调试器</span><span class="sxs-lookup"><span data-stu-id="3d042-110">Interrupt and break debugger</span></span>          | <span data-ttu-id="3d042-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="3d042-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="3d042-112"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="3d042-112"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="3d042-113">执行当前行/突出显示的文本</span><span class="sxs-lookup"><span data-stu-id="3d042-113">Execute current line/highlighted text</span></span> | <span data-ttu-id="3d042-114"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="3d042-114"><kbd>F8</kbd></span></span>                | <span data-ttu-id="3d042-115"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="3d042-115"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="3d042-116">列出可用代码片段</span><span class="sxs-lookup"><span data-stu-id="3d042-116">List available snippets</span></span>               | <span data-ttu-id="3d042-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="3d042-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="3d042-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="3d042-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="3d042-119">自定义键绑定</span><span class="sxs-lookup"><span data-stu-id="3d042-119">Custom Key bindings</span></span>

<span data-ttu-id="3d042-120">也可以在 VSCode 中[配置自己的键绑定](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)。</span><span class="sxs-lookup"><span data-stu-id="3d042-120">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="tab-completion"></a><span data-ttu-id="3d042-121">Tab 自动补全</span><span class="sxs-lookup"><span data-stu-id="3d042-121">Tab completion</span></span>

<span data-ttu-id="3d042-122">若要启用更类似于 ISE 的 Tab 自动补全，请添加以下设置：</span><span class="sxs-lookup"><span data-stu-id="3d042-122">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> <span data-ttu-id="3d042-123">此设置已直接添加到 VSCode（而不是扩展中）。</span><span class="sxs-lookup"><span data-stu-id="3d042-123">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="3d042-124">其行为由 VSCode 直接决定，并且不能由扩展更改。</span><span class="sxs-lookup"><span data-stu-id="3d042-124">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="3d042-125">执行时控制台上无焦点</span><span class="sxs-lookup"><span data-stu-id="3d042-125">No focus on console when executing</span></span>

<span data-ttu-id="3d042-126">使用 <kbd>F8</kbd> 执行时，要在编辑器中保持焦点：</span><span class="sxs-lookup"><span data-stu-id="3d042-126">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

<span data-ttu-id="3d042-127">出于辅助功能目的，默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="3d042-127">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="3d042-128">启动时不要启动集成控制台</span><span class="sxs-lookup"><span data-stu-id="3d042-128">Don't start integrated console on startup</span></span>

<span data-ttu-id="3d042-129">若要在启动时停止集成控制台，请设置：</span><span class="sxs-lookup"><span data-stu-id="3d042-129">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="3d042-130">后台 PowerShell 进程仍将启动，因为它提供 IntelliSense、脚本分析、符号导航等。但控制台不会显示。</span><span class="sxs-lookup"><span data-stu-id="3d042-130">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="3d042-131">假设默认情况下文件是 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3d042-131">Assume files are PowerShell by default</span></span>

<span data-ttu-id="3d042-132">若要创建新/无标题文件，请默认注册为 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="3d042-132">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a><span data-ttu-id="3d042-133">配色方案</span><span class="sxs-lookup"><span data-stu-id="3d042-133">Color scheme</span></span>

<span data-ttu-id="3d042-134">有许多可供 VSCode 使用的 ISE 主题，从而使编辑器看起来更像 ISE。</span><span class="sxs-lookup"><span data-stu-id="3d042-134">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="3d042-135">在[命令面板]中，键入 `theme` 以获得 `Preferences: Color Theme`，并按 <kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="3d042-135">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="3d042-136">从下拉列表中选择 `PowerShell ISE`。</span><span class="sxs-lookup"><span data-stu-id="3d042-136">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="3d042-137">可以通过以下工具在设置中设置该主题：</span><span class="sxs-lookup"><span data-stu-id="3d042-137">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a><span data-ttu-id="3d042-138">PowerShell 命令资源管理器</span><span class="sxs-lookup"><span data-stu-id="3d042-138">PowerShell Command Explorer</span></span>

<span data-ttu-id="3d042-139">感谢 [@corbob](https://github.com/corbob) 的工作，PowerShell 扩展开始有其自己的命令资源管理器。</span><span class="sxs-lookup"><span data-stu-id="3d042-139">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="3d042-140">在[命令面板]中，键入 `PowerShell Command Explorer` 并按 <kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="3d042-140">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="3d042-141">在 ISE 中打开</span><span class="sxs-lookup"><span data-stu-id="3d042-141">Open in the ISE</span></span>

<span data-ttu-id="3d042-142">如果最终仍想要在 ISE 中打开一个文件，可以使用 <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>。</span><span class="sxs-lookup"><span data-stu-id="3d042-142">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="3d042-143">其他资源</span><span class="sxs-lookup"><span data-stu-id="3d042-143">Other resources</span></span>

- <span data-ttu-id="3d042-144">4sysops 上有[一篇有关如何将 VSCode 配置得更像 ISE 的精彩文章](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/)。</span><span class="sxs-lookup"><span data-stu-id="3d042-144">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="3d042-145">Mike F Robbins 撰写了一篇关于如何设置 VSCode 的[出色文章](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/)。</span><span class="sxs-lookup"><span data-stu-id="3d042-145">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="3d042-146">Learn PowerShell 上有一篇关于为 PowerShell 设置 VSCode 的[优秀文章](https://www.learnpwsh.com/setup-vs-code-for-powershell/)。</span><span class="sxs-lookup"><span data-stu-id="3d042-146">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="3d042-147">更多设置</span><span class="sxs-lookup"><span data-stu-id="3d042-147">More settings</span></span>

<span data-ttu-id="3d042-148">如果知道更多让 ISE 用户更熟悉 VSCode 的方法，请参与编写本文档。如果正在寻找兼容性配置，但找不到任何方法来启用它，则[提出问题](https://github.com/PowerShell/vscode-powershell/issues/new/choose)，然后询问！</span><span class="sxs-lookup"><span data-stu-id="3d042-148">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="3d042-149">此外，我们始终乐于接受 PR 并欢迎投稿！</span><span class="sxs-lookup"><span data-stu-id="3d042-149">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="3d042-150">VSCode 提示</span><span class="sxs-lookup"><span data-stu-id="3d042-150">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="3d042-151">命令面板</span><span class="sxs-lookup"><span data-stu-id="3d042-151">Command Palette</span></span>

<span data-ttu-id="3d042-152"><kbd>F1</kbd> 或 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>（macOS 上为 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>）</span><span class="sxs-lookup"><span data-stu-id="3d042-152"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="3d042-153">在 VSCode 中执行命令的简便方法。</span><span class="sxs-lookup"><span data-stu-id="3d042-153">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="3d042-154">有关详细信息，请参阅 [VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette)。</span><span class="sxs-lookup"><span data-stu-id="3d042-154">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[命令面板]: #command-palette
[Command Palette]: #command-palette
