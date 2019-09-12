---
ms.date: 09/06/2019
keywords: powershell,cmdlet
title: PowerShell 5.0 ISE 中的新增功能
ms.openlocfilehash: a719baef0da1600f0a5377e1b72c81b67e37eef2
ms.sourcegitcommit: a74ae7ed089301992fed201fbe55d827a622afa0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70746225"
---
# <a name="whats-new-in-the-windows-powershell-50-ise"></a>Windows PowerShell 5.0 ISE 中的新增功能

本主题介绍已在 Windows PowerShell (R) 集成脚本环境 (ISE) 的各版本中引入的新增功能和更新功能。

## <a name="feature-description"></a>功能描述

Windows PowerShell ISE 是一款主机应用程序，让你可以在直观的图形环境中编写、运行和测试脚本与模块。 其主要功能，如语法着色、Tab 自动补全、可视调试、Unicode 遵从和上下文相关帮助，将为你带来丰富的脚本编写体验。

有关详细信息，请参阅 [Windows PowerShell ISE 简介](../components/ise/Introducing-the-Windows-PowerShell-ISE.md)。

下表列出了 Windows PowerShell 中此版本的 Windows PowerShell ISE 的新增功能和更改功能。

## <a name="intellisense"></a>Intellisense

> 在 ISE 3.0 中添加

Intellisense 是一个自动完成辅助功能，是 Windows PowerShell ISE 的一部分。
Intellisense 会在你键入时显示可单击的菜单，其中包括可能匹配的 cmdlet、参数、参数值、文件或文件夹。

**更改增添了什么价值？**

新增 Intellisense 功能后，使用 Windows PowerShell ISE 创建脚本时，可以更容易地发现 cmdlet 和语法。 在创建新脚本时，还可以使用 Windows PowerShell ISE 了解 Windows PowerShell。

**工作原理的不同之处是什么？**

当在 Windows PowerShell ISE 中键入 cmdlet 时，会显示一个可滚动和可点击的菜单，并可在其中浏览和选择适当的命令。

## <a name="snippets"></a>代码段

> 在 ISE 3.0 中添加

*代码段*是 Windows PowerShell 代码的一小部分，它可以插入到你在 Windows PowerShell ISE 中创建的脚本。 Windows PowerShell ISE 附带一组默认的代码段。 在 Windows PowerShell ISE 中工作的同时，可通过使用 `New-Snippet` cmdlet 添加代码段。

**更改增添了什么价值？**

通过使用代码段，可以快速组建脚本以自动运行你的环境。

**工作原理的不同之处是什么？**

若要在 Windows PowerShell 3.0 或更高版本中使用代码段，请在“编辑  ”菜单上，单击“启动代码段  ”，或按 <kbd>Ctrl</kbd>+<kbd>J</kbd>。

## <a name="add-on-tools"></a>附加工具

> 在 PowerShell 3.0 中添加

Windows PowerShell ISE 现在支持使用对象模型的附加工具。 这些附加工具是 Windows Presentation Foundation (WPF) 控件，在控制台中显示为垂直或水平窗格。 窗格中的多个附加工具会显示为选项卡式控件。 你还可以添加或删除由 Microsoft 以外的参与方创建的附加工具。 有关详细信息，请参阅 [Windows PowerShell ISE 脚本对象模型的用途](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)。

**更改增添了什么价值？**

借助附加工具，可以使用可添加功能和增强脚本编写体验的工具来扩展和自定义 Windows PowerShell ISE。

**工作原理的不同之处是什么？**

Windows PowerShell ISE 3.0 及更高版本附带**命令**附加工具。 借助**命令**附加工具可以浏览 cmdlet，以及使用**脚本**和**控制台**窗格并行访问有关 cmdlet 的帮助。

可通过使用  “附加工具”菜单上的  “打开附加工具网站”命令找到其他附加工具。

## <a name="restart-manager-and-auto-save"></a>重启管理器和自动保存

> 在 PowerShell 3.0 中添加

Windows PowerShell ISE 每隔两分钟在单独的位置上自动保存你打开的脚本。 当 Windows PowerShell ISE 在意外崩溃或重新启动后重新启动时，它会恢复在上一个会话中打开的脚本，即使脚本未保存也是如此。

