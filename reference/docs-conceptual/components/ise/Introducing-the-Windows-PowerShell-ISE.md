---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Windows PowerShell ISE 简介
ms.openlocfilehash: 09a28b295855fd2a3c62bba8a681399dae3454f8
ms.sourcegitcommit: 3402a478cf118c11a5642038eb117bc76553e3ab
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53411576"
---
# <a name="the-windows-powershell-ise"></a><span data-ttu-id="dabf9-103">Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="dabf9-103">The Windows PowerShell ISE</span></span>

<span data-ttu-id="dabf9-104">Windows PowerShell 集成脚本环境 (ISE) 是 Windows PowerShell 的主机应用程序。</span><span class="sxs-lookup"><span data-stu-id="dabf9-104">The Windows PowerShell Integrated Scripting Environment (ISE) is a host application for Windows PowerShell.</span></span> <span data-ttu-id="dabf9-105">在 ISE 中，可以运行命令并编写、 测试，并在单个基于 Windows 的图形用户界面中调试脚本。</span><span class="sxs-lookup"><span data-stu-id="dabf9-105">In the ISE, you can run commands and write, test, and debug scripts in a single Windows-based graphic user interface.</span></span> <span data-ttu-id="dabf9-106">ISE 的右到左的语言提供了多行编辑、 tab 自动补全、 语法颜色设置、 选择性执行、 上下文相关帮助和支持。</span><span class="sxs-lookup"><span data-stu-id="dabf9-106">The ISE provides multiline editing, tab completion, syntax coloring, selective execution, context-sensitive help, and support for right-to-left languages.</span></span> <span data-ttu-id="dabf9-107">将菜单项和键盘快捷方式映射到许多将会在 Windows PowerShell 控制台中执行的相同任务。</span><span class="sxs-lookup"><span data-stu-id="dabf9-107">Menu items and keyboard shortcuts are mapped to many of the same tasks that you would do in the Windows PowerShell console.</span></span> <span data-ttu-id="dabf9-108">例如，当脚本在 ISE 中调试时，您可以右键单击在编辑窗格中设置断点的代码行上。</span><span class="sxs-lookup"><span data-stu-id="dabf9-108">For example, when you debug a script in the ISE, you can right-click on a line of code in the edit pane to set a breakpoint.</span></span>

## <a name="support"></a><span data-ttu-id="dabf9-109">支持</span><span class="sxs-lookup"><span data-stu-id="dabf9-109">Support</span></span>

