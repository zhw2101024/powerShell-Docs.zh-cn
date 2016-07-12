---
title: "管理当前位置"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: a9f9e7a7-3ea8-47d3-bbb4-6e437f6d4a4a
translationtype: Human Translation
ms.sourcegitcommit: ffd2151603eb87f007e6596624a126585840f8a4
ms.openlocfilehash: 22c5df4f62f21f690800eaffe47afee604cc61d3

---

# 管理当前位置
在文件资源管理器中导航文件夹系统时，通常具有一个特定的工作位置（即当前打开的文件夹）。 通过单击当前文件夹中的项，可轻松对其进行操作。 对于命令行接口（例如 Cmd.exe），当你位于特定文件所在的相同文件夹中时，你可以通过指定一个相对较短的名称来访问它，而无需指定该文件的完整路径。 当前目录称为工作目录。

Windows PowerShell 使用名词 **Location** 来引用工作目录，并实现一系列 cmdlet 以检查你的位置并对其进行操作。

### 获取你的当前位置 (Get\-Location)
若要确定你的当前目录位置的路径，请输入 **Get\-Location** 命令：

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> Get\-Location cmdlet 类似于 BASH shell 中的 **pwd** 命令。 Set\-Location cmdlet 类似于 Cmd.exe 中的 **cd** 命令。

### 设置你的当前位置 (Set\-Location)
**Get\-Location** 命令与 **Set\-Location** 命令结合使用。 **Set\-Location** 命令允许你指定当前目录位置。

```
PS> Set-Location -Path C:\Windows
```

输入命令后，你将注意到你不会收到任何有关该命令影响的直接反馈。 执行某项操作的大多数 Windows PowerShell 命令可生成很少的输出或根本不会生成输出，因为该输出并不总是有用。 若要验证在你输入 **Set\-Location** 命令时是否已成功更改目录，请在输入 **Set\-Location** 命令时包含 **\-PassThru** 参数：

```
PS> Set-Location -Path C:\Windows -PassThru
Path
----
C:\WINDOWS
```

可将 **\-PassThru** 参数与 Windows PowerShell 中的许多 Set 命令结合使用，以在没有默认输出的情况下返回有关结果的信息。

采用在大多数 UNIX 和 Windows 命令 shell 中指定路径的相同方式，指定相对于当前位置的路径。 在相对路径的标准表示法中，句点 (**.**) 表示当前文件夹，而双句点 (**..**) 表示当前位置的父目录。

例如，如果你位于 **C:\\Windows** 文件夹中，则句点 (**.**) 表示 **C:\\Windows**，而双句点 (**..**) 表示 **C:**。 你可以从当前位置更改到 C: 驱动器的根目录，方法是键入：

<pre>PS> Set-Location -Path .. -PassThru Path ---- C:\</pre>

相同的技术适用于非文件系统驱动器（例如 **HKLM:**）的 Windows PowerShell 驱动器。 可以在注册表中将你的位置设置为 HKLM\\Software 项，方法是键入：

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

然后，可以通过使用相对路径将目录位置更改为父目录，它是 Windows PowerShell HKLM: 驱动器的根目录：

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

可以键入 Set\-Location，或使用任何用于 Set\-Location（cd、chdir、sl）的内置 Windows PowerShell 别名。 例如：

```
cd -Path C:\Windows
```

```
chdir -Path .. -PassThru
```

```
sl -Path HKLM:\SOFTWARE -PassThru
```

### 保存和重新调用最近的位置（Push\-Location 和 Pop\-Location）
当更改位置时，它有助于跟踪你访问过的位置并使你能够返回到之前的位置。 Windows PowerShell 中的 **Push\-Location** cmdlet 将创建一个你访问过的目录路径的有序历史记录（“堆栈”），你可以通过使用补充的 **Pop\-Location** cmdlet 在目录路径历史记录上返回到之前位置。

例如，Windows PowerShell 通常在用户的主目录中启动。

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> 字词 *stack* 在许多编程设置（包括 .NET Framework）中具有特殊含义。 例如项的物理堆栈，你放置在堆栈上的最后一项是可以从堆栈中提取的第一个项。 将项添加到堆栈俗称为将项“推送”到堆栈上。 从堆栈中提取项俗称为将项从堆栈中“弹出”。

若要将当前位置推送到堆栈上，然后将其移动到“本地设置”文件夹，请键入：

```
PS> Push-Location -Path "Local Settings"
```

然后，你可以将“本地设置”位置推送到堆栈上，并将其移动到临时文件夹，方法是通过键入：

```
PS> Push-Location -Path Temp
```

可以验证是否通过输入 **Get\-Location** 命令更改了目录：

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

然后，可以通过输入 **Pop\-Location** 命令弹回到最近访问的目录中，并且通过输入 **Get\-Location** 命令验证该更改：

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

像使用 **Set\-Location** cmdlet 一样，当你输入 **Pop\-Location** cmdlet 来显示输入的目录时，可以包含 **\-PassThru** 参数：

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

还可以将 Location cmdlet 与网络路径结合使用。 如果你有一个名为 FS01 并且共享名为 Public 的服务器，你可以通过键入以下内容更改你的位置

```
Set-Location \\FS01\Public
```

或

```
Push-Location \\FS01\Public
```

可以使用 **Push\-Location** 和 **Set\-Location** 命令将位置更改为任何可用的驱动器。 例如，如果你有驱动号为 D 且包含数据 CD 的本地 CD\-ROM 驱动器，可以通过输入 **Set\-Location D:** 命令将该位置更改为 CD 驱动器。

如果驱动器是空的，你将获得以下错误消息：

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

使用命令行接口时，使用文件资源管理器检查可用的物理驱动器会很不方便。 此外，文件资源管理器不会向你显示所有 Windows PowerShell 驱动器。 Windows PowerShell 提供一组命令，用于对 Windows PowerShell 驱动器进行操作，我们将在下一步讨论这些命令。




<!--HONumber=Jul16_HO1-->


