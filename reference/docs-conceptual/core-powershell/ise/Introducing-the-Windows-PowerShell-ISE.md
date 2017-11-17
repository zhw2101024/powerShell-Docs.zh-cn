---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Windows PowerShell ISE 简介"
ms.openlocfilehash: 75242c20548e2e83397867214417a48806c897ec
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/08/2017
---
# <a name="introducing-the-windows-powershell-ise"></a><span data-ttu-id="9771a-103">Windows PowerShell ISE 简介</span><span class="sxs-lookup"><span data-stu-id="9771a-103">Introducing the Windows PowerShell ISE</span></span>
<span data-ttu-id="9771a-104">Windows PowerShell 集成脚本环境 (ISE) 是 Windows PowerShell 的主机应用程序。</span><span class="sxs-lookup"><span data-stu-id="9771a-104">The Windows PowerShell Integrated Scripting Environment (ISE) is a host application for Windows PowerShell.</span></span> <span data-ttu-id="9771a-105">在 Windows PowerShell ISE 中，你可以在单个基于 Windows 的图形用户界面（包含多行编辑、Tab 自动补全、语法颜色设置、选择性执行、上下文相关帮助以及从右向左语言支持功能）中运行命令并编写、测试和调试脚本。</span><span class="sxs-lookup"><span data-stu-id="9771a-105">In Windows PowerShell ISE, you can run commands and write, test, and debug scripts in a single Windows-based graphic user interface with multiline editing, tab completion, syntax coloring, selective execution, context-sensitive help, and support for right-to-left languages.</span></span>
<span data-ttu-id="9771a-106">你可以使用菜单项和键盘快捷方式执行许多将会在 Windows PowerShell 控制台中执行的相同任务。</span><span class="sxs-lookup"><span data-stu-id="9771a-106">You can use menu items and keyboard shortcuts to perform many of the same tasks that you would perform in the Windows PowerShell console.</span></span>  <span data-ttu-id="9771a-107">例如，当你在 Windows PowerShell ISE 中调试脚本以在脚本中设置行断点时，右键单击代码行，然后单击**切换断点**。</span><span class="sxs-lookup"><span data-stu-id="9771a-107">For example, when you debug a script in the Windows PowerShell ISE, to set a line breakpoint in a script, right-click the line of code, and then click **Toggle Breakpoint**.</span></span>

<span data-ttu-id="9771a-108">尝试 Windows PowerShell ISE 中的这些功能。</span><span class="sxs-lookup"><span data-stu-id="9771a-108">Try these features in Windows PowerShell ISE.</span></span>

- <span data-ttu-id="9771a-109">多行编辑：若要在“命令”窗格中的当前行下插入一个空行，请按 SHIFT+ENTER。</span><span class="sxs-lookup"><span data-stu-id="9771a-109">Multiline editing: To insert a blank line under the current line in the Command pane, press SHIFT+ENTER.</span></span>

- <span data-ttu-id="9771a-110">选择性执行：若要运行部分脚本，请选择要运行的文本，然后单击“运行脚本”按钮。</span><span class="sxs-lookup"><span data-stu-id="9771a-110">Selective execution: To run part of a script, select the text you want to run, and then click the **Run Script** button.</span></span> <span data-ttu-id="9771a-111">或者，按 F5。</span><span class="sxs-lookup"><span data-stu-id="9771a-111">Or, press F5.</span></span>

- <span data-ttu-id="9771a-112">上下文相关帮助：键入 **Invoke-Item**，然后按 F1。</span><span class="sxs-lookup"><span data-stu-id="9771a-112">Context-sensitive help: Type **Invoke-Item**, and then press F1.</span></span> <span data-ttu-id="9771a-113">帮助文件将打开到 **Invoke-Item** cmdlet 的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="9771a-113">The Help file opens to the Help topic for the **Invoke-Item** cmdlet.</span></span>

<span data-ttu-id="9771a-114">Windows PowerShell ISE 允许你自定义其外观的某些方面。</span><span class="sxs-lookup"><span data-stu-id="9771a-114">The Windows PowerShell ISE lets you customize some aspects of its appearance.</span></span> <span data-ttu-id="9771a-115">它还具有自己的 Windows PowerShell 配置文件，你可以在其中存储在 Windows PowerShell ISE 中使用的函数、别名、变量和命令。</span><span class="sxs-lookup"><span data-stu-id="9771a-115">It also has its own Windows PowerShell profile, where you can store functions, aliases, variables, and commands you use in the Windows PowerShell ISE.</span></span>

### <a name="to-start-the-windows-powershell-ise"></a><span data-ttu-id="9771a-116">启动 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="9771a-116">To start the Windows PowerShell ISE</span></span>

1. <span data-ttu-id="9771a-117">执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="9771a-117">Do one of the following:</span></span>

    -   <span data-ttu-id="9771a-118">单击“开始”，依次指向“所有程序”和“Windows PowerShell V2”，然后单击 **Windows PowerShell ISE**。</span><span class="sxs-lookup"><span data-stu-id="9771a-118">Click **Start**, point to **All Programs**, point to **Windows PowerShell V2**, and then click **Windows PowerShell ISE**.</span></span>

    -   <span data-ttu-id="9771a-119">在 Windows PowerShell console Cmd.exe 或“运行”框中，键入 **powershell_ise.exe**。</span><span class="sxs-lookup"><span data-stu-id="9771a-119">In the Windows PowerShell console Cmd.exe, or in the Run box, type, **powershell_ise.exe**.</span></span>

### <a name="to-get-help-in-the-windows-powershell-ise"></a><span data-ttu-id="9771a-120">在 Windows PowerShell ISE 中获取帮助</span><span class="sxs-lookup"><span data-stu-id="9771a-120">To get Help in the Windows PowerShell ISE</span></span>

- <span data-ttu-id="9771a-121">在“帮助”菜单上，单击“Windows PowerShell 帮助”。</span><span class="sxs-lookup"><span data-stu-id="9771a-121">On the **Help** menu, click **Windows PowerShell Help**.</span></span> <span data-ttu-id="9771a-122">或者，按 F1。</span><span class="sxs-lookup"><span data-stu-id="9771a-122">Or, press F1.</span></span> <span data-ttu-id="9771a-123">打开的文件介绍了 Windows PowerShell ISE 和 Windows PowerShell，其中包括 Get-Help cmdlet 中提供的所有帮助。</span><span class="sxs-lookup"><span data-stu-id="9771a-123">The file that opens describes Windows PowerShell ISE and Windows PowerShell, including all of the help available from the Get-Help cmdlet.</span></span>

