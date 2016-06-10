---
title:  如何在 Windows PowerShell ISE 中编写和运行脚本
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  62f916d9-b3a1-484a-bdfb-41f57112c22b
---

# 如何在 Windows PowerShell ISE 中编写和运行脚本
本主题说明如何在脚本窗格中创建、编辑、运行以及保存脚本。

-   [如何创建和运行脚本](#bkmk_1)

-   [如何在脚本窗格中编写和编辑文本](#bkmk_2)

-   [如何保存脚本](#bkmk_3)

## <a name="bkmk_1"></a>如何创建和运行脚本
你可以在脚本窗格中打开和编辑 Windows PowerShellÂ® 文件。 Windows PowerShellÂ® 中相关的特定文件类型包括脚本文件 (.ps1)、脚本数据文件 (.psd1) 和脚本模块文件 (.psm1)。 这些文件类型在脚本窗格编辑器中是经语法颜色设置的。 可能在脚本窗格中打开的其他常见文件类型有配置文件 (.ps1xml)、XML 文件和文本文件。

> [!NOTE]
> Windows PowerShell 执行策略确定你是否可以运行脚本并加载 Windows PowerShell 配置文件。 默认执行策略（受限）可以防止运行所有脚本，并防止加载配置文件。 若要将执行策略更改为允许加载和使用配置文件，请参阅 [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/en-us/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) 和 [about_Signing [v4]](https://technet.microsoft.com/en-us/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d)。

### 创建新的脚本文件
在工具栏上，单击“新建”，或在“文件”菜单上，单击“新建”。 创建的文件将出现在当前 PowerShell 选项卡下的新建文件选项卡中。 请记住，仅当有多个选项卡时，PowerShell 选项卡才可见。 默认情况下，将创建类型脚本文件 (.ps1)，但它可以使用新的名称和扩展名进行保存。 可以在同一个 PowerShell 选项卡中创建多个脚本文件。

### 打开现有的脚本
在工具栏上，单击“打开…”，或在“文件”菜单上，单击“打开”。 在“打开”对话框中，选择想要打开的文件。 打开的文件将出现在新选项卡中。

### 关闭脚本选项卡
单击你想要关闭的脚本的脚本选项卡，然后执行以下其中一项操作：

1.  单击脚本选项卡上的“关闭”图标 (X)。

2.  在“文件”菜单中，单击“关闭”。

如果自上次保存后该文件已被更改，系统会提示你保存或丢弃该文件。

### 显示文件路径
在文件选项卡中，指向文件名。 脚本文件的完整限定路径显示在工具提示中。

### 运行脚本
在工具栏上，单击“运行脚本”，或在“文件”菜单上，单击“运行”。

### 运行脚本的一部分

1.  在脚本窗格中，选择脚本的一部分。

2.  在“文件”菜单上，单击“运行选定内容”，或者在工具栏上，单击“运行选定内容”。

### 停止正在运行的脚本
在工具栏上，单击“停止操作”，按 CTRL+BREAK，或者在“文件”菜单上，单击“停止操作”。 按 **CTRL+C** 也适用，除非当前已选定文本，在这种情况下 **CTRL+C** 将映射为所选文本的副本函数。

## <a name="bkmk_2"></a>如何在脚本窗格中编写和编辑文本
使用以下步骤来在脚本窗格中编辑文本。 你可以复制、剪切、粘贴、查找和替换文本。 还可以撤消和重做刚执行的上一个操作。 执行这些操作的键盘快捷方式与用于所有 Windows 应用程序的相同。

### 在脚本窗格中输入文本

1.  通过在脚本窗格中单击任意位置，或单击“视图”菜单中的“转到脚本窗格”，将光标移到脚本窗格中。

2.  创建脚本。 语法颜色设置和 Tab 自动补全使得 Windows PowerShell ISE 中的这一体验更为丰富。

3.  有关使用 Tab 自动补全功能协助键入的详细信息，请参阅[如何在脚本窗格和控制台窗格中使用 Tab 自动补全](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md)。

### 在脚本窗格中查找文本

1.  若要查找任何位置中的文本，请按 **CTRL+F**，或在“编辑”菜单上，单击“在脚本中查找”。

2.  若要查找光标位置后的文本，请按 **F3**，或在“编辑”菜单上，单击“在脚本中查找下一个”。

3.  若要查找光标位置前的文本，请按 **SHIFT+F3**，或在“编辑”菜单上，单击“在脚本中查找上一个”。

### 在脚本窗格中查找并替换文本
按 **CRTL+H** 或在“编辑”菜单上，单击“在脚本中替换”。 输入想要查找的文本和想要替换它的文本，然后按 **ENTER**。

### 转到脚本窗格中文本的特定行

1.  在脚本窗格中，按 **CTRL+G**，或在“编辑”菜单上，单击“转到行”。

2.  输入行号。

### 复制脚本窗格中的文本

1.  在脚本窗格中，选择想要从中复制的文本。

2.  按 **CTRL+C** 或在工具栏上，单击“复制”图标，或在“编辑”菜单上，单击“复制”。

### 剪切脚本窗格中的文本

1.  在脚本窗格中，选择想要从中剪切的文本。

2.  按 **CTRL+X** 或在工具栏上，单击“剪切”图标，或在“编辑”菜单上，单击“剪切”。

### 将文本粘贴到脚本窗格
按 **CTRL+V** 或在工具栏上，单击“粘贴”图标，或在“编辑”菜单上，单击“粘贴”。

### 撤消脚本窗格中的操作
按 **CTRL+Z** 或在工具栏上，单击“撤消”图标，或在“编辑”菜单上，单击“撤消”。

### 重做脚本窗格中的操作
按 **CTRL+Y** 或在工具栏上，单击“重做”图标，或在“编辑”菜单上，单击“重做”。

## <a name="bkmk_3"></a>如何保存脚本
使用以下步骤来保存并命名脚本。 脚本名称旁将出现一个星号，用于标记更改后尚未保存的文件。 保存该文件后，星号将消失。

### 保存脚本
按 **CTRL+S** 或在工具栏上，单击“保存”图标，或在“编辑”菜单上，单击“保存”。

### 保存并命名脚本

1.  在“文件”菜单上，单击“另存为”。 将出现“另存为”对话框。

2.  在“文件名称”框中，输入文件的名称。

3.  在“保存类型”框中，选择文件类型。 例如，在“保存类型”框中，选择 “PowerShell Scripts (* .ps1)”。

4.  单击“保存”。

### 以 ASCII 编码保存脚本
默认情况下，Windows PowerShell ISE 将新的脚本文件 (.ps1)、脚本数据文件 (.psd1) 和脚本模块文件 (.psm1) 保存为 Unicode (BigEndianUnicode)。 若要以另一种编码保存脚本，如 ASCII (ANSI)，请对 [$psISE.CurrentFile](https://technet.microsoft.com/en-us/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile) 对象使用 **Save** 或 **SaveAs** 方法。

以下命令使用 ASCII 编码将新脚本保存为 MyScript.ps1。

```
$psise.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

下面的命令使用 ASCII 编码，将当前脚本文件替换为具有相同名称的文件。

```
$psise.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

以下命令将获取当前文件的编码。

```
$psise.CurrentFile.encoding
```

Windows PowerShell ISE 支持以下编码选项：ASCII、BigEndianUnicode、Unicode、UTF32、UTF7、UTF8 和默认值。 默认选项的值因系统而异。

Windows PowerShell ISE 不会更改在其他编辑器中创建的脚本的编码，即使你使用的是 Windows PowerShell ISE 中的“保存”或“另存为”命令。

## 另请参阅
[使用 Windows PowerShell ISE](Using-the-Windows-PowerShell-ISE.md)



<!--HONumber=May16_HO2-->


