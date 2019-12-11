---
ms.date: 09/09/2019
keywords: powershell,cmdlet
title: 附录 1 - 兼容性别名
ms.openlocfilehash: 2351fdf23711fe1417f7e3fc3cca5b642d5a59fc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "70848163"
---
# <a name="appendix-1---compatibility-aliases"></a>附录 1 - 兼容性别名

PowerShell 具有多个别名，使 UNIX  和 cmd.exe  用户可以使用熟悉的命令。
下表显示了这些命令及其相关的 PowerShell cmdlet 和 PowerShell 别名：

|cmd.exe命令|UNIX 命令|PowerShell Cmdlet|PowerShell 别名|
|---------------|----------------|--------------|------------|
|**cls**|**clear**|`Clear-Host`（函数）|`cls`|
|**copy**|**cp**|`Copy-Item`|`cpi`|
|**dir**|**ls**|`Get-ChildItem`|`gci`|
|**type**|**cat**|`Get-Content`|`gc`|
|**move**|**mv**|`Move-Item`|`mi`|
|**md**|**mkdir**|`New-Item`|`ni`|
|**pushd**|**pushd**|`Push-Location`|`pushd`|
|**popd**|**popd**|`Pop-Location`|`popd`|
|**del**、**erase**、**rd**、**rmdir**|**rm**|`Remove-Item`|`ri`|
|**ren**|**mv**|`Rename-Item`|`rni`|
|**cd**、**chdir**|**cd**|`Set-Location`|`sl`|

若要查找 PowerShell 别名，请使用 [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet。 若要显示 cmdlet 的别名，请使用 Definition  参数并指定 cmdlet 名称。
或者，要查找别名的 cmdlet 名称，请使用 name  参数并指定别名。

```powershell
Get-Alias -Definition Get-ChildItem
```

```Output
CommandType     Name
-----------     ----
Alias           dir -> Get-ChildItem
Alias           gci -> Get-ChildItem
Alias           ls -> Get-ChildItem
```

```powershell
Get-Alias -Name gci
```

```Output
CommandType     Name
-----------     ----
Alias           gci -> Get-ChildItem
```
