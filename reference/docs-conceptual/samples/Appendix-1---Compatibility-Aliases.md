---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 附录 1 - 兼容性别名
ms.openlocfilehash: 553b9f01d6b5e3f4e04f1a75c25979b54dc205da
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030333"
---
# <a name="appendix-1---compatibility-aliases"></a>附录 1 - 兼容性别名

Windows PowerShell 具有几个转换别名，它们让 UNIX 和 Cmd 用户能够在 Windows PowerShell 中使用熟悉的命令名称的。 下表中显示的是最常见的别名，别名后带有 Windows PowerShell 命令和标准 Windows PowerShell 别名（如果存在）。

你可以通过使用 Get-Alias cmdlet 从 Windows PowerShell 内部找到任何别名指向的 Windows PowerShell 命令。 例如，键入 **get-alias cls**。

```
CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

|CMD 命令|UNIX 命令|PS 命令|PS 别名|
|---------------|----------------|--------------|------------|
|**dir**|**ls**|**Get-ChildItem**|**gci**|
|**cls**|**clear**|**Clear-Host**（函数）|**cls**|
|**del, erase, rmdir**|**rm**|**Remove-Item**|**ri**|
|**copy**|**cp**|**Copy-Item**|**ci**|
|**move**|**mv**|**Move-Item**|**mi**|
|**rename**|**mv**|**Rename-Item**|**rni**|
|**type**|**cat**|**Get-Content**|**gc**|
|**cd**|**cd**|**Set-Location**|**sl**|
|**md**|**mkdir**|**New-Item**|**ni**|
|**pushd**|**pushd**|**Push-Location**|**pushd**|
|**popd**|**popd**|**Pop-Location**|**popd**|
