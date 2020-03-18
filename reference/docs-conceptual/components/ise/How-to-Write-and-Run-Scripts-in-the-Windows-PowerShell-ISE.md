---
ms.date: 01/02/2020
keywords: powershell,cmdlet
title: 如何在 Windows PowerShell ISE 中编写和运行脚本
ms.openlocfilehash: 2e3122a3b436ba878d2c5f9d72d4f9e024d4d031
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "79402524"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a>如何在 Windows PowerShell ISE 中编写和运行脚本

本文说明如何在脚本窗格中创建、编辑、运行以及保存脚本。

## <a name="how-to-create-and-run-scripts"></a>如何创建和运行脚本

可以在脚本窗格中打开和编辑 Windows PowerShell 文件。 Windows PowerShell 中的相关特定文件类型有脚本文件 (`.ps1`)、脚本数据文件 (`.psd1`) 和脚本模块文件 (`.psm1`)。 这些文件类型在脚本窗格编辑器中是经语法颜色设置的。 可在脚本窗格中打开的其他常见文件类型有配置文件 (`.ps1xml`)、XML 文件和文本文件。

> [!NOTE]
> Windows PowerShell 执行策略确定你是否可以运行脚本并加载 Windows PowerShell 配置文件。 默认执行策略（受限）可以防止运行所有脚本，并防止加载配置文件。 若要更改执行策略以允许加载和使用配置文件，请参阅 [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) 和 [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)。

### <a name="to-create-a-new-script-file"></a>创建新的脚本文件

在工具栏上，单击“新建”  ，或在“文件”  菜单上，单击“新建”  。 创建的文件将出现在当前 PowerShell 选项卡下的新建文件选项卡中。请记住，仅当有多个选项卡时，PowerShell 选项卡才可见。 默认情况下，将创建类型脚本文件 (`.ps1`)，但它可以使用新的名称和扩展名进行保存。 可以在同一个 PowerShell 选项卡中创建多个脚本文件。

### <a name="to-open-an-existing-script"></a>打开现有的脚本

在工具栏上，单击“打开”，或在“文件”菜单上，单击“打开”    。 在“打开”对话框中，选择想要打开的文件。  打开的文件将出现在新选项卡中。

### <a name="to-close-a-script-tab"></a>关闭脚本选项卡

单击要关闭的文件选项卡的“关闭”  图标 (X  )，或选择“文件”  菜单，然后单击“关闭”  。

如果自上次保存后该文件已被更改，系统会提示你保存或丢弃该文件。

### <a name="to-display-the-file-path"></a>显示文件路径

在文件选项卡中，指向文件名。 脚本文件的完整限定路径显示在工具提示中。

### <a name="to-run-a-script"></a>运行脚本

在工具栏上，单击“运行脚本”，或在“文件”菜单上，单击“运行”。   

### <a name="to-run-a-portion-of-a-script"></a>运行脚本的一部分

1. 在脚本窗格中，选择脚本的一部分。
2. 在“文件”菜单上，单击“运行选定内容”，或者在工具栏上，单击“运行选定内容”。   

### <a name="to-stop-a-running-script"></a>停止正在运行的脚本

有几种方法可用来停止正在运行的脚本。

- 单击工具栏上的“停止操作” 
- 按 <kbd>CTRL</kbd>+<kbd>BREAK</kbd>
- 选择“文件”  菜单，然后单击“停止操作”  。

按 <kbd>CTRL</kbd>+<kbd>C</kbd> 也适用，除非当前已选定文本，在这种情况下，<kbd>CTRL</kbd>+<kbd>C</kbd> 将映射为所选文本的复制函数。

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a>如何在脚本窗格中编写和编辑文本

可以在脚本窗格中复制、剪切、粘贴、查找和替换文本。 还可以撤消和重做刚执行的上一个操作。 这些操作的键盘快捷方式与用于所有 Windows 应用程序的相同。

### <a name="to-enter-text-in-the-script-pane"></a>在脚本窗格中输入文本

1. 通过在脚本窗格中单击任意位置，或单击“视图”菜单中的“转到脚本窗格”，将光标移到脚本窗格中。  
2. 创建脚本。 语法颜色设置和 Tab 自动补全提供 Windows PowerShell ISE 中更丰富的体验。
3. 有关使用 Tab 自动补全功能协助键入的详细信息，请参阅[如何在脚本窗格和控制台窗格中使用 Tab 自动补全](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md)。

### <a name="to-find-text-in-the-script-pane"></a>在脚本窗格中查找文本

