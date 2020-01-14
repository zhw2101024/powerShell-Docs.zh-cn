---
ms.date: 01/02/2020
keywords: powershell,cmdlet
title: 如何在 Windows PowerShell ISE 中调试脚本
ms.openlocfilehash: c5da80f3e0e013448533c80bbe1957a301be38f5
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737111"
---
# <a name="how-to-debug-scripts-in-windows-powershell-ise"></a>如何在 Windows PowerShell ISE 中调试脚本

本文介绍了如何使用 Windows PowerShell 集成脚本环境 (ISE) 直观调试功能，在本地计算机上调试脚本。

## <a name="how-to-manage-breakpoints"></a>如何管理断点

断点是脚本中你想要操作暂停的指定位置，这样你可以检查变量的当前状态和脚本运行的环境。
一旦你的脚本被断点暂停，你可以在控制台窗格中运行命令来检查你的脚本状态。 你可以输出变量或运行其他命令。 甚至可以修改对正在运行的脚本的上下文可见的任何变量的值。 检查完你想要查看的内容后，可以恢复该脚本的运行。

可以在 Windows PowerShell 调试环境中设置三种类型的断点：

1. 行断点   在脚本运行期间，当达到所指定的行时，脚本暂停

1. **变量断点。** 每当指定变量的值发生变化时，脚本就会暂停。

1. **命令断点。** 在脚本运行期间，每当要运行指定命令时，脚本暂停。 它可以包括参数，以便仅对所需操作进一步筛选断点。 该命令还可以是你创建的函数。

其中，在 Windows PowerShell ISE 调试环境中，只有行断点可以通过使用菜单或键盘快捷方式进行设置。 可以设置其他两种类型的断点，但应通过使用 [Set-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Set-PSBreakpoint.md) cmdlet 从控制台窗格中进行设置。 本部分介绍了如何通过使用菜单（若有）在 Windows PowerShell ISE 中执行调试任务，并通过脚本从控制台窗格中执行更广泛的命令。

### <a name="to-set-a-breakpoint"></a>设置断点

仅当保存脚本后，才可以在其中设置断点。 右键单击你想要设置行断点的行，然后单击“**切换断点**”。 或者，单击你想要设置的行断点所在的行，然后按 <kbd>F9</kbd>，或在“调试”菜单上，单击“切换断点”。  

以下脚本是如何通过使用 [Set-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Set-PSBreakpoint.md) cmdlet 从控制台窗格中设置变量断点的示例。

```powershell
# This command sets a breakpoint on the Server variable in the Sample.ps1 script.
Set-PSBreakpoint -Script sample.ps1 -Variable Server
```

### <a name="list-all-breakpoints"></a>列出所有断点

在当前 Windows PowerShell 会话中显示所有断点。

在“调试”菜单上，单击“列表断点”。   以下脚本是如何通过使用 [Get-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Get-PSBreakpoint.md) cmdlet 从控制台窗格中列出所有断点的示例。

```powershell
# This command lists all breakpoints in the current session.
Get-PSBreakpoint
```

### <a name="remove-a-breakpoint"></a>移除断点

移除断点会将其删除。

