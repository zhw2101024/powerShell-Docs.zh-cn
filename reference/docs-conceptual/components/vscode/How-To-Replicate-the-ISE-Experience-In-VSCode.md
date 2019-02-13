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
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>如何复制 Visual Studio Code 中的 ISE 体验

适用于 VSCode 的 PowerShell 扩展不会查找在 PowerShell ISE 的完整功能奇偶一致性，而有功能到位，才能使 VSCode 体验更自然的 ISE 的用户。

本文档会尝试将在 VSCode 以使用户体验更熟悉相比在 ISE 中可配置的列表设置。

## <a name="key-bindings"></a>键绑定

| 功能                              | ISE 绑定                  | VSCode 绑定                              |
| ----------------                      | -----------                  | --------------                              |
| 中断并中断调试器          | <kbd>Ctrl</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
| 执行当前突出显示行/文本 | <kbd>F8</kbd>                | <kbd>F8</kbd>                               |
| 列表可用代码段               | <kbd>Ctrl</kbd>+<kbd>J</kbd> | <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd> |

### <a name="custom-key-bindings"></a>自定义键绑定

你可以[配置你自己的键绑定](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)也 VSCode 中。

## <a name="tab-completion"></a>Tab 自动补全

若要启用更类似于 ISE 的 tab 自动补全，请添加此设置：

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> 此设置已添加到 VSCode 直接 （而不是扩展中）。 其行为由 VSCode 直接确定，无法更改的扩展插件。

## <a name="no-focus-on-console-when-executing"></a>在控制台上执行时没有焦点

若要在使用执行时，在编辑器中保持焦点<kbd>F8</kbd>:

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

默认值是`true`用于可访问性目的。

## <a name="dont-start-integrated-console-on-startup"></a>不要在启动时开始集成的控制台

若要在启动时停止集成的控制台，请设置：

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> 后台 PowerShell 进程仍将启动，因为它提供 IntelliSense，脚本分析、 符号导航，等等。但不会显示在控制台中。

## <a name="assume-files-are-powershell-by-default"></a>假设文件默认情况下是 PowerShell

若要使新/无标题文件，因为 PowerShell 默认情况下注册：

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a>配色方案

有大量 ISE 主题适用于 VSCode 将看起来更像 ISE 编辑器。

在中[命令面板]类型`theme`若要获取`Preferences: Color Theme`然后按<kbd>Enter</kbd>。
在下拉列表中，选择`PowerShell ISE`。

可以使用在设置中设置此主题：

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a>PowerShell 命令资源管理器

衷心感谢的工作成果[ @corbob ](https://github.com/corbob)，PowerShell 扩展具有其自己命令资源管理器的开始部分。

在中[命令面板]，输入`PowerShell Command Explorer`然后按<kbd>Enter</kbd>。

## <a name="open-in-the-ise"></a>在 ISE 中打开

如果您会得到想是否仍要在 ISE 中打开一个文件，则可以使用<kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>。

## <a name="other-resources"></a>其他资源

- 具有 4sysops[优秀文章](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/)配置 VSCode 是更像是在 ISE。
- 具有 Mike F Robbins[优秀文章](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/)设置 VSCode。
- 了解 PowerShell 具有[出色写入](https://www.learnpwsh.com/setup-vs-code-for-powershell/)获取 VSCode 的 PowerShell 安装程序。

## <a name="more-settings"></a>更多设置

如果您知道的更多方式进行 VSCode 感觉更熟悉的 ISE 用户，参与此文档。如果要查找的兼容性配置但找不到任何方式来启用它，请[提出问题](https://github.com/PowerShell/vscode-powershell/issues/new/choose)并提出你的问题 ！

我们始终乐于接受 Pr 和贡献也 ！

## <a name="vscode-tips"></a>VSCode 提示

### <a name="command-palette"></a>命令面板

<kbd>F1</kbd>或者<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd>移位</kbd>+<kbd>P</kbd>在 macOS 上)

在 VSCode 中执行命令的简便方法。
有关详细信息，请参阅[VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette)。

[命令面板]: #command-palette
