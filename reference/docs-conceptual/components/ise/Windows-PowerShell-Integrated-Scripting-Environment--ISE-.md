---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows PowerShell 集成脚本环境 (ISE)
ms.assetid: f156b92d-0203-46d2-89c7-b4989d32e3d2
ms.openlocfilehash: 3002c2cb7213b1c2d7201dddf5ff3c0651fad767
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057479"
---
# <a name="windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="cc92b-103">Windows PowerShell 集成脚本环境 (ISE)</span><span class="sxs-lookup"><span data-stu-id="cc92b-103">Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

<span data-ttu-id="cc92b-104">Windows PowerShell 集成脚本环境 (ISE) 是 Windows PowerShell 引擎和语言的两个主机之一。</span><span class="sxs-lookup"><span data-stu-id="cc92b-104">The Windows PowerShell Integrated Scripting Environment (ISE) is one of two hosts for the Windows PowerShell engine and language.</span></span> <span data-ttu-id="cc92b-105">借助它你可以采取 Windows PowerShell 控制台中不可用的方式来编写、运行并测试脚本。</span><span class="sxs-lookup"><span data-stu-id="cc92b-105">With it you can write, run, and test scripts in ways that are not available in the Windows PowerShell Console.</span></span> <span data-ttu-id="cc92b-106">ISE 添加了语法着色、Tab 自动补全、IntelliSense、可视调试和上下文相关帮助。</span><span class="sxs-lookup"><span data-stu-id="cc92b-106">The ISE adds syntax-coloring, tab completion, IntelliSense, visual debugging, and context sensitive Help.</span></span>

<span data-ttu-id="cc92b-107">ISE 使你能够在控制台窗格中运行命令，但它也支持可用于同时查看脚本的源代码的窗格和可以插入到 ISE 中的其他工具。</span><span class="sxs-lookup"><span data-stu-id="cc92b-107">The ISE lets you run commands in a console pane, but it also supports panes that you can use to simultaneously view the source code of your script and other tools that can plug into the ISE.</span></span> <span data-ttu-id="cc92b-108">甚至可以同时打开多个脚本窗口，当你正调试的脚本使用其他脚本或模块中定义的函数时，这将特别有用。</span><span class="sxs-lookup"><span data-stu-id="cc92b-108">You can even open up multiple script windows at the same time, which is especially helpful when you are debugging a script that uses functions defined in other scripts or modules.</span></span>

## <a name="whats-new"></a><span data-ttu-id="cc92b-109">新增功能</span><span class="sxs-lookup"><span data-stu-id="cc92b-109">What’s New</span></span>

<span data-ttu-id="cc92b-110">以下是最新的 PowerShell 版本中已添加到 ISE 的一些功能。</span><span class="sxs-lookup"><span data-stu-id="cc92b-110">Here are some of the features that have been added to the ISE in the most recent releases of PowerShell.</span></span>

### <a name="added-in-powershell-30-windows-server-2012-windows-8"></a><span data-ttu-id="cc92b-111">PowerShell 3.0 中的新添功能（Windows Server 2012、Windows 8）</span><span class="sxs-lookup"><span data-stu-id="cc92b-111">Added in PowerShell 3.0 (Windows Server 2012, Windows 8)</span></span>

<span data-ttu-id="cc92b-112">**IntelliSense** 通过在你进行键入时，显示匹配的 cmdlet、参数、参数值、文件或文件夹来自动完成你的命令。</span><span class="sxs-lookup"><span data-stu-id="cc92b-112">**IntelliSense** automatically completes your commands by displaying menus of matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="cc92b-113">**代码片段**是代码的一小部分，它可以轻松插入到你编写的脚本中。</span><span class="sxs-lookup"><span data-stu-id="cc92b-113">**Snippets** are short sections of code that you can easily insert into the scripts your write.</span></span> <span data-ttu-id="cc92b-114">有用的代码片段的集合包含在框中，你可以通过使用 **New-Snippet** cmdlet 添加更多的代码片段。</span><span class="sxs-lookup"><span data-stu-id="cc92b-114">A collection of useful snippets is included in the box and you can more by using the **New-Snippet** cmdlet.</span></span>

