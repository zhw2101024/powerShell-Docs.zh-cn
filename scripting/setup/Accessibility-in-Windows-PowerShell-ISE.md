---
title:  Windows PowerShell ISE 中的辅助功能
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  a078f9d1-dd6b-4323-b16d-0622cd993aa8
---

# Windows PowerShell ISE 中的辅助功能
本主题介绍 Windows PowerShellÂ® 集成脚本环境 (ISE) 的辅助功能，也许对你有所帮助。

* [如何更改控制台和脚本窗格的大小和位置](#bkmk_1)
* [编辑文本的键盘快捷方式](#bkmk_2)
* [运行脚本的键盘快捷方式](#bkmk_3)
* [自定义视图的键盘快捷方式](#bkmk_4)
* [用于调试脚本的键盘快捷方式](#bkmk_5)
* [Windows PowerShell 选项卡的键盘快捷方式](#bkmk_6)
* [启动和退出的键盘快捷方式](#bkmk_7)

Microsoft 致力于使其产品和服务更便于每个人使用。 下列主题提供有关使 Windows PowerShell ISE 更便于残障人士访问的功能、产品和服务的信息。

Windows PowerShell ISE 支持高对比度模式。 为方便有视觉障碍的用户，通过用于管理断点的 cmdlet（例如 [Get-PSBreakpoint](https://technet.microsoft.com/en-us/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) 和 [Set-PSBreakpoint](https://technet.microsoft.com/en-us/library/6afd5d2c-a285-4796-8607-3cbf49471420)）提供断点信息。 有关详细信息，请参阅[如何在 Windows PowerShell ISE 中调试脚本](../core-powershell/ise/How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md#bkmk_1)中的“如何管理断点”。 除了 Microsoft Windows 中的辅助功能和实用工具外，以下功能也能使残障人士更轻松地访问 Windows PowerShell ISE：

-   键盘快捷方式

-   语法着色表和使用 [$psISE.Options](https://technet.microsoft.com/en-us/library/75e2a76f-f3d1-490b-ad5d-e3829946aabb) 脚本对象修改多个其他颜色设置的能力。

-   文字大小更改

## <a name="bkmk_1"></a>如何更改控制台和脚本窗格的大小和位置
可以使用以下步骤更改控制台窗格和脚本窗格的大小和位置。 再次打开 Windows PowerShell ISE 时，将会保留你对大小和位置所做的更改。

### 调整脚本窗格和控制台窗格的大小

1.  将鼠标指针放在脚本窗格和控制台窗格之间的拆分行上。

2.  当鼠标指针更改为双向箭头时，拖动边框来更改窗格的大小。

### 移动脚本窗格和控制台窗格
执行下列操作之一：

-   若要将脚本窗格移动到命令和输出窗格上方，请按 **CTRL+1**，或单击工具栏上的“显示脚本窗格顶部”图标，或单击“视图”菜单上的“显示脚本窗格顶部”。

-   若要将脚本窗格移动到控制台窗格的右侧，请按 **CTRL+2**，或单击工具栏上的“显示脚本窗格右侧”图标，或单击“视图”菜单上的“显示脚本窗格右侧”。

-   若要最大化脚本窗格，请按 **CTRL+3**，或单击工具栏上的“显示最大化脚本窗格”图标，或单击“视图”菜单上的“显示最大化脚本窗格”。

-   若要最大化控制台窗格并隐藏脚本窗格，请在选项卡行的最右侧边缘上单击“隐藏脚本窗格”图标，在“视图”菜单上单击以取消选择“显示脚本窗格”菜单选项。

-   若要在控制台窗格最大化时显示脚本窗格，请在选项卡行的最右侧边缘上单击“隐藏脚本窗格”图标，或在“视图”菜单上单击以选择“显示脚本窗格”菜单选项。

## <a name="bkmk_2"></a>编辑文本的键盘快捷方式
编辑文本时可以使用以下键盘快捷方式。

|操作|键盘快捷方式|用于|
|----------|----------------------|----------|
|**复制**|CTRL+C|脚本窗格、命令窗格、输出窗格|
|**剪切**|CTRL+X|脚本窗格、命令窗格|
|**在脚本中查找**|CTRL+F|脚本窗格|
|**在脚本中查找下一个**|F3|脚本窗格|
|**在脚本中查找上一个**|SHIFT+F3|脚本窗格|
|**粘贴**|CTRL+V|脚本窗格、命令窗格|
|**重做**|CTRL+Y|脚本窗格、命令窗格|
|**在脚本中替换**|CTRL+H|脚本窗格|
|**保存**|CTRL+S|脚本窗格|
|**全选**|CTRL+A|脚本窗格、命令窗格、输出窗格|
|**撤消**|CTRL+Z|脚本窗格、命令窗格|

## <a name="bkmk_3"></a>运行脚本的键盘快捷方式
在脚本窗格中运行脚本时，可使用以下键盘快捷方式。

|操作|键盘快捷方式|
|----------|---------------------|
|**“新建”**|CTRL+N|
|**打开**|CTRL+O|
|**运行**|F5|
|**运行选定内容**|F8|
|**停止执行**|CTRL+BREAK。 可以在上下文不明确时（未选定任何文本时）使用 CTRL+C。|
|**Tab**（切换到下一个脚本）|CTRL+TAB **注意：**仅当打开单个 PowerShell 选项卡时，或打开多个 PowerShell 选项卡而焦点位于脚本窗格中时，切换到下一个脚本才有效。|
|**Tab**（切换到上一个脚本）|CTRL+SHIFT+TAB **注意：**仅当打开单个 PowerShell 选项卡时，或打开多个 PowerShell 选项卡而焦点位于脚本窗格中时，切换到上一个脚本才有效。|

## <a name="bkmk_4"></a>自定义视图的键盘快捷方式
可以使用以下键盘快捷方式在 Windows PowerShell ISE 中自定义视图。 可从应用程序中的所有窗格对它们进行访问。

|操作|键盘快捷方式|
|----------|---------------------|
|**转到命令窗格**|CTRL+D|
|**转到输出窗格**|CTRL+SHIFT+O|
|**转到脚本窗格**|CTRL+I|
|**显示脚本窗格**|CTRL+R|
|**隐藏脚本窗格**|CTRL+R|
||
|**向上移动脚本窗格**|CTRL+1|
|**向右移动脚本窗格**|CTRL+2|
|**最大化脚本窗格**|CTRL+3|
|**放大**|CTRL+加号|
|**缩小**|CTRL+减号|

## <a name="bkmk_5"></a>用于调试脚本的键盘快捷方式
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
|**继续**|C|命令窗格，调试脚本时|
|**步入**|S|命令窗格，调试脚本时|
|**步越**|V|命令窗格，调试脚本时|
|**步出**|O|命令窗格，调试脚本时|
|重复上一命令（用于步入或步越）|Enter|命令窗格，调试脚本时|
|**显示调用堆栈**|K|命令窗格，调试脚本时|
|**停止调试**|Q|命令窗格，调试脚本时|
|**列出脚本**|L|命令窗格，调试脚本时|
|**显示控制台调试命令**|H 或 ?|命令窗格，调试脚本时|

## <a name="bkmk_6"></a>Windows PowerShell 选项卡的键盘快捷方式
使用 Windows PowerShell 选项卡时，可使用以下键盘快捷方式。

|操作|键盘快捷方式|
|----------|---------------------|
|**关闭 PowerShell 选项卡**|CTRL+W|
|**新建 PowerShell 选项卡**|CTRL+T|
|**上一个 PowerShell 选项卡**|CTRL+SHIFT+TAB。 此快捷方式仅在任意 PowerShell 选项卡上都未打开任何文件时起作用。|
|**下一个 Windows PowerShell 选项卡**|CTRL+TAB。 此快捷方式仅在任意 PowerShell 选项卡上都未打开任何文件时起作用。|

## <a name="bkmk_7"></a>启动和退出的键盘快捷方式
可以使用以下键盘快捷方式来启动 Windows PowerShell 控制台 (PowerShell.exe) 或退出 Windows PowerShell ISE。

|操作|键盘快捷方式|
|----------|---------------------|
|**退出**|ALT+F4|
|**启动 PowerShell.exe**（Windows PowerShell 控制台）|CTRL+SHIFT+P|

## 另请参阅
[使用 Windows PowerShell ISE](../core-powershell/ise/Using-the-Windows-PowerShell-ISE.md)



<!--HONumber=May16_HO2-->