1. 若要查找任何位置中的文本，请按 <kbd>CTRL</kbd>+<kbd>F</kbd>，或在“编辑”  菜单上，单击“在脚本中查找”  。
2. 若要查找光标位置后的文本，请按 <kbd>F3</kbd>，或在“编辑”菜单上，单击“在脚本中查找下一个”。  
3. 若要查找光标位置前的文本，请按 <kbd>SHIFT</kbd>+<kbd>F3</kbd>，或在“编辑”  菜单上，单击“在脚本中查找上一个”  。

### <a name="to-find-and-replace-text-in-the-script-pane"></a>在脚本窗格中查找并替换文本

按 <kbd>CTRL</kbd>+<kbd>H</kbd>，或单击“编辑”  菜单上的“在脚本中替换”  。 输入要查找的文本和替换文本，然后按 ENTER<kbd></kbd>。

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a>转到脚本窗格中文本的特定行

1. 在脚本窗格中，按 <kbd>CTRL</kbd>+<kbd>G</kbd>，或在“编辑”  菜单上，单击“转到行”  。

2. 输入行号。

### <a name="to-copy-text-in-the-script-pane"></a>复制脚本窗格中的文本

1. 在脚本窗格中，选择想要从中复制的文本。

2. 按 <kbd>CTRL</kbd>+<kbd>C</kbd> 或在工具栏上单击“复制”  图标，或在“编辑”  菜单上，单击“复制”  。

### <a name="to-cut-text-in-the-script-pane"></a>剪切脚本窗格中的文本

1. 在脚本窗格中，选择想要从中剪切的文本。
2. 按 <kbd>CTRL</kbd>+<kbd>X</kbd> 或在工具栏上单击“剪切”  图标，或在“编辑”  菜单上，单击“剪切”  。

### <a name="to-paste-text-into-the-script-pane"></a>将文本粘贴到脚本窗格

按 <kbd>CTRL</kbd>+<kbd>V</kbd> 或在工具栏上单击“粘贴”  图标，或在“编辑”  菜单上，单击“粘贴”  。

### <a name="to-undo-an-action-in-the-script-pane"></a>撤消脚本窗格中的操作

按 <kbd>CTRL</kbd>+<kbd>Z</kbd> 或在工具栏上单击“撤消”  图标，或在“编辑”  菜单上，单击“撤消”  。

### <a name="to-redo-an-action-in-the-script-pane"></a>重做脚本窗格中的操作

按 <kbd>CTRL</kbd>+<kbd>Y</kbd> 或在工具栏上单击“重做”  图标，或在“编辑”  菜单上，单击“重做”  。

## <a name="how-to-save-a-script"></a>如何保存脚本

脚本名称旁将出现一个星号，用于标记更改后尚未保存的文件。 保存该文件后，星号将消失。

### <a name="to-save-a-script"></a>保存脚本

按 <kbd>CTRL</kbd>+<kbd>S</kbd> 或在工具栏上单击“保存”  图标，或在“文件”  菜单上，单击“保存”  。

### <a name="to-save-and-name-a-script"></a>保存并命名脚本

1. 在“文件”菜单上，单击“另存为”。   将出现“另存为”对话框。 
2. 在“文件名称”框中，输入文件的名称。 
3. 在“保存类型”框中，选择文件类型。  例如，在“另存为类型”  框中，选择“PowerShell 脚本 (`*.ps1`)”。
4. 单击“ **保存**”。

### <a name="to-save-a-script-in-ascii-encoding"></a>以 ASCII 编码保存脚本

默认情况下，Windows PowerShell ISE 将新的脚本文件 (`.ps1`)、脚本数据文件 (`.psd1`) 和脚本模块文件 (`.psm1`) 保存为 Unicode (BigEndianUnicode)。 若要以另一种编码保存脚本，如 ASCII (ANSI)，请对 [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md) 对象使用 **Save** 或 **SaveAs** 方法。

以下命令使用 ASCII 编码将新脚本保存为 MyScript.ps1。

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

下面的命令使用 ASCII 编码，将当前脚本文件替换为具有相同名称的文件。

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

以下命令将获取当前文件的编码。

```powershell
$psISE.CurrentFile.encoding
```

Windows PowerShell ISE 支持以下编码选项：ASCII、BigEndianUnicode、Unicode、UTF32、UTF7、UTF8 和默认值。 默认选项的值因系统而异。

使用“保存”或“另存为”命令时，Windows PowerShell ISE 不会更改脚本文件的编码。

## <a name="see-also"></a>另请参阅

- [探究 Windows PowerShell ISE](exploring-the-windows-powershell-ise.md)
