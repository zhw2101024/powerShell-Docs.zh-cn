---
ms.date: 01/02/2020
keywords: powershell,cmdlet
title: 如何在 Windows PowerShell ISE 中编写和运行脚本
ms.openlocfilehash: 2e3122a3b436ba878d2c5f9d72d4f9e024d4d031
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737060"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a><span data-ttu-id="d8ca4-103">如何在 Windows PowerShell ISE 中编写和运行脚本</span><span class="sxs-lookup"><span data-stu-id="d8ca4-103">How to Write and Run Scripts in the Windows PowerShell ISE</span></span>

<span data-ttu-id="d8ca4-104">本文说明如何在脚本窗格中创建、编辑、运行以及保存脚本。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-104">This article describes how to create, edit, run, and save scripts in the Script Pane.</span></span>

## <a name="how-to-create-and-run-scripts"></a><span data-ttu-id="d8ca4-105">如何创建和运行脚本</span><span class="sxs-lookup"><span data-stu-id="d8ca4-105">How to create and run scripts</span></span>

<span data-ttu-id="d8ca4-106">可以在脚本窗格中打开和编辑 Windows PowerShell 文件。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-106">You can open and edit Windows PowerShell files in the Script Pane.</span></span> <span data-ttu-id="d8ca4-107">Windows PowerShell 中的相关特定文件类型有脚本文件 (`.ps1`)、脚本数据文件 (`.psd1`) 和脚本模块文件 (`.psm1`)。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-107">Specific file types of interest in Windows PowerShell are script files (`.ps1`), script data files (`.psd1`), and script module files (`.psm1`).</span></span> <span data-ttu-id="d8ca4-108">这些文件类型在脚本窗格编辑器中是经语法颜色设置的。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-108">These file types are syntax colored in the Script Pane editor.</span></span> <span data-ttu-id="d8ca4-109">可在脚本窗格中打开的其他常见文件类型有配置文件 (`.ps1xml`)、XML 文件和文本文件。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-109">Other common file types you may open in the Script Pane are configuration files (`.ps1xml`), XML files, and text files.</span></span>

