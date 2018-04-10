---
ms.date: 10/17/2017
contributor: keithb
ms.topic: reference
keywords: 库,powershell,cmdlet,psget
title: PrereleaseScript
ms.openlocfilehash: 575babd6bc373e99a4e924fafef6e9edeec972d4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="prerelease-versions-of-scripts"></a>预发行版脚本

从版本 1.6.0 开始，PowerShellGet 和 PowerShell 库都支持将 1.0.0 以上的版本标记为预发行版。 在此功能之前，预发行项仅限于以 0 开头的版本。 这些功能的目标是为 [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) 版本控制约定提供更好的支持，并且不会破坏 PowerShell 版本 3 及更高版本或 PowerShellGet 现有版本的向后兼容性。
本主题重点介绍特定于脚本的功能。 模块的等效功能在[预发行模块版本](../module/PrereleaseModule.md)主题中介绍。 使用这些功能，发布服务器可以将脚本标识为 2.5.0-alpha 版，随后可发布用于取代预发行版本的 2.5.0 生产就绪版。

在高级别中，预发行版脚本功的能包括：

* 将预发行版字符串后缀添加到脚本清单中的版本字符串。
当脚本发布到 PowerShell 库后，会从清单中提取此数据，用于标识预发行项。
* 获取预发行项要求将 -AllowPrerelease 标志添加到 PowerShellGet 命令 Find-Script、Install-Script、Update-Script 和 Save-Script。
如果未指定标志，则不会显示预发行项。
* Find-Script、Get-InstalledScript 显示的脚本版本，以及在 PowerShell 库中显示的脚本版本在显示时会附加预发行版字符串，如 2.5.0-alpha。

以下介绍了这些功能的详细信息。


## <a name="identifying-a-script-version-as-a-prerelease"></a>将脚本版本标识为预发行版

PowerShellGet 对脚本的预发行版本的支持比模块更容易。
仅 PowerShellGet 支持脚本版本控制，因此添加预发行字符串不会引起兼容性问题。
要将 PowerShell 库中的脚本标识为预发行版，请将预发行后缀添加到脚本元数据中格式正确的版本字符串中。

具有预发行版本的脚本清单的示例部分如下所示：
```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>

```

要使用预发行后缀，版本字符串必须满足以下要求：

* 版本为 3 段式的 Major.Minor.Build 时，只能指定预发行后缀。 这符合 SemVer v1.0.0 的要求
* 预发行后缀是以连字符开头的字符串，并且可能包含 ASCII 字母数字 [0-9A-Za-z-]
* 此时仅支持 SemVer v1.0.0 预发行字符串，因此预发行后缀不得包含句点或 + [.+]，而在 SemVer 2.0 中允许包含
* 支持的预发行版字符串的示例包括：-alpha、-alpha1、-BETA、-update20171020

__预发行版本控制对排序顺序和安装文件夹的影响__

使用预发行版本时，排序顺序会发生更改，这在发布到 PowerShell 库时，以及使用 PowerShellGet 命令安装脚本时非常重要。
如果两个脚本版本都具有该版本号，则排序顺序基于连字符后面的字符串部分。 因此，2.5.0-alpha 版低于 2.5.0-beta 版，而 2.5.0-beta 版低于 2.5.0-gamma 版。
如果两个脚本具有相同的版本号，并且只有一个脚本具有预发行版字符串，则不具有预发行版后缀的脚本会假定为生产就绪版本，在排序时的版本要比预发行版本高。
例如，在比较 2.5.0 和 2.5.0-beta 版本时，2.5.0 版本会视为两者中更高的版本。

在发布到 PowerShell 库时，默认情况下，发布的脚本版本必须高于 PowerShell 库中以前发布的任何版本。
发布服务器可能会使用 2.5.0-beta 或不具有预发行版后缀的 2.5.0 更新版本 2.5.0-alpha。

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a>使用 PowerShellGet 命令查找和获取预发行项

使用 PowerShellGet Find-Script、Install-Script、Update-Script 和 Save-Script 命令处理预发行项需要添加 -AllowPrerelease 标志。
如果已指定 -AllowPrerelease，则会包括预发行项（如存在）。
如果未指定 -AllowPrerelease 标志，则不会显示预发行项。

PowerShellGet 脚本命令中这种情况的唯一例外是 Get-InstalledScript，以及某些情况下的 Uninstall-Script。

* Get-InstalledScript 始终在版本字符串中自动显示预发行信息（如存在）。
* Uninstall-Script 在未指定任何版本时默认卸载最新版本的脚本。 该行为尚未更改。 但是，如果预发行版本是使用 -RequiredVersion 指定的，则需要 -AllowPrerelease。

## <a name="examples"></a>示例
```powershell
# Assume the PowerShell Gallery has TestPackage versions 1.8.0 and 1.9.0-alpha. If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> Find-Script TestPackage

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Find-Script TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# To install a prerelease, you must specify -AllowPrerelease. Specifying a prerelease version string is not sufficient.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha
PackageManagement\Find-Package : No match was found for the specified search criteria and script name 'TestPackage'.
Try Get-PSRepository to see all available registered script repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exceptio
   n
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# Note that Get-InstalledScript shows the prerelease version.
# If -RequiredVersion is not specified, all installed scripts will be displayed by Get-InstalledScript
```

如果未提供 -RequiredVersion，Uninstall-Script 会删除最新版本的脚本。
如果已指定 -RequiredVersion，并且是预发行版，则必须将 -AllowPrerelease 添加到命令中。

``` powershell
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha
Uninstall-Script: The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Unnstall-Script TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Script], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-script


C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
# Since script versions are not installed side-by-side, the above could be simply "Uninstall-Script TestPackage"

C:\windows\system32> Get-Installedscript TestPackage
PackageManagement\Get-Package : No match was found for the specified search criteria and script names 'testpackage'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.5.0.0\PSModule.psm1:4088 char:9
+         PackageManagement\Get-Package @PSBoundParameters | Microsoft. ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...lets.GetPackage:GetPackage) [Get-Package], Exception
    + FullyQualifiedErrorId : NoMatchFound,Microsoft.PowerShell.PackageManagement.Cmdlets.GetPackage


```



## <a name="more-details"></a>详细信息
### <a name="prerelease-module-versionsmoduleprereleasemodulemd"></a>[预发行模块版本](../module/PrereleaseModule.md)
### <a name="find-scriptpsgetfind-scriptmd"></a>[Find-script](./psget_find-script.md)
### <a name="install-scriptpsgetinstall-scriptmd"></a>[Install-script](./psget_install-script.md)
### <a name="save-scriptpsgetsave-scriptmd"></a>[Save-script](./psget_save-script.md)
### <a name="update-scriptpsgetupdate-scriptmd"></a>[Update-script](./psget_update-script.md)
### <a name="get-installedscriptpsgetget-installedscriptmd"></a>[Get-Installedscript](./psget_get-installedscript.md)
### <a name="uninstall-scriptpsgetuninstall-scriptmd"></a>[UnInstall-script](./psget_uninstall-script.md)