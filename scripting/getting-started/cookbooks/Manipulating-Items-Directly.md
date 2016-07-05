---
title: "直接操作项"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 8cbd4867-917d-41ea-9ff0-b8e765509735
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: b7e752a1615da4540106ec32754f873c5d7aa5d9

---

# 直接操作项
在 Windows PowerShell 驱动器中看到的元素（例如文件系统驱动器中的文件和文件夹），以及 Windows PowerShell 注册表驱动器中的注册表项在 Windows PowerShell 中均称为*项*。 用于使用这些项的 cmdlet 名称中具有名词 **Item**。

**Get\-Command \-Noun Item** 命令的输出显示有九个 Windows PowerShell 项 cmdlet。

```
PS> Get-Command -Noun Item

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Clear-Item                      Clear-Item [-Path] <String[]...
Cmdlet          Copy-Item                       Copy-Item [-Path] <String[]>...
Cmdlet          Get-Item                        Get-Item [-Path] <String[]> ...
Cmdlet          Invoke-Item                     Invoke-Item [-Path] <String[...
Cmdlet          Move-Item                       Move-Item [-Path] <String[]>...
Cmdlet          New-Item                        New-Item [-Path] <String[]> ...
Cmdlet          Remove-Item                     Remove-Item [-Path] <String[...
Cmdlet          Rename-Item                     Rename-Item [-Path] <String>...
Cmdlet          Set-Item                        Set-Item [-Path] <String[]> ...
```

### 创建新项 (New\-Item)
若要在文件系统中创建新项，请使用 **New\-Item** cmdlet。 包含带有项的路径的 **Path** 参数，以及值为“file”或“directory”的 **ItemType** 参数。

例如，若要在 C:\\Temp 目录中创建名为“New.Directory”的新目录，请键入：

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

若要创建文件，请将 **ItemType** 参数的值更改为“file”。 例如，若要在 New.Directory 目录中创建名为“file1.txt”的文件，请键入：

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

可以使用相同技术创建新的注册表项。 事实上，注册表项更容易创建，因为 Windows 注册表中的唯一项类型就是注册表项。 （注册表条目是项*属性*。）例如，若要在 CurrentVersion 子项中创建名为“\_Test”的项，请键入：

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

在键入注册表路径时，请确保在 Windows PowerShell 驱动器名称中包含冒号 (**:**)，如 HKLM: 和 HKCU:。 如果不带冒号，则 Windows PowerShell 无法识别路径中的驱动器名称。

### 为什么注册表值不是项
当使用 **Get\-ChildItem** cmdlet 查找注册表项中的项时，你将永远不会看到实际的注册表条目或对应的值。

例如，注册表项 **HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Run** 通常包含若干注册表条目，用于表示在系统启动时运行的应用程序。

但是，当使用 **Get\-ChildItem** 查找注册表项中的子项时，你只会看到注册表项的 **OptionalComponents** 子项：

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run
   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

尽管将注册表条目视为项会很方便，但无法确保指定的注册表条目路径是唯一的。 路径表示法不区分名为 **Run** 的注册表子项和 **Run** 子项中的 **(Default)** 注册表条目。 此外，由于注册表项名称可以包含反斜杠字符 (**\\**)，因此如果注册表项是项目，则无法使用路径表示法区分名为 **Windows\\CurrentVersion\\Run** 的注册表项和此路径中的子项。

### 重命名现有项 (Rename\-Item)
若要更改文件或文件夹的名称，请使用 **Rename\-Item** cmdlet。 以下命令将 **file1.txt** 文件的名称更改为 **fileOne.txt**。

```
PS> Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

**Rename\-Item** cmdlet 可以更改文件或文件夹的名称，但它不能移动项。 以下命令将失败，因为它尝试将文件从 New.Directory 目录移动到 Temp 目录。

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

### 移动项 (Move\-Item)
若要移动文件或文件夹，请使用 **Move\-Item** cmdlet。

例如，以下命令将 New.Directory 目录从 C:\\temp 目录移动到 C: 驱动器的根目录。 若要验证该项是否已移动，请包含 **Move\-Item** cmdlet 的 **PassThru** 参数。 在没有 **Passthru** 的情况下，**Move\-Item** cmdlet 不显示任何结果。

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

### 复制项 (Copy\-Item)
如果你熟悉其他 shell 中的复制操作，你可能会发现 Windows PowerShell 中的 **Copy\-Item** cmdlet 行为不正常。 将项从一个位置复制到另一个位置时，Copy\-Item 默认不复制其内容。

例如，如果将 **New.Directory** 目录从 C: 驱动器复制到 C:\\temp 目录，命令会成功运行，但不会复制 New.Directory 目录中的文件。

```
PS> Copy-Item -Path C:\New.Directory -Destination C:\temp
```

如果显示 **C:\\temp\\New.Directory** 的内容，你将发现它未包含任何文件：

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

为什么 **Copy\-Item** cmdlet 不将内容复制到新位置？

**Copy\-Item** cmdlet 的设计目标是通用；它不再仅仅用于复制文件和文件夹。 此外，即使在复制文件和文件夹时，你也可能只想要复制容器，而不是复制其中的项。

若要复制文件夹中的所有内容，请在命令中包含 **Copy\-Item** cmdlet 的 **Recurse** 参数。 如果你已复制目录，而未复制其内容，则可添加 **Force** 参数，该参数允许你覆盖空文件夹。

```
PS> Copy-Item -Path C:\New.Directory -Destination C:\temp -Recurse -Force -Passthru
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18   1:53 PM            New.Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

### 删除项 (Remove\-Item)
若要删除文件和文件夹，请使用 **Remove\-Item** cmdlet。 可进行重要且不可逆更改的 Windows PowerShell cmdlet（例如 **Remove\-Item**）在你输入其命令时通常会提示你进行确认。 例如，如果你尝试删除 **New.Directory** 文件夹，系统将提示你确认命令，因为该文件夹中包含文件：

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

由于“是”****是默认响应，因此若要删除文件夹及其文件，请按“Enter”****键。 若要删除文件夹而不进行确认，请使用 **\-Recurse** 参数。

```
PS> Remove-Item C:\temp\New.Directory -Recurse
```

### 执行项 (Invoke\-Item)
Windows PowerShell 使用 **Invoke\-Item** cmdlet 针对文件或文件夹执行默认操作。 此默认操作由注册表中的默认应用程序处理程序确定；效果与在文件资源管理器中双击该项的效果相同。

例如，假设你要运行以下命令：

```
PS> Invoke-Item C:\WINDOWS
```

位于 C:\\Windows 中的“资源管理器”窗口将会出现，正如双击 C:\\Windows 文件夹一样。

如果在 Windows Vista 之前的系统上调用 **Boot.ini** 文件：

```
PS> Invoke-Item C:\boot.ini
```

如果 .ini 文件类型与记事本相关联，则 boot.ini 文件将在记事本中打开。




<!--HONumber=Jun16_HO4-->


