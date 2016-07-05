---
title: "如何在 Windows PowerShell ISE 中使用控制台窗格"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 44d67705-87c7-4a69-a53e-6471fdebb757
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 29e73b1bfd8efea2b53299c52bf65117f7c535f5

---

# 如何在 Windows PowerShell ISE 中使用控制台窗格
Windows PowerShellÂ® 集成脚本环境 (ISE) 的“控制台”窗格的运行方式和独立的 Windows PowerShell ISE 控制台窗口完全一样。

若要在控制台窗格中运行命令，请键入命令，然后按 ENTER 键。 若要输入按顺序执行的多个命令，请在命令之间键入 SHIFT\+ENTER。 有关键入命令的帮助，请参阅[如何在脚本窗格和控制台窗格中使用 Tab 自动补全](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md)。

若要停止某个命令，在工具栏上单击“**停止操作**”，或按 CTRL\+BREAK。 如果上下文是明确的，还可以使用 CTRL\+C 来停止命令。 例如，如果当前窗格中已选择了一些文本，那么 CTRL\+C 将映射为复制操作。

从 Windows PowerShell v3 起，“输出”窗格与“控制台”窗格已结合。 这样的好处是能像独立的 Windows PowerShell 控制台一样运行，并消除了两者分离后所需过程的差异。 您可以：

-   从控制台窗格中选择文本并将其复制到剪贴板，以便在任何其他窗口中粘贴。 若要选择文本，单击输出窗格并按住鼠标，同时将鼠标拖动到你想要捕获的文本上。 你还可以按住 **SHIFT** 的同时使用光标箭头键选择文本。 然后按 CTRL\+C 或单击工具栏中的“**复制**”图标。

-   将所选文本粘贴在当前光标位置。 单击工具栏上的“粘贴”按钮。****

-   清除控制台窗格中的所有文本。 若要清除控制台窗格，可以单击工具栏上的“**清除控制台窗格**”图标或运行 **Clear\-Host** 命令或其别名 **cls**。

## 另请参阅
[使用 Windows PowerShell ISE](Using-the-Windows-PowerShell-ISE.md)




<!--HONumber=Jun16_HO4-->


