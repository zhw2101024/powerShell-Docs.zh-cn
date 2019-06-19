---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 如何在 Windows PowerShell ISE 中创建 PowerShell 选项卡
ms.openlocfilehash: 7baf9a4051a196045d53eebf8ce5260bdc1bc55a
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030581"
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a><span data-ttu-id="78c2d-103">如何在 Windows PowerShell ISE 中创建 PowerShell 选项卡</span><span class="sxs-lookup"><span data-stu-id="78c2d-103">How to Create a PowerShell Tab in Windows PowerShell ISE</span></span>

<span data-ttu-id="78c2d-104">使用 Windows PowerShell 集成脚本环境 (ISE) 中的选项卡，可在相同的应用程序中同时创建并使用多个执行环境。</span><span class="sxs-lookup"><span data-stu-id="78c2d-104">Tabs in the Windows PowerShell Integrated Scripting Environment (ISE) allow you to simultaneously create and use several execution environments within the same application.</span></span>
<span data-ttu-id="78c2d-105">每个 PowerShell 选项卡对应于单独的执行环境或会话。</span><span class="sxs-lookup"><span data-stu-id="78c2d-105">Each PowerShell tab corresponds to a separate execution environment or session.</span></span>

> [!NOTE]
> <span data-ttu-id="78c2d-106">在一个选项卡中创建的变量、函数和别名不会延续到另一个。</span><span class="sxs-lookup"><span data-stu-id="78c2d-106">Variables, functions, and aliases that you create in one tab do not carry over to another.</span></span> <span data-ttu-id="78c2d-107">它们属于不同的 Windows PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="78c2d-107">They are different Windows PowerShell sessions.</span></span>

<span data-ttu-id="78c2d-108">使用下列步骤打开或关闭 Windows PowerShell 中的选项卡。</span><span class="sxs-lookup"><span data-stu-id="78c2d-108">Use the following steps to open or close a tab in Windows PowerShell.</span></span>
<span data-ttu-id="78c2d-109">若要重命名选项卡，在 Windows PowerShell 选项卡脚本对象上设置 [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) 属性。</span><span class="sxs-lookup"><span data-stu-id="78c2d-109">To rename a tab, set the [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) property on the Windows PowerShell Tab scripting object.</span></span>

## <a name="to-create-and-use-a-new-powershell-tab"></a><span data-ttu-id="78c2d-110">创建和使用新的 PowerShell 选项卡</span><span class="sxs-lookup"><span data-stu-id="78c2d-110">To create and use a new PowerShell Tab</span></span>

<span data-ttu-id="78c2d-111">在“文件”菜单上，单击“新建 PowerShell 选项卡”。   新的 PowerShell 选项卡始终作为活动窗口打开。</span><span class="sxs-lookup"><span data-stu-id="78c2d-111">On the **File** menu, click **New PowerShell Tab**. The new PowerShell tab always opens as the active window.</span></span>
<span data-ttu-id="78c2d-112">PowerShell 选项卡按打开顺序进行递增编号。</span><span class="sxs-lookup"><span data-stu-id="78c2d-112">PowerShell tabs are incrementally numbered in the order that they are opened.</span></span>
<span data-ttu-id="78c2d-113">每个选项卡都与其自己的 Windows PowerShell 控制台窗口相关联。</span><span class="sxs-lookup"><span data-stu-id="78c2d-113">Each tab is associated with its own Windows PowerShell console window.</span></span>
<span data-ttu-id="78c2d-114">你一次可以最多打开 32 个具有其各自会话的 PowerShell 选项卡（在 Windows PowerShell ISE 2.0 中的上限为 8 个）。</span><span class="sxs-lookup"><span data-stu-id="78c2d-114">You can have up to 32 PowerShell tabs with their own session open at a time (this is limited to 8 on Windows PowerShell ISE 2.0.)</span></span>

