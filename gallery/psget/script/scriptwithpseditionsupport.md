---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: scriptwithpseditionsupport
ms.technology: powershell
ms.openlocfilehash: aac38b9a5b133b0b7982e7748e1483a0774599a2
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="script-with-compatible-powershell-editions"></a>具有兼容的 PowerShell 版本的脚本
从版本 5.1 开始，PowerShell 以表现出不同功能集和平台兼容性的不同版本提供。

- **桌面版：**以 .NET Framework 为基础构建，提供与面向在完整功能 Windows 版本（如服务器核心和 Windows 桌面）上运行的 PowerShell 版本的脚本和模块的兼容性。
- **核心版：**以 .NET Core 为基础构建，提供与面向在缩减功能 Windows 版本（如 Nano Server 和 Windows IoT）上运行的 PowerShell 版本的脚本和模块的兼容性。

正在运行的 PowerShell 版本显示在 $PSVersionTable.的 PSEdition 属性中。
```powershell
$PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.14300.1000
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
CLRVersion                     4.0.30319.42000
BuildVersion                   10.0.14300.1000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

脚本编写者可以防止执行脚本，除非它使用 #requires 语句的 PSEdition 参数在 PowerShell 的兼容版本上运行。
```powershell
Set-Content C:\script.ps1 -Value "#requires -PSEdition Core
Get-Process -Name PowerShell"
Get-Content C:\script.ps1
#requires -PSEdition Core
Get-Process -Name PowerShell

C:\script.ps1
C:\script.ps1 : The script 'script.ps1' cannot be run because it contained a "#requires" statement for PowerShell Core edition. The edition of PowerShell that is required by the script does not match the currently running PowerShell Desktop edition.
At line:1 char:1
+ C:\script.ps1
+ ~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (script.ps1:String) [], RuntimeException
    + FullyQualifiedErrorId : ScriptRequiresUnmatchedPSEdition
```

PowerShell 库用户可以查找特定 PowerShell 版本上受支持的脚本的列表。
不带 PSEdition_Desktop 和 PSEditon_Core 的脚本可以在 PowerShell Desktop 版本上运行。

```powershell

# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEditon_Desktop

# Find scripts supported on PowerShell Core editions
Find-Script -Tag PSEditon_Core

```

## <a name="more-details"></a>详细信息
### <a name="modules-with-pseditionsmodulemodulewithpseditionsupportmd"></a>[PSEditions 模块](../module/modulewithpseditionsupport.md)
### <a name="pseditions-support-on-powershellgallerypsgallerypsgallerypseditionsmd"></a>[PowerShell 库的 PSEditions 支持](../../psgallery/psgallery_pseditions.md)

