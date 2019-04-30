---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Windows PowerShell ISE 简介
ms.openlocfilehash: 729c8535dbcfcd2c51070b8beac5d328375f36ae
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057399"
---
# <a name="the-windows-powershell-ise"></a><span data-ttu-id="760b5-103">Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="760b5-103">The Windows PowerShell ISE</span></span>

<span data-ttu-id="760b5-104">Windows PowerShell 集成脚本环境 (ISE) 是 Windows PowerShell 的主机应用程序。</span><span class="sxs-lookup"><span data-stu-id="760b5-104">The Windows PowerShell Integrated Scripting Environment (ISE) is a host application for Windows PowerShell.</span></span> <span data-ttu-id="760b5-105">在 ISE 中，可以在单个基于 Windows 的图形用户界面中运行命令并编写、测试和调试脚本。</span><span class="sxs-lookup"><span data-stu-id="760b5-105">In the ISE, you can run commands and write, test, and debug scripts in a single Windows-based graphic user interface.</span></span> <span data-ttu-id="760b5-106">ISE 提供多行编辑、Tab 自动补全、语法颜色设置、选择性执行、上下文相关帮助以及对从右到左语言的支持。</span><span class="sxs-lookup"><span data-stu-id="760b5-106">The ISE provides multiline editing, tab completion, syntax coloring, selective execution, context-sensitive help, and support for right-to-left languages.</span></span> <span data-ttu-id="760b5-107">将菜单项和键盘快捷方式映射到许多将会在 Windows PowerShell 控制台中执行的相同任务。</span><span class="sxs-lookup"><span data-stu-id="760b5-107">Menu items and keyboard shortcuts are mapped to many of the same tasks that you would do in the Windows PowerShell console.</span></span> <span data-ttu-id="760b5-108">例如，在 ISE 中调试脚本时，可以右键单击编辑窗格中的代码行来设置断点。</span><span class="sxs-lookup"><span data-stu-id="760b5-108">For example, when you debug a script in the ISE, you can right-click on a line of code in the edit pane to set a breakpoint.</span></span>

## <a name="support"></a><span data-ttu-id="760b5-109">支持</span><span class="sxs-lookup"><span data-stu-id="760b5-109">Support</span></span>

