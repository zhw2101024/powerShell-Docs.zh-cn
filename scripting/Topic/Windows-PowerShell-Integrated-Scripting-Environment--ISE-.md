---
title: Windows PowerShell 集成脚本环境 (ISE)
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f156b92d-0203-46d2-89c7-b4989d32e3d2
---
# Windows PowerShell 集成脚本环境 (ISE)
Windows PowerShell 集成脚本环境 (ISE) 是 Windows PowerShell 引擎和语言的两个主机之一。 借助它你可以采取 Windows PowerShell 控制台中不可用的方式来编写、运行并测试脚本。 ISE 添加了语法着色、Tab 自动补全、IntelliSense、可视调试和上下文相关帮助。

ISE 使你能够在控制台窗格中运行命令，但它也支持可用于同时查看脚本的源代码的窗格和可以插入到 ISE 中的其他工具。 甚至可以同时打开多个脚本窗口，当你正调试的脚本使用其他脚本或模块中定义的函数时，这将特别有用。

## <a name="BKMK_NEW"></a>新增功能
以下是最新的 PowerShell 版本中已添加到 ISE 的一些功能。

### PowerShell 3.0 中的新添功能（Windows Server 2012、Windows 8）
**IntelliSense** 通过在你进行键入时，显示匹配的 cmdlet、参数、参数值、文件或文件夹来自动完成你的命令。

**代码片段**是代码的一小部分，它可以轻松插入到你编写的脚本中。 有用的代码片段的集合包含在框中，你可以通过使用 **New-Snippet** cmdlet 添加更多的代码片段。

向 ISE 添加功能的**附加工具**可以通过编写与 [Windows PowerShell ISE 脚本对象模型](assetId:///69b047d0-da79-413e-b948-8e45d05d1f85)相交互的代码进行创建。 这些工具可以在选项卡式窗格中显示控件，或在后台以不可见的方式工作。 **命令**附加工具是一个好例子，包含在 3.0 版及更高版本中，可显示可用命令及其帮助的列表。

**重启管理器和自动保存**每两分钟会自动保存你的脚本，有助于避免在发生崩溃或意外重启时造成的工作丢失。

**最近使用列表**现在是“打开文件”菜单的一部分，方便打开你最常使用的文件。

**合并的控制台窗格**。 在以前的 ISE 版本中有独立的“命令”和“输出”窗格。 它们现在合并成单一的窗格，可以更直接地模仿你在 Windows Powershell 控制台中所见的内容。

**命令行开关**。 几个新的命令行开关使你更好地控制 ISE 的工作方式。 –NoProfile 无需运行配置文件脚本即可启动 ISE。 –Help 与 ISE 一起使用可打开帮助窗口。 –mta 以“多线程单元模式”启动 ISE。 默认为单线程。

**新编辑器功能**使创建并阅读代码更加容易：

-   **XML 语法着色**。 ISE 编辑器现在以对 Windows PowerShell 代码语法进行着色的相同方法对 XML 语法进行着色。

-   **大括号匹配** ISE [!INCLUDE[ise_2](../Token/ise_2_md.md)] 突出显示匹配的大括号，帮助你确保与你左大括号匹配的右大括号的数量正确。 使用 CTRL- [ 以查找与光标所在的左大括号匹配的右大括号。

-   **大纲视图**。 可以通过单击左边距中的加号和减号，折叠或展开代码部分。 这样会更容易地找到你在较长脚本中要查找的代码。

-   **拖放式文字编辑**。 你可以选择文本块，并将其拖动到其他位置来移动它。 如果在拖动所选文本时按住 Ctrl 键，这样就成了复制而不是移动。

-   **分析错误显示**。 Windows PowerShell 在你输入时会检查你的脚本。 如果它检测错误，会在有问题代码下面显示红色波浪线。 当你将鼠标悬停在指示的错误上时，工具提示会为你显示发现的问题。

-   **缩放**。 你可以通过使用 ISE 窗口右下角的滑块放大你的文本便于更轻松地阅读或是缩小文本以查看更大的图片。

-   **丰富的文本复制和粘贴**。 当你从 ISE 中复制到剪贴板时，所选文本的字体、大小和颜色信息都会被复制。

-   **块选择**。 你可以通过在用鼠标选定脚本窗格中文本的同时按住 ALT 键，或通过按 **Alt+Shift+箭头**键来选定块状的文本块。

### PowerShell 2.0 中的新添功能（Windows Server 2008 R2、Windows 7）
ISE 随 PowerShell v2.0 一同引入。

## 运行 Windows PowerShell ISE 的要求
ISE 可在任何运行 Windows PowerShell v2.0 或更高版本的计算机上使用。 每个 Windows 和 Windows Server 版本都包含一个 Windows PowerShell 和 ISE 版本，但你可以通过安装 Windows Management Framework 升级至最新的可用版本。 运行此搜索以查找最新的可用版本：[下载](http://www.microsoft.com/en-us/search/DownloadResults.aspx?q=%22windows%20management%20framework%22%20PowerShell&sortby=Relevancy~Descending)。 请注意：任何标记为“预览版”的条目都是预发布的代码，并不具备完整的功能。

> [!NOTE]
> 由于 [!INCLUDE[ise_2](../Token/ise_2_md.md)] 需要图形用户界面，因此你无法在 Windows Server 的服务器核心选项上运行它。

## <a name="BKMK_LINKS"></a>另请参阅
[使用 Windows PowerShell 集成脚本环境](http://technet.microsoft.com/library/cc732148.aspx)



<!--HONumber=Apr16_HO1-->


