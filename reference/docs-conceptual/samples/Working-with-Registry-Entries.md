---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 使用注册表条目
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: 8483b6f98739697b24a13055dfffbc7b5bacc2cc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "55677154"
---
# <a name="working-with-registry-entries"></a>使用注册表条目

因为注册表条目是项的属性而无法直接浏览，因此我们在使用它们时需要采取略有不同的方式。

### <a name="listing-registry-entries"></a>列出注册表条目

可采用许多不同的方法检查注册表条目。 最简单的方法是获取与某个项相关联的属性名称。 例如，若要查看注册表项中的条目的名称`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`，使用`Get-Item`。 注册表项具有一个通用名称为“Property”的属性，它是项中的注册表条目的列表。
以下命令选择 Property 属性并扩展这些项，以便它们可在列表中显示：

```powershell
Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion |
  Select-Object -ExpandProperty Property
```

```Output
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

若要在可读性更强的窗体中查看注册表条目，请使用`Get-ItemProperty`:

```powershell
Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

```Output
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

你可以将“`*.*`.”表示法用于引用当前位置。 可以使用`Set-Location`更改为**CurrentVersion**注册表容器第一个：

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

或者，可以使用内置 HKLM PSDrive 与`Set-Location`:

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

然后，你可以将“`*.*`.”表示法用于当前位置以列出属性，而无需指定完整路径：

```powershell
Get-ItemProperty -Path .
```

```Output
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

路径扩展的工作方式相同方式与其在文件系统中，因此您可以从以下位置获得**ItemProperty**列出了`HKLM:\SOFTWARE\Microsoft\Windows\Help`使用`Get-ItemProperty -Path ..\Help`。

### <a name="getting-a-single-registry-entry"></a>获取单个注册表条目

如果你希望在注册表项中检索特定条目，可以使用几种可能的方法之一。 本示例查找的值**DevicePath**中`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`。

使用`Get-ItemProperty`，使用**路径**参数指定的密钥名称和**名称**参数指定的名称**DevicePath**条目。

```powershell
Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath
```

```Output
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
> 尽管`Get-ItemProperty`已**筛选器**， **Include**，和**排除**参数，它们不能用于按属性名称进行筛选。 这些参数引用注册表项，即项路径和不注册表项。 注册表条目是项属性。

另一种方法是使用 Reg.exe 命令行工具。 有关 reg.exe 的帮助，请键入`reg.exe /?`在命令提示符。 若要查找 DevicePath 条目，请使用 reg.exe，如以下命令中所示：

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

还可以使用 **WshShell COM** 对象查找某些注册表条目，尽管此方法对大型二进制数据或包含诸如“\\”字符的注册表条目名称不起作用也是如此。 将属性名称附加到带有 \\ 分隔符的项路径：

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

### <a name="setting-a-single-registry-entry"></a>设置一个注册表项

如果你想要更改注册表项中的特定项，可以使用几个可能的方法之一。 此示例修改**路径**下的项`HKEY_CURRENT_USER\Environment`。 **路径**项指定在哪里可以找到可执行文件。

1. 检索的当前值**路径**条目使用`Get-ItemProperty`。
2. 添加新值，将其与分离`;`。
3. 使用`Set-ItemProperty`与指定的键、 条目名称和要修改的注册表项值。

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> 尽管`Set-ItemProperty`已**筛选器**， **Include**，和**排除**参数，它们不能用于按属性名称进行筛选。 这些参数引用注册表项（即项路径），而不引用注册表条目（即项属性）。

另一种方法是使用 Reg.exe 命令行工具。 有关 reg.exe 的帮助，请键入 **reg.exe /?**
。

下面的示例更改**路径**条目通过删除在上面的示例添加的路径。
`Get-ItemProperty` 仍可用于检索要避免必须分析从返回的字符串的当前值`reg query`。 **SubString**并**LastIndexOf**方法用于检索最后一个路径添加到**路径**条目。

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

### <a name="creating-new-registry-entries"></a>创建新注册表条目

若要将一个名为"PowerShellPath"的新项添加到**CurrentVersion**密钥、 使用`New-ItemProperty`替换为密钥、 条目名称和条目的值的路径。 对于此示例中，我们将采用 Windows PowerShell 变量的值`$PSHome`，其中可存储 Windows PowerShell 安装目录的路径。

你可以通过使用以下命令来将新条目添加到项，该命令还会返回有关新条目的信息：

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

```Output
PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows
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

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

此外可以替代预先存在的注册表条目值，通过添加**Force**参数到任何`New-ItemProperty`命令。

### <a name="renaming-registry-entries"></a>重命名注册表条目

若要重命名**PowerShellPath**条目为"PSHome"，使用`Rename-ItemProperty`:

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

若要显示重命名的值，请将 **PassThru** 参数添加到该命令。

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a>删除注册表条目

若要删除 PSHome 和 PowerShellPath 注册表条目，请使用`Remove-ItemProperty`:

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
