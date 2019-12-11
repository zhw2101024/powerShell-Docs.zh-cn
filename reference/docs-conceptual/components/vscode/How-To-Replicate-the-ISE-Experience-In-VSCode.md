---
title: 如何复制 Visual Studio Code 中的 ISE 体验
description: 如何复制 Visual Studio Code 中的 ISE 体验
ms.date: 08/06/2018
ms.openlocfilehash: d5542e9a3a48b1ae64356309be669418edf6c79e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74117473"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>如何复制 Visual Studio Code 中的 ISE 体验

虽然适用于 VSCode 的 PowerShell 扩展并不寻求与 PowerShell ISE 的完全功能奇偶一致性，但有些功能可以让 ISE 用户更自然地体验 VSCode。

本文档尝试列出可以在 VSCode 中配置的设置，以使用户获得与 ISE 相比更熟悉的体验。

## <a name="key-bindings"></a>键绑定

| 功能                              | ISE 绑定                  | VSCode 绑定                              |
| ----------------                      | -----------                  | --------------                              |
| 干扰并中断调试器          | <kbd>Ctrl</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
| 执行当前行/突出显示的文本 | <kbd>F8</kbd>                | <kbd>F8</kbd>                               |
| 列出可用代码片段               | <kbd>Ctrl</kbd>+<kbd>J</kbd> | <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd> |

### <a name="custom-key-bindings"></a>自定义键绑定

也可以在 VSCode 中[配置自己的键绑定](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)。

## <a name="simplified-ise-like-ui"></a>简化的类似 ISE 的 UI

如果希望简化 Visual Studio Code UI，以便看起来更接近 ISE 的 UI，请应用以下两个设置：

```json
"workbench.activityBar.visible": false,
"debug.openDebug": "neverOpen",
```

这会在红色框内隐藏下面的“活动栏”和“调试侧边栏”部分：

![突出显示的部分包括“活动栏”和“调试侧边栏”](images/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

最终结果如下所示：

![简化的 VS Code 视图](images/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

## <a name="tab-completion"></a>Tab 自动补全

若要启用更类似于 ISE 的 Tab 自动补全，请添加以下设置：

```json
"editor.tabCompletion": "on",
```

> [!NOTE]
> 此设置已直接添加到 VSCode（而不是扩展中）。 其行为由 VSCode 直接决定，并且不能由扩展更改。

## <a name="no-focus-on-console-when-executing"></a>执行时控制台上无焦点

使用 <kbd>F8</kbd> 执行时，要在编辑器中保持焦点：

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

出于辅助功能目的，默认值为 `true`。

## <a name="dont-start-integrated-console-on-startup"></a>启动时不要启动集成控制台

若要在启动时停止集成控制台，请设置：

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> 后台 PowerShell 进程仍将启动，因为它提供 IntelliSense、脚本分析、符号导航等。但控制台不会显示。

## <a name="assume-files-are-powershell-by-default"></a>假设默认情况下文件是 PowerShell

若要创建新/无标题文件，请默认注册为 PowerShell：

```json
"files.defaultLanguage": "powershell",
```

## <a name="color-scheme"></a>配色方案

有许多可供 VSCode 使用的 ISE 主题，从而使编辑器看起来更像 ISE。

在[命令面板]中，键入 `theme` 以获得 `Preferences: Color Theme`，并按 <kbd>Enter</kbd>。
从下拉列表中选择 `PowerShell ISE`。

可以通过以下工具在设置中设置该主题：

```json
"workbench.colorTheme": "PowerShell ISE",
```

## <a name="powershell-command-explorer"></a>PowerShell 命令资源管理器

感谢 [@corbob](https://github.com/corbob) 的工作，PowerShell 扩展开始有其自己的命令资源管理器。

在[命令面板]中，键入 `PowerShell Command Explorer` 并按 <kbd>Enter</kbd>。

## <a name="open-in-the-ise"></a>在 ISE 中打开

如果最终仍想要在 ISE 中打开一个文件，可以使用 <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>。

## <a name="other-resources"></a>其他资源

- 4sysops 上有[一篇有关如何将 VSCode 配置得更像 ISE 的精彩文章](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/)。
- Mike F Robbins 撰写了一篇关于如何设置 VSCode 的[出色文章](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/)。
- Learn PowerShell 上有一篇关于为 PowerShell 设置 VSCode 的[优秀文章](https://www.learnpwsh.com/setup-vs-code-for-powershell/)。

## <a name="more-settings"></a>更多设置

如果知道更多让 ISE 用户更熟悉 VSCode 的方法，请参与编写本文档。如果正在寻找兼容性配置，但找不到任何方法来启用它，则[提出问题](https://github.com/PowerShell/vscode-powershell/issues/new/choose)，然后询问！

此外，我们始终乐于接受 PR 并欢迎投稿！

## <a name="vscode-tips"></a>VSCode 提示

### <a name="command-palette"></a>命令面板

<kbd>F1</kbd> 或 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>（macOS 上为 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>）

在 VSCode 中执行命令的简便方法。
有关详细信息，请参阅 [VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette)。

[命令面板]: #command-palette
