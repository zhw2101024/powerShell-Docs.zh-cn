---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 如何在 Windows PowerShell ISE 中使用控制台窗格
ms.assetid: 44d67705-87c7-4a69-a53e-6471fdebb757
ms.openlocfilehash: 5bbbdd3b1f0324ff1a4f2298459f58640c4dc9a6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057350"
---
# <a name="how-to-use-the-console-pane-in-the-windows-powershell-ise"></a><span data-ttu-id="a9f44-103">如何在 Windows PowerShell ISE 中使用控制台窗格</span><span class="sxs-lookup"><span data-stu-id="a9f44-103">How to Use the Console Pane in the Windows PowerShell ISE</span></span>

<span data-ttu-id="a9f44-104">Windows PowerShell 集成脚本环境 (ISE) 的“控制台”窗格的运行方式和独立的 Windows PowerShell ISE 控制台窗口完全一样。</span><span class="sxs-lookup"><span data-stu-id="a9f44-104">The Console pane in the Windows PowerShell Integrated Scripting Environment (ISE) operates exactly like the stand-alone Windows PowerShell ISE console window.</span></span>

<span data-ttu-id="a9f44-105">若要在控制台窗格中运行命令，请键入命令，然后按 ENTER 键。</span><span class="sxs-lookup"><span data-stu-id="a9f44-105">To run a command in the Console Pane, type a command, and then press ENTER.</span></span> <span data-ttu-id="a9f44-106">若要输入多个命令并且你想要按顺序执行这些命令，请在命令之间键入 SHIFT+ENTER。</span><span class="sxs-lookup"><span data-stu-id="a9f44-106">To enter multiple commands that you want to execute in sequence, type SHIFT+ENTER between commands.</span></span> <span data-ttu-id="a9f44-107">有关键入命令的帮助，请参阅[如何在脚本窗格和控制台窗格中使用 Tab 自动补全](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md)。</span><span class="sxs-lookup"><span data-stu-id="a9f44-107">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for help in typing commands.</span></span>

<span data-ttu-id="a9f44-108">若要停止某个命令，在工具栏上，单击“**停止操作**”，或按 CTRL+BREAK。</span><span class="sxs-lookup"><span data-stu-id="a9f44-108">To stop a command, on the toolbar, click **Stop Operation**, or press CTRL+BREAK.</span></span> <span data-ttu-id="a9f44-109">如果上下文是明确的，你还可以使用 CTRL+C 来停止命令。</span><span class="sxs-lookup"><span data-stu-id="a9f44-109">You can also use CTRL+C to stop a command if the context is unambiguous.</span></span> <span data-ttu-id="a9f44-110">例如，如果当前窗格中已选择了一些文本，那么 CTRL+C 将映射为复制操作。</span><span class="sxs-lookup"><span data-stu-id="a9f44-110">For example, if some text has been selected in the current Pane, then CTRL+C maps to the copy operation.</span></span>

<span data-ttu-id="a9f44-111">从 Windows PowerShell v3 起，“输出”窗格与“控制台”窗格已结合。</span><span class="sxs-lookup"><span data-stu-id="a9f44-111">Beginning in Windows PowerShell v3, the Output pane was combined with the Console pane.</span></span> <span data-ttu-id="a9f44-112">这样的好处是能像独立的 Windows PowerShell 控制台一样运行，并消除了两者分离后所需过程的差异。</span><span class="sxs-lookup"><span data-stu-id="a9f44-112">This has the benefit of behaving like the stand-alone Windows PowerShell console and eliminates the differences in procedures that were needed when they were separate.</span></span> <span data-ttu-id="a9f44-113">您可以：</span><span class="sxs-lookup"><span data-stu-id="a9f44-113">You can:</span></span>

- <span data-ttu-id="a9f44-114">从控制台窗格中选择文本并将其复制到剪贴板，以便在任何其他窗口中粘贴。</span><span class="sxs-lookup"><span data-stu-id="a9f44-114">Select and copy text from the Console pane to the Clipboard for pasting in any other window.</span></span> <span data-ttu-id="a9f44-115">若要选择文本，单击输出窗格并按住鼠标，同时将鼠标拖动到你想要捕获的文本上。</span><span class="sxs-lookup"><span data-stu-id="a9f44-115">To select text, click and hold the mouse in the output pane while dragging the mouse over the text you want to capture.</span></span> <span data-ttu-id="a9f44-116">你还可以按住 **SHIFT** 的同时使用光标箭头键选择文本。</span><span class="sxs-lookup"><span data-stu-id="a9f44-116">You can also use the cursor arrow keys while holding **SHIFT** to select text.</span></span> <span data-ttu-id="a9f44-117">然后按 CTRL+C 或单击工具栏中的“**复制**”图标。</span><span class="sxs-lookup"><span data-stu-id="a9f44-117">Then press CTRL+C or click the **Copy** icon in the toolbar.</span></span>

- <span data-ttu-id="a9f44-118">将所选文本粘贴在当前光标位置。</span><span class="sxs-lookup"><span data-stu-id="a9f44-118">Paste the selected text at a current cursor position.</span></span> <span data-ttu-id="a9f44-119">单击工具栏上的“粘贴”按钮。</span><span class="sxs-lookup"><span data-stu-id="a9f44-119">Click the **Paste** icon on the toolbar.</span></span>

- <span data-ttu-id="a9f44-120">清除控制台窗格中的所有文本。</span><span class="sxs-lookup"><span data-stu-id="a9f44-120">Clear all the text in the Console pane.</span></span> <span data-ttu-id="a9f44-121">若要清除控制台窗格，你可以单击工具栏上的“**清除控制台窗格**”或运行 **Clear-Host** 命令或其别名 **cls**。</span><span class="sxs-lookup"><span data-stu-id="a9f44-121">To clear the Console pane, you can click the **Clear Console Pane** icon on the toolbar, or run the command **Clear-Host** or its alias, **cls**.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9f44-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a9f44-122">See Also</span></span>

- [<span data-ttu-id="a9f44-123">Windows PowerShell ISE 简介</span><span class="sxs-lookup"><span data-stu-id="a9f44-123">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)