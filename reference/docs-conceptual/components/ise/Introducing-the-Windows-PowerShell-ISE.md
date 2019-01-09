---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Windows PowerShell ISE 简介
ms.openlocfilehash: 09a28b295855fd2a3c62bba8a681399dae3454f8
ms.sourcegitcommit: 3402a478cf118c11a5642038eb117bc76553e3ab
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53411576"
---
# <a name="the-windows-powershell-ise"></a>Windows PowerShell ISE

Windows PowerShell 集成脚本环境 (ISE) 是 Windows PowerShell 的主机应用程序。 在 ISE 中，可以运行命令并编写、 测试，并在单个基于 Windows 的图形用户界面中调试脚本。 ISE 的右到左的语言提供了多行编辑、 tab 自动补全、 语法颜色设置、 选择性执行、 上下文相关帮助和支持。 将菜单项和键盘快捷方式映射到许多将会在 Windows PowerShell 控制台中执行的相同任务。 例如，当脚本在 ISE 中调试时，您可以右键单击在编辑窗格中设置断点的代码行上。

## <a name="support"></a>支持

在 ISE 首次随 Windows PowerShell V2 和的重新设计了 PowerShell V3。 在 ISE 中所有受支持版本的 Windows PowerShell 最多和包括 Windows PowerShell V5.1 支持。 在 ISE 中，但是，处于维护模式，可能会添加任何新功能。
此外，没有 ISE 与 PowerShell v6 和更高版本的支持。 用户，他们希望一种图形工具，可用于管理 PowerShell scrips，等等，应考虑[Visual Studio Code](https://code.visualstudio.com/)。

## <a name="key-features"></a>关键功能

在 Windows PowerShell ISE 中的主要功能包括：

- 多行编辑：若要在“命令”窗格中的当前行下插入一个空行，请按 SHIFT+ENTER。
- 选择性执行：要运行部分脚本，请选择要运行的文本，然后单击“运行脚本”按钮。 或者，按 F5。
- 上下文相关帮助：键入 Invoke-Item，然后按 F1。 帮助文件将打开到 Invoke-Item cmdlet 的文章。

Windows PowerShell ISE 允许你自定义其外观的某些方面。 它还具有其自己的 Windows PowerShell 配置文件脚本。

## <a name="to-start-the-windows-powershell-ise"></a>启动 Windows PowerShell ISE

单击“开始”，选择“Windows PowerShell”，然后单击“Windows PowerShell ISE”。
或者，可以在任何命令 shell 或“运行”框中键入 `powershell_ise.exe`。

## <a name="to-get-help-in-the-windows-powershell-ise"></a>在 Windows PowerShell ISE 中获取帮助

在“帮助”菜单上，单击“Windows PowerShell 帮助”。 或者，按 F1。 打开的文件介绍了 Windows PowerShell ISE 和 Windows PowerShell，其中包括 Get-Help cmdlet 中提供的所有帮助。
