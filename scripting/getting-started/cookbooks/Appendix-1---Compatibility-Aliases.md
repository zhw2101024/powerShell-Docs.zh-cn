---
title: 附录 1 - 兼容性别名
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
---
# 附录 1 - 兼容性别名
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
|**cls**|**clear**|**Clear-Host**（函数）|N/A|
|**del, erase, rmdir**|**rm**|**Remove-Item**|**ri**|
|**copy**|**cp**|**Copy-Item**|**ci**|
|**move**|**mv**|**Move-Item**|**mi**|
|**重命名**|**mv**|**Rename-Item**|**rni**|
|**类型**|**cat**|**Get-Content**|**gc**|
|**cd**|**cd**|**Set-Location**|**sl**|
|**md**|**mkdir**|**New-Item**|**ni**|
|N/A|**pushd**|**Push-Location**|N/A|
|N/A|**popd**|**Pop-Location**|N/A|



<!--HONumber=Apr16_HO1-->


