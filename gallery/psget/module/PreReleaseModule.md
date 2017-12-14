---
ms.date: 2017-09-26
contributor: keithb
ms.topic: reference
keywords: "库,powershell,cmdlet,psget"
title: PrereleaseModule
ms.openlocfilehash: d2c629d0e0ec0d4a4adafe5994a37d3985d13a06
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2017
---
# <a name="prerelease-module-versions"></a>预发行模块版本
从版本 1.6.0 开始，PowerShellGet 和 PowerShell 库都支持将 1.0.0 以上的版本标记为预发行版。 在此功能之前，预发行项仅限于以 0 开头的版本。 这些功能的目标是为 [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) 版本控制约定提供更好的支持，并且不会破坏 PowerShell 版本 3 及更高版本或 PowerShellGet 现有版本的向后兼容性。 本主题重点介绍特定于模块的功能。 脚本的等效功能在[预发行版脚本](../script/PrereleaseScript.md)主题中介绍。 使用这些功能，发布服务器可以将模块或脚本标识为版本 2.5.0-alpha，随后可发布用于取代预发行版本的生产就绪版本 2.5.0。 

在高级别中，预发行模块的功能包括：

* 在模块清单的 PSData 部分添加预发行版字符串将模块标识为预发行版本。 当模块发布到 PowerShell 库后，会从清单中提取此数据，用于标识预发行项。
* 获取预发行项要求将 -AllowPrerelease 标志添加到 PowerShellGet 命令 Find-Module、Install-Module、Update-Module 和 Save-Module。 如果未指定标志，则不会显示预发行项。  
* Find-Module、Get-InstalledModule 显示的模块版本，以及在 PowerShell 库中显示的模块版本会显示为附加了预发行版字符串的单个字符串，如 2.5.0-alpha。 

以下介绍了这些功能的详细信息。 

这些更改不会影响内置于 PowerShell 的模块版本支持，并与 PowerShell 3.0、4.0 和 5 兼容。 

## <a name="identifying-a-module-version-as-a-prerelease"></a>将模块版本标识为预发行版 

PowerShellGet 对预发行版本的支持要求在模块清单中使用两个字段：

* 如果使用预发行版本，包含在模块清单中的 ModuleVersion 必须为 3 段式版本，且必须符合现有的 PowerShell 版本控制。 版本格式为 A.B.C，其中 A、B 和 C 均为整数。 
* 预发行版字符串指定于模块清单、PrivateData 的 PSData 部分。 下面是对预发行版字符串的详细要求。 

用于将模块定义为预发行版的模块清单的示例部分如下所示：
```powershell
@{
    ModuleVersion = '2.5.0'
    #---
    PrivateData = @{
        PSData = @{
            Prerelease = 'alpha'
        }
    }
}
```

对预发行版字符串的详细要求如下： 

* ModuleVersion 为 Major.Minor.Build 的 3 段时，可能只指定预发行版字符串。 这符合 SemVer v1.0.0 的要求。
* 连字符是内部版本号和预发行版字符串之间的分隔符。 连字符只能作为第一个字符包含在预发行版字符串中。
* 预发行版字符串可以只包含 ASCII 字母数字 [0-9A-Za-z-]。 预发行版字符串最好以 alpha 字符开头，这样在扫描项列表时，可以更轻松地辨认这是预发行版本。 
* 此时仅支持 SemVer v1.0.0 预发行字符串。 预发行版字符串不得包含句点或 + [.+]，而在 SemVer 2.0 中允许包含。 
* 支持的预发行版字符串的示例包括：-alpha、-alpha1、-BETA、-update20171020

__预发行版本控制对排序顺序和安装文件夹的影响__

使用预发行版本时，排序顺序会发生更改，这在发布到 PowerShell 库时，以及使用 PowerShellGet 命令安装模块时非常重要。 如果预发行版字符串是针对两个模块指定的，则排序顺序基于连字符后面的字符串部分。 因此，2.5.0-alpha 版低于 2.5.0-beta 版，而 2.5.0-beta 版低于 2.5.0-gamma 版。 如果两个模块具有相同的 ModuleVersion，并且只有一个模块具有预发行版字符串，则不具有预发行版字符串的模块会假定为生产就绪版本，在排序时的版本要比具有预发行版字符串的预发行版本高。 例如，在比较 2.5.0 和 2.5.0-beta 版本时，2.5.0 版本会视为两者中更高的版本。 

在发布到 PowerShell 库时，默认情况下，发布的模块版本必须高于 PowerShell 库中以前发布的任何版本。 

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a>使用 PowerShellGet 命令查找和获取预发行项

使用 PowerShellGet Find-Module、Install-Module、Update-Module 和 Save-Module 命令处理预发行项需要添加 -AllowPrerelease 标志。 如果已指定 -AllowPrerelease，则会包括预发行项（如存在）。
如果未指定 -AllowPrerelease 标志，则不会显示预发行项。 

PowerShellGet 模块命令中这种情况的唯一例外是 Get-InstalledModule，以及某些情况下的 Uninstall-Module。 

* Get-InstalledModule 始终在模块的版本字符串中自动显示预发行信息。 
* Uninstall-Module 在未指定任何版本时默认卸载最新版本的模块。 该行为尚未更改。 但是，如果预发行版本是使用 -RequiredVersion 指定的，则需要 -AllowPrerelease。 

## <a name="examples"></a>示例
```powershell
# Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha. If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> find-module TestPackage 

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

# To install a prerelease, always specify -AllowPrerelease. Specifying a prerelease version string is not sufficient. 

C:\windows\system32> Install-module TestPackage -RequiredVersion 1.9.0-alpha
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exceptio
   n
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

```

如果模块仅仅是因为指定的预发行版而有所区别，则不支持并行安装该模块的各版本。 使用 PowerShellGet 安装模块时，通过使用 ModuleVersion 创建文件夹名称，并行安装同一模块的不同版本。 不含预发行版字符串的 ModuleVersion 可用作文件夹名称。 用户安装 MyModule 的 2.5.0-alpha 版本时，会安装到 MyModule\2.5.0 文件夹。 如果用户之后安装 2.5.0-beta，则 2.5.0-beta 版本会覆盖文件夹 MyModule\2.5.0 的内容。 此方法的一个优点是安装生产就绪版本后无需卸载预发行版本。 以下示例展示了期望的效果：


``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-beta     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-beta      TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

```

如果未通过 -RequiredVersion，Uninstall-Module 会删除最新版本的模块。 如果已指定 -RequiredVersion，并且是预发行版，则必须将 -AllowPrerelease 添加到命令中。 

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
2.0.0-alpha1    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Unnstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-Module



C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
2.0.0-alpha1    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...


```



## <a name="more-details"></a>详细信息
### <a name="prerelease-script-versionsscriptprereleasescriptmd"></a>[预发行脚本版本](../script/PrereleaseScript.md)
### <a name="find-modulepsgetfind-modulemd"></a>[Find-Module](./psget_find-module.md)
### <a name="install-modulepsgetinstall-modulemd"></a>[Install-Module](./psget_install-module.md)
### <a name="save-modulepsgetsave-modulemd"></a>[Save-Module](./psget_save-module.md)
### <a name="update-modulepsgetupdate-modulemd"></a>[Update-Module](./psget_update-module.md)
### <a name="get-installedmodulepsgetget-installedmodulemd"></a>[Get-InstalledModule](./psget_get-installedmodule.md)
### <a name="uninstall-modulepsgetuninstall-modulemd"></a>[UnInstall-Module](./psget_uninstall-module.md)
