---
title: 探究 Windows PowerShell ISE
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e0d2c6e8-5126-40e7-a1e1-d1cff29fe94a
---
# 探究 Windows PowerShell ISE
Windows PowerShellÂ® 集成脚本环境 (ISE) 可用于创建、运行和调试命令与脚本。 Windows PowerShell ISE 包含菜单栏、Windows PowerShell 选项卡、工具栏、脚本选项卡、脚本窗格、控制台窗格、状态栏、文字大小滑块和区分上下文的帮助。

> [!NOTE]
> 以 Windows PowerShell ISE 3.0 开头的命令和输出窗格已合并为单一的控制台窗格。

## 菜单栏
菜单栏包含“文件”、“编辑”、“视图”、“工具”、“调试”、“加载项”和“帮助”菜单。 菜单上的按钮允许执行与编写和运行脚本以及在 Windows PowerShell ISE 中运行命令相关的任务。 此外，可以通过运行使用 [Windows PowerShell ISE 脚本对象模型](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md)的脚本将[外接程序工具](../../core-powershell/ise/The-ISEAddOnTool-Object.md)放置在菜单栏上.

> [!NOTE]
> 在 Windows PowerShell ISE 2.0 中，不存在“工具”和“加载项”菜单。

## Windows PowerShell 选项卡
Windows PowerShell 选项卡是 Windows PowerShell 脚本可在其中运行的环境。 可以在 Windows PowerShell ISE 中打开新的 Windows PowerShell 选项卡以在本地计算机或远程计算机上创建单独的环境。 最多可同时打开八个 PowerShell 选项卡。

## 工具栏
下面的按钮位于工具栏上。

|按钮|功能|
|----------|------------|
|**“新建”**|打开新脚本。|
|**打开**|打开现有脚本或文件。|
|**保存**|保存脚本或文件。|
|**剪切**|剪切所选文本并将其复制到剪贴板。|
|**复制**|将选择的文本复制到剪贴板。|
|**粘贴**|将剪贴板内容粘贴到光标所在位置。|
|**清除输出窗格**|清除输出窗格中的所有内容。|
|**撤消**|撤销刚才执行的操作。|
|**重做**|执行刚才撤销的操作。|
|**运行脚本**|运行脚本。|
|**运行所选项**|运行脚本的选定部分。|
|**停止执行**|停止正在运行的脚本。|
|**新建远程 PowerShell 选项卡**|创建将在远程计算机上建立会话的新 PowerShell 选项卡。 将出现一个对话框，提示你输入建立远程连接所需的详细信息。|
|**启动 PowerShell.exe**|打开 Windows PowerShell 控制台。|
|**顶部显示脚本窗格**|将脚本窗格移动到显示器顶部。|
|**右侧显示脚本窗格**|将脚本窗格移动到显示器右侧。|
|**最大化显示脚本窗格**|最大化脚本窗格。|

## 脚本选项卡
显示正在编辑的脚本的名称。 可以单击脚本选项卡以选择你想编辑的脚本。

当指向脚本选项卡时，脚本文件的完整限定路径将显示在工具提示中。

## 脚本窗格
允许创建和运行脚本。 可以在脚本窗格中打开、编辑和运行现有脚本。

## 输出窗格
显示已运行的命令和脚本的结果。 还可以在输出窗格中复制和清除内容。

## 命令窗格
允许编写命令。 可以在命令窗格中运行单行命令或多行命令。 按 SHIFT+ENTER 以输入多行命令的每一行，并在输入最后一行后按 ENTER 以执行该多行命令。 命令窗格顶部显示的提示将展示当前工作目录的路径。

## 状态栏
允许查看你运行的命令和脚本是否完成。 状态栏位于显示器最底部。 错误消息的已选部分将显示在状态栏中。

## 文字大小滑块
增大或减小屏幕上的文字大小。

## 帮助
可在 Web 上的 TechNet 库中找到有关 Windows PowerShell ISE 的帮助。 可以通过单击“帮助”菜单上的“Windows PowerShell ISE 帮助”打开帮助，或通过在任意位置（光标在脚本窗格或控制台窗格中的 cmdlet 名称上时除外）按 F1 键打开帮助。 从“帮助”菜单还可以运行 Update-Help cmdlet 和显示命令窗口，该命令窗口可显示某个 cmdlet 的所有参数并允许你在易于使用的窗体中填写参数，从而帮助你构造命令。

## 另请参阅
[使用 Windows PowerShell ISE](../../core-powershell/ise/Using-the-Windows-PowerShell-ISE.md)


<!--HONumber=May16_HO2-->