<span data-ttu-id="cc92b-115">向 ISE 添加功能的**附加工具**可以通过编写与 [Windows PowerShell ISE 脚本对象模型](../../core-powershell/ise/The-ISE-Object-Model-Hierarchy.md)相交互的代码进行创建。</span><span class="sxs-lookup"><span data-stu-id="cc92b-115">**Add-on tools** that add features to the ISE can be created by writing code that interacts with [The Windows PowerShell ISE Scripting Object Model](../../core-powershell/ise/The-ISE-Object-Model-Hierarchy.md).</span></span>

<span data-ttu-id="cc92b-116">这些工具可以在选项卡式窗格中显示控件，或在后台以不可见的方式工作。</span><span class="sxs-lookup"><span data-stu-id="cc92b-116">These tools can display controls in a tabbed pane or work invisibly in the background.</span></span> <span data-ttu-id="cc92b-117">**命令**附加工具是一个好例子，包含在 3.0 版及更高版本中，可显示可用命令及其帮助的列表。</span><span class="sxs-lookup"><span data-stu-id="cc92b-117">The **Commands** add-on is a good example and is included with version 3.0 and later that displays a list of the available commands and their Help.</span></span>

<span data-ttu-id="cc92b-118">**重启管理器和自动保存**每两分钟会自动保存你的脚本，有助于避免在发生崩溃或意外重启时造成的工作丢失。</span><span class="sxs-lookup"><span data-stu-id="cc92b-118">**Restart Manager and Auto-save** automatically save your scripts every two minutes to help you avoid the loss of your work in the event of a crash or unexpected restart.</span></span>

<span data-ttu-id="cc92b-119">**最近使用列表**现在是“打开文件”菜单的一部分，方便打开你最常使用的文件。</span><span class="sxs-lookup"><span data-stu-id="cc92b-119">**Most Recently Used list** is now part of the File Open menu to make it easier to get to the files you use most often.</span></span>

<span data-ttu-id="cc92b-120">**合并的控制台窗格**。</span><span class="sxs-lookup"><span data-stu-id="cc92b-120">**Merged Console pane**.</span></span> <span data-ttu-id="cc92b-121">在以前的 ISE 版本中有独立的“命令”和“输出”窗格。</span><span class="sxs-lookup"><span data-stu-id="cc92b-121">In previous versions of the ISE there were separate Command and Output panes.</span></span> <span data-ttu-id="cc92b-122">它们现在合并成单一的窗格，可以更直接地模仿你在 Windows PowerShell 控制台中所见的内容。</span><span class="sxs-lookup"><span data-stu-id="cc92b-122">They are now combined into a single pane that more directly mimics what you see in the Windows PowerShell Console.</span></span>

<span data-ttu-id="cc92b-123">**命令行开关**。</span><span class="sxs-lookup"><span data-stu-id="cc92b-123">**Command-line switches**.</span></span> <span data-ttu-id="cc92b-124">几个新的命令行开关使你更好地控制 ISE 的工作方式。</span><span class="sxs-lookup"><span data-stu-id="cc92b-124">Several new command-line switches give you more control over the way the ISE works.</span></span> <span data-ttu-id="cc92b-125">-NoProfile 无需运行配置文件脚本即可启动 ISE。</span><span class="sxs-lookup"><span data-stu-id="cc92b-125">-NoProfile starts the ISE without running a profile script.</span></span> <span data-ttu-id="cc92b-126">-Help 与 ISE 一起使用可打开帮助窗口。</span><span class="sxs-lookup"><span data-stu-id="cc92b-126">-Help opens up a help window with the ISE.</span></span> <span data-ttu-id="cc92b-127">-mta 以“多线程单元模式”启动 ISE。</span><span class="sxs-lookup"><span data-stu-id="cc92b-127">-mta starts the ISE in “multi-threaded apartment mode”.</span></span> <span data-ttu-id="cc92b-128">默认为单线程。</span><span class="sxs-lookup"><span data-stu-id="cc92b-128">The default is single-threaded.</span></span>