<span data-ttu-id="dabf9-110">在 ISE 首次随 Windows PowerShell V2 和的重新设计了 PowerShell V3。</span><span class="sxs-lookup"><span data-stu-id="dabf9-110">The ISE was first introduced with Windows PowerShell V2 and was re-designed with PowerShell V3.</span></span> <span data-ttu-id="dabf9-111">在 ISE 中所有受支持版本的 Windows PowerShell 最多和包括 Windows PowerShell V5.1 支持。</span><span class="sxs-lookup"><span data-stu-id="dabf9-111">The ISE is supported in all supported versions of Windows PowerShell up to and including Windows PowerShell V5.1.</span></span> <span data-ttu-id="dabf9-112">在 ISE 中，但是，处于维护模式，可能会添加任何新功能。</span><span class="sxs-lookup"><span data-stu-id="dabf9-112">The ISE, however, is in maintennce mode and no new features are likely to be added.</span></span>
<span data-ttu-id="dabf9-113">此外，没有 ISE 与 PowerShell v6 和更高版本的支持。</span><span class="sxs-lookup"><span data-stu-id="dabf9-113">Additionally, there is no support for the ISE with PowerShell v6 and beyond.</span></span> <span data-ttu-id="dabf9-114">用户，他们希望一种图形工具，可用于管理 PowerShell scrips，等等，应考虑[Visual Studio Code](https://code.visualstudio.com/)。</span><span class="sxs-lookup"><span data-stu-id="dabf9-114">Users wanting a graphical tool with which to manage PowerShell scrips, etc, should consider [Visual Studio Code](https://code.visualstudio.com/).</span></span>

## <a name="key-features"></a><span data-ttu-id="dabf9-115">关键功能</span><span class="sxs-lookup"><span data-stu-id="dabf9-115">Key Features</span></span>

<span data-ttu-id="dabf9-116">在 Windows PowerShell ISE 中的主要功能包括：</span><span class="sxs-lookup"><span data-stu-id="dabf9-116">Key features in Windows PowerShell ISE include:</span></span>

- <span data-ttu-id="dabf9-117">多行编辑：若要在“命令”窗格中的当前行下插入一个空行，请按 SHIFT+ENTER。</span><span class="sxs-lookup"><span data-stu-id="dabf9-117">Multiline editing: To insert a blank line under the current line in the Command pane, press SHIFT+ENTER.</span></span>
- <span data-ttu-id="dabf9-118">选择性执行：要运行部分脚本，请选择要运行的文本，然后单击“运行脚本”按钮。</span><span class="sxs-lookup"><span data-stu-id="dabf9-118">Selective execution: To run part of a script, select the text you want to run, and then click the **Run Script** button.</span></span> <span data-ttu-id="dabf9-119">或者，按 F5。</span><span class="sxs-lookup"><span data-stu-id="dabf9-119">Or, press F5.</span></span>
- <span data-ttu-id="dabf9-120">上下文相关帮助：键入 Invoke-Item，然后按 F1。</span><span class="sxs-lookup"><span data-stu-id="dabf9-120">Context-sensitive help: Type **Invoke-Item**, and then press F1.</span></span> <span data-ttu-id="dabf9-121">帮助文件将打开到 Invoke-Item cmdlet 的文章。</span><span class="sxs-lookup"><span data-stu-id="dabf9-121">The Help file opens to the article for the **Invoke-Item** cmdlet.</span></span>

<span data-ttu-id="dabf9-122">Windows PowerShell ISE 允许你自定义其外观的某些方面。</span><span class="sxs-lookup"><span data-stu-id="dabf9-122">The Windows PowerShell ISE lets you customize some aspects of its appearance.</span></span> <span data-ttu-id="dabf9-123">它还具有其自己的 Windows PowerShell 配置文件脚本。</span><span class="sxs-lookup"><span data-stu-id="dabf9-123">It also has its own Windows PowerShell profile script.</span></span>

## <a name="to-start-the-windows-powershell-ise"></a><span data-ttu-id="dabf9-124">启动 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="dabf9-124">To start the Windows PowerShell ISE</span></span>

<span data-ttu-id="dabf9-125">单击“开始”，选择“Windows PowerShell”，然后单击“Windows PowerShell ISE”。</span><span class="sxs-lookup"><span data-stu-id="dabf9-125">Click **Start**, select **Windows PowerShell**, and then click **Windows PowerShell ISE**.</span></span>
<span data-ttu-id="dabf9-126">或者，可以在任何命令 shell 或“运行”框中键入 `powershell_ise.exe`。</span><span class="sxs-lookup"><span data-stu-id="dabf9-126">Alternately, you can type `powershell_ise.exe` in any command shell or in the Run box.</span></span>

## <a name="to-get-help-in-the-windows-powershell-ise"></a><span data-ttu-id="dabf9-127">在 Windows PowerShell ISE 中获取帮助</span><span class="sxs-lookup"><span data-stu-id="dabf9-127">To get Help in the Windows PowerShell ISE</span></span>

<span data-ttu-id="dabf9-128">在“帮助”菜单上，单击“Windows PowerShell 帮助”。</span><span class="sxs-lookup"><span data-stu-id="dabf9-128">On the **Help** menu, click **Windows PowerShell Help**.</span></span> <span data-ttu-id="dabf9-129">或者，按 F1。</span><span class="sxs-lookup"><span data-stu-id="dabf9-129">Or, press F1.</span></span> <span data-ttu-id="dabf9-130">打开的文件介绍了 Windows PowerShell ISE 和 Windows PowerShell，其中包括 Get-Help cmdlet 中提供的所有帮助。</span><span class="sxs-lookup"><span data-stu-id="dabf9-130">The file that opens describes Windows PowerShell ISE and Windows PowerShell, including all of the help available from the Get-Help cmdlet.</span></span>
