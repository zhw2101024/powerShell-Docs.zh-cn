---
title:  PowerShell 50 ISE 中的新增功能
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  38648d47-7c27-4b37-a40e-ad29948519c2
---

# Windows PowerShell ISE 中的新增功能
本主题介绍已在 Windows PowerShellÂ® 集成脚本环境 (ISE) 的各版本中引入的新增功能和更新功能。

## <a name="overview"></a>功能描述
Windows PowerShell ISE 是一款主机应用程序，让你可以在直观的图形环境中编写、运行和测试脚本与模块。 其语法着色、Tab 补齐、可视调试、Unicode 遵从以及上下文相关帮助等主要功能可为您提供丰富的脚本编写体验。

有关 Windows PowerShell ISE 的概述，请参阅 [Windows PowerShell 集成脚本环境概述](https://technet.microsoft.com/en-us/library/3c1892c2-bf84-4cb6-af26-1f453be9e671)。

## <a name="versions"></a>Windows PowerShell ISE 中的新增功能和更改功能
下表列出了 Windows PowerShell 中此版本的 Windows PowerShell ISE 的新增功能和更改功能。

|功能/功能|Windows PowerShell ISE 4.0|Windows PowerShell ISE 3.0|Windows PowerShell ISE 2.0|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|**[Intellisense](#BKMK_Intellisense)**|X|X||
|**[代码段](#bkmk_snippets)**|X|X||
|**[外接程序工具](#BKMK_AddOnTools)**|X|X||
|**[重启管理器和自动保存](#BKMK_RestartMgr)**|X|X||
|**[控制台窗格](#BKMK_ConsolePane)**|X|X||
|**[最近使用的列表](#BKMK_MRU)**|X|X||
|**[命令行开关](#BKMK_CommandLine)**|X|X||
|**[新的编辑器功能](#BKMK_NewEditorFeatures)**|X|X||
|**[新的帮助查看器窗口](#BKMK_NewHelpViewer)**|X|X||
|**[Show-Command cmdlet](#BKMK_ShowCommand)**|X|X||

### <a name="BKMK_Intellisense"></a>Intellisense
**在 ISE 3.0 中添加**

Intellisense 是一个自动完成帮助功能，是 Windows PowerShell ISE 的一部分。 Intellisense 会在你进行键入时显示可单击的菜单，以提供可能匹配的 cmdlet、参数、参数值、文件或文件夹。

**这一更改增添了什么价值？**

添加 Intellisense 后，使用 Windows PowerShell ISE 创建脚本时，可以更容易地发现 cmdlet 和语法。 在创建新脚本时，还可以使用 Windows PowerShell ISE 了解 Windows PowerShell。

**工作原理的不同之处是什么？**

当在 Windows PowerShell ISE 3.0 或更高版本中键入 cmdlet 时，会显示一个可滚动和可点击的菜单，并可在其中浏览和选择适当的命令。

### <a name="BKMK_Snippets"></a>代码段
**在 ISE 3.0 中添加**

*代码段*是 Windows PowerShell 代码的一小部分，它可以插入到你在 Windows PowerShell ISE 中创建的脚本。 Windows PowerShell ISE 附带一组默认的代码段。 在 Windows PowerShell ISE 中工作的同时，可通过使用 **New\-Snippet** cmdlet 添加代码段。

**这一更改增添了什么价值？**

通过使用代码段，可以快速组建脚本以自动运行你的环境。

**工作原理的不同之处是什么？**

若要在 Windows PowerShell 3.0 或更高版本中使用代码段，请在**编辑**菜单上，单击**启动代码段**，或按**Ctrl\-J**。

### <a name="BKMK_AddOnTools"></a>附加工具
**在 PowerShell 3.0 中添加**

Windows PowerShell ISE 现在支持附加工具，这些工具是通过使用对象模型添加的 Windows Presentation Foundation (WPF) 控件。 外接程序工具可以在控制台窗格中垂直或水平显示。 窗格中的多个外接程序工具显示为选项卡式控件。 你还可以添加或删除由 Microsoft 以外的参与方创建的外接程序工具。 有关如何导入或删除外接程序工具的详细信息，请参阅 [Windows PowerShell ISE 操作](http://technet.microsoft.com/library/cc732148.aspx)。

**这一更改增添了什么价值？**

附加工具使你能够使用工具扩展和自定义 Windows PowerShell ISE 或使你能够向 Windows PowerShell ISE 添加功能，这些工具可以实现更好的脚本编写效果。

**工作原理的不同之处是什么？**

Windows PowerShell ISE 3.0 版及更高版本附带**命令**附加工具。 **命令**外接程序使你能够浏览 cmdlet，并使用**脚本**和**控制台**窗格并行访问有关 cmdlet 的帮助。

可通过使用**外接程序**菜单上的**打开外接程序工具网站**命令找到其他外接程序。

### <a name="BKMK_RestartMgr"></a>重启管理器和自动保存
**在 PowerShell 3.0 中添加**

Windows PowerShell ISE 每隔两分钟在单独的位置上自动保存你打开的脚本。  如果 Windows PowerShell ISE 停止工作或操作系统重新启动，则重新启动 Windows PowerShell ISE 后，它会恢复上次会话中打开的脚本（即使你未保存这些脚本）。

要更改自动保存间隔，可在控制台窗格中运行下面的命令：**$psise.Options.AutoSaveMinuteInterval**。

**这一更改增添了什么价值？**

你已经了解意外重启时将自动保存你打开的脚本，现在便可以在 Windows PowerShell ISE 中工作了。

**工作原理的不同之处是什么？**

Windows PowerShell ISE 2.0 在发生意外重启时不会自动保存脚本。

### <a name="BKMK_MRU"></a>最近使用列表
**在 PowerShell 3.0 中添加**

Windows PowerShell ISE 现在具有最近使用过的文件列表。 在 Windows PowerShell ISE 中打开文件时，文件会添加到“文件”菜单上的最近使用列表中。

若要更改最近使用列表中的文件默认数量，在控制台窗格中运行以下命令：**$psise.Options.MruCount**。

**这一更改增添了什么价值？**

现在可以使用最近使用列表轻松地访问频繁使用的文件。

**工作原理的不同之处是什么？**

Windows PowerShell ISE 2.0 不具有最近使用列表。

### <a name="BKMK_ConsolePane"></a>控制台窗格
**在 PowerShell 3.0 中添加**

第一版 Windows PowerShell ISE 中可用的单独的命令窗格和输出窗格现在合并成了一个控制台窗格。 该控制台窗格的功能和外观与典型的 Windows PowerShell 控制台类似，但经过了以下改进（本主题对其中大多数进行了介绍）。

-   用于输入文本（而非输出文本）的语法着色，包括 XML 语法

-   Intellisense

-   大括号匹配

-   错误指示

-   对 Unicode 的完全支持

-   **F1** 上下文相关帮助

-   **Ctrl+F1** 上下文相关显示命令

-   对复杂脚本和从右向左语言的支持

-   字体支持

-   缩放

-   行选择模式和块选择模式

-   当你在控制台中按“向上”箭头查看历史记录时，命令行处会保留你所键入的内容

**这一更改增添了什么价值？**

这些新增的控制台窗格变化提供了与控制台界面更加一致的脚本编写体验。

**工作原理的不同之处是什么？**

Windows PowerShell ISE 2.0 具有单独的命令和输出窗格。

### <a name="BKMK_CommandLine"></a>命令行开关
**在 PowerShell 3.0 中添加**

如果从命令行（通过键入 **Powershell\_ise.exe**）启动 Windows PowerShell ISE，则可以添加下列新的命令行开关。

-   *\-NoProfile*：在不运行 **$profile** 的情况下启动 Windows PowerShell ISE

-   *-Help*：显示帮助窗口

-   *\-mta*在多线程的单元模式下启动 Windows PowerShell ISE。 Windows PowerShell ISE 的默认操作模式是单线程的单元模式，或*\-sta*。

**这一更改增添了什么价值？**

这些新增的命令行开关使你能够控制运行 Windows PowerShell ISE 的环境。

**工作原理的不同之处是什么？**

Windows PowerShell ISE 2.0 不识别这些命令行开关。

### <a name="BKMK_NewEditorFeatures"></a>新的编辑器功能
**在 PowerShell 3.0 中添加**

其他 Windows PowerShell ISE 编辑功能包括：

-   **XML 语法着色**Windows PowerShell ISE 现在以对 Windows PowerShell 语法进行着色的相同方法对 XML 语法进行着色。

-   **大括号匹配** Windows PowerShell ISE 包括大括号匹配和突出显示，并可以通过以下方式使用：（例如，如果已选择左大括号，则可使用 **Go to Match** 命令或 **Ctrl \+ ]** 定位右大括号）。

-   **大纲视图** 脚本窗格支持大纲显示，允许通过单击左边距中的 (+) 或 (-) 来实现代码段的折叠或展开。 你可以使用大括号或 **#region** 和 **#endregion** 标记来标记可折叠段的开头或末尾。 若要展开或折叠所有区域，请按 **Ctrl+M**。

-   **拖放文本编辑**Windows PowerShell ISE 现在支持拖放文本编辑。 可以选择任何文本块，并通过将该文本拖动到编辑器或控制台中的另一个位置来移动文本。 如果拖动所选文本时按住 Ctrl 键不放，则释放鼠标按钮时，文本便会复制到新位置。 在此版本的 Windows PowerShell ISE 以及以前版本的 Windows PowerShell ISE 中，当您将文件拖放到 Windows PowerShell ISE 中，Windows PowerShell ISE 会打开该文件。

-   **分析错误显示** 分析错误用红色下划线指示。 当你将鼠标悬停在某个指示的错误上时，工具提示文本会显示在代码中发现的问题。

-   **缩放** 可以通过使用缩放滑块（位于 Windows PowerShell ISE 窗口右下角），或在控制台窗格中输入命令 **$psise.options.Zoom** 来设置控制台内容的缩放百分比。

-   **富文本复制和粘贴** 在 Windows PowerShell ISE 中将内容复制到剪贴板时，会保留原选定内容的字体、大小和颜色信息。

-   **块选择** 你可以通过在用鼠标选定脚本窗格中文本的同时按住 ALT 键，或通过按 **Alt+Shift+箭头**键来选定文本块。

**这一更改增添了什么价值？**

这些新增的编辑功能提供更一致、更强大的编辑环境。

**工作原理的不同之处是什么？**

Windows PowerShell ISE 2.0 中不具有这些编辑增强功能。

### <a name="BKMK_NewHelpViewer"></a>新的帮助查看器窗口
**在 PowerShell 3.0 中添加**

当你将光标置于某个 cmdlet 中，或突出显示某个 cmdlet 的一部分时，按 **F1** 会打开新的帮助查看器，其中显示了有关突出显示的 cmdlet 的上下文相关帮助。 要显示 Windows PowerShell 的“关于”帮助，可在控制台窗格中键入**operators**，然后按**F1**。

使用此功能之前，必须先从 Microsoft 网站下载最新版本的 Windows PowerShell 帮助主题。 当你以管理员身份运行 Windows PowerShell ISE 时，下载“帮助”主题的最简单方法是在控制台窗格中运行 **Update\-Help** cmdlet。

可以修改 **F1** 键寻找帮助的位置。 在“工具”\/“选项”菜单中“常规设置”选项卡上的“其他设置”下，可以设置或清除复选框“使用本地帮助内容而非联机内容”。 如果勾选了此复选框，客户端便会在模块文件夹中的已下载帮助中查找 cmdlet 帮助。  如果清除了该复选框，则客户端会在 TechNet 库中查找 cmdlet 帮助。

**这一更改增添了什么价值？**

在无需离开当前 cmdlet 或脚本的情况下，上下文相关帮助提供了无缝的学习体验。

**工作原理的不同之处是什么？**

在 Windows PowerShell ISE 的早期版本中按 F1 会打开本地计算机上的帮助文件。 在 Windows PowerShell ISE 3.0 及更高版本中，会打开一个窗口，其中包含该 cmdlet 的可搜索和可配置的帮助。 此帮助体验是 Windows PowerShell ISE 3.0 的新增功能，可更新帮助是 Windows PowerShell 3.0 的新增功能。

### <a name="BKMK_ShowCommand"></a>Show\-Command cmdlet
**在 PowerShell 3.0 中添加**

**Show-Command** cmdlet 使你能够通过填写图形表单来编写或运行 cmdlet 或函数。 该表单使用户可在图形环境中使用 Windows PowerShell。 **Show\-Command** 还可以让高级脚本编写者快速创建基于 Windows PowerShell 的 GUI。

**这一更改增添了什么价值？**

通过在 Windows PowerShell 脚本中使用 **Show\-Command**，可以为用户提供其熟悉的图形环境。 **Show\-Command** 还有助于引导用户了解 Windows PowerShell。

**工作原理的不同之处是什么？**

Show\-Command 是新的 Windows PowerShell ISE 3.0。

## <a name="BKMK_LINKS"></a>另请参阅
有关在 Windows PowerShell 中使用 Windows PowerShell ISE 的详细信息，请参阅以下链接。

-   [使用 Windows PowerShell 集成脚本环境](../core-powershell/ise/Using-the-Windows-PowerShell-ISE.md)

-   [TechNet Wiki 上的 ISE](http://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)

-   [脚本中心](http://technet.microsoft.com/scriptcenter/default)



<!--HONumber=May16_HO2-->


