---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: "psget_save 脚本"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: ceb3ee918e594d23b3ba2e097d197dd0ff6a0971

---

# Save-Script

Save-Script cmdlet 可通过将其保存到特定位置来查看脚本文件。

## 说明

Save-Script cmdlet 将保存指定脚本。

## Cmdlet 语法

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## Cmdlet 联机帮助参考

[Save-Script](http://go.microsoft.com/fwlink/?LinkId=619786)

## 示例命令

### 示例 1：保存存储库中的脚本
此命令将 GalleryINT 存储库中 Fabrikam-ClientScript 脚本的最新版本保存到本地文件夹 C:\ScriptSharingDemo

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### 示例 2：通过从 Find-Script cmdlet 管道传递保存脚本的版本

第一个命令会从存储库 GalleryINT 中找到 Fabrikam-ClientScript 版本 1.5，并将其保存到文件夹 C:\ScriptSharingDemo

第二个命令验证保存的脚本元数据。

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```




<!--HONumber=Oct16_HO2-->


