---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 如何在脚本窗格和控制台窗格中使用 Tab 自动补全
ms.openlocfilehash: 9fcb85668673adb1de596660d37e56f6607a4064
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030994"
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a>如何在脚本窗格和控制台窗格中使用 Tab 自动补全

在脚本窗格或在命令窗格中进行键入时，Tab 自动补全将提供自动帮助。 使用以下步骤来利用此功能：

## <a name="to-automatically-complete-a-command-entry"></a>自动完成命令输入

在命令窗格或脚本窗格中，键入命令的几个字符，然后按 TAB 以选择所需补全文本。 如果有多个项以你最初键入的文本开头，那么继续按 Tab，直到出现所需的项。 Tab 自动补全可以帮助键入 cmdlet 名、参数名、变量名、对象属性名或文件路径。

> [!NOTE]
> 在脚本窗格中，仅当你编辑 .ps1、.psd1 或 .psm1 文件时，按 TAB 才会自动完成命令。 在命令窗格中键入时，Tab 自动补全随时都起作用。

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a>自动完成 cmdlet 参数输入

在命令窗格或脚本窗格中，键入 cmdlet 后跟一个短划线，然后按 TAB 键。

例如，键入 `Get-Process -`，然后多次按 TAB 键以显示 cmdlet 的每个参数。

## <a name="see-also"></a>另请参阅

- [Windows PowerShell ISE 简介](Introducing-the-Windows-PowerShell-ISE.md)
- [如何创建 PowerShell 选项卡](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)
