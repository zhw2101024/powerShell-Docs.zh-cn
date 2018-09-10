---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Windows PowerShell ISE 简介
ms.openlocfilehash: d27a0eb594d7271121cee59f38d096995cc98648
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133069"
---
# <a name="introducing-the-windows-powershell-ise"></a><span data-ttu-id="c28db-103">Windows PowerShell ISE 简介</span><span class="sxs-lookup"><span data-stu-id="c28db-103">Introducing the Windows PowerShell ISE</span></span>

<span data-ttu-id="c28db-104">Windows PowerShell 集成脚本环境 (ISE) 是 Windows PowerShell 的主机应用程序。</span><span class="sxs-lookup"><span data-stu-id="c28db-104">The Windows PowerShell Integrated Scripting Environment (ISE) is a host application for Windows PowerShell.</span></span> <span data-ttu-id="c28db-105">在 Windows PowerShell ISE 中，可以在单个基于 Windows 的图形用户界面中运行命令并编写、测试和调试脚本。</span><span class="sxs-lookup"><span data-stu-id="c28db-105">In Windows PowerShell ISE, you can run commands and write, test, and debug scripts in a single Windows-based graphic user interface.</span></span> <span data-ttu-id="c28db-106">该界面提供多行编辑、Tab 自动补全、语法颜色设置、选择性执行、上下文相关帮助以及对从右到左语言的支持。</span><span class="sxs-lookup"><span data-stu-id="c28db-106">The interface provides multiline editing, tab completion, syntax coloring, selective execution, context-sensitive help, and support for right-to-left languages.</span></span> <span data-ttu-id="c28db-107">将菜单项和键盘快捷方式映射到许多将会在 Windows PowerShell 控制台中执行的相同任务。</span><span class="sxs-lookup"><span data-stu-id="c28db-107">Menu items and keyboard shortcuts are mapped to many of the same tasks that you would do in the Windows PowerShell console.</span></span> <span data-ttu-id="c28db-108">例如，在 Windows PowerShell ISE 中调试脚本时，可以右键单击代码行来设置断点。</span><span class="sxs-lookup"><span data-stu-id="c28db-108">For example, when you debug a script in the Windows PowerShell ISE, you can right-click on a line of code to set a breakpoint.</span></span>

<span data-ttu-id="c28db-109">尝试 Windows PowerShell ISE 中的这些功能。</span><span class="sxs-lookup"><span data-stu-id="c28db-109">Try these features in Windows PowerShell ISE.</span></span>

- <span data-ttu-id="c28db-110">多行编辑：若要在“命令”窗格中的当前行下插入一个空行，请按 SHIFT+ENTER。</span><span class="sxs-lookup"><span data-stu-id="c28db-110">Multiline editing: To insert a blank line under the current line in the Command pane, press SHIFT+ENTER.</span></span>
- <span data-ttu-id="c28db-111">选择性执行：若要运行部分脚本，请选择要运行的文本，然后单击“运行脚本”按钮。</span><span class="sxs-lookup"><span data-stu-id="c28db-111">Selective execution: To run part of a script, select the text you want to run, and then click the **Run Script** button.</span></span> <span data-ttu-id="c28db-112">或者，按 F5。</span><span class="sxs-lookup"><span data-stu-id="c28db-112">Or, press F5.</span></span>
- <span data-ttu-id="c28db-113">上下文相关帮助：键入 **Invoke-Item**，然后按 F1。</span><span class="sxs-lookup"><span data-stu-id="c28db-113">Context-sensitive help: Type **Invoke-Item**, and then press F1.</span></span> <span data-ttu-id="c28db-114">帮助文件将打开到 Invoke-Item cmdlet 的文章。</span><span class="sxs-lookup"><span data-stu-id="c28db-114">The Help file opens to the article for the **Invoke-Item** cmdlet.</span></span>

<span data-ttu-id="c28db-115">Windows PowerShell ISE 允许你自定义其外观的某些方面。</span><span class="sxs-lookup"><span data-stu-id="c28db-115">The Windows PowerShell ISE lets you customize some aspects of its appearance.</span></span> <span data-ttu-id="c28db-116">它还具有其自己的 Windows PowerShell 配置文件脚本。</span><span class="sxs-lookup"><span data-stu-id="c28db-116">It also has its own Windows PowerShell profile script.</span></span>

## <a name="to-start-the-windows-powershell-ise"></a><span data-ttu-id="c28db-117">启动 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="c28db-117">To start the Windows PowerShell ISE</span></span>

<span data-ttu-id="c28db-118">单击“开始”，选择“Windows PowerShell”，然后单击“Windows PowerShell ISE”。</span><span class="sxs-lookup"><span data-stu-id="c28db-118">Click **Start**, select **Windows PowerShell**, and then click **Windows PowerShell ISE**.</span></span>
<span data-ttu-id="c28db-119">或者，可以在任何命令 shell 或“运行”框中键入 `powershell_ise.exe`。</span><span class="sxs-lookup"><span data-stu-id="c28db-119">Alternately, you can type `powershell_ise.exe` in any command shell or in the Run box.</span></span>

## <a name="to-get-help-in-the-windows-powershell-ise"></a><span data-ttu-id="c28db-120">在 Windows PowerShell ISE 中获取帮助</span><span class="sxs-lookup"><span data-stu-id="c28db-120">To get Help in the Windows PowerShell ISE</span></span>

<span data-ttu-id="c28db-121">在“帮助”菜单上，单击“Windows PowerShell 帮助”。</span><span class="sxs-lookup"><span data-stu-id="c28db-121">On the **Help** menu, click **Windows PowerShell Help**.</span></span> <span data-ttu-id="c28db-122">或者，按 F1。</span><span class="sxs-lookup"><span data-stu-id="c28db-122">Or, press F1.</span></span> <span data-ttu-id="c28db-123">打开的文件介绍了 Windows PowerShell ISE 和 Windows PowerShell，其中包括 Get-Help cmdlet 中提供的所有帮助。</span><span class="sxs-lookup"><span data-stu-id="c28db-123">The file that opens describes Windows PowerShell ISE and Windows PowerShell, including all of the help available from the Get-Help cmdlet.</span></span>