要更改自动保存间隔，可在控制台窗格中运行下面的命令：`$psise.Options.AutoSaveMinuteInterval`。

**更改增添了什么价值？**

你已经了解打开的脚本会自动保存，现在便可以在 Windows PowerShell ISE 中工作了。

**工作原理的不同之处是什么？**

Windows PowerShell ISE 2.0 不会自动保存脚本。

## <a name="most-recently-used-list"></a>最近使用的列表

> 在 PowerShell 3.0 中添加

Windows PowerShell ISE 现在具有最近使用过的文件列表。 在 Windows PowerShell ISE 中打开文件时，文件会添加到“文件”  菜单上的最近使用列表中。

若要更改最近使用列表中的文件默认数量，请在控制台窗格中运行以下命令：`$psise.Options.MruCount`。

**更改增添了什么价值？**

现在可以使用最近使用列表轻松地访问频繁使用的文件。

**工作原理的不同之处是什么？**

Windows PowerShell ISE 2.0 没有最近使用列表。

## <a name="console-pane"></a>控制台窗格

> 在 PowerShell 3.0 中添加

第一版 Windows PowerShell ISE 中可用的单独的命令窗格和输出窗格现在合并成了一个控制台窗格。 该控制台窗格的功能和外观与典型的 Windows PowerShell 控制台类似，但经过了以下改进：

- 用于输入文本（而非输出文本）的语法着色，包括 XML 语法
- Intellisense
- 大括号匹配
- 错误指示
- 对 Unicode 的完全支持
- <kbd>F1</kbd> 上下文相关帮助
- <kbd>Ctrl</kbd>+<kbd>F1</kbd> 上下文相关的 Show-Command
- 对复杂脚本和从右向左语言的支持
- 字体支持
- 缩放
- 行选择模式和块选择模式
- 当你在控制台中按“向上”<kbd></kbd>箭头查看历史记录时，命令行处会保留你所键入的内容

**更改增添了什么价值？**

这些新增的控制台窗格变化提供了与控制台界面更加一致的脚本编写体验。

**工作原理的不同之处是什么？**

Windows PowerShell ISE 2.0 具有单独的命令和输出窗格。

## <a name="command-line-switches"></a>命令行开关

> 在 PowerShell 3.0 中添加

如果从命令行（通过键入 **powershell_ise.exe**）启动 Windows PowerShell ISE，则可以添加下列新的命令行开关。

- `-NoProfile`：在不运行 `$profile` 的情况下启动 Windows PowerShell ISE
- `-Help`：显示帮助窗口
- `-mta`：在多线程的单元模式下启动 Windows PowerShell ISE。 Windows PowerShell ISE 的默认操作模式是单线程的单元模式或 `-sta`。

**更改增添了什么价值？**

这些新增的命令行开关使你能够控制运行 Windows PowerShell ISE 的环境。

**工作原理的不同之处是什么？**

Windows PowerShell ISE 2.0 不识别这些命令行开关。

## <a name="new-editor-features"></a>新的编辑器功能

> 在 PowerShell 3.0 中添加

其他 Windows PowerShell ISE 编辑功能包括：

