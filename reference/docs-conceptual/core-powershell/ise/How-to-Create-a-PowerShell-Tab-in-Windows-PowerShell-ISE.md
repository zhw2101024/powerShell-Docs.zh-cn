---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "如何在 Windows PowerShell ISE 中创建 PowerShell 选项卡"
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
ms.openlocfilehash: 7dc92275c30ad783ad71b2a4825e9cc0d26d1691
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2017
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a><span data-ttu-id="32bab-103">如何在 Windows PowerShell ISE 中创建 PowerShell 选项卡</span><span class="sxs-lookup"><span data-stu-id="32bab-103">How to Create a PowerShell Tab in Windows PowerShell ISE</span></span>
<span data-ttu-id="32bab-104">使用 Windows PowerShell® 集成脚本环境 (ISE) 中的选项卡，可在相同的应用程序中同时创建并使用多个执行环境。</span><span class="sxs-lookup"><span data-stu-id="32bab-104">Tabs in the Windows PowerShell® Integrated Scripting Environment (ISE) allow you to simultaneously create and use several execution environments within the same application.</span></span> <span data-ttu-id="32bab-105">每个 PowerShell 选项卡对应于单独的执行环境或会话。</span><span class="sxs-lookup"><span data-stu-id="32bab-105">Each PowerShell tab corresponds to a separate execution environment or session.</span></span>

> [!NOTE]
> <span data-ttu-id="32bab-106">在一个选项卡中创建的变量、函数和别名不会延续到另一个。</span><span class="sxs-lookup"><span data-stu-id="32bab-106">Variables, functions, and aliases that you create in one tab do not carry over to another.</span></span> <span data-ttu-id="32bab-107">它们属于不同的 Windows PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="32bab-107">They are different Windows PowerShell sessions.</span></span>

