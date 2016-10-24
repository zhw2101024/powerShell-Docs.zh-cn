---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: psget_get installedscript
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: f809c5c8f5a28c01c67ee4c4453ecca7796838c4

---

# Get-InstalledScript

获取计算机上的已安装脚本。

## 说明

Get-InstalledScript cmdlet 获取计算机上的已安装 PowerShell 脚本。

对于每个已安装脚本，Get-InstalledScript 将返回 PSRepositoryItemInfo 对象，可根据需要将其通过管道传递到 Uninstall-Script 以卸载已安装的脚本。

- Get-InstalledScript 可根据名称、版本参数筛选已安装的脚本。
- Get-InstalledScript 可使用版本参数进行筛选：MinimumVersion、MaximumVersion、RequiredVersion、AllVersions。
  - 这些参数彼此排斥，但 MinmimumVersion 和 MaximumVersion 除外。
  - 这些版本参数只允许具有单个脚本名称，而不能具有任何通配符。
  - 如果未指定 RequiredVersion 参数，Get-InstalledScript 将返回等于或高于指定最低版本的已安装脚本的最新版本，若未指定最低版本，则返回脚本的最新版本。 
  - 如果指定了 RequiredVersion 参数，Get-InstalledScript 仅返回与指定版本完全匹配的已安装脚本版本。

## Cmdlet 语法

```powershell
Get-Command -Name Get-InstalledScript -Module PowerShellGet -Syntax
```

## Cmdlet 联机帮助参考

[Get-InstalledScript](http://go.microsoft.com/fwlink/?LinkId=619790)

## 示例命令

```powershell

# Get all scripts installed using PowerShellGet cmdlets
Get-InstalledScript

# Get a specific installed script
Get-InstalledScript Show-Tree

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.0      Show-Tree                           PSGallery            Script to show the layout of PowerShell namespaces (Tr...

# Get installed script with wildcards
Get-InstalledScript -Name *Azure*

# Get all versions of an installed script
Get-InstalledScript -Name Connect-O365 -AllVersions

# Get installed script with MinimumVersion
Get-InstalledScript -Name Connect-O365 -MinimumVersion 1.1

# Get installed script with MaximumVersion
Get-InstalledScript -Name Connect-O365 -MaximumVersion 1.6.3

# Get installed script with version range
Get-InstalledScript -Name Connect-O365 -MinimumVersion 1.1 -MaximumVersion 1.6.3

# Get installed script with RequiredVersion
Get-InstalledScript -Name Connect-O365 -RequiredVersion 1.4

# Properties of Get-InstalledScript returned object
Get-InstalledScript Show-Tree | Format-List * -Force

Name                       : Show-Tree
Version                    : 1.0.0
Type                       : Script
Description                : Script to show the layout of PowerShell namespaces (Trees) using ASCII
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 10:15:35 PM
InstalledDate              : 5/4/2016 11:44:13 PM
UpdatedDate                :
LicenseUri                 :
ProjectUri                 :
IconUri                    :
Tags                       : {Nano, PSScript}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               :
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {description, installeddate, tags, PackageManagementProvider...}
InstalledLocation          : C:\Program Files\WindowsPowerShell\Scripts


```




<!--HONumber=Oct16_HO2-->


