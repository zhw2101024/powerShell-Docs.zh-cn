---
title:  使用注册表项
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  91bfaecd-8684-48b4-ad86-065dfe6dc90a
---

# 使用注册表项
由于注册表项是 Windows PowerShell 驱动器上的项，因此使用它们的方法和使用文件及文件夹的方法非常相似。 一个关键区别在于，基于注册表的 Windows PowerShell 驱动器上的每个项都是一个容器，就像文件系统驱动器上有一个文件夹一样。 但是，注册表条目及其关联的值只是项的属性，而不是不同的项。

### 列出注册表项的所有子项
可以通过使用 **Get-ChildItem** 直接显示某个注册表项中的所有项目。 添加可选的 **Force** 参数以显示隐藏项或系统项。 例如，以下命令将直接显示 Windows PowerShell 驱动器 HKCU（对应于 HKEY_CURRENT_USER 注册表 Hive）中的项：

```
PS> Get-ChildItem -Path hkcu:\

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

SKC  VC Name                           Property
---  -- ----                           --------
  2   0 AppEvents                      {}
  7  33 Console                        {ColorTable00, ColorTable01, ColorTab...
 25   1 Control Panel                  {Opened}
  0   5 Environment                    {APR_ICONV_PATH, INCLUDE, LIB, TEMP...}
  1   7 Identities                     {Last Username, Last User ...
  4   0 Keyboard Layout                {}
...
```

这些是注册表编辑器 (Regedit.exe) 中 HKEY_CURRENT_USER 下可见的顶级项。

还可以通过指定注册表提供程序的名称（后跟“**::**”）来指定此注册表路径。 注册表提供程序的全名是 **Microsoft.PowerShell.Core\Registry**，但此名称可以缩短至只有 **Registry**。 任一以下命令都可直接列出 HKCU 下面的内容：

```
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

这些命令将仅列出直接包含的项，类似于使用 Cmd.exe 的 **DIR** 命令或 UNIX shell 中的 **ls**。 为了显示包含的项，需要指定 **Recurse** 参数。 若要列出 HKCU 中的所有注册表项，请使用以下命令（此操作可能需要很长的时间。）：

```
Get-ChildItem -Path hkcu:\ -Recurse
```

**Get-ChildItem** 可以通过其 **Path**、**Filter**、**Include** 和 **Exclude** 参数执行复杂的筛选功能，但这些参数通常只基于名称。 还可以通过使用 **Where-Object**cmdlet 基于项的其他属性执行复杂的筛选。 下面的命令用于查找只有一个子项并且刚好具有 4 个值的 HKCU:\Software 中的所有项：

```
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

### 复制项
复制通过 **Copy-Item** 完成。 下面的命令将 HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion 及其所有属性复制到 HKCU:\，从而创建名为“CurrentVersion”的新项：

```
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

如果你在注册表编辑器中检查此新项或通过使用 **Get-ChildItem**，你会注意到在新位置中没有包含的子项的副本。 为了复制容器的所有内容，需要指定 **Recurse** 参数。 若要使上述的复制命令递归，你将使用此命令：

```
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

你仍然可以使用已有的其他可用工具执行文件系统复制。 任何注册表编辑工具（包括 reg.exe、regini.exe 和 regedit.exe）以及支持注册表编辑的 COM 对象（如 WScript.Shell 和 WMI 的 StdRegProv 类）均可用于 Windows PowerShell。

### 创建项
在注册表中创建新项比在文件系统中创建新项简单。 由于所有注册表项都是容器，因此，你无需指定项类型；只需提供一个明确的路径即可，如：

```
New-Item -Path hkcu:\software\_DeleteMe
```

此外还可以使用基于提供程序的路径来指定某项：

```
New-Item -Path Registry::HKCU\_DeleteMe
```

### 删除项
从本质而言，删除项对所有提供程序都是相同的。 以下命令将以无提示方式删除项：

```
Remove-Item -Path hkcu:\Software\_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

### 删除特定项下的所有项
可以通过使用 **Remove-Item** 删除包含的项，但如果项包含任何其他内容，系统将提示你确认该删除。 例如，如果我们尝试删除我们创建的 HKCU:\CurrentVersion 子项，我们将看到：

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

若要在无提示下删除包含的项，请指定 **-Recurse** 参数：

```
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

如果想要删除 HKCU:\CurrentVersion 中的所有项而不是 HKCU:\CurrentVersion 本身，则可以改为使用：

```
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```



<!--HONumber=May16_HO2-->