<span data-ttu-id="cc92b-129">**新编辑器功能**使创建并阅读代码更加容易：</span><span class="sxs-lookup"><span data-stu-id="cc92b-129">**New editor features** make it easier to create and read your code:</span></span>

- <span data-ttu-id="cc92b-130">**XML 语法着色**。</span><span class="sxs-lookup"><span data-stu-id="cc92b-130">**XML syntax coloring**.</span></span> <span data-ttu-id="cc92b-131">ISE 编辑器现在以对 Windows PowerShell 代码语法进行着色的相同方法对 XML 语法进行着色。</span><span class="sxs-lookup"><span data-stu-id="cc92b-131">The ISE editor now colors XML syntax in the same way as it colors Windows PowerShell code syntax.</span></span>

- <span data-ttu-id="cc92b-132">**大括号匹配**</span><span class="sxs-lookup"><span data-stu-id="cc92b-132">**Brace matching**.</span></span> <span data-ttu-id="cc92b-133">Windows PowerShell ISE 突出显示匹配的大括号，帮助你确保与左大括号匹配的右大括号的数量正确。</span><span class="sxs-lookup"><span data-stu-id="cc92b-133">The ISEWindows PowerShell ISE highlights matching braces to help you ensure you have the right number of closing braces to match your opening ones.</span></span> <span data-ttu-id="cc92b-134">使用 CTRL- \[ 以查找与光标所在的左大括号匹配的右大括号。</span><span class="sxs-lookup"><span data-stu-id="cc92b-134">Use CTRL-\[ to locate the closing brace that matches the opening brace that the cursor is on.</span></span>

- <span data-ttu-id="cc92b-135">**大纲视图**。</span><span class="sxs-lookup"><span data-stu-id="cc92b-135">**Outline view**.</span></span> <span data-ttu-id="cc92b-136">可以通过单击左边距中的加号和减号，折叠或展开代码部分。</span><span class="sxs-lookup"><span data-stu-id="cc92b-136">You can collapse or expand sections of your code by clicking the plus and minus signs in the left margin.</span></span> <span data-ttu-id="cc92b-137">这样会更容易地找到你在较长脚本中要查找的代码。</span><span class="sxs-lookup"><span data-stu-id="cc92b-137">This makes it easier to find the code you’re looking for in a long script.</span></span>

- <span data-ttu-id="cc92b-138">**拖放式文字编辑**。</span><span class="sxs-lookup"><span data-stu-id="cc92b-138">**Drag and drop text editing**.</span></span> <span data-ttu-id="cc92b-139">你可以选择文本块，并将其拖动到其他位置来移动它。</span><span class="sxs-lookup"><span data-stu-id="cc92b-139">You can select a block of text and drag it to another location to move it.</span></span> <span data-ttu-id="cc92b-140">如果在拖动所选文本时按住 Ctrl 键，这样就成了复制而不是移动。</span><span class="sxs-lookup"><span data-stu-id="cc92b-140">If you hold down the Ctrl key while you drag the selected text you copy instead of move.</span></span>

- <span data-ttu-id="cc92b-141">**分析错误显示**。</span><span class="sxs-lookup"><span data-stu-id="cc92b-141">**Parse error display**.</span></span> <span data-ttu-id="cc92b-142">Windows PowerShell 在你输入时会检查你的脚本。</span><span class="sxs-lookup"><span data-stu-id="cc92b-142">Windows PowerShell examines your script as you type.</span></span> <span data-ttu-id="cc92b-143">如果它检测错误，会在有问题代码下面显示红色波浪线。</span><span class="sxs-lookup"><span data-stu-id="cc92b-143">If it detects an error, it shows a red squiggle under the offending code.</span></span> <span data-ttu-id="cc92b-144">当你将鼠标悬停在指示的错误上时，工具提示会为你显示发现的问题。</span><span class="sxs-lookup"><span data-stu-id="cc92b-144">When you hover over the indicated error, a tooltip shows you the problem that was found.</span></span>

- <span data-ttu-id="cc92b-145">**缩放**。</span><span class="sxs-lookup"><span data-stu-id="cc92b-145">**Zoom**.</span></span> <span data-ttu-id="cc92b-146">你可以通过使用 ISE 窗口右下角的滑块放大你的文本便于更轻松地阅读或是缩小文本以查看更大的图片。</span><span class="sxs-lookup"><span data-stu-id="cc92b-146">You can zoom in on your text to make it easier to read or zoom out to see the bigger picture by using the slider in the bottom-right corner of the ISE window.</span></span>

- <span data-ttu-id="cc92b-147">**丰富的文本复制和粘贴**。</span><span class="sxs-lookup"><span data-stu-id="cc92b-147">**Rich text copy and paste**.</span></span> <span data-ttu-id="cc92b-148">当你从 ISE 中复制到剪贴板时，所选文本的字体、大小和颜色信息都会被复制。</span><span class="sxs-lookup"><span data-stu-id="cc92b-148">When you copy from the ISE to the clipboard, the font, size, and color information of the selected text is included.</span></span>

- <span data-ttu-id="cc92b-149">**块选择**。</span><span class="sxs-lookup"><span data-stu-id="cc92b-149">**Block selection**.</span></span> <span data-ttu-id="cc92b-150">你可以通过在用鼠标选定脚本窗格中文本的同时按住 ALT 键，或通过按 **Alt+Shift+箭头**键来选定块状的文本块。</span><span class="sxs-lookup"><span data-stu-id="cc92b-150">You can select a block-shaped chunk of text by holding down the ALT key while selecting text in the script pane with your mouse, or by pressing **Alt+Shift+Arrow**.</span></span>

### <a name="added-in-powershell-20-windows-server-2008-r2-windows-7"></a><span data-ttu-id="cc92b-151">PowerShell 2.0 中的新增功能（Windows Server 2008 R2、Windows 7）</span><span class="sxs-lookup"><span data-stu-id="cc92b-151">Added in PowerShell 2.0 (Windows Server 2008 R2, Windows 7)</span></span>

<span data-ttu-id="cc92b-152">ISE 随 PowerShell v2.0 一同引入。</span><span class="sxs-lookup"><span data-stu-id="cc92b-152">The ISE was introduced with PowerShell v2.0.</span></span>

## <a name="requirements-for-running-the-windows-powershell-ise"></a><span data-ttu-id="cc92b-153">运行 Windows PowerShell ISE 的要求</span><span class="sxs-lookup"><span data-stu-id="cc92b-153">Requirements for running the Windows PowerShell ISE</span></span>

<span data-ttu-id="cc92b-154">可以在任何运行 Windows PowerShell v2.0 或更高版本的 Windows 计算机上使用 ISE。</span><span class="sxs-lookup"><span data-stu-id="cc92b-154">The ISE is available on any Windows computer that can run Windows PowerShell v2.0 or later.</span></span> <span data-ttu-id="cc92b-155">每个 Windows 和 Windows Server 版本都包含一个 Windows PowerShell 和 ISE 版本，但你可以通过安装 Windows Management Framework (WMF) 升级至最新的可用版本。</span><span class="sxs-lookup"><span data-stu-id="cc92b-155">Each version of Windows and Windows Server includes a version of Windows PowerShell and the ISE, but you can upgrade to the latest available by installing the Windows Management Framework (WMF).</span></span> <span data-ttu-id="cc92b-156">有关详细信息，请参阅 [WMF](/powershell/wmf) 文档。</span><span class="sxs-lookup"><span data-stu-id="cc92b-156">See the [WMF](/powershell/wmf) documentation for more information.</span></span>

> [!NOTE]
> <span data-ttu-id="cc92b-157">由于 Windows PowerShell ISE 需要图形用户界面，因此你无法在 Windows Server 的 Server Core 选项上运行它。</span><span class="sxs-lookup"><span data-stu-id="cc92b-157">Because Windows PowerShell ISE requires a graphical user interface, you can’t run it on the Server Core option of Windows Server.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc92b-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cc92b-158">See also</span></span>

[<span data-ttu-id="cc92b-159">Windows PowerShell ISE 脚本对象模型的用途</span><span class="sxs-lookup"><span data-stu-id="cc92b-159">Purpose of the windows power shell ise scripting object model</span></span>](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)