<span data-ttu-id="760b5-110">ISE 先随 Windows PowerShell V2 一起引入，然后随 PowerShell V3 一起重新设计。</span><span class="sxs-lookup"><span data-stu-id="760b5-110">The ISE was first introduced with Windows PowerShell V2 and was re-designed with PowerShell V3.</span></span> <span data-ttu-id="760b5-111">包括 Windows PowerShell V5.1 在内的所有支持的 Windows PowerShell 版本都支持 ISE。</span><span class="sxs-lookup"><span data-stu-id="760b5-111">The ISE is supported in all supported versions of Windows PowerShell up to and including Windows PowerShell V5.1.</span></span> <span data-ttu-id="760b5-112">但是，ISE 处于维护模式，可能不会添加任何新功能。</span><span class="sxs-lookup"><span data-stu-id="760b5-112">The ISE, however, is in maintenance mode and no new features are likely to be added.</span></span>
<span data-ttu-id="760b5-113">此外，不支持具有 PowerShell v6 及更高版本的 ISE。</span><span class="sxs-lookup"><span data-stu-id="760b5-113">Additionally, there is no support for the ISE with PowerShell v6 and beyond.</span></span> <span data-ttu-id="760b5-114">想要使用图形工具管理 PowerShell 脚本等的用户应考虑使用 [Visual Studio Code](https://code.visualstudio.com/)。</span><span class="sxs-lookup"><span data-stu-id="760b5-114">Users wanting a graphical tool with which to manage PowerShell scripts, etc, should consider [Visual Studio Code](https://code.visualstudio.com/).</span></span>

## <a name="key-features"></a><span data-ttu-id="760b5-115">关键功能</span><span class="sxs-lookup"><span data-stu-id="760b5-115">Key Features</span></span>

<span data-ttu-id="760b5-116">Windows PowerShell ISE 中的关键功能包括：</span><span class="sxs-lookup"><span data-stu-id="760b5-116">Key features in Windows PowerShell ISE include:</span></span>

- <span data-ttu-id="760b5-117">多行编辑：若要在“命令”窗格中的当前行下插入一个空行，请按 SHIFT+ENTER。</span><span class="sxs-lookup"><span data-stu-id="760b5-117">Multiline editing: To insert a blank line under the current line in the Command pane, press SHIFT+ENTER.</span></span>
- <span data-ttu-id="760b5-118">选择性执行：要运行部分脚本，请选择要运行的文本，然后单击“运行脚本”按钮。</span><span class="sxs-lookup"><span data-stu-id="760b5-118">Selective execution: To run part of a script, select the text you want to run, and then click the **Run Script** button.</span></span> <span data-ttu-id="760b5-119">或者，按 F5。</span><span class="sxs-lookup"><span data-stu-id="760b5-119">Or, press F5.</span></span>
- <span data-ttu-id="760b5-120">上下文相关帮助：键入 Invoke-Item，然后按 F1。</span><span class="sxs-lookup"><span data-stu-id="760b5-120">Context-sensitive help: Type **Invoke-Item**, and then press F1.</span></span> <span data-ttu-id="760b5-121">帮助文件将打开到 Invoke-Item cmdlet 的文章。</span><span class="sxs-lookup"><span data-stu-id="760b5-121">The Help file opens to the article for the **Invoke-Item** cmdlet.</span></span>

<span data-ttu-id="760b5-122">Windows PowerShell ISE 允许你自定义其外观的某些方面。</span><span class="sxs-lookup"><span data-stu-id="760b5-122">The Windows PowerShell ISE lets you customize some aspects of its appearance.</span></span> <span data-ttu-id="760b5-123">它还具有其自己的 Windows PowerShell 配置文件脚本。</span><span class="sxs-lookup"><span data-stu-id="760b5-123">It also has its own Windows PowerShell profile script.</span></span>

## <a name="to-start-the-windows-powershell-ise"></a><span data-ttu-id="760b5-124">启动 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="760b5-124">To start the Windows PowerShell ISE</span></span>

<span data-ttu-id="760b5-125">单击“开始”，选择“Windows PowerShell”，然后单击“Windows PowerShell ISE”。</span><span class="sxs-lookup"><span data-stu-id="760b5-125">Click **Start**, select **Windows PowerShell**, and then click **Windows PowerShell ISE**.</span></span>
<span data-ttu-id="760b5-126">或者，可以在任何命令 shell 或“运行”框中键入 `powershell_ise.exe`。</span><span class="sxs-lookup"><span data-stu-id="760b5-126">Alternately, you can type `powershell_ise.exe` in any command shell or in the Run box.</span></span>

## <a name="to-get-help-in-the-windows-powershell-ise"></a><span data-ttu-id="760b5-127">在 Windows PowerShell ISE 中获取帮助</span><span class="sxs-lookup"><span data-stu-id="760b5-127">To get Help in the Windows PowerShell ISE</span></span>

<span data-ttu-id="760b5-128">在“帮助”菜单上，单击“Windows PowerShell 帮助”。</span><span class="sxs-lookup"><span data-stu-id="760b5-128">On the **Help** menu, click **Windows PowerShell Help**.</span></span> <span data-ttu-id="760b5-129">或者，按 F1。</span><span class="sxs-lookup"><span data-stu-id="760b5-129">Or, press F1.</span></span> <span data-ttu-id="760b5-130">打开的文件介绍了 Windows PowerShell ISE 和 Windows PowerShell，其中包括 Get-Help cmdlet 中提供的所有帮助。</span><span class="sxs-lookup"><span data-stu-id="760b5-130">The file that opens describes Windows PowerShell ISE and Windows PowerShell, including all of the help available from the Get-Help cmdlet.</span></span>
