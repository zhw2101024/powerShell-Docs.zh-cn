---
title: "附录 1：兼容性别名"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
ms.openlocfilehash: fc715f9ba2a1dc61d2549d5370371fe2b29fa063
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
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

