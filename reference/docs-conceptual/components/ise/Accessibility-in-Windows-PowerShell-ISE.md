---
ms.date: 12/19/2019
keywords: powershell,cmdlet
title: Windows PowerShell ISE 中的辅助功能
ms.openlocfilehash: e618daca98d76f767a8b60a3425760bfc0bd0f64
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736277"
---
# <a name="accessibility-in-windows-powershell-ise"></a>Windows PowerShell ISE 中的辅助功能

本主题介绍 Windows PowerShell 集成脚本环境 (ISE) 的辅助功能，也许对你有所帮助。

- [如何更改控制台和脚本窗格的大小和位置](#how-to-change-the-size-and-location-of-the-console-and-script-panes)
- [编辑文本的键盘快捷方式](#keyboard-shortcuts-for-editing-text)
- [运行脚本的键盘快捷方式](#keyboard-shortcuts-for-running-scripts)
- [自定义视图的键盘快捷方式](#keyboard-shortcuts-for-customizing-the-view)
- [调试脚本的键盘快捷方式](#keyboard-shortcuts-for-debugging-scripts)
- [Windows PowerShell 选项卡的键盘快捷方式](#keyboard-shortcuts-for-windows-powershell-tabs)
- [启动和退出的键盘快捷方式](#keyboard-shortcuts-for-starting-and-exiting)
- [使用 cmdlet 管理断点](#breakpoint-management)

Microsoft 致力于使其产品和服务更便于每个人使用。 下列主题提供有关使 Windows PowerShell ISE 更便于残障人士访问的功能、产品和服务的信息。

除了 Microsoft Windows 中的辅助功能和实用工具外，以下功能也能使残障人士更轻松地访问 Windows PowerShell ISE：

- 键盘快捷方式

- 语法着色表和使用 [$psISE.Options](object-model/The-ISEOptions-Object.md) 脚本对象修改多个其他颜色设置的能力。

- 文字大小更改

## <a name="how-to-change-the-size-and-location-of-the-console-and-script-panes"></a>如何更改控制台和脚本窗格的大小和位置

可以使用以下步骤更改控制台窗格和脚本窗格的大小和位置。 再次打开 Windows PowerShell ISE 时，将会保留你对大小和位置所做的更改。

### <a name="to-resize-the-script-pane-and-console-pane"></a>调整脚本窗格和控制台窗格的大小

1. 将鼠标指针放在脚本窗格和控制台窗格之间的拆分行上。

2. 当鼠标指针更改为双向箭头时，拖动边框来更改窗格的大小。

### <a name="to-move-the-script-pane-and-console-pane"></a>移动脚本窗格和控制台窗格

执行下列操作之一：

- 若要将脚本窗格移动到控制台窗格上方，请按 <kbd>CTRL</kbd>+<kbd>1</kbd>，或单击工具栏上的“顶部显示脚本窗格”图标，或单击“视图”菜单上的“顶部显示脚本窗格”。

- 若要将脚本窗格移动到控制台窗格的右侧，请按 <kbd>CTRL</kbd>+<kbd>2</kbd>，或单击工具栏上的“右侧显示脚本窗格”图标，或单击“视图”菜单上的“右侧显示脚本窗格”。

- 若要最大化脚本窗格，请按 <kbd>CTRL</kbd>+<kbd>3</kbd>，或单击工具栏上的“最大化显示脚本窗格”图标，或单击“视图”菜单上的“最大化显示脚本窗格”。

- 若要最大化控制台窗格并隐藏脚本窗格，请在选项卡行的最右侧边缘上单击“隐藏脚本窗格”图标，在“视图”菜单上单击以取消选择“显示脚本窗格”菜单选项。

- 若要在控制台窗格最大化时显示脚本窗格，请在选项卡行的最右侧边缘上单击“隐藏脚本窗格”图标，或在“视图”菜单上单击以选择“显示脚本窗格”菜单选项。

## <a name="keyboard-shortcuts-for-editing-text"></a>编辑文本的键盘快捷方式

编辑文本时可以使用以下键盘快捷方式。

|           操作            |       键盘快捷方式       |          用于           |
| --------------------------- | ------------------------------ | ------------------------- |
| **Copy**                    | <kbd>CTRL</kbd>+<kbd>C</kbd>   | 脚本窗格、控制台窗格 |
| **剪切**                     | <kbd>CTRL</kbd>+<kbd>X</kbd>   | 脚本窗格、控制台窗格 |
| **在脚本中查找**          | <kbd>CTRL</kbd>+<kbd>F</kbd>   | 脚本窗格               |
| **在脚本中查找下一个**     | <kbd>F3</kbd>                  | 脚本窗格               |
| **在脚本中查找上一个** | <kbd>SHIFT</kbd>+<kbd>F3</kbd> | 脚本窗格               |
| **粘贴**                   | <kbd>CTRL</kbd>+<kbd>V</kbd>   | 脚本窗格、控制台窗格 |
| **重做**                    | <kbd>CTRL</kbd>+<kbd>Y</kbd>   | 脚本窗格、控制台窗格 |
| **在脚本中替换**       | <kbd>CTRL</kbd>+<kbd>H</kbd>   | 脚本窗格               |
| **保存**                    | <kbd>CTRL</kbd>+<kbd>S</kbd>   | 脚本窗格               |
| **全选**              | <kbd>CTRL</kbd>+<kbd>A</kbd>   | 脚本窗格、控制台窗格 |
| **撤消**                    | <kbd>CTRL</kbd>+<kbd>Z</kbd>   | 脚本窗格、控制台窗格 |

## <a name="keyboard-shortcuts-for-running-scripts"></a>运行脚本的键盘快捷方式

在脚本窗格中运行脚本时，可使用以下键盘快捷方式。

|            操作            |                                                                                                     键盘快捷方式                                                                                                      |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **新建**                      | <kbd>CTRL</kbd>+<kbd>N</kbd>                                                                                                                                                                                               |
| **打开**                     | <kbd>CTRL</kbd>+<kbd>O</kbd>                                                                                                                                                                                               |
| **运行**                      | <kbd>F5</kbd>                                                                                                                                                                                                              |
| **运行选定内容**            | <kbd>F8</kbd>                                                                                                                                                                                                              |
| **停止执行**           | <kbd>CTRL</kbd>+<kbd>BREAK</kbd>。 可以在上下文不明确时（未选定任何文本时）使用 <kbd>CTRL</kbd>+<kbd>C</kbd>。                                                                               |
| **Tab**（切换到下一个脚本）     | <kbd>CTRL</kbd>+<kbd>TAB</kbd> **注意：** 按 Tab 键切换到下一个脚本仅适用于打开单个 PowerShell 选项卡或打开多个 PowerShell 选项卡，但焦点在脚本窗格中的情况。                |
| **Tab**（切换到上一个脚本） | <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>TAB</kbd> **注意：** 按 Tab 键切换到上一个脚本适用于仅打开一个 PowerShell 选项卡或打开多个 PowerShell 选项卡，但焦点在脚本窗格中的情况。 |

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>自定义视图的键盘快捷方式

可以使用以下键盘快捷方式在 Windows PowerShell ISE 中自定义视图。 可从应用程序中的所有窗格对它们进行访问。

|           操作           |         键盘快捷方式        |
| -------------------------- | -------------------------------- |
| **转到控制台窗格**     | <kbd>CTRL</kbd>+<kbd>D</kbd>     |
| **转到脚本窗格**      | <kbd>CTRL</kbd>+<kbd>I</kbd>     |
| **显示脚本窗格**       | <kbd>CTRL</kbd>+<kbd>R</kbd>     |
| **隐藏脚本窗格**       | <kbd>CTRL</kbd>+<kbd>R</kbd>     |
| **向上移动脚本窗格**    | <kbd>CTRL</kbd>+<kbd>1</kbd>     |
| **向右移动脚本窗格** | <kbd>CTRL</kbd>+<kbd>2</kbd>     |
| **最大化脚本窗格**   | <kbd>CTRL</kbd>+<kbd>3</kbd>     |
| **放大**                | <kbd>CTRL</kbd>+<kbd>+</kbd>  |
| **缩小**               | <kbd>CTRL</kbd>+<kbd>-</kbd> |

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>用于调试脚本的键盘快捷方式

调试脚本时，可使用以下键盘快捷方式。

|           操作           |               键盘快捷方式                |                用于                |
| -------------------------- | ---------------------------------------------- | ------------------------------------ |
| **运行/继续**           | <kbd>F5</kbd>                                  | 脚本窗格，调试脚本时 |
| **步入**              | <kbd>F11</kbd>                                 | 脚本窗格，调试脚本时 |
| **步越**              | <kbd>F10</kbd>                                 | 脚本窗格，调试脚本时 |
| **步出**               | <kbd>SHIFT</kbd>+<kbd>F11</kbd>                | 脚本窗格，调试脚本时 |
| **显示调用堆栈**     | <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>  | 脚本窗格，调试脚本时 |
| **列出断点**       | <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>L</kbd>  | 脚本窗格，调试脚本时 |
| **切换断点**      | <kbd>F9</kbd>                                  | 脚本窗格，调试脚本时 |
| **移除所有断点** | <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>F9</kbd> | 脚本窗格，调试脚本时 |
| **停止调试器**          | <kbd>SHIFT</kbd>+<kbd>F5</kbd>                 | 脚本窗格，调试脚本时 |

> [!NOTE]
> 在 Windows PowerShell ISE 中调试脚本时，也可以使用为 Windows PowerShell 控制台而设计的键盘快捷方式。 若要使用这些快捷方式，必须在控制台窗格中输入该快捷方式并按 ENTER。

|                 操作                  |      键盘快捷方式       |                用于                 |
| --------------------------------------- | ---------------------------- | ------------------------------------- |
| **继续**                            | <kbd>C</kbd>                 | 控制台窗格，调试脚本时 |
| **步入**                           | <kbd>S</kbd>                 | 控制台窗格，调试脚本时 |
| **步越**                           | <kbd>V</kbd>                 | 控制台窗格，调试脚本时 |
| **步出**                            | <kbd>O</kbd>                 | 控制台窗格，调试脚本时 |
| **重复上一个命令**（步入/步越） | <kbd>ENTER</kbd>             | 控制台窗格，调试脚本时 |
| **显示调用堆栈**                  | <kbd>K</kbd>                 | 控制台窗格，调试脚本时 |
| **停止调试**                      | <kbd>Q</kbd>                 | 控制台窗格，调试脚本时 |
| **列出脚本**                     | <kbd>L</kbd>                 | 控制台窗格，调试脚本时 |
| **显示控制台调试命令**  | <kbd>H</kbd> 或 <kbd>?</kbd> | 控制台窗格，调试脚本时 |

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Windows PowerShell 选项卡的键盘快捷方式

使用 Windows PowerShell 选项卡时，可使用以下键盘快捷方式。

|             操作              |                                 键盘快捷方式                                  |
| ------------------------------- | ---------------------------------------------------------------------------------- |
| **关闭 PowerShell 选项卡**        | <kbd>CTRL</kbd>+<kbd>W</kbd>                                                       |
| **新建 PowerShell 选项卡**          | <kbd>CTRL</kbd>+<kbd>T</kbd>                                                       |
| **上一个 PowerShell 选项卡**     | <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>TAB</kbd>（仅在任意 PowerShell 选项卡上都未打开任何文件时）                 |
| **下一个 Windows PowerShell 选项卡** | <kbd>CTRL</kbd>+<kbd>TAB</kbd>（仅在任意 PowerShell 选项卡上都未打开任何文件时） |

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>启动和退出的键盘快捷方式

可以使用以下键盘快捷方式来启动 Windows PowerShell 控制台 (PowerShell.exe) 或退出 Windows PowerShell ISE。

|                        操作                         |               键盘快捷方式               |
| ----------------------------------------------------- | --------------------------------------------- |
| **退出**                                              | <kbd>ALT</kbd>+<kbd>F4</kbd>                  |
| **启动 PowerShell.exe**（Windows PowerShell 控制台） | <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>P</kbd> |

## <a name="breakpoint-management"></a>断点管理

为方便有视觉障碍的用户，通过用于管理断点的 cmdlet（例如 [Get-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Get-PSBreakpoint.md) 和 [Set-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Set-PSBreakpoint.md)）提供断点信息。
有关详细信息，请参阅[如何在 Windows PowerShell ISE 中调试脚本](How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md)中的“如何管理断点”。

## <a name="see-also"></a>另请参阅

[Windows PowerShell ISE 简介](Introducing-the-Windows-PowerShell-ISE.md)
