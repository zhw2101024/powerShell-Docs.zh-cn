---
title: "使用注册表条目"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: d7fb731bc2527e324271bc75f00112a67a1147e3

---

# 使用注册表条目
因为注册表条目是项的属性而无法直接浏览，因此我们在使用它们时需要采取略有不同的方式。

### 列出注册表条目
可采用许多不同的方法检查注册表条目。 最简单的方法是获取与某个项相关联的属性名称。 例如，若要查看注册表项 **HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion** 中的条目的名称，请使用 **Get\-Item**。 注册表项具有一个通用名称为“Property”的属性，它是项中的注册表条目的列表。 以下命令选择 Property 属性并扩展这些项，以便它们可在列表中显示：

```
PS> Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion | Select-Object -ExpandProperty Property
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

若要在可读性更强的窗体中查看注册表条目，请使用 **Get\-ItemProperty**：

```
PS> Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion

PSPath              : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows\CurrentVersion
PSParentPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows
PSChildName         : CurrentVersion
PSDrive             : HKLM
PSProvider          : Microsoft.PowerShell.Core\Registry
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
CommonFilesDir      : C:\Program Files\Common Files
ProductId           : 76487-338-1167776-22465
WallPaperDir        : C:\WINDOWS\Web\Wallpaper
MediaPath           : C:\WINDOWS\Media
ProgramFilesPath    : C:\Program Files
PF_AccessoriesName  : Accessories
(default)           :
```

该项的 Windows PowerShell 相关的属性全都带有“PS”前缀，例如 **PSPath**、**PSParentPath**、**PSChildName** 和 **PSProvider**。

你可以将“**.**”表示法用于引用当前位置。 你可以先使用 **Set\-Location** 更改为 **CurrentVersion** 注册表容器：

```
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

另外，你可以将内置 HKLM PSDrive 与 **Set\-Location** 结合使用：

```
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

然后，你可以将“**.**”表示法用于当前位置以列出属性，而无需指定完整路径：

```
PS> Get-ItemProperty -Path .
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

路径扩展的工作方式与其在文件系统中的工作方式相同，因此在此位置中，你可以通过使用 **Get\-ItemProperty \-Path ..\\Help** 来获取 **HKLM:\\SOFTWARE\\Microsoft\\Windows\\Help** 的 **ItemProperty** 列表。

### 获取单个注册表条目
如果你希望在注册表项中检索特定条目，可以使用几种可能的方法之一。 此示例在 **HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion** 中查找 **DevicePath** 的值。

通过使用 **Get\-ItemProperty**，可使用 **Path** 参数指定项的名称，使用 **Name** 参数指定 **DevicePath** 条目的名称。

```
PS> Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath

PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

此命令返回标准 Windows PowerShell 属性以及 **DevicePath** 属性。

> [!NOTE]
> 尽管 **Get\-ItemProperty** 具有 **Filter**、**Include** 和 **Exclude** 参数，但它们无法用于按属性名称进行筛选。 这些参数引用注册表项（即项路径），而不引用注册表条目（即项属性）。

另一种方法是使用 Reg.exe 命令行工具。 有关 reg.exe 的帮助，请在命令提示符下键入 **reg.exe \/?** 。 若要查找 DevicePath 条目，请使用 reg.exe，如以下命令中所示：

```
PS> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath

! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

还可以使用 **WshShell COM** 对象查找某些注册表条目，尽管此方法对大型二进制数据或包含诸如“\\”字符的注册表条目名称不起作用也是如此。 将属性名称附加到带有 \\ 分隔符的项路径：

```
PS> (New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
%SystemRoot%\inf
```

### 创建新注册表条目
若要将名为“PowerShellPath”的新条目添加到 **CurrentVersion** 项，请将 **New\-ItemProperty** 与该项的路径、条目名称和条目的值一起使用。 对于此示例，我们将采用 Windows PowerShell 变量 **$PSHome** 的值，该变量可存储 Windows PowerShell 的安装目录的路径。

你可以通过使用以下命令来将新条目添加到项，该命令还会返回有关新条目的信息：

```
PS> New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome

PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

**PropertyType** 必须是以下表格中的 **Microsoft.Win32.RegistryValueKind** 枚举成员的名称：

|PropertyType 值|含义|
|----------------------|-----------|
|Binary|二进制数据|
|DWord|一个数字，类型为有效的 UInt32|
|ExpandString|一个字符串，可包含动态扩展的环境变量|
|MultiString|一个多行字符串|
|字符串|任意字符串值|
|QWord|8 字节的二进制数据|

> [!NOTE]
> 你可以通过为 **Path** 参数指定一组值来将注册表条目添加到多个位置：

```
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

你还可以替代预先存在的注册表条目值，方法是将 **Force** 参数添加到任何 **New\-ItemProperty** 命令。

### 重命名注册表条目
若要将 **PowerShellPath** 条目重命名为“PSHome”，请使用 **Rename\-ItemProperty**：

```
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

若要显示重命名的值，请将 **PassThru** 参数添加到该命令。

```
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### 删除注册表条目
若要删除 PSHome 和 PowerShellPath 注册表条目，请使用 **Remove\-ItemProperty**：

```
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```




<!--HONumber=Jun16_HO4-->