如果你认为稍后还可能再次使用，请考虑改为[禁用断点](#disable-a-breakpoint)。 右键单击你想要移除的断点所在的行，然后单击“切换断点”。 
或者，单击你想要移除的断点所在的行，然后在“调试”菜单上，单击“切换断点”。   以下脚本是如何通过使用 [Remove-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Remove-PSBreakpoint.md) cmdlet 从控制台窗格中移除具有指定 ID 的断点的示例。

```powershell
# This command deletes the breakpoint with breakpoint ID 2.
Remove-PSBreakpoint -Id 2
```

### <a name="remove-all-breakpoints"></a>移除所有断点

若要移除在当前会话中定义的所有断点，在“调试”菜单上，单击“移除所有断点”。  

以下脚本是如何通过使用 [Remove-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Remove-PSBreakpoint.md) cmdlet 从控制台窗格中移除所有断点的示例。

```powershell
# This command deletes all of the breakpoints in the current session.
Get-PSBreakpoint | Remove-PSBreakpoint
```

### <a name="disable-a-breakpoint"></a>禁用断点

禁用断点不会将断点移除；只是会将其关闭，直至启用。 若要禁用特定行断点，右键单击你想要禁用的行断点所在的行，然后单击“**切换断点**”。 或者，单击你想要禁用的断点所在的行，然后按 <kbd>F9</kbd>，或在“调试”菜单上，单击“禁用断点”。   以下脚本是如何通过使用 [Disable-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Disable-PSBreakpoint.md) cmdlet 从控制台窗格中移除具有指定 ID 的断点的示例。

```powershell
# This command disables the breakpoint with breakpoint ID 0.
Disable-PSBreakpoint -Id 0
```

### <a name="disable-all-breakpoints"></a>禁用所有断点

禁用断点不会将断点移除；只是会将其关闭，直至启用。 若要禁用在当前会话中的所有断点，在“调试”菜单上，单击“禁用所有断点”。   以下脚本是如何通过使用 [Disable-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Disable-PSBreakpoint.md) cmdlet 从控制台窗格中禁用所有断点的示例。

```powershell
# This command disables all breakpoints in the current session.
# You can abbreviate this command as: "gbp | dbp".
Get-PSBreakpoint | Disable-PSBreakpoint
```

### <a name="enable-a-breakpoint"></a>启用断点

若要启用特定断点，右键单击你想要启用的断点所在的行，然后单击“**启用断点**”。 或者，单击你想要启用的断点所在的行，然后按 <kbd>F9</kbd>，或在“调试”菜单上，单击“启用断点”。   以下脚本是如何通过使用 [Enable-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Enable-PSBreakpoint.md) cmdlet 从控制台窗格中启用特定断点的示例。

```powershell
# This command enables breakpoints with breakpoint IDs 0, 1, and 5.
Enable-PSBreakpoint -Id 0, 1, 5
```

### <a name="enable-all-breakpoints"></a>启用所有断点

若要启用在当前会话中定义的所有断点，在“调试”菜单上，单击“启用所有断点”。   以下脚本是如何通过使用 [Enable-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Enable-PSBreakpoint.md) cmdlet 从控制台窗格中启用所有断点的示例。

```powershell
# This command enables all breakpoints in the current session.
# You can abbreviate the command by using their aliases: "gbp | ebp".
Get-PSBreakpoint | Enable-PSBreakpoint
```

## <a name="how-to-manage-a-debugging-session"></a>如何管理调试会话

开始调试之前，必须设置一个或多个断点。 你不能设置一个断点，除非已保存你想要调试的脚本。 有关如何设置断点的说明，请参阅[如何管理断点](#how-to-manage-breakpoints)或 [Set-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Set-PSBreakpoint.md)。
开始调试后，将无法编辑脚本，除非停止调试。 运行之前，将自动保存设置有一个或多个断点的脚本。

### <a name="to-start-debugging"></a>启动调试

按 <kbd>F5</kbd> 或在工具栏上，单击“**运行脚本**”图标，或在“**调试**”菜单上，单击“**运行/继续**”。 脚本将一直运行，直到它遇到第一个断点。 它将在此处暂停操作，并突出显示它暂停时所在的行。

### <a name="to-continue-debugging"></a>继续调试

按 <kbd>F5</kbd> 或在工具栏上，单击“运行脚本”图标，或在“调试”菜单上，单击“运行/继续”或在控制台窗格中，键入 `C`，然后按 <kbd>ENTER</kbd>。    这将导致脚本继续运行到下一个断点，或如果接下来没有遇到任何断点的话运行到脚本的末尾。

### <a name="to-view-the-call-stack"></a>查看调用堆栈

调用堆栈会显示脚本中的当前运行位置。 如果脚本在由其他函数调用的函数中运行，则会由输出中的附加行在显示中表示。 最底行显示原始脚本以及脚本中调用函数所在的行。 下一行显示该函数以及函数中可能调用了另一个函数所在的行。 最顶行显示设置了断点的当前行的当前上下文。

若要在暂停时查看当前调用堆栈，请按 <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>，或在“调试”菜单上单击“显示调用堆栈”，或在控制台窗格中键入 `K`，然后按 <kbd>ENTER</kbd>。  

### <a name="to-stop-debugging"></a>停止调试

按 <kbd>SHIFT</kbd>+<kbd>F5</kbd>，或在“调试”菜单上单击“停止调试器”，或在控制台窗格中键入 `Q`，然后按 <kbd>ENTER</kbd>。  

## <a name="how-to-step-over-step-into-and-step-out-while-debugging"></a>如何在调试过程中步越、步入和步出

单步执行是一次运行一条语句的过程。 你可以在一个代码行上停止，然后检查变量的值和系统状态。 下表描述了常见的调试任务，如步越、步入和步出。

| 调试任务 |                                                                                                                   说明                                                                                                                    |                                                      如何在 PowerShell ISE 中完成它                                                       |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| **步入**  | 执行当前的语句，然后在下一个语句处停止。 如果当前语句是一个函数或脚本调用，则调试器将单步调试该函数或脚本，或者停止在下一条语句上。                      | 按 <kbd>F11</kbd>，或在“调试”菜单上，单击“步入”，或者，在控制台窗格中，键入 `S`，然后按 <kbd>ENTER</kbd>。                   |
| **步越**  | 执行当前的语句，然后在下一个语句处停止。 如果当前语句是函数或脚本调用，调试器会执行整个函数或脚本，并在函数调用后的下一个语句处停止。 | 按 <kbd>F10</kbd>，或在“调试”菜单上，单击“步越”，或者，在控制台窗格中，键入 `V`，然后按 <kbd>ENTER</kbd>。                   |
| **步出**   | 跳出当前函数，如果函数是嵌套的则返回上一级。 如果在主正文中，脚本将执行到末尾，或到下一个断点。 将执行跳过的语句，但不会单步遍历。                   | 按 <kbd>SHIFT</kbd>+<kbd>F11</kbd>，或在“调试”菜单上单击“步出”，或在控制台窗格中键入 `O`，然后按 <kbd>ENTER</kbd>。   |
| **继续**   | 继续执行到结束，或到下一个断点。 将执行已跳过的函数和调用，但不会进行单步遍历。                                                                                                          | 按 <kbd>F5</kbd>，或在“调试”菜单上，单击“运行/继续”，或者，在控制台窗格中，键入 `C`，然后按 <kbd>ENTER</kbd>。                 |

## <a name="how-to-display-the-values-of-variables-while-debugging"></a>如何在调试时显示变量的值

单步遍历代码时，可以在脚本中显示变量的当前值。

### <a name="to-display-the-values-of-standard-variables"></a>显示标准变量的值

使用下列方法之一：

- 在脚本窗格中，将鼠标悬停在变量上，以在工具提示中显示它的值。

- 在控制台窗格中，键入变量的名称并按 <kbd>ENTER</kbd>。

ISE 中的所有窗格始终位于同一作用域中。 因此，调试脚本时，你在控制台窗格中键入的命令在脚本作用域中运行。 这样，你便可以使用控制台窗格查找变量的值，并调用仅在脚本中定义的函数。

### <a name="to-display-the-values-of-automatic-variables"></a>显示自动变量的值

调试脚本时，可以使用前述方法显示几乎所有变量的值。 但是，这些方法不适用于以下自动变量。

- `$_`

- `$Input`

- `$MyInvocation`

- `$PSBoundParameters`

- `$Args`

如果你尝试显示这些变量中的任何一个的值，你将获取调试器使用的内部管道中变量的值，而不是脚本中变量的值。 对于一些变量（`$_`、`$Input`、`$MyInvocation`、`$PSBoundParameters` 和 `$Args`），可以使用以下方法解决此问题：

1. 在脚本中，将自动变量的值分配给一个新变量。

1. 通过将鼠标悬停在脚本窗格中新变量上，或通过在控制台窗格中键入新变量来显示新变量的值。

例如，若要显示 `$MyInvocation` 变量的值，在脚本中，将该值分配给一个新变量（如 `$scriptName`），然后将鼠标悬停在 `$scriptName` 变量上，或键入此变量以显示其值。

```powershell
# In C:\ps-test\MyScript.ps1
$scriptName = $MyInvocation.MyCommand.Path
```

```PowerShell
# In the Console Pane:
.\MyScript.ps1
$scriptName
```

```Output
C:\ps-test\MyScript.ps1
```

## <a name="see-also"></a>另请参阅

- [探究 Windows PowerShell ISE](exploring-the-windows-powershell-ise.md)
