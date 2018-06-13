---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 如何在 Windows PowerShell ISE 中编写和运行脚本
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: 4d7c5352ef1dac6f63a50433676068f83a920db5
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2018
ms.locfileid: "34483111"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a><span data-ttu-id="3cb3d-103">如何在 Windows PowerShell ISE 中编写和运行脚本</span><span class="sxs-lookup"><span data-stu-id="3cb3d-103">How to Write and Run Scripts in the Windows PowerShell ISE</span></span>

<span data-ttu-id="3cb3d-104">本主题说明如何在脚本窗格中创建、编辑、运行以及保存脚本。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-104">This topic describes how to create, edit, run, and save scripts in the Script Pane.</span></span>

## <a name="how-to-create-and-run-scripts"></a><span data-ttu-id="3cb3d-105">如何创建和运行脚本</span><span class="sxs-lookup"><span data-stu-id="3cb3d-105">How to create and run scripts</span></span>

<span data-ttu-id="3cb3d-106">可以在脚本窗格中打开和编辑 Windows PowerShell 文件。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-106">You can open and edit Windows PowerShell files in the Script Pane.</span></span> <span data-ttu-id="3cb3d-107">Windows PowerShell 中的相关特定文件类型有脚本文件 (.ps1)、脚本数据文件 (.psd1) 和脚本模块文件 (.psm1)。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-107">Specific file types of interest in Windows PowerShell are script files (.ps1), script data files (.psd1), and script module files (.psm1).</span></span> <span data-ttu-id="3cb3d-108">这些文件类型在脚本窗格编辑器中是经语法颜色设置的。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-108">These file types are syntax colored in the Script Pane editor.</span></span> <span data-ttu-id="3cb3d-109">可能在脚本窗格中打开的其他常见文件类型有配置文件 (.ps1xml)、XML 文件和文本文件。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-109">Other common file types you may open in the Script Pane are configuration files (.ps1xml), XML files, and text files.</span></span>

