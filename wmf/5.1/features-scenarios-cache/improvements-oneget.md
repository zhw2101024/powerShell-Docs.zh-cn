---
title: "WMF 5.1（预览版）中的 OneGet 功能改进"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 57049ff138604b0e13c8fd949ae14da05cb03a4b
ms.openlocfilehash: 1d0bd545b52ef56045f2ec740b05c4e0fd93bb67

---

# OneGet 改进
WMF 5.1 包含一些修复和改进，用于解决 WMF 5.0 版本中的一些用户体验缺口。 

##删除了版本别名

**情形**：如果你在系统上安装了包 P1 的版本 1.0 和 2.0，并且要卸载版本 1.0，则会运行“uninstall-package -name P1 -version 1.0”，并且预计在运行该 cmdlet 之后将卸载版本 1.0。 但是结果是卸载了版本 2.0。 
    
出现此问题是因为“-version”参数是“-minimumversion”参数的别名。 当 OneGet 查找具有最低版本 1.0 的合格包时，它会返回最新版本。 在正常情况下需要此行为，因为查找最新版本通常是所需结果。 但是，它不应该应用于 uninstall-package 情况。
    
**解决方案**：在 WMF 5.1 中，在 OneGet 和 PowerShellGet 中完全删除了 -version 别名。 

##多个用于启动 NuGet 提供程序的提示

**情形**：在计算机上首次运行 Find-Module 或 Install-module 或是其他 OneGet cmdlet 时，OneGet 会尝试启动 NuGet 提供程序。 它这样做是因为 PowerShellGet 提供程序还使用 NuGet 提供程序来下载 PowerShell 模块。 OneGet 随后会提示用户输入安装 NuGet 提供程序的权限。 用户选择“yes”进行启动之后，会安装最新版本的 NuGet 提供程序。 
    
但是在某些情况下，当在计算机上安装了旧版本的 NuGet 提供程序时，较旧版本的 NuGet 有时会先加载到 PowerShell 会话中（这是 OneGet 中的争用条件）。 但是 PowerShellGet 需要更新版本的 NuGet 提供程序来正常运行，因此 PowerShellGet 会要求 OneGet 再次启动 NuGet 提供程序。 这会导致出现多个用于启动 NuGet 提供程序的提示。

**解决方案**：在 WMF 5.1 中，OneGet 现在加载最新版本的 NuGet 提供程序，以避免出现多个用于启动 NuGet 提供程序的提示。

还可以通过手动删除旧版本的 NuGet 提供程序（NuGet-Anycpu.exe，如果在 $env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies 中存在）来解决此问题


##在仅具有 intranet 访问的计算机上支持 OneGet

**情形**：在 WMF 5.0 中，OneGet 不支持仅具有 intranet（但没有 internet）访问的计算机。

**解决方案**：在 WMF 5.1 中，可以按照以下步骤允许 intranet 计算机使用 OneGet：

1. 使用 Install-PackageProvider NuGet，通过具有 internet 连接的其他计算机下载 NuGet 提供程序。

2. 在 $env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget 或 $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget 下查找 NuGet 提供程序。 

3. 将二进制文件复制到 intranet 计算机可以访问的文件夹或网络共享位置，然后使用“Install-PackageProvider NuGet -Source <Path to folder>”安装 NuGet 提供程序。


##事件日志记录改进

安装包时，你会更改计算机的状态。 在 WMF 5.1 中，OneGet 现在针对安装、卸载和保存包活动将事件记录到 Windows 事件日志中。 事件通道在操作方面与 PowerShell 相同，即，Microsoft-Windows-PowerShell。

##对基本身份验证的支持

在 WMF 5.1 中，OneGet 支持从需要基本身份验证的存储库查找和安装包。 你可以向 Find-Package 和 Install-Package cmdlet 提供凭据。 例如：

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
##支持在代理后面使用 OneGet

在 WMF 5.1 中，OneGet 现在采用新的代理参数：-ProxyCredential 和 -Proxy。 使用这些参数可以向 OneGet cmdlet 指定代理 URL 和凭据。 默认情况下，会使用系统代理设置。 例如：

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```



<!--HONumber=Jul16_HO3-->


