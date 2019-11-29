---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Windows PowerShell ISE 简介
ms.openlocfilehash: 1723c11f38966cfffec9a6b3e4cb7b2304f19e7a
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416290"
---
# <a name="the-windows-powershell-ise"></a>Windows PowerShell ISE

Windows PowerShell 集成脚本环境 (ISE) 是 Windows PowerShell 的主机应用程序。 在 ISE 中，可以在单个基于 Windows 的图形用户界面中运行命令并编写、测试和调试脚本。 ISE 提供多行编辑、Tab 自动补全、语法颜色设置、选择性执行、上下文相关帮助以及对从右到左语言的支持。 将菜单项和键盘快捷方式映射到许多将会在 Windows PowerShell 控制台中执行的相同任务。 例如，在 ISE 中调试脚本时，可以右键单击编辑窗格中的代码行来设置断点。

## <a name="support"></a>支持

ISE 先随 Windows PowerShell V2 一起引入，然后随 PowerShell V3 一起重新设计。 包括 Windows PowerShell V5.1 在内的所有支持的 Windows PowerShell 版本都支持 ISE。

> [!NOTE]
> PowerShell ISE 不再处于主动功能开发状态。 作为 Windows 的随附组件，它仍会获得安全性和高优先级服务修补程序的官方支持。
> 目前没有从 Windows 中删除 ISE 的计划。
>
> PowerShell v6 及更高版本中不支持 ISE。 寻求替换 ISE 的用户应使用 [Visual Studio Code](https://code.visualstudio.com/) 和 [PowerShell 扩展](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell)。

## <a name="key-features"></a>关键功能

Windows PowerShell ISE 中的关键功能包括：

- 多行编辑：若要在“命令”窗格中的当前行下插入一个空行，请按 <kbd>SHIFT</kbd>+<kbd>ENTER</kbd>。
- 选择性执行：要运行部分脚本，请选择要运行的文本，然后单击“运行脚本”按钮  。 或者，按 <kbd>F5</kbd>。
- 上下文相关帮助：键入 `Invoke-Item`，然后按 <kbd>F1</kbd>。 帮助文件将打开到 `Invoke-Item` cmdlet 的文章。

Windows PowerShell ISE 允许你自定义其外观的某些方面。 它还具有其自己的 Windows PowerShell 配置文件脚本。

## <a name="to-start-the-windows-powershell-ise"></a>启动 Windows PowerShell ISE

单击“开始”  ，选择“Windows PowerShell”  ，然后单击“Windows PowerShell ISE”  。
或者，可以在任何命令 shell 或“运行”框中键入 `powershell_ise.exe`。

## <a name="to-get-help-in-the-windows-powershell-ise"></a>在 Windows PowerShell ISE 中获取帮助

在“帮助”菜单上，单击“Windows PowerShell 帮助”。   或者，按 <kbd>F1</kbd>。 打开的文件介绍了 Windows PowerShell ISE 和 Windows PowerShell，其中包括 `Get-Help` cmdlet 中提供的所有帮助。