> [!NOTE]
> <span data-ttu-id="3cb3d-110">Windows PowerShell 执行策略确定你是否可以运行脚本并加载 Windows PowerShell 配置文件。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-110">The Windows PowerShell execution policy determines whether you can run scripts and load Windows PowerShell profiles and configuration files.</span></span> <span data-ttu-id="3cb3d-111">默认执行策略（受限）可以防止运行所有脚本，并防止加载配置文件。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-111">The default execution policy, Restricted, prevents all scripts from running, and prevents loading profiles.</span></span> <span data-ttu-id="3cb3d-112">若要将执行策略更改为允许加载和使用配置文件，请参阅 [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) 和 [about_Signing [v4]](https://technet.microsoft.com/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d)。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-112">To change the execution policy to allow profiles to load and be used, see [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) and [about_Signing [v4]](https://technet.microsoft.com/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).</span></span>

### <a name="to-create-a-new-script-file"></a><span data-ttu-id="3cb3d-113">创建新的脚本文件</span><span class="sxs-lookup"><span data-stu-id="3cb3d-113">To create a new script file</span></span>

<span data-ttu-id="3cb3d-114">在工具栏上，单击“新建”，或在“文件”菜单上，单击“新建”。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-114">On the toolbar, click **New** , or on the **File** menu, click **New**.</span></span> <span data-ttu-id="3cb3d-115">创建的文件将出现在当前 PowerShell 选项卡下的新建文件选项卡中。请记住，仅当有多个选项卡时，PowerShell 选项卡才可见。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-115">The created file appears in a new file tab under the current PowerShell tab. Remember that the PowerShell tabs are only visible when there are more than one.</span></span> <span data-ttu-id="3cb3d-116">默认情况下，将创建类型脚本文件 (.ps1)，但它可以使用新的名称和扩展名进行保存。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-116">By default a file of type script (.ps1) is created, but it can be saved with a new name and extension.</span></span> <span data-ttu-id="3cb3d-117">可以在同一个 PowerShell 选项卡中创建多个脚本文件。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-117">Multiple script files can be created in the same PowerShell tab.</span></span>

### <a name="to-open-an-existing-script"></a><span data-ttu-id="3cb3d-118">打开现有的脚本</span><span class="sxs-lookup"><span data-stu-id="3cb3d-118">To open an existing script</span></span>

<span data-ttu-id="3cb3d-119">在工具栏上，单击“打开”，或在“文件”菜单上，单击“打开”。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-119">On the toolbar, click **Open**, or on the **File** menu, click **Open**.</span></span> <span data-ttu-id="3cb3d-120">在“打开”对话框中，选择想要打开的文件。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-120">In the **Open** dialog box, select the file you want to open.</span></span> <span data-ttu-id="3cb3d-121">打开的文件将出现在新选项卡中。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-121">The opened file appears in a new tab.</span></span>

### <a name="to-close-a-script-tab"></a><span data-ttu-id="3cb3d-122">关闭脚本选项卡</span><span class="sxs-lookup"><span data-stu-id="3cb3d-122">To close a script tab</span></span>

<span data-ttu-id="3cb3d-123">单击你想要关闭的脚本的脚本选项卡，然后执行以下其中一项操作：</span><span class="sxs-lookup"><span data-stu-id="3cb3d-123">Click the script tab of the script you want to close, then do one of the following:</span></span>

1. <span data-ttu-id="3cb3d-124">单击脚本选项卡上的“关闭”图标 (X)。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-124">Click the **Close** icon (X) on the script tab.</span></span>

2. <span data-ttu-id="3cb3d-125">在“文件”菜单中，单击“关闭”。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-125">On the **File** menu, click **Close**.</span></span>

<span data-ttu-id="3cb3d-126">如果自上次保存后该文件已被更改，系统会提示你保存或丢弃该文件。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-126">If the file has been altered since it was last saved, you are prompted to save or discard it.</span></span>

### <a name="to-display-the-file-path"></a><span data-ttu-id="3cb3d-127">显示文件路径</span><span class="sxs-lookup"><span data-stu-id="3cb3d-127">To display the file path</span></span>

<span data-ttu-id="3cb3d-128">在文件选项卡中，指向文件名。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-128">On the file tab, point to the file name.</span></span> <span data-ttu-id="3cb3d-129">脚本文件的完整限定路径显示在工具提示中。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-129">The fully qualified path to the script file appears in a tooltip.</span></span>

### <a name="to-run-a-script"></a><span data-ttu-id="3cb3d-130">运行脚本</span><span class="sxs-lookup"><span data-stu-id="3cb3d-130">To run a script</span></span>

<span data-ttu-id="3cb3d-131">在工具栏上，单击“运行脚本”，或在“文件”菜单上，单击“运行”。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-131">On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.</span></span>

### <a name="to-run-a-portion-of-a-script"></a><span data-ttu-id="3cb3d-132">运行脚本的一部分</span><span class="sxs-lookup"><span data-stu-id="3cb3d-132">To run a portion of a script</span></span>

1. <span data-ttu-id="3cb3d-133">在脚本窗格中，选择脚本的一部分。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-133">In the Script Pane, select a portion of a script.</span></span>

2. <span data-ttu-id="3cb3d-134">在“文件”菜单上，单击“运行选定内容”，或者在工具栏上，单击“运行选定内容”。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-134">On the **File** menu, click **Run Selection**, or on the toolbar, click **Run Selection**.</span></span>

### <a name="to-stop-a-running-script"></a><span data-ttu-id="3cb3d-135">停止正在运行的脚本</span><span class="sxs-lookup"><span data-stu-id="3cb3d-135">To stop a running script</span></span>

<span data-ttu-id="3cb3d-136">在工具栏上，单击“**停止操作**”，按 CTRL+BREAK，或者在“**文件**”菜单上，单击“**停止操作**”。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-136">On the toolbar, click **Stop Operation**, press CTRL+BREAK, or on the **File** menu, click **Stop Operation**.</span></span> <span data-ttu-id="3cb3d-137">按 **CTRL+C** 也适用，除非当前已选定文本，在这种情况下 **CTRL+C** 将映射为所选文本的副本函数。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-137">Pressing **CTRL+C** also works unless some text is currently selected, in which case **CTRL+C** maps to the copy function for the selected text.</span></span>

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a><span data-ttu-id="3cb3d-138">如何在脚本窗格中编写和编辑文本</span><span class="sxs-lookup"><span data-stu-id="3cb3d-138">How to write and edit text in the Script Pane</span></span>

<span data-ttu-id="3cb3d-139">使用以下步骤来在脚本窗格中编辑文本。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-139">Use the following steps to edit text in the Script Pane.</span></span> <span data-ttu-id="3cb3d-140">你可以复制、剪切、粘贴、查找和替换文本。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-140">You can copy, cut, paste, find, and replace text.</span></span> <span data-ttu-id="3cb3d-141">还可以撤消和重做刚执行的上一个操作。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-141">You can also undo and redo the last action you just performed.</span></span> <span data-ttu-id="3cb3d-142">执行这些操作的键盘快捷方式与用于所有 Windows 应用程序的相同。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-142">The keyboard shortcuts for performing these actions are the same as those used for all Windows applications.</span></span>

### <a name="to-enter-text-in-the-script-pane"></a><span data-ttu-id="3cb3d-143">在脚本窗格中输入文本</span><span class="sxs-lookup"><span data-stu-id="3cb3d-143">To enter text in the Script Pane</span></span>

1. <span data-ttu-id="3cb3d-144">通过在脚本窗格中单击任意位置，或单击“视图”菜单中的“转到脚本窗格”，将光标移到脚本窗格中。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-144">Move the cursor to the Script Pane by clicking anywhere in the Script Pane, or by clicking **Go to Script Pane** in the **View** menu.</span></span>

2. <span data-ttu-id="3cb3d-145">创建脚本。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-145">Create a script.</span></span> <span data-ttu-id="3cb3d-146">语法颜色设置和 Tab 自动补全使得 Windows PowerShell ISE 中的这一体验更为丰富。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-146">Syntax coloring and tab completion make this a richer experience in Windows PowerShell ISE.</span></span>

3. <span data-ttu-id="3cb3d-147">有关使用 Tab 自动补全功能协助键入的详细信息，请参阅[如何在脚本窗格和控制台窗格中使用 Tab 自动补全](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md)。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-147">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for details about using the tab completion feature to help in typing.</span></span>

### <a name="to-find-text-in-the-script-pane"></a><span data-ttu-id="3cb3d-148">在脚本窗格中查找文本</span><span class="sxs-lookup"><span data-stu-id="3cb3d-148">To find text in the Script Pane</span></span>

1. <span data-ttu-id="3cb3d-149">若要查找任何位置中的文本，请按 **CTRL+F**，或在“**编辑**”菜单上，单击“**在脚本中查找**”。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-149">To find text anywhere, press **CTRL+F** or, on the **Edit** menu, click **Find in Script**.</span></span>

2. <span data-ttu-id="3cb3d-150">若要查找光标位置后的文本，请按 **F3**，或在“编辑”菜单上，单击“在脚本中查找下一个”。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-150">To find text after the cursor, press **F3** or, on the **Edit** menu, click **Find Next in Script**.</span></span>

3. <span data-ttu-id="3cb3d-151">若要查找光标位置前的文本，请按 **SHIFT+F3**，或在“**编辑**”菜单上，单击“**在脚本中查找上一个**”。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-151">To find text before the cursor, press **SHIFT+F3** or, on the **Edit** menu, click **Find Previous in Script**.</span></span>

### <a name="to-find-and-replace-text-in-the-script-pane"></a><span data-ttu-id="3cb3d-152">在脚本窗格中查找并替换文本</span><span class="sxs-lookup"><span data-stu-id="3cb3d-152">To find and replace text in the Script Pane</span></span>

<span data-ttu-id="3cb3d-153">按 CTRL+H，或单击“编辑”菜单上的“在脚本中替换”。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-153">Press **CTRL+H** or, on the **Edit** menu, click **Replace in Script**.</span></span> <span data-ttu-id="3cb3d-154">输入想要查找的文本和想要替换它的文本，然后按 **ENTER**。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-154">Enter both the text you want to find and the text with which you want to replace it, and then press **ENTER**.</span></span>

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a><span data-ttu-id="3cb3d-155">转到脚本窗格中文本的特定行</span><span class="sxs-lookup"><span data-stu-id="3cb3d-155">To go to a particular line of text in the Script Pane</span></span>

1. <span data-ttu-id="3cb3d-156">在脚本窗格中，按 **CTRL+G**，或在“**编辑**”菜单上，单击“**转到行**”。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-156">In the Script Pane, press **CTRL+G** or, on the **Edit** menu, click **Go to Line**.</span></span>

2. <span data-ttu-id="3cb3d-157">输入行号。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-157">Enter a line number.</span></span>

### <a name="to-copy-text-in-the-script-pane"></a><span data-ttu-id="3cb3d-158">复制脚本窗格中的文本</span><span class="sxs-lookup"><span data-stu-id="3cb3d-158">To copy text in the Script Pane</span></span>

1. <span data-ttu-id="3cb3d-159">在脚本窗格中，选择想要从中复制的文本。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-159">In the Script Pane, select the text that you want to copy.</span></span>

2. <span data-ttu-id="3cb3d-160">按 **CTRL+C** 或在工具栏上，单击“**复制**”图标，或在“**编辑**”菜单上，单击“**复制**”。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-160">Press **CTRL+C** or, on the toolbar, click the **Copy** icon, or on the **Edit** menu, click **Copy**.</span></span>

### <a name="to-cut-text-in-the-script-pane"></a><span data-ttu-id="3cb3d-161">剪切脚本窗格中的文本</span><span class="sxs-lookup"><span data-stu-id="3cb3d-161">To cut text in the Script Pane</span></span>

1. <span data-ttu-id="3cb3d-162">在脚本窗格中，选择想要从中剪切的文本。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-162">In the Script Pane, select the text that you want to cut.</span></span>

2. <span data-ttu-id="3cb3d-163">按 **CTRL+X** 或在工具栏上，单击“**剪切**”图标，或在“**编辑**”菜单上，单击“**剪切**”。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-163">Press **CTRL+X** or, on the toolbar, click the **Cut** icon, or on the **Edit** menu, click **Cut**.</span></span>

### <a name="to-paste-text-into-the-script-pane"></a><span data-ttu-id="3cb3d-164">将文本粘贴到脚本窗格</span><span class="sxs-lookup"><span data-stu-id="3cb3d-164">To paste text into the Script Pane</span></span>

<span data-ttu-id="3cb3d-165">按 **CTRL+V** 或在工具栏上，单击“**粘贴**”图标，或在“**编辑**”菜单上，单击“**粘贴**”。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-165">Press **CTRL+V** or, on the toolbar, click the **Paste** icon, or on the **Edit** menu, click **Paste**.</span></span>

### <a name="to-undo-an-action-in-the-script-pane"></a><span data-ttu-id="3cb3d-166">撤消脚本窗格中的操作</span><span class="sxs-lookup"><span data-stu-id="3cb3d-166">To undo an action in the Script Pane</span></span>

<span data-ttu-id="3cb3d-167">按 **CTRL+Z** 或在工具栏上，单击“**撤消**”图标，或在“**编辑**”菜单上，单击“**撤消**”。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-167">Press **CTRL+Z** or, on the toolbar, click the **Undo** icon, or on the **Edit** menu, click **Undo**.</span></span>

### <a name="to-redo-an-action-in-the-script-pane"></a><span data-ttu-id="3cb3d-168">重做脚本窗格中的操作</span><span class="sxs-lookup"><span data-stu-id="3cb3d-168">To redo an action in the Script Pane</span></span>

<span data-ttu-id="3cb3d-169">按 **CTRL+Y** 或在工具栏上，单击“**重做**”图标，或在“**编辑**”菜单上，单击“**重做**”。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-169">Press **CTRL+Y** or, on the toolbar, click the **Redo** icon, or on the **Edit** menu, click **Redo**.</span></span>

## <a name="how-to-save-a-script"></a><span data-ttu-id="3cb3d-170">如何保存脚本</span><span class="sxs-lookup"><span data-stu-id="3cb3d-170">How to save a script</span></span>

<span data-ttu-id="3cb3d-171">使用以下步骤来保存并命名脚本。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-171">Use the following steps to save and name a script.</span></span> <span data-ttu-id="3cb3d-172">脚本名称旁将出现一个星号，用于标记更改后尚未保存的文件。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-172">An asterisk appears next to the script name to mark a file that has not been saved since it was altered.</span></span> <span data-ttu-id="3cb3d-173">保存该文件后，星号将消失。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-173">The asterisk disappears when the file is saved.</span></span>

### <a name="to-save-a-script"></a><span data-ttu-id="3cb3d-174">保存脚本</span><span class="sxs-lookup"><span data-stu-id="3cb3d-174">To save a script</span></span>

<span data-ttu-id="3cb3d-175">按 **CTRL+S** 或在工具栏上，单击“**保存**”图标，或在“**编辑**”菜单上，单击“**保存**”。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-175">Press **CTRL+S** or, on the toolbar, click the **Save** icon, or on the **File** menu, click **Save**.</span></span>

### <a name="to-save-and-name-a-script"></a><span data-ttu-id="3cb3d-176">保存并命名脚本</span><span class="sxs-lookup"><span data-stu-id="3cb3d-176">To save and name a script</span></span>

1. <span data-ttu-id="3cb3d-177">在“文件”菜单上，单击“另存为”。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-177">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="3cb3d-178">将出现“另存为”对话框。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-178">The **Save As** dialog box will appear.</span></span>

2. <span data-ttu-id="3cb3d-179">在“文件名称”框中，输入文件的名称。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-179">In the **File name** box, enter a name for the file.</span></span>

3. <span data-ttu-id="3cb3d-180">在“保存类型”框中，选择文件类型。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-180">In the **Save as type** box, select a file type.</span></span> <span data-ttu-id="3cb3d-181">例如，在“另存为类型”框中，选择“œPowerShell 脚本(\* .ps1)”。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-181">For example, in the **Save as type** box, select 'œPowerShell Scripts (\* .ps1)'.</span></span>

4. <span data-ttu-id="3cb3d-182">单击“保存”。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-182">Click **Save**.</span></span>

### <a name="to-save-a-script-in-ascii-encoding"></a><span data-ttu-id="3cb3d-183">以 ASCII 编码保存脚本</span><span class="sxs-lookup"><span data-stu-id="3cb3d-183">To save a script in ASCII encoding</span></span>

<span data-ttu-id="3cb3d-184">默认情况下，Windows PowerShell ISE 将新的脚本文件 (.ps1)、脚本数据文件 (.psd1) 和脚本模块文件 (.psm1) 保存为 Unicode (BigEndianUnicode)。若要以另一种编码保存脚本，如 ASCII (ANSI)，请对 [$psISE.CurrentFile](https://technet.microsoft.com/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile) 对象使用 Save 或 SaveAs 方法。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-184">By default, Windows PowerShell ISE saves new script files (.ps1), script data files (.psd1), and script module files (.psm1) as Unicode (BigEndianUnicode) by default.Â To save a script in another encoding, such as ASCII (ANSI), use the **Save** or **SaveAs** methods on the [$psISE.CurrentFile](https://technet.microsoft.com/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile) object.</span></span>

<span data-ttu-id="3cb3d-185">以下命令使用 ASCII 编码将新脚本保存为 MyScript.ps1。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-185">The following command saves a new script as MyScript.ps1 with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

<span data-ttu-id="3cb3d-186">下面的命令使用 ASCII 编码，将当前脚本文件替换为具有相同名称的文件。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-186">The following command replaces the current script file with a file with the same name, but with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

<span data-ttu-id="3cb3d-187">以下命令将获取当前文件的编码。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-187">The following command gets the encoding of the current file.</span></span>

```powershell
$psISE.CurrentFile.encoding
```

<span data-ttu-id="3cb3d-188">Windows PowerShell ISE 支持以下编码选项：ASCII、BigEndianUnicode、Unicode、UTF32、UTF7、UTF8 和默认值。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-188">Windows PowerShell ISE supports the following encoding options: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 and Default.</span></span> <span data-ttu-id="3cb3d-189">默认选项的值因系统而异。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-189">The value of the Default option varies with the system.</span></span>

<span data-ttu-id="3cb3d-190">Windows PowerShell ISE 不会更改在其他编辑器中创建的脚本的编码，即使你使用的是 Windows PowerShell ISE 中的“保存”或“另存为”命令。</span><span class="sxs-lookup"><span data-stu-id="3cb3d-190">Windows PowerShell ISE does not change the encoding of scripts that were created by in other editors, even when you use the Save or Save As commands in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="3cb3d-191">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3cb3d-191">See Also</span></span>

- [<span data-ttu-id="3cb3d-192">探究 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="3cb3d-192">Exploring the Windows PowerShell ISE</span></span>](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)