<span data-ttu-id="78c2d-115">请注意，单击工具栏上的“新建”或“打开”图标不会创建新的具有单独会话的选项卡。  </span><span class="sxs-lookup"><span data-stu-id="78c2d-115">Note that clicking the **New** or **Open** icons on the toolbar does not create a new tab with a separate session.</span></span>
<span data-ttu-id="78c2d-116">相反，这些按钮将在带有会话的当前处于活动状态的选项卡上打开新的或现有脚本文件。</span><span class="sxs-lookup"><span data-stu-id="78c2d-116">Instead, those buttons open a new or existing script file on the currently active tab with a session.</span></span>
<span data-ttu-id="78c2d-117">你可以通过每个选项卡和会话打开多个脚本文件。</span><span class="sxs-lookup"><span data-stu-id="78c2d-117">You can have multiple script files open with each tab and session.</span></span>
<span data-ttu-id="78c2d-118">适用于会话的脚本选项卡仅当相关联的会话处于活动状态时，才显示在会话选项卡下方。</span><span class="sxs-lookup"><span data-stu-id="78c2d-118">The script tabs for a session only appear below the session tabs when the associated session is active.</span></span>

<span data-ttu-id="78c2d-119">若要使 PowerShell 选项卡处于活动状态，请单击选项卡。若要从所有打开的 PowerShell 选项卡中进行选择，请在“视图”菜单上，单击你想要使用 PowerShell 选项卡。 </span><span class="sxs-lookup"><span data-stu-id="78c2d-119">To make a PowerShell tab active, click the tab. To select from all PowerShell tabs that are open, on the **View** menu, click the PowerShell tab you want to use.</span></span>

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a><span data-ttu-id="78c2d-120">创建和使用新的远程 PowerShell 选项卡</span><span class="sxs-lookup"><span data-stu-id="78c2d-120">To create and use a new Remote PowerShell tab</span></span>

<span data-ttu-id="78c2d-121">在“文件”菜单上，单击“新建远程 PowerShell 选项卡”，以在远程计算机上建立会话。  </span><span class="sxs-lookup"><span data-stu-id="78c2d-121">On the **File** menu, click **New Remote PowerShell Tab** to establish a session on a remote computer.</span></span>
<span data-ttu-id="78c2d-122">将出现一个对话框，提示你输入建立远程连接所需的详细信息。</span><span class="sxs-lookup"><span data-stu-id="78c2d-122">A dialog box appears and prompts you to enter details required to establish the remote connection.</span></span>
<span data-ttu-id="78c2d-123">远程选项卡功能与本地 PowerShell 选项卡类似，但命令和脚本在远程计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="78c2d-123">The remote tab functions just like a local PowerShell tab, but the commands and scripts are run on the remote computer.</span></span>

## <a name="to-close-a-powershell-tab"></a><span data-ttu-id="78c2d-124">关闭 PowerShell 选项卡</span><span class="sxs-lookup"><span data-stu-id="78c2d-124">To close a PowerShell Tab</span></span>

<span data-ttu-id="78c2d-125">若要关闭选项卡，你可以使用以下任一技巧：</span><span class="sxs-lookup"><span data-stu-id="78c2d-125">To close a tab, you can use any of the following techniques:</span></span>

- <span data-ttu-id="78c2d-126">单击要关闭的选项卡。</span><span class="sxs-lookup"><span data-stu-id="78c2d-126">Click the tab that you want to close.</span></span>

- <span data-ttu-id="78c2d-127">在“文件”菜单上，单击“关闭 PowerShell 选项卡”，或单击活动选项卡上的“关闭”按钮 (**X**) 以关闭选项卡。  </span><span class="sxs-lookup"><span data-stu-id="78c2d-127">On the **File** menu, click **Close PowerShell Tab**, or click  the Close button  (**X**) on an active tab to close the tab.</span></span>

<span data-ttu-id="78c2d-128">如果你在将关闭的 PowerShell 选项卡中打开了未保存的文件，系统会提示你保存或丢弃这些文件。</span><span class="sxs-lookup"><span data-stu-id="78c2d-128">If you have unsaved files open in the PowerShell tab that you are closing, you are prompted to save or discard them.</span></span>
<span data-ttu-id="78c2d-129">有关如何保存脚本的详细信息，请参阅[如何保存脚本](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script)。</span><span class="sxs-lookup"><span data-stu-id="78c2d-129">For more information about how to save a script, see [How to Save a Script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span></span>

## <a name="see-also"></a><span data-ttu-id="78c2d-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="78c2d-130">See Also</span></span>

- [<span data-ttu-id="78c2d-131">Windows PowerShell ISE 简介</span><span class="sxs-lookup"><span data-stu-id="78c2d-131">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="78c2d-132">如何在 Windows PowerShell ISE 中使用控制台窗格</span><span class="sxs-lookup"><span data-stu-id="78c2d-132">How to Use the Console Pane in the Windows PowerShell ISE</span></span>](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)
