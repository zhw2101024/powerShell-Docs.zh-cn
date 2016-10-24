---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: psget_unregister psrepository
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: 7d9c24ebb20756a2f7852692532ac6ec7e558ca9

---

# Unregister-PSRepository

取消注册存储库。

## 说明

Unregister-PSRepository cmdlet 为当前用户注销存储库。
- 允许为企业和断开连接的方案注销和重新注册 PSGallery 存储库。
- 用户可重新注册 PSGallery，只需运行 `Register-PSRepository -Default`
- 由于 PSGallery 是 Publish-Module 和 Publish-Script cmdlet 中的默认发布存储库，如果 PSGallery 在已注册的存储库列表中不可用，将会引发错误。

## Cmdlet 语法

```powershell
Get-Command -Name Unregister-PSRepository -Module PowerShellGet -Syntax
```
## Cmdlet 联机帮助参考

[Unregister-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517130)

## 示例命令

```powershell
Unregister-PSRepository -Name "MyPrivateGallery"

Get-PSRepository exp | Unregister-PSRepository
```

### 允许为企业和断开连接的方案注销和重新注册 PSGallery 存储库。
```powershell

# Unregister PSGallery repository
Unregister-PSRepository PSGallery

# Publish-Module throws an error when PSGallery is not a registered repository
Publish-Module -Name MyModule
publish-module : Unable to find repository 'PSGallery'. Use Get-PSRepository to see all available repositories. Try again after specifying a valid repository name. You can use 'Register-PSRepository -Default' to register the PSGallery repository.
At line:1 char:1
+ publish-module -name mymodule
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (PSGallery:String) [Publish-Module], ArgumentException
    + FullyQualifiedErrorId : PSGalleryNotFound,Publish-Module

# Re-register PSGallery repository
Register-PSRepository -Default
```




<!--HONumber=Oct16_HO2-->


