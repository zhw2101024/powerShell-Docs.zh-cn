---
title: 如何在 Windows PowerShell ISE 中创建 PowerShell 选项卡
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
---
# 如何在 Windows PowerShell ISE 中创建 PowerShell 选项卡
Windows PowerShellÂ® 集成脚本环境 (ISE) 中的选项卡让你可以在相同的应用程序中同时创建并使用多个执行环境。 每个 PowerShell 选项卡对应于单独的执行环境或会话。

> [!NOTE]
> 在一个选项卡中创建的变量、函数和别名不会延续到另一个。 它们属于不同的 Windows PowerShell 会话。

使用下列步骤打开或关闭 Windows PowerShell 中的选项卡。 若要重命名选项卡，在 Windows PowerShell 选项卡脚本对象上设置 [DisplayName](https://technet.microsoft.com/en-us/library/a9b58556-951b-4f48-b3ae-b351b7564360#Displayname) 属性。

## 创建和使用新的 PowerShell 选项卡
在“文件”菜单上，单击“新建 PowerShell 选项卡”。 新的 PowerShell 选项卡始终作为活动窗口打开。 PowerShell 选项卡按打开顺序进行递增编号。 每个选项卡都与其自己的 Windows PowerShell 控制台窗口相关联。 你一次可以最多打开 32 个具有其各自会话的 PowerShell 选项卡（在 Windows PowerShell ISE 2.0 中的上限为 8 个）。

请注意，单击工具栏上的“新建”或“打开”图标不会创建新的具有单独会话的选项卡。  相反，这些按钮将在带有会话的当前处于活动状态的选项卡上打开新的或现有脚本文件。 你可以通过每个选项卡和会话打开多个脚本文件。 适用于会话的脚本选项卡仅当相关联的会话处于活动状态时，才显示在会话选项卡下方。

若要使 PowerShell 选项卡处于活动状态，请单击选项卡。 若要从所有打开的 PowerShell 选项卡中进行选择，请在“视图”菜单上，单击你想要使用 PowerShell 选项卡。

## 创建和使用新的远程 PowerShell 选项卡
在“文件”菜单上，单击“新建远程 PowerShell 选项卡”，以在远程计算机上建立会话。 将出现一个对话框，提示你输入建立远程连接所需的详细信息。 远程选项卡功能与本地 PowerShell 选项卡类似，但命令和脚本在远程计算机上运行。

## 关闭 PowerShell 选项卡
若要关闭选项卡，你可以使用以下任一技巧：

-   单击要关闭的选项卡。

-   在“文件”菜单上，单击“关闭 PowerShell 选项卡”，或单击活动选项卡上的“关闭”按钮 (**X**) 以关闭选项卡。

如果你在将关闭的 PowerShell 选项卡中打开了未保存的文件，系统会提示你保存或丢弃这些文件。 有关如何保存脚本的详细信息，请参阅[如何保存脚本](https://technet.microsoft.com/en-us/library/162f594d-efd3-4234-9960-45e56e6eadc8).

## 另请参阅
[使用 Windows PowerShell ISE](Using-the-Windows-PowerShell-ISE.md)
[如何在 Windows PowerShell ISE 中使用控制台窗格](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)



<!--HONumber=May16_HO2-->


