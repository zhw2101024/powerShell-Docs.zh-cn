---
title:  管理 Windows PowerShell 驱动器
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  bd809e38-8de9-437a-a250-f30a667d11b4
---

# 管理 Windows PowerShell 驱动器
*Windows PowerShell 驱动器*是一个数据存储位置，你可以像访问 Windows PowerShell 中的文件系统驱动器那样访问它。 Windows PowerShell 提供程序将为你创建一些驱动器，例如文件系统驱动器（包括 C: 和 D:）、注册表驱动器（HKCU: 和 HKLM:）和证书驱动器 (Cert:)，你也可以创建自己的 Windows PowerShell 驱动器。 这些驱动器非常有用，但它们仅在 Windows PowerShell 内可用。 你无法通过使用其他 Windows 工具（如文件资源管理器或 Cmd.exe）访问它们。

Windows PowerShell 可针对适用于 Windows PowerShell 驱动器的命令使用名词 **PSDrive**。 有关 Windows PowerShell 会话中的 Windows PowerShell 驱动器列表，请使用 **Get-PSDrive** cmdlet。

```
PS> Get-PSDrive

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
Alias      Alias
C          FileSystem    C:\                                 ...And Settings\me
cert       Certificate   \
D          FileSystem    D:\
Env        Environment
Function   Function
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
Variable   Variable
```

尽管显示内容中的驱动器与你的系统上的驱动器有所不同，但是该列表将看起来类似于 **Get-PSDrive** 命令的输出（如上所示）。

文件系统驱动器是 Windows PowerShell 驱动器的子集。 你可以通过 Provider 列中的 FileSystem 条目标识文件系统驱动器。 （Windows PowerShell 中的文件系统驱动器受 Windows PowerShell FileSystem 提供程序支持。）

若要查看 **Get-PSDrive** cmdlet 的语法，请使用 **Syntax** 参数键入 **Get-Command** 命令：

```
PS> Get-Command -Name Get-PSDrive -Syntax
Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

**PSProvider** 参数允许你仅显示受特定提供程序支持的 Windows PowerShell 驱动器。 例如，若要仅显示受 Windows PowerShell FileSystem 提供程序支持的 Windows PowerShell 驱动器，请使用 **PSProvider** 参数和 **FileSystem** 值键入 **Get-PSDrive** 命令：

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

若要查看表示注册表配置单元的 Windows PowerShell 驱动器，请使用 **PSProvider** 参数来仅显示受 Windows PowerShell Registry 提供程序支持的 Windows PowerShell 驱动器：

<pre>PS> Get-PSDrive -PSProvider Registry Name       Provider      Root                                   CurrentLocation ----       --------      ----                                   --------------- HKCU       Registry      HKEY_CURRENT_USER HKLM       Registry      HKEY_LOCAL_MACHINE</pre>

你还可以将标准 Location cmdlet 与 Windows PowerShell 驱动器结合使用：

<pre>PS> Set-Location HKLM:\SOFTWARE PS> Push-Location .\Microsoft PS> Get-Location Path ---- HKLM:\SOFTWARE\Microsoft</pre>

### 添加新的 Windows PowerShell 驱动器 (New-PSDrive)
你可以通过使用 **New-PSDrive** 命令添加自己的 Windows PowerShell 驱动器。 若要获取 **New-PSDrive** 命令的语法，请使用 **Syntax** 参数输入 **Get-Command** 命令：

```
PS> Get-Command -Name New-PSDrive -Syntax
New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

若要创建一个新的 Windows PowerShell 驱动器，你必须提供三个参数：

-   驱动器的名称（可使用任何有效的 Windows PowerShell 名称）

-   PSProvider（将“FileSystem”用于文件系统位置，将“Registry”用于注册表位置）

-   根，即指向新驱动器的根目录的路径

例如，你可以创建一个名为“Office”的驱动器，它将映射到包含你的计算机上的 Microsoft Office 应用程序的文件夹（例如 **C:\Program Files\Microsoft Office\OFFICE11**）。 若要创建该驱动器，请键入以下命令：

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Micr
osoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE] 一般情况下，路径不区分大小写。

在执行所有 Windows PowerShell 驱动器时，请参考新的 Windows PowerShell 驱动器，格式是其名称后面跟一个冒号 (**:**)。

Windows PowerShell 驱动器可以使许多任务变得更简单。 例如，Windows 注册表中的某些最重要的项的路径长度非常长，难以访问且难以记住这些路径。 关键的配置信息位于 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion** 下。 若要查看和更改 CurrentVersion 注册表项中的项，你可以创建一个其根在该项中的 Windows PowerShell 驱动器，方法是键入：

<pre>PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\W indows\CurrentVersion Name       Provider      Root                                   CurrentLocation ----       --------      ----                                   --------------- cvkey      Registry      HKLM\Software\Microsoft\Windows\...</pre>

然后，你可以像对任何其他驱动器一样，将位置更改为 **cvkey:** 驱动器：

`PS> cd cvkey:`

或者：

<pre>PS> Set-Location cvkey: -PassThru Path ---- cvkey:\</pre>

New-PsDrive cmdlet 仅将新的驱动器添加到当前 Windows PowerShell 会话中。 如果关闭 Windows PowerShell 窗口，则会丢失新的驱动器。 若要保存 Windows PowerShell 驱动器，请使用 Export-Console cmdlet 导出当前 Windows PowerShell 会话，然后使用 PowerShell.exe **PSConsoleFile** 参数来将其导入。 或者，将新的驱动器添加到 Windows PowerShell 配置文件中。

### 删除 Windows PowerShell 驱动器 (Remove-PSDrive)
你可以通过使用 **Remove-PSDrive** cmdlet 从 Windows PowerShell 中删除驱动器。 **Remove-PSDrive** cmdlet 易于使用；若要删除特定 Windows PowerShell 驱动器，只需提供 Windows PowerShell 驱动器名称。

例如，如果已添加 **Office:** Windows PowerShell 驱动器（如 **New-PSDrive** 主题中所示），则可以通过键入以下内容将其删除：

```
PS> Remove-PSDrive -Name Office
```

若要删除 **cvkey:** Windows PowerShell 驱动器（同样，如 **New-PSDrive** 主题中所示），请使用以下命令：

```
PS> Remove-PSDrive -Name cvkey
```

可以轻松删除 Windows PowerShell 驱动器，但是如果你位于该驱动器中，则无法删除它。 例如：

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

### 添加和删除 Windows PowerShell 之外的驱动器
Windows PowerShell 检测在 Windows 中添加或删除的文件系统驱动器，包括映射的网络驱动器、附加的 USB 驱动器，以及通过使用 **net use** 命令或来自 Windows 脚本宿主 (WSH) 脚本的 **WScript.NetworkMapNetworkDrive** 和 **RemoveNetworkDrive** 方法删除的驱动器。



<!--HONumber=May16_HO2-->


