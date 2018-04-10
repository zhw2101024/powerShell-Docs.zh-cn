---
ms.date: 10/17/2017
contributor: keithb
ms.topic: reference
keywords: 库,powershell,cmdlet,psget
title: Save-Script
ms.openlocfilehash: 67697fc0e70fb31cad9ad5ae7ce01debef160b81
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="save-script"></a>Save-Script

Save-Script cmdlet 可通过将其保存到特定位置来查看脚本文件。

## <a name="description"></a>说明

Save-Script cmdlet 将保存指定脚本。

## <a name="cmdlet-syntax"></a>Cmdlet 语法

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a>Cmdlet 联机帮助参考

[Save-Script](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a>示例命令

### <a name="example-1-save-a-script-from-a-repository"></a>示例 1：保存存储库中的脚本
此命令将 GalleryINT 存储库中 Fabrikam-ClientScript 脚本的最新版本保存到本地文件夹 C:\ScriptSharingDemo

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a>示例 2：通过从 Find-Script cmdlet 管道传递保存脚本的版本

第一个命令会从存储库 GalleryINT 中找到 Fabrikam-ClientScript 版本 1.5，并将其保存到文件夹 C:\ScriptSharingDemo

第二个命令验证保存的脚本元数据。

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

### <a name="example-3-save-a-prerelease-version-of-a-script-from-a-repository"></a>示例 3：保存存储库中的预发行版脚本
此命令将 GalleryINT 存储库中 Fabrikam-ClientScript 脚本的最新版本保存到本地文件夹 C:\ScriptSharingDemo

```powershell
Save-Script -Name Fabrikam-ClientScript -Path C:\ScriptSharingDemo -AllowPrerelease
```