> [!NOTE]
> <span data-ttu-id="d8ca4-110">Windows PowerShell 执行策略确定你是否可以运行脚本并加载 Windows PowerShell 配置文件。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-110">The Windows PowerShell execution policy determines whether you can run scripts and load Windows PowerShell profiles and configuration files.</span></span> <span data-ttu-id="d8ca4-111">默认执行策略（受限）可以防止运行所有脚本，并防止加载配置文件。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-111">The default execution policy, Restricted, prevents all scripts from running, and prevents loading profiles.</span></span> <span data-ttu-id="d8ca4-112">若要更改执行策略以允许加载和使用配置文件，请参阅 [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) 和 [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-112">To change the execution policy to allow profiles to load and be used, see [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) and [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).</span></span>

### <a name="to-create-a-new-script-file"></a><span data-ttu-id="d8ca4-113">创建新的脚本文件</span><span class="sxs-lookup"><span data-stu-id="d8ca4-113">To create a new script file</span></span>

<span data-ttu-id="d8ca4-114">在工具栏上，单击“新建”  ，或在“文件”  菜单上，单击“新建”  。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-114">On the toolbar, click **New**, or on the **File** menu, click **New**.</span></span> <span data-ttu-id="d8ca4-115">创建的文件将出现在当前 PowerShell 选项卡下的新建文件选项卡中。请记住，仅当有多个选项卡时，PowerShell 选项卡才可见。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-115">The created file appears in a new file tab under the current PowerShell tab. Remember that the PowerShell tabs are only visible when there are more than one.</span></span> <span data-ttu-id="d8ca4-116">默认情况下，将创建类型脚本文件 (`.ps1`)，但它可以使用新的名称和扩展名进行保存。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-116">By default a file of type script (`.ps1`) is created, but it can be saved with a new name and extension.</span></span> <span data-ttu-id="d8ca4-117">可以在同一个 PowerShell 选项卡中创建多个脚本文件。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-117">Multiple script files can be created in the same PowerShell tab.</span></span>

### <a name="to-open-an-existing-script"></a><span data-ttu-id="d8ca4-118">打开现有的脚本</span><span class="sxs-lookup"><span data-stu-id="d8ca4-118">To open an existing script</span></span>

<span data-ttu-id="d8ca4-119">在工具栏上，单击“打开”，或在“文件”菜单上，单击“打开”    。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-119">On the toolbar, click **Open**, or on the **File** menu, click **Open**.</span></span> <span data-ttu-id="d8ca4-120">在“打开”对话框中，选择想要打开的文件。 </span><span class="sxs-lookup"><span data-stu-id="d8ca4-120">In the **Open** dialog box, select the file you want to open.</span></span> <span data-ttu-id="d8ca4-121">打开的文件将出现在新选项卡中。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-121">The opened file appears in a new tab.</span></span>

### <a name="to-close-a-script-tab"></a><span data-ttu-id="d8ca4-122">关闭脚本选项卡</span><span class="sxs-lookup"><span data-stu-id="d8ca4-122">To close a script tab</span></span>

<span data-ttu-id="d8ca4-123">单击要关闭的文件选项卡的“关闭”  图标 (X  )，或选择“文件”  菜单，然后单击“关闭”  。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-123">Click the **Close** icon (**X**) of the file tab you want to close or select the **File** menu and click **Close**.</span></span>

<span data-ttu-id="d8ca4-124">如果自上次保存后该文件已被更改，系统会提示你保存或丢弃该文件。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-124">If the file has been altered since it was last saved, you're prompted to save or discard it.</span></span>

### <a name="to-display-the-file-path"></a><span data-ttu-id="d8ca4-125">显示文件路径</span><span class="sxs-lookup"><span data-stu-id="d8ca4-125">To display the file path</span></span>

<span data-ttu-id="d8ca4-126">在文件选项卡中，指向文件名。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-126">On the file tab, point to the file name.</span></span> <span data-ttu-id="d8ca4-127">脚本文件的完整限定路径显示在工具提示中。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-127">The fully qualified path to the script file appears in a tooltip.</span></span>

### <a name="to-run-a-script"></a><span data-ttu-id="d8ca4-128">运行脚本</span><span class="sxs-lookup"><span data-stu-id="d8ca4-128">To run a script</span></span>

<span data-ttu-id="d8ca4-129">在工具栏上，单击“运行脚本”，或在“文件”菜单上，单击“运行”。   </span><span class="sxs-lookup"><span data-stu-id="d8ca4-129">On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.</span></span>

### <a name="to-run-a-portion-of-a-script"></a><span data-ttu-id="d8ca4-130">运行脚本的一部分</span><span class="sxs-lookup"><span data-stu-id="d8ca4-130">To run a portion of a script</span></span>

1. <span data-ttu-id="d8ca4-131">在脚本窗格中，选择脚本的一部分。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-131">In the Script Pane, select a portion of a script.</span></span>
2. <span data-ttu-id="d8ca4-132">在“文件”菜单上，单击“运行选定内容”，或者在工具栏上，单击“运行选定内容”。   </span><span class="sxs-lookup"><span data-stu-id="d8ca4-132">On the **File** menu, click **Run Selection**, or on the toolbar, click **Run Selection**.</span></span>

### <a name="to-stop-a-running-script"></a><span data-ttu-id="d8ca4-133">停止正在运行的脚本</span><span class="sxs-lookup"><span data-stu-id="d8ca4-133">To stop a running script</span></span>

<span data-ttu-id="d8ca4-134">有几种方法可用来停止正在运行的脚本。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-134">There are several ways to stop a running script.</span></span>

- <span data-ttu-id="d8ca4-135">单击工具栏上的“停止操作” </span><span class="sxs-lookup"><span data-stu-id="d8ca4-135">Click **Stop Operation** on the toolbar</span></span>
- <span data-ttu-id="d8ca4-136">按 <kbd>CTRL</kbd>+<kbd>BREAK</kbd></span><span class="sxs-lookup"><span data-stu-id="d8ca4-136">Press <kbd>CTRL</kbd>+<kbd>BREAK</kbd></span></span>
- <span data-ttu-id="d8ca4-137">选择“文件”  菜单，然后单击“停止操作”  。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-137">Select the **File** menu and click **Stop Operation**.</span></span>

<span data-ttu-id="d8ca4-138">按 <kbd>CTRL</kbd>+<kbd>C</kbd> 也适用，除非当前已选定文本，在这种情况下，<kbd>CTRL</kbd>+<kbd>C</kbd> 将映射为所选文本的复制函数。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-138">Pressing <kbd>CTRL</kbd>+<kbd>C</kbd> also works unless some text is currently selected, in which case <kbd>CTRL</kbd>+<kbd>C</kbd> maps to the copy function for the selected text.</span></span>

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a><span data-ttu-id="d8ca4-139">如何在脚本窗格中编写和编辑文本</span><span class="sxs-lookup"><span data-stu-id="d8ca4-139">How to write and edit text in the Script Pane</span></span>

<span data-ttu-id="d8ca4-140">可以在脚本窗格中复制、剪切、粘贴、查找和替换文本。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-140">You can copy, cut, paste, find, and replace text in the Script Pane.</span></span> <span data-ttu-id="d8ca4-141">还可以撤消和重做刚执行的上一个操作。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-141">You can also undo and redo the last action you just performed.</span></span> <span data-ttu-id="d8ca4-142">这些操作的键盘快捷方式与用于所有 Windows 应用程序的相同。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-142">The keyboard shortcuts for these actions are the same shortcuts used for all Windows applications.</span></span>

### <a name="to-enter-text-in-the-script-pane"></a><span data-ttu-id="d8ca4-143">在脚本窗格中输入文本</span><span class="sxs-lookup"><span data-stu-id="d8ca4-143">To enter text in the Script Pane</span></span>

1. <span data-ttu-id="d8ca4-144">通过在脚本窗格中单击任意位置，或单击“视图”菜单中的“转到脚本窗格”，将光标移到脚本窗格中。  </span><span class="sxs-lookup"><span data-stu-id="d8ca4-144">Move the cursor to the Script Pane by clicking anywhere in the Script Pane, or by clicking **Go to Script Pane** in the **View** menu.</span></span>
2. <span data-ttu-id="d8ca4-145">创建脚本。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-145">Create a script.</span></span> <span data-ttu-id="d8ca4-146">语法颜色设置和 Tab 自动补全提供 Windows PowerShell ISE 中更丰富的体验。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-146">Syntax coloring and tab completion provide a richer editing experience in Windows PowerShell ISE.</span></span>
3. <span data-ttu-id="d8ca4-147">有关使用 Tab 自动补全功能协助键入的详细信息，请参阅[如何在脚本窗格和控制台窗格中使用 Tab 自动补全](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md)。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-147">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for details about using the tab completion feature to help in typing.</span></span>

### <a name="to-find-text-in-the-script-pane"></a><span data-ttu-id="d8ca4-148">在脚本窗格中查找文本</span><span class="sxs-lookup"><span data-stu-id="d8ca4-148">To find text in the Script Pane</span></span>

1. <span data-ttu-id="d8ca4-149">若要查找任何位置中的文本，请按 <kbd>CTRL</kbd>+<kbd>F</kbd>，或在“编辑”  菜单上，单击“在脚本中查找”  。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-149">To find text anywhere, press <kbd>CTRL</kbd>+<kbd>F</kbd> or, on the **Edit** menu, click **Find in Script**.</span></span>
2. <span data-ttu-id="d8ca4-150">若要查找光标位置后的文本，请按 <kbd>F3</kbd>，或在“编辑”菜单上，单击“在脚本中查找下一个”。  </span><span class="sxs-lookup"><span data-stu-id="d8ca4-150">To find text after the cursor, press <kbd>F3</kbd> or, on the **Edit** menu, click **Find Next in Script**.</span></span>
3. <span data-ttu-id="d8ca4-151">若要查找光标位置前的文本，请按 <kbd>SHIFT</kbd>+<kbd>F3</kbd>，或在“编辑”  菜单上，单击“在脚本中查找上一个”  。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-151">To find text before the cursor, press <kbd>SHIFT</kbd>+<kbd>F3</kbd> or, on the **Edit** menu, click **Find Previous in Script**.</span></span>

### <a name="to-find-and-replace-text-in-the-script-pane"></a><span data-ttu-id="d8ca4-152">在脚本窗格中查找并替换文本</span><span class="sxs-lookup"><span data-stu-id="d8ca4-152">To find and replace text in the Script Pane</span></span>

<span data-ttu-id="d8ca4-153">按 <kbd>CTRL</kbd>+<kbd>H</kbd>，或单击“编辑”  菜单上的“在脚本中替换”  。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-153">Press <kbd>CTRL</kbd>+<kbd>H</kbd> or, on the **Edit** menu, click **Replace in Script**.</span></span> <span data-ttu-id="d8ca4-154">输入要查找的文本和替换文本，然后按 ENTER<kbd></kbd>。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-154">Enter the text you want to find and the replacement text, then press <kbd>ENTER</kbd>.</span></span>

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a><span data-ttu-id="d8ca4-155">转到脚本窗格中文本的特定行</span><span class="sxs-lookup"><span data-stu-id="d8ca4-155">To go to a particular line of text in the Script Pane</span></span>

1. <span data-ttu-id="d8ca4-156">在脚本窗格中，按 <kbd>CTRL</kbd>+<kbd>G</kbd>，或在“编辑”  菜单上，单击“转到行”  。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-156">In the Script Pane, press <kbd>CTRL</kbd>+<kbd>G</kbd> or, on the **Edit** menu, click **Go to Line**.</span></span>

2. <span data-ttu-id="d8ca4-157">输入行号。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-157">Enter a line number.</span></span>

### <a name="to-copy-text-in-the-script-pane"></a><span data-ttu-id="d8ca4-158">复制脚本窗格中的文本</span><span class="sxs-lookup"><span data-stu-id="d8ca4-158">To copy text in the Script Pane</span></span>

1. <span data-ttu-id="d8ca4-159">在脚本窗格中，选择想要从中复制的文本。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-159">In the Script Pane, select the text that you want to copy.</span></span>

2. <span data-ttu-id="d8ca4-160">按 <kbd>CTRL</kbd>+<kbd>C</kbd> 或在工具栏上单击“复制”  图标，或在“编辑”  菜单上，单击“复制”  。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-160">Press <kbd>CTRL</kbd>+<kbd>C</kbd> or, on the toolbar, click the **Copy** icon, or on the **Edit** menu, click **Copy**.</span></span>

### <a name="to-cut-text-in-the-script-pane"></a><span data-ttu-id="d8ca4-161">剪切脚本窗格中的文本</span><span class="sxs-lookup"><span data-stu-id="d8ca4-161">To cut text in the Script Pane</span></span>

1. <span data-ttu-id="d8ca4-162">在脚本窗格中，选择想要从中剪切的文本。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-162">In the Script Pane, select the text that you want to cut.</span></span>
2. <span data-ttu-id="d8ca4-163">按 <kbd>CTRL</kbd>+<kbd>X</kbd> 或在工具栏上单击“剪切”  图标，或在“编辑”  菜单上，单击“剪切”  。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-163">Press <kbd>CTRL</kbd>+<kbd>X</kbd> or, on the toolbar, click the **Cut** icon, or on the **Edit** menu, click **Cut**.</span></span>

### <a name="to-paste-text-into-the-script-pane"></a><span data-ttu-id="d8ca4-164">将文本粘贴到脚本窗格</span><span class="sxs-lookup"><span data-stu-id="d8ca4-164">To paste text into the Script Pane</span></span>

<span data-ttu-id="d8ca4-165">按 <kbd>CTRL</kbd>+<kbd>V</kbd> 或在工具栏上单击“粘贴”  图标，或在“编辑”  菜单上，单击“粘贴”  。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-165">Press <kbd>CTRL</kbd>+<kbd>V</kbd> or, on the toolbar, click the **Paste** icon, or on the **Edit** menu, click **Paste**.</span></span>

### <a name="to-undo-an-action-in-the-script-pane"></a><span data-ttu-id="d8ca4-166">撤消脚本窗格中的操作</span><span class="sxs-lookup"><span data-stu-id="d8ca4-166">To undo an action in the Script Pane</span></span>

<span data-ttu-id="d8ca4-167">按 <kbd>CTRL</kbd>+<kbd>Z</kbd> 或在工具栏上单击“撤消”  图标，或在“编辑”  菜单上，单击“撤消”  。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-167">Press <kbd>CTRL</kbd>+<kbd>Z</kbd> or, on the toolbar, click the **Undo** icon, or on the **Edit** menu, click **Undo**.</span></span>

### <a name="to-redo-an-action-in-the-script-pane"></a><span data-ttu-id="d8ca4-168">重做脚本窗格中的操作</span><span class="sxs-lookup"><span data-stu-id="d8ca4-168">To redo an action in the Script Pane</span></span>

<span data-ttu-id="d8ca4-169">按 <kbd>CTRL</kbd>+<kbd>Y</kbd> 或在工具栏上单击“重做”  图标，或在“编辑”  菜单上，单击“重做”  。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-169">Press <kbd>CTRL</kbd>+<kbd>Y</kbd> or, on the toolbar, click the **Redo** icon, or on the **Edit** menu, click **Redo**.</span></span>

## <a name="how-to-save-a-script"></a><span data-ttu-id="d8ca4-170">如何保存脚本</span><span class="sxs-lookup"><span data-stu-id="d8ca4-170">How to save a script</span></span>

<span data-ttu-id="d8ca4-171">脚本名称旁将出现一个星号，用于标记更改后尚未保存的文件。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-171">An asterisk appears next to the script name to mark a file that hasn't been saved since it was changed.</span></span> <span data-ttu-id="d8ca4-172">保存该文件后，星号将消失。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-172">The asterisk disappears when the file is saved.</span></span>

### <a name="to-save-a-script"></a><span data-ttu-id="d8ca4-173">保存脚本</span><span class="sxs-lookup"><span data-stu-id="d8ca4-173">To save a script</span></span>

<span data-ttu-id="d8ca4-174">按 <kbd>CTRL</kbd>+<kbd>S</kbd> 或在工具栏上单击“保存”  图标，或在“文件”  菜单上，单击“保存”  。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-174">Press <kbd>CTRL</kbd>+<kbd>S</kbd> or, on the toolbar, click the **Save** icon, or on the **File** menu, click **Save**.</span></span>

### <a name="to-save-and-name-a-script"></a><span data-ttu-id="d8ca4-175">保存并命名脚本</span><span class="sxs-lookup"><span data-stu-id="d8ca4-175">To save and name a script</span></span>

1. <span data-ttu-id="d8ca4-176">在“文件”菜单上，单击“另存为”。  </span><span class="sxs-lookup"><span data-stu-id="d8ca4-176">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="d8ca4-177">将出现“另存为”对话框。 </span><span class="sxs-lookup"><span data-stu-id="d8ca4-177">The **Save As** dialog box will appear.</span></span>
2. <span data-ttu-id="d8ca4-178">在“文件名称”框中，输入文件的名称。 </span><span class="sxs-lookup"><span data-stu-id="d8ca4-178">In the **File name** box, enter a name for the file.</span></span>
3. <span data-ttu-id="d8ca4-179">在“保存类型”框中，选择文件类型。 </span><span class="sxs-lookup"><span data-stu-id="d8ca4-179">In the **Save as type** box, select a file type.</span></span> <span data-ttu-id="d8ca4-180">例如，在“另存为类型”  框中，选择“PowerShell 脚本 (`*.ps1`)”。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-180">For example, in the **Save as type** box, select 'PowerShell Scripts (`*.ps1`)'.</span></span>
4. <span data-ttu-id="d8ca4-181">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-181">Click **Save**.</span></span>

### <a name="to-save-a-script-in-ascii-encoding"></a><span data-ttu-id="d8ca4-182">以 ASCII 编码保存脚本</span><span class="sxs-lookup"><span data-stu-id="d8ca4-182">To save a script in ASCII encoding</span></span>

<span data-ttu-id="d8ca4-183">默认情况下，Windows PowerShell ISE 将新的脚本文件 (`.ps1`)、脚本数据文件 (`.psd1`) 和脚本模块文件 (`.psm1`) 保存为 Unicode (BigEndianUnicode)。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-183">By default, Windows PowerShell ISE saves new script files (`.ps1`), script data files (`.psd1`), and script module files (`.psm1`) as Unicode (BigEndianUnicode) by default.</span></span> <span data-ttu-id="d8ca4-184">若要以另一种编码保存脚本，如 ASCII (ANSI)，请对 [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md) 对象使用 **Save** 或 **SaveAs** 方法。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-184">To save a script in another encoding, such as ASCII (ANSI), use the **Save** or **SaveAs** methods on the [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md) object.</span></span>

<span data-ttu-id="d8ca4-185">以下命令使用 ASCII 编码将新脚本保存为 MyScript.ps1。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-185">The following command saves a new script as MyScript.ps1 with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

<span data-ttu-id="d8ca4-186">下面的命令使用 ASCII 编码，将当前脚本文件替换为具有相同名称的文件。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-186">The following command replaces the current script file with a file with the same name, but with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

<span data-ttu-id="d8ca4-187">以下命令将获取当前文件的编码。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-187">The following command gets the encoding of the current file.</span></span>

```powershell
$psISE.CurrentFile.encoding
```

<span data-ttu-id="d8ca4-188">Windows PowerShell ISE 支持以下编码选项：ASCII、BigEndianUnicode、Unicode、UTF32、UTF7、UTF8 和默认值。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-188">Windows PowerShell ISE supports the following encoding options: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8, and Default.</span></span> <span data-ttu-id="d8ca4-189">默认选项的值因系统而异。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-189">The value of the Default option varies with the system.</span></span>

<span data-ttu-id="d8ca4-190">使用“保存”或“另存为”命令时，Windows PowerShell ISE 不会更改脚本文件的编码。</span><span class="sxs-lookup"><span data-stu-id="d8ca4-190">Windows PowerShell ISE doesn't change the encoding of script files when you use the Save or Save As commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8ca4-191">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d8ca4-191">See Also</span></span>

- [<span data-ttu-id="d8ca4-192">探究 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="d8ca4-192">Exploring the Windows PowerShell ISE</span></span>](exploring-the-windows-powershell-ise.md)
