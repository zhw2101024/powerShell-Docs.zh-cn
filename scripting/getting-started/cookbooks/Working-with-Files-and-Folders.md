---
title:  使用文件和文件夹
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  c0ceb96b-e708-45f3-803b-d1f61a48f4c1
---

# 使用文件和文件夹
在 Windows PowerShell 驱动器中导航和操作其上面的项类似于操作 Windows 物理磁盘驱动器上的文件和文件夹。 本节我们将讨论如何处理特定文件和文件夹操作任务。

### 列出某个文件夹内的所有文件和文件夹
可以通过使用 **Get-ChildItem** 直接获取某个文件夹中的所有项目。 添加可选的 **Force** 参数以显示隐藏项或系统项。 例如，此命令将显示 Windows PowerShell 驱动器 C（它与 Windows 物理驱动器 C 相同）的直观内容：

```
Get-ChildItem -Force C:\
```

该命令将仅列出直接包含的项，类似于使用 Cmd.exe 的 **DIR** 命令或 UNIX shell 中的 **ls**。 为了显示包含的项，你还需要指定 **-Recurse** 参数。 （这可能需要相当长的时间才能完成。）列出 C 驱动器上的所有内容：

```
Get-ChildItem -Force C:\ -Recurse
```

**Get-ChildItem** 可以使用其 **Path**、**Filter**、**Include** 和 **Exclude** 参数筛选项，但那些通常只基于名称。 还可以通过使用 **Where-Object** 基于项的其他属性执行复杂的筛选。

下面的命令用于查找上次于 2005 年 10 月 1 日之后修改，并且不小于 1 兆字节，也不大于 10 兆字节的 Program Files 文件夹中的所有可执行文件：

```
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt "2005-10-01") -and ($_.Length -ge 1m) -and ($_.Length -le 10m)}
```

### 复制文件和文件夹
复制通过 **Copy-Item** 完成。 以下命令用于将 C:\boot.ini 备份到 C:\boot.bak：

```
Copy-Item -Path c:\boot.ini -Destination c:\boot.bak
```

如果目标文件已存在，则复制尝试失败。 若要覆盖预先存在的目标，请使用 Force 参数：

```
Copy-Item -Path c:\boot.ini -Destination c:\boot.bak -Force
```

即使当目标为只读时，该命令也有效。

复制文件夹的操作方式与此相同。 此命令用于以递归方式将文件夹 C:\temp\test1 复制到新文件夹 c:\temp\DeleteMe：

```
Copy-Item C:\temp\test1 -Recurse c:\temp\DeleteMe
```

还可以复制选定的项。 以下命令用于将 c:\data 中任意位置包含的所有 .txt 文件复制到 c:\temp\text：

```
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination c:\temp\text
```

你仍然可以使用其他工具执行文件系统复制。 XCOPY、ROBOCOPY 和 COM 对象（如 **Scripting.FileSystemObject**）都适用于 Windows PowerShell。 例如，可以使用 Windows Script Host **Scripting.FileSystem COM** 类将 C:\boot.ini 备份到 C:\boot.bak：

```
(New-Object -ComObject Scripting.FileSystemObject).CopyFile("c:\boot.ini", "c:\boot.bak")
```

### 创建文件和文件夹
创建新项的操作方式在所有 Windows PowerShell 提供程序上都相同。 如果某个 Windows PowerShell 提供程序具有多个类型的项（例如，用于区分目录和文件的 FileSystem Windows PowerShell 提供程序），则需要指定项类型。

以下命令可创建一个新文件夹 C:\temp\New Folder：

```
New-Item -Path 'C:\temp\New Folder' -ItemType "directory"
```

以下命令可创建新的空文件 C:\temp\New Folder\file.txt：

```
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType "file"
```

### 删除某个文件夹内的所有文件和文件夹
你可以使用 **Remove-Item** 删除包含的项，但如果项包含任何其他内容，系统将提示你确认该删除。 例如，如果尝试删除包含其他项的文件夹 C:\temp\DeleteMe，则在删除该文件夹之前 Windows PowerShell 会提示你确认：

```
Remove-Item C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

如果不希望系统针对每个包含的项都提示你，则指定 **Recurse** 参数：

```
Remove-Item C:\temp\DeleteMe -Recurse
```

### 将本地文件夹映射为 Windows 可访问驱动器
你还可以使用 **subst** 命令映射本地文件夹。 以下命令可在根路径为本地 Program Files 的目录中创建本地驱动器 P:：

```
subst p: $env:programfiles
```

正如网络驱动器一样，使用 **subst** 在 Windows PowerShell 内映射的驱动器将对 Windows PowerShell shell 立即可见。

### 将文本文件数据读取到数组中
文本数据更常见的存储格式之一是采用文件形式，其中单独的行被视为不同的数据元素。 **Get-Content** cmdlet 可用于一步读取整个文件，如下所示：

```
PS> Get-Content -Path C:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
 /noexecute=AlwaysOff /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=" Microsoft Windows XP Professional 
with Data Execution Prevention" /noexecute=optin /fastdetect
```

**Get-Content** 已将从文件读取的数据视为数组，其中每行文件内容视为一个元素。 可以通过检查返回的内容的**长度**来确认此点：

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

此命令对于直接从 Windows PowerShell 获取列表信息最为有用。 例如，你可能会在文件 C:\temp\domainMembers.txt 中存储计算机名称或 IP 地址的列表，其中文件的每一行上一个名称。 你可以使用 **Get-Content** 来检索文件内容并将它们放在变量 **$Computers** 中：

```
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

**$Computers** 现在是一个数组，其中每个元素包含一个计算机名。



<!--HONumber=May16_HO2-->


