---
title: 如何在 Windows PowerShell ISE 中使用控制台窗格
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 44d67705-87c7-4a69-a53e-6471fdebb757
---
# 如何在 Windows PowerShell ISE 中使用控制台窗格
[!INCLUDE[ise_1](../Token/ise_1_md.md)] 中的控制台窗格的运行方式和独立的 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 控制台窗口完全一样。

若要在控制台窗格中运行命令，请键入命令，然后按 ENTER 键。 若要输入多个命令并且你想要按顺序执行这些命令，请在命令之间键入 SHIFT+ENTER。 有关键入命令的帮助，请参阅[如何在脚本窗格和控制台窗格中使用 Tab 自动补全](../Topic/How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md)。

若要停止某个命令，在工具栏上，单击“停止操作”，或按 CTRL+BREAK。 如果上下文是明确的，你还可以使用 CTRL+C 来停止命令。 例如，如果当前窗格中已选择了一些文本，那么 CTRL+C 将映射为复制操作。

从 [!INCLUDE[wps_2](../Token/wps_2_md.md)] V3 起，输出窗格与控制台窗格已结合。 这样的好处是能像独立的 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 控制台一样运行，并消除了两者分离时所需过程中的差异。 您可以：

-   从控制台窗格中选择文本并将其复制到剪贴板，以便在任何其他窗口中粘贴。 若要选择文本，单击输出窗格并按住鼠标，同时将鼠标拖动到你想要捕获的文本上。 你还可以按住 **SHIFT** 的同时使用光标箭头键选择文本。 然后按 CTRL+C 或单击工具栏中的“复制”图标。

-   将所选文本粘贴在当前光标位置。 单击工具栏上的“粘贴”按钮。

-   清除控制台窗格中的所有文本。 若要清除控制台窗格，你可以单击工具栏上的“清除控制台窗格”或运行 **Clear-Host** 命令或其别名 **cls**。

## 另请参阅
[使用 Windows PowerShell ISE](../Topic/Using-the-Windows-PowerShell-ISE.md)



<!--HONumber=Apr16_HO1-->


