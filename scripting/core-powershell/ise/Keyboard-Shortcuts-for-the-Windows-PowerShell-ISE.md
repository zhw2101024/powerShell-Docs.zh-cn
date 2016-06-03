---
title: Windows PowerShell ISE 的键盘快捷方式
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8328b946-0f02-4ef4-ac28-2743a1b4043b
---
# Windows PowerShell ISE 的键盘快捷方式
使用以下键盘快捷方式在 Windows PowerShellÂ® 集成脚本环境 (ISE) 中执行操作。 Windows PowerShell ISE 可作为 Windows Server 和 Windows 客户端操作系统的一部分，但是也可作为 [Windows Management Framework 4.0 下载包](http://go.microsoft.com/fwlink/?LinkID=293881)的一部分安装在早期的 Windows 操作系统上.

## 编辑文本的键盘快捷方式
编辑文本时可以使用以下键盘快捷方式。

|操作|键盘快捷方式|用于|
|----------|----------------------|----------|
|**帮助**|F1|脚本窗格“重要提示”：你可以指定 F1 帮助来自 Web 上的 TechNet 库或下载的帮助（请参阅“更新帮助”）。 若要选择，请单击“工具”、“选项”，然后在“常规设置”选项卡上，设置或清除“使用本地帮助内容，而不是联机内容”。|
|**复制**|CTRL+C|脚本窗格、命令窗格、输出窗格|
|**剪切**|CTRL+X|脚本窗格、命令窗格|
|**展开或折叠大纲**|CTRL+M|脚本窗格|
|**在脚本中查找**|CTRL+F|脚本窗格|
|**在脚本中查找下一个**|F3|脚本窗格|
|**在脚本中查找上一个**|SHIFT+F3|脚本窗格|
|**查找匹配的括号**|CTRL+]|脚本窗格|
|**粘贴**|CTRL+V|脚本窗格、命令窗格|
|**重做**|CTRL+Y|脚本窗格、命令窗格|
|**在脚本中替换**|CTRL+H|脚本窗格|
|**保存**|CTRL+S|脚本窗格|
|**全选**|CTRL+A|脚本窗格、命令窗格、输出窗格|
|**显示代码段**|CTRL+J|脚本窗格、命令窗格|
|**撤消**|CTRL+Z|脚本窗格、命令窗格|

## 运行脚本的键盘快捷方式
在脚本窗格中运行脚本时，可使用以下键盘快捷方式。

|操作|键盘快捷方式|
|----------|---------------------|
|**“新建”**|CTRL+N|
|**打开**|CTRL+O|
|**运行**|F5|
|**运行选定内容**|F8|
|**停止执行**|CTRL+BREAK。 可以在上下文不明确时（未选定任何文本时）使用 CTRL+C。|
|**Tab**（切换到下一个脚本）|CTRL+TAB 注意：单击 Tab 键切换到下一个脚本仅适用于你打开一个 Windows PowerShell 选项卡或打开多个 Windows PowerShell 选项卡，但焦点在脚本窗格中的情况。|
|**Tab**（切换到上一个脚本）|CTRL+SHIFT+TAB 注意：单击 Tab 键切换到上一个脚本适用于仅打开一个 Windows PowerShell 选项卡或打开多个 Windows PowerShell 选项卡，但焦点在脚本窗格中的情况。|

## 自定义视图的键盘快捷方式
可以使用以下键盘快捷方式在 Windows PowerShell ISE 中自定义视图。 可从应用程序中的所有窗格对它们进行访问。

|操作|键盘快捷方式|
|----------|---------------------|
|**转到命令 (v2) 或控制台（v3 和更高版本）窗格**|CTRL+D|
|**转到输出窗格（仅 v2）**|CTRL+SHIFT+O|
|**转到脚本窗格**|CTRL+I|
|**显示脚本窗格**|CTRL+R|
|**隐藏脚本窗格**|CTRL+R|
|**向上移动脚本窗格**|CTRL+1|
|**向右移动脚本窗格**|CTRL+2|
|**最大化脚本窗格**|CTRL+3|
|**放大**|CTRL+加号|
|**缩小**|CTRL+减号|

## 用于调试脚本的键盘快捷方式
调试脚本时，可使用以下键盘快捷方式。

|操作|键盘快捷方式|用于|
|----------|---------------------|----------|
|**运行/继续**|F5|脚本窗格，调试脚本时|
|**步入**|F11|脚本窗格，调试脚本时|
|**步越**|F10|脚本窗格，调试脚本时|
|**步出**|SHIFT+F11|脚本窗格，调试脚本时|
|**显示调用堆栈**|CTRL+SHIFT+D|脚本窗格，调试脚本时|
|**列出断点**|CTRL+SHIFT+L|脚本窗格，调试脚本时|
|**切换断点**|F9|脚本窗格，调试脚本时|
|**移除所有断点**|CTRL+SHIFT+F9|脚本窗格，调试脚本时|
|**停止调试器**|SHIFT+F5|脚本窗格，调试脚本时|

> [!NOTE]
> 在 Windows PowerShell ISE 中调试脚本时，也可以使用为 Windows PowerShell 控制台而设计的键盘快捷方式。 若要使用这些快捷方式，必须在命令窗格中键入该快捷方式并按 ENTER。

|操作|键盘快捷方式|用于|
|----------|---------------------|----------|
|**继续**|C|控制台窗格，调试脚本时|
|**步入**|S|控制台窗格，调试脚本时|
|**步越**|V|控制台窗格，调试脚本时|
|**步出**|O|控制台窗格，调试脚本时|
|重复上一命令（用于步入或步越）|Enter|控制台窗格，调试脚本时|
|**显示调用堆栈**|K|控制台窗格，调试脚本时|
|**停止调试**|Q|控制台窗格，调试脚本时|
|**列出脚本**|L|控制台窗格，调试脚本时|
|**显示控制台调试命令**|H 或 ?|控制台窗格，调试脚本时|

## Windows PowerShell 选项卡的键盘快捷方式
使用 Windows PowerShell 选项卡时，可使用以下键盘快捷方式。

|操作|键盘快捷方式|
|----------|---------------------|
|**关闭 PowerShell 选项卡**|CTRL+W|
|**新建 PowerShell 选项卡**|CTRL+T|
|**上一个 PowerShell 选项卡**|CTRL+SHIFT+TAB。 此快捷键仅在所有 Windows PowerShell 选项卡上都未打开任何文件时可用。|
|**下一个 Windows PowerShell 选项卡**|CTRL+TAB。 此快捷键仅在所有 Windows PowerShell 选项卡上都未打开任何文件时可用。|

## 启动和退出的键盘快捷方式
可以使用以下键盘快捷方式来启动 Windows PowerShell 控制台 (PowerShell.exe) 或退出 Windows PowerShell ISE。

|操作|键盘快捷方式|
|----------|---------------------|
|**退出**|ALT+F4|
|**启动 PowerShell.exe**（Windows PowerShell 控制台）|CTRL+SHIFT+P|

## 另请参阅
[PowerShell 杂志：Windows PowerShell ISE 键盘快捷键的完整列表](http://www.powershellmagazine.com/2013/01/29/the-complete-list-of-powershell-ise-3-0-keyboard-shortcuts/)



<!--HONumber=May16_HO2-->


