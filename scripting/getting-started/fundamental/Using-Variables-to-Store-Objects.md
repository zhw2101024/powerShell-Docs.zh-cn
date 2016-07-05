---
title: "使用变量存储对象"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: c3bcf9dc6f70383e971d9c1ae75ec78860111de9

---

# 使用变量存储对象
Windows PowerShell 处理对象。 Windows PowerShell 允许你创建实质上是命名对象的变量以保留输出以供以后使用。 如果你习惯在其他 Shell 中处理变量，请记住，Windows PowerShell 变量是对象，而非文本。

始终使用初始字符 $ 指定变量，并且可以在其名称中包含任何字母数字字符或下划线。

### 创建变量
可以通过键入有效的变量名称来创建变量：

```
PS> $loc
PS>
```

这将不返回任何结果，因为 **$loc** 不具有值。 你可以在同一步骤中创建变量并为其赋值。 Windows PowerShell 仅当变量不存在时才创建变量；否则，它会将指定的值赋给现有变量。 若要将你的当前位置存储在变量 **$loc**中，请键入：

```
$loc = Get-Location
```

当你键入此命令时，不会显示任何输出，因为已将输出发送给 $loc。 在 Windows PowerShell 中，未定向的数据将始终发送到屏幕，所显示的输出正是这一事实的副作用。 键入 $loc 将显示你的当前位置：

```
PS> $loc

Path
----
C:\temp
```

你可以使用 **Get\-Member** 以显示有关变量内容的信息。 通过管道将 $loc 传递至 Get\-Member 会向你显示这是一个 **PathInfo** 对象，就像 Get\-Location 的输出一样：

```
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

### 操作变量
Windows PowerShell 提供多个用以操作变量的命令。 你可以通过键入以下内容看到可读形式的完整列表：

```
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

除了你在当前的 Windows PowerShell 会话中创建的变量，还存在多个系统定义的变量。 你可以使用 **Remove\-Variable** cmdlet 来清除所有不受 Windows PowerShell 控制的变量。 键入以下命令来清除所有变量：

```
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

这将生成你在下方看到的确认提示。

```
Confirm
Are you sure you want to perform this action?
Performing operation "Remove Variable" on Target "Name: Error".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):A
```

然后，如果你运行 **Get\-Variable** cmdlet，你会看到其余的 Windows PowerShell 变量。 由于还存在一个变量 Windows PowerShell 驱动器，你也可以通过键入以下内容显示所有的 Windows PowerShell 变量：

```
Get-ChildItem variable:
```

### 使用 Cmd.exe 变量
虽然 Windows PowerShell 不是 Cmd.exe，但它在命令 Shell 环境中运行，并且可以在 Windows 的任何环境中使用相同的可用变量。 这些变量通过名为 **env** 的驱动器进行公开： 你可以通过键入以下内容查看这些变量：

```
Get-ChildItem env:
```

虽然标准变量 cmdlet 并不用于处理 **env:** 变量，但你仍可以通过指定 **env:** 前缀来使用它们。 例如，若要查看操作系统根目录，你可以通过键入以下内容从 Windows PowerShell 内部使用命令shell **%SystemRoot%** 变量：

```
PS> $env:SystemRoot
C:\WINDOWS
```

你还可以从 Windows PowerShell 内部创建和修改环境变量。 从 Windows PowerShell 访问的环境变量遵循针对 Windows 中其他环境变量的一般规则。




<!--HONumber=Jun16_HO4-->