<span data-ttu-id="32bab-108">使用下列步骤打开或关闭 Windows PowerShell 中的选项卡。</span><span class="sxs-lookup"><span data-stu-id="32bab-108">Use the following steps to open or close a tab in Windows PowerShell.</span></span> <span data-ttu-id="32bab-109">若要重命名选项卡，在 Windows PowerShell 选项卡脚本对象上设置 [DisplayName](The-PowerShellTab-Object.md#Displayname) 属性。</span><span class="sxs-lookup"><span data-stu-id="32bab-109">To rename a tab, set the [DisplayName](The-PowerShellTab-Object.md#Displayname) property on the Windows PowerShell Tab scripting object.</span></span>

## <a name="to-create-and-use-a-new-powershell-tab"></a><span data-ttu-id="32bab-110">创建和使用新的 PowerShell 选项卡</span><span class="sxs-lookup"><span data-stu-id="32bab-110">To create and use a new PowerShell Tab</span></span>
<span data-ttu-id="32bab-111">在“文件”菜单上，单击“新建 PowerShell 选项卡”。</span><span class="sxs-lookup"><span data-stu-id="32bab-111">On the **File** menu, click **New PowerShell Tab**.</span></span> <span data-ttu-id="32bab-112">新的 PowerShell 选项卡始终作为活动窗口打开。</span><span class="sxs-lookup"><span data-stu-id="32bab-112">The new PowerShell tab always opens as the active window.</span></span> <span data-ttu-id="32bab-113">PowerShell 选项卡按打开顺序进行递增编号。</span><span class="sxs-lookup"><span data-stu-id="32bab-113">PowerShell tabs are incrementally numbered in the order that they are opened.</span></span> <span data-ttu-id="32bab-114">每个选项卡都与其自己的 Windows PowerShell 控制台窗口相关联。</span><span class="sxs-lookup"><span data-stu-id="32bab-114">Each tab is associated with its own Windows PowerShell console window.</span></span> <span data-ttu-id="32bab-115">你一次可以最多打开 32 个具有其各自会话的 PowerShell 选项卡（在 Windows PowerShell ISE 2.0 中的上限为 8 个）。</span><span class="sxs-lookup"><span data-stu-id="32bab-115">You can have up to 32 PowerShell tabs with their own session open at a time (this is limited to 8 on Windows PowerShell ISE 2.0.)</span></span>

<span data-ttu-id="32bab-116">请注意，单击工具栏上的“新建”或“打开”图标不会创建新的具有单独会话的选项卡。</span><span class="sxs-lookup"><span data-stu-id="32bab-116">Note that clicking the **New** or **Open** icons on the toolbar does not create a new tab with a separate session.</span></span>  <span data-ttu-id="32bab-117">相反，这些按钮将在带有会话的当前处于活动状态的选项卡上打开新的或现有脚本文件。</span><span class="sxs-lookup"><span data-stu-id="32bab-117">Instead, those buttons open a new or existing script file on the currently active tab with a session.</span></span> <span data-ttu-id="32bab-118">你可以通过每个选项卡和会话打开多个脚本文件。</span><span class="sxs-lookup"><span data-stu-id="32bab-118">You can have multiple script files open with each tab and session.</span></span> <span data-ttu-id="32bab-119">适用于会话的脚本选项卡仅当相关联的会话处于活动状态时，才显示在会话选项卡下方。</span><span class="sxs-lookup"><span data-stu-id="32bab-119">The script tabs for a session only appear below the session tabs when the associated session is active.</span></span>

<span data-ttu-id="32bab-120">若要使 PowerShell 选项卡处于活动状态，请单击选项卡。</span><span class="sxs-lookup"><span data-stu-id="32bab-120">To make a PowerShell tab active, click the tab.</span></span> <span data-ttu-id="32bab-121">若要从所有打开的 PowerShell 选项卡中进行选择，请在“视图”菜单上，单击你想要使用 PowerShell 选项卡。</span><span class="sxs-lookup"><span data-stu-id="32bab-121">To select from all PowerShell tabs that are open, on the **View** menu, click the PowerShell tab you want to use.</span></span>

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a><span data-ttu-id="32bab-122">创建和使用新的远程 PowerShell 选项卡</span><span class="sxs-lookup"><span data-stu-id="32bab-122">To create and use a new Remote PowerShell tab</span></span>
<span data-ttu-id="32bab-123">在“文件”菜单上，单击“新建远程 PowerShell 选项卡”，以在远程计算机上建立会话。</span><span class="sxs-lookup"><span data-stu-id="32bab-123">On the **File** menu, click **New Remote PowerShell Tab** to establish a session on a remote computer.</span></span> <span data-ttu-id="32bab-124">将出现一个对话框，提示你输入建立远程连接所需的详细信息。</span><span class="sxs-lookup"><span data-stu-id="32bab-124">A dialog box appears and prompts you to enter details required to establish the remote connection.</span></span> <span data-ttu-id="32bab-125">远程选项卡功能与本地 PowerShell 选项卡类似，但命令和脚本在远程计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="32bab-125">The remote tab functions just like a local PowerShell tab, but the commands and scripts are run on the remote computer.</span></span>

## <a name="to-close-a-powershell-tab"></a><span data-ttu-id="32bab-126">关闭 PowerShell 选项卡</span><span class="sxs-lookup"><span data-stu-id="32bab-126">To close a PowerShell Tab</span></span>
<span data-ttu-id="32bab-127">若要关闭选项卡，你可以使用以下任一技巧：</span><span class="sxs-lookup"><span data-stu-id="32bab-127">To close a tab, you can use any of the following techniques:</span></span>

-   <span data-ttu-id="32bab-128">单击要关闭的选项卡。</span><span class="sxs-lookup"><span data-stu-id="32bab-128">Click the tab that you want to close.</span></span>

-   <span data-ttu-id="32bab-129">在“文件”菜单上，单击“关闭 PowerShell 选项卡”，或单击活动选项卡上的“关闭”按钮 (**X**) 以关闭选项卡。</span><span class="sxs-lookup"><span data-stu-id="32bab-129">On the **File** menu, click **Close PowerShell Tab**, or click  the Close button  (**X**) on an active tab to close the tab.</span></span>

<span data-ttu-id="32bab-130">如果你在将关闭的 PowerShell 选项卡中打开了未保存的文件，系统会提示你保存或丢弃这些文件。</span><span class="sxs-lookup"><span data-stu-id="32bab-130">If you have unsaved files open in the PowerShell tab that you are closing, you are prompted to save or discard them.</span></span> <span data-ttu-id="32bab-131">有关如何保存脚本的详细信息，请参阅[如何保存脚本](https://technet.microsoft.com/library/162f594d-efd3-4234-9960-45e56e6eadc8)。</span><span class="sxs-lookup"><span data-stu-id="32bab-131">For more information about how to save a script, see [How to Save a Script](https://technet.microsoft.com/library/162f594d-efd3-4234-9960-45e56e6eadc8).</span></span>

## <a name="see-also"></a><span data-ttu-id="32bab-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="32bab-132">See Also</span></span>
- [<span data-ttu-id="32bab-133">使用 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="32bab-133">Using the Windows PowerShell ISE</span></span>](Using-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="32bab-134">如何在 Windows PowerShell ISE 中使用控制台窗格</span><span class="sxs-lookup"><span data-stu-id="32bab-134">How to Use the Console Pane in the Windows PowerShell ISE</span></span>](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)

