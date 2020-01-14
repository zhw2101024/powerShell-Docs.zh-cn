---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 使用注册表项
ms.openlocfilehash: 3feaf6d26db51a507434a6cec1f1095c9013efc8
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736839"
---
# <a name="working-with-registry-keys"></a>使用注册表项

由于注册表项是 PowerShell 驱动器上的项，因此使用它们的方法和使用文件及文件夹的方法非常相似。 一个关键区别在于，基于注册表的 PowerShell 驱动器上的每个项都是一个容器，就像文件系统驱动器上有一个文件夹一样。 但是，注册表条目及其关联的值只是项的属性，而不是不同的项。

## <a name="listing-all-subkeys-of-a-registry-key"></a>列出注册表项的所有子项

可以通过使用 `Get-ChildItem` 直接显示某个注册表项中的所有项目。 添加可选的 **Force** 参数以显示隐藏项或系统项。 例如，以下命令将直接显示 PowerShell 驱动器 `HKCU:`（对应于 `HKEY_CURRENT_USER` 注册表 Hive）中的项：

```powershell
Get-ChildItem -Path HKCU:\ | Select-Object Name
```

```Output
   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

Name
----
HKEY_CURRENT_USER\AppEvents
HKEY_CURRENT_USER\Console
HKEY_CURRENT_USER\Control Panel
HKEY_CURRENT_USER\DirectShow
HKEY_CURRENT_USER\dummy
HKEY_CURRENT_USER\Environment
HKEY_CURRENT_USER\EUDC
HKEY_CURRENT_USER\Keyboard Layout
HKEY_CURRENT_USER\MediaFoundation
HKEY_CURRENT_USER\Microsoft
HKEY_CURRENT_USER\Network
HKEY_CURRENT_USER\Printers
HKEY_CURRENT_USER\Software
HKEY_CURRENT_USER\System
HKEY_CURRENT_USER\Uninstall
HKEY_CURRENT_USER\WXP
HKEY_CURRENT_USER\Volatile Environment
```

这些是注册表编辑器 (Regedit.exe) 中 `HKEY_CURRENT_USER` 下可见的顶级项。

还可以通过指定注册表提供程序的名称（后跟“`::`”）来指定此注册表路径。 注册表提供程序的全名是 `Microsoft.PowerShell.Core\Registry`，但是可以将其缩短为仅 `Registry`。 任一以下命令都可直接列出 `HKCU:` 下面的内容。

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

这些命令将仅列出直接包含的项，类似于使用 Cmd.exe 中的 `DIR`  或 UNIX shell 中的 `ls`。 为了显示包含的项，需要指定 **Recurse** 参数。 若要列出 `HKCU:` 中的所有注册表项，请使用以下命令。

```powershell
Get-ChildItem -Path HKCU:\ -Recurse
```

`Get-ChildItem` 可以通过其 Path  、Filter  、Include  和 Exclude  参数执行复杂的筛选功能，但这些参数通常只基于名称。 还可以通过使用 `Where-Object` cmdlet 基于项的其他属性执行复杂的筛选。 下面的命令用于查找 `HKCU:\Software` 中不止只有一个子项并且刚好具有 4 个值的所有项：

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse |
  Where-Object {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

## <a name="copying-keys"></a>复制项

复制通过 `Copy-Item` 完成。 下面的示例将 `HKLM:\SOFTWARE\Microsoft\Windows\` 的 `CurrentVersion` 子项及其所有属性复制到 `HKCU:\`。

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU:
```

如果你在注册表编辑器中或通过使用 `Get-ChildItem` 检查此新项，你会注意到在新位置中没有所包含子项的副本。 为了复制容器的所有内容，需要指定 **Recurse** 参数。 若要使上述的复制命令递归，你将使用此命令：

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU: -Recurse
```

你仍然可以使用已有的其他可用工具执行文件系统复制。 任何注册表编辑工具（包括 reg.exe  、regini.exe  和 regedit.exe  ）以及支持注册表编辑的 COM 对象（如 WScript.Shell  和 WMI 的 StdRegProv  类）均可用于 Windows PowerShell。

## <a name="creating-keys"></a>创建项

在注册表中创建新项比在文件系统中创建新项简单。 由于所有注册表项都是容器，因此，你无需指定项类型；只需提供一个明确的路径即可，如：

```powershell
New-Item -Path HKCU:\Software_DeleteMe
```

此外还可以使用基于提供程序的路径来指定某项：

```powershell
New-Item -Path Registry::HKCU\Software_DeleteMe
```

## <a name="deleting-keys"></a>删除项

从本质而言，删除项对所有提供程序都是相同的。 以下命令将以无提示方式删除项：

```powershell
Remove-Item -Path HKCU:\Software_DeleteMe
Remove-Item -Path 'HKCU:\key with spaces in the name'
```

## <a name="removing-all-keys-under-a-specific-key"></a>删除特定项下的所有项

可以通过使用 `Remove-Item` 删除包含的项，但如果项包含任何其他内容，系统将提示你确认该删除。 例如，如果我们尝试删除我们创建的 `HKCU:\CurrentVersion` 子项，我们将看到：

```powershell
Remove-Item -Path HKCU:\CurrentVersion
```

```Output
Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

若要在无提示下删除包含的项，请指定 Recurse  参数：

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

如果要删除 `HKCU:\CurrentVersion` 中的所有项，但不删除 `HKCU:\CurrentVersion` 本身，则可以改用：

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```
