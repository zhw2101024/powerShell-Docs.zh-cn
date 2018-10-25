---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 如何在脚本窗格和控制台窗格中使用 Tab 自动补全
ms.assetid: 3b752c3c-0bd0-4eca-a2d3-2d5a37fd9d84
ms.openlocfilehash: 24a3f00987ff5ca4bf82d1a3206857ec3c4b3f09
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851129"
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a><span data-ttu-id="1079b-103">如何在脚本窗格和控制台窗格中使用 Tab 自动补全</span><span class="sxs-lookup"><span data-stu-id="1079b-103">How to Use Tab Completion in the Script Pane and Console Pane</span></span>

<span data-ttu-id="1079b-104">在脚本窗格或在命令窗格中进行键入时，Tab 自动补全将提供自动帮助。</span><span class="sxs-lookup"><span data-stu-id="1079b-104">Tab completion provides automatic help when you are typing in the Script Pane or in the Command Pane.</span></span> <span data-ttu-id="1079b-105">使用以下步骤来利用此功能：</span><span class="sxs-lookup"><span data-stu-id="1079b-105">Use the following steps to take advantage of this feature:</span></span>

## <a name="to-automatically-complete-a-command-entry"></a><span data-ttu-id="1079b-106">自动完成命令输入</span><span class="sxs-lookup"><span data-stu-id="1079b-106">To automatically complete a command entry</span></span>

<span data-ttu-id="1079b-107">在命令窗格或脚本窗格中，键入命令的几个字符，然后按 TAB 以选择所需补全文本。</span><span class="sxs-lookup"><span data-stu-id="1079b-107">In the Command Pane or Script Pane, type a few characters of a command and then press TAB to select the desired completion text.</span></span> <span data-ttu-id="1079b-108">如果有多个项以你最初键入的文本开头，那么继续按 Tab，直到出现所需的项。</span><span class="sxs-lookup"><span data-stu-id="1079b-108">If multiple items begin with the text that you initially typed, then continue pressing Tab until the item you want appears.</span></span> <span data-ttu-id="1079b-109">Tab 自动补全可以帮助键入 cmdlet 名、参数名、变量名、对象属性名或文件路径。</span><span class="sxs-lookup"><span data-stu-id="1079b-109">Tab completion can help with typing a cmdlet name, parameter name, variable name, object property name, or a file path.</span></span>

> [!NOTE]
> <span data-ttu-id="1079b-110">在脚本窗格中，仅当你编辑 .ps1、.psd1 或 .psm1 文件时，按 TAB 才会自动完成命令。</span><span class="sxs-lookup"><span data-stu-id="1079b-110">In the Script Pane, pressing TAB will automatically complete a command only when you are editing .ps1, .psd1, or .psm1 files.</span></span> <span data-ttu-id="1079b-111">在命令窗格中键入时，Tab 自动补全随时都起作用。</span><span class="sxs-lookup"><span data-stu-id="1079b-111">Tab completion works any time when you are typing in the Command Pane.</span></span>

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a><span data-ttu-id="1079b-112">自动完成 cmdlet 参数输入</span><span class="sxs-lookup"><span data-stu-id="1079b-112">To automatically complete a cmdlet parameter entry</span></span>

<span data-ttu-id="1079b-113">在命令窗格或脚本窗格中，键入 cmdlet 后跟一个短划线，然后按 TAB 键。</span><span class="sxs-lookup"><span data-stu-id="1079b-113">In the Command Pane or Script pane, type a cmdlet followed by a dash and then press TAB.</span></span>

<span data-ttu-id="1079b-114">例如，键入 `Get-Process -`，然后多次按 TAB 键以显示 cmdlet 的每个参数。</span><span class="sxs-lookup"><span data-stu-id="1079b-114">For example, type `Get-Process -` and then press TAB multiple times to display each of the parameters for the cmdlet in turn.</span></span>

## <a name="see-also"></a><span data-ttu-id="1079b-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1079b-115">See Also</span></span>

- [<span data-ttu-id="1079b-116">Windows PowerShell ISE 简介</span><span class="sxs-lookup"><span data-stu-id="1079b-116">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="1079b-117">如何创建 PowerShell 选项卡</span><span class="sxs-lookup"><span data-stu-id="1079b-117">How to Create a PowerShell Tab</span></span>](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)