- **XML 语法着色** - Windows PowerShell ISE 现在以对 Windows PowerShell 语法进行着色的相同方法对 XML 语法进行着色。
- **大括号匹配** - Windows PowerShell ISE 包括大括号匹配和突出显示，并可以通过以下方式使用：（例如，如果已选择左大括号，则可使用 **Go to Match** 命令或 <kbd>Ctrl</kbd>+<kbd>]</kbd> 定位右大括号）。
- **大纲视图** 脚本窗格支持大纲显示，允许通过单击左边距中的 (+) 或 (-) 来实现代码段的折叠或展开。 可以使用大括号或 `#region` 和 `#endregion` 标记来标记可折叠段的开头或末尾。 若要展开或折叠所有区域，请按 <kbd>Ctrl</kbd>+<kbd>M</kbd>。
- **拖放文本编辑** - Windows PowerShell ISE 现在支持拖放文本编辑。 可以选择任何文本块，并通过将该文本拖动到编辑器或控制台中的另一个位置来移动文本。 如果拖动所选文本时按住 <kbd>Ctrl</kbd> 键不放，则释放鼠标按钮时，文本便会复制到新位置。 在此版本的 Windows PowerShell ISE 中，当你将文件拖放到 Windows PowerShell ISE 中，Windows PowerShell ISE 会打开该文件。
- **分析错误显示** - 分析错误用红色下划线指示。 当你将鼠标悬停在某个指示的错误上时，工具提示文本会显示在代码中发现的问题。
- **缩放** - 若要设置控制台内容的缩放百分比，可以使用缩放滑块（位于 Windows PowerShell ISE 窗口右下角），也可以在控制台窗格中输入命令 `$psise.options.Zoom`。
- **富文本复制和粘贴** - 在 Windows PowerShell ISE 中将内容复制到剪贴板时，会保留原选定内容的字体、大小和颜色信息。
- **块选择** - 可以通过在用鼠标选定脚本窗格中文本的同时按住 <kbd>ALT</kbd> 键，或通过按 <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>箭头键</kbd> 来选定文本块。

**更改增添了什么价值？**

这些新增的编辑功能提供更一致、更强大的编辑环境。

**工作原理的不同之处是什么？**

Windows PowerShell ISE 2.0 中不具有这些编辑增强功能。

## <a name="new-help-viewer-window"></a>新的帮助查看器窗口

> 在 PowerShell 3.0 中添加

当你将光标置于某个 cmdlet 中，或突出显示某个 cmdlet 的一部分时，按 <kbd>F1</kbd> 会打开新的帮助查看器，其中显示了有关突出显示的 cmdlet 的上下文相关帮助。 要显示 Windows PowerShell 的“关于”帮助，可在控制台窗格中键入 `operators`  ，然后按 <kbd>F1</kbd>。

使用此功能之前，必须先从 Microsoft 网站下载最新版本的 Windows PowerShell 帮助主题。 当你以管理员身份运行 Windows PowerShell ISE 时，下载“帮助”主题的最简单方法是在控制台窗格中运行 `Update-Help` cmdlet。

可以修改 <kbd>F1</kbd> 键寻找帮助的位置。 在“工具”  /“选项”  菜单中“常规设置”  选项卡上的“其他设置”  下，可以设置或清除复选框“使用本地帮助内容而非联机内容”  。 勾选此复选框后，客户端便会在模块文件夹中的已下载帮助中查找 cmdlet 帮助。 如果清除该复选框，客户端将查找联机帮助。

**更改增添了什么价值？**

在无需离开当前 cmdlet 或脚本的情况下，上下文相关帮助提供了完整的学习体验。

**工作原理的不同之处是什么？**

在 Windows PowerShell ISE 的早期版本中按 <kbd>F1</kbd> 会打开本地计算机上的帮助文件。 在 Windows PowerShell ISE 3.0 及更高版本中，会打开一个窗口，其中包含该 cmdlet 的可搜索和可配置的帮助。 此帮助体验是 Windows PowerShell ISE 3.0 的新增功能，可更新帮助是 Windows PowerShell 3.0 的新增功能。

## <a name="show-command-cmdlet"></a>Show-Command cmdlet

> 在 PowerShell 3.0 中添加

`Show-Command` cmdlet 使你能够通过填写图形表单来编写或运行 cmdlet 或函数。 该表单使用户可在图形环境中使用 Windows PowerShell。
`Show-Command` 还可以让高级脚本编写者快速创建基于 Windows PowerShell 的 GUI。

**更改增添了什么价值？**

通过在 Windows PowerShell 脚本中使用 `Show-Command`，可以为用户提供其熟悉的图形环境。 `Show-Command` 还有助于引导用户了解 Windows PowerShell。

**工作原理的不同之处是什么？**

`Show-Command` 是新的 Windows PowerShell ISE 3.0。

## <a name="see-also"></a>另请参阅

若要详细了解如何使用 Windows PowerShell ISE，请参阅[了解 Windows PowerShell 集成脚本环境](../getting-started/fundamental/exploring-the-windows-powershell-ise.md)。
