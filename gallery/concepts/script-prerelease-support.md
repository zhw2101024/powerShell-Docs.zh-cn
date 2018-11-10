---
ms.date: 10/17/2017
contributor: keithb
keywords: 库,powershell,cmdlet,psget
title: 预发行版脚本
ms.openlocfilehash: 4e7eab682008ed57163c51fe3a61a744b347bef2
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002729"
---
# <a name="prerelease-versions-of-scripts"></a><span data-ttu-id="7b33a-103">预发行版脚本</span><span class="sxs-lookup"><span data-stu-id="7b33a-103">Prerelease versions of scripts</span></span>

<span data-ttu-id="7b33a-104">从版本 1.6.0 开始，PowerShellGet 和 PowerShell 库都支持将 1.0.0 以上的版本标记为预发行版。</span><span class="sxs-lookup"><span data-stu-id="7b33a-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="7b33a-105">在此功能之前，预发行包仅限于以 0 开头的版本。</span><span class="sxs-lookup"><span data-stu-id="7b33a-105">Prior to this feature, prerelease packages were limited to having a version beginning with 0.</span></span> <span data-ttu-id="7b33a-106">这些功能的目标是为 [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) 版本控制约定提供更好的支持，并且不会破坏 PowerShell 版本 3 及更高版本或 PowerShellGet 现有版本的向后兼容性。</span><span class="sxs-lookup"><span data-stu-id="7b33a-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="7b33a-107">本主题重点介绍特定于脚本的功能。</span><span class="sxs-lookup"><span data-stu-id="7b33a-107">This topic focuses on the script-specific features.</span></span> <span data-ttu-id="7b33a-108">模块的等效功能在[预发行模块版本](module-prerelease-support.md)主题中介绍。</span><span class="sxs-lookup"><span data-stu-id="7b33a-108">The equivalent features for modules are in the [Prerelease Module Versions](module-prerelease-support.md) topic.</span></span> <span data-ttu-id="7b33a-109">使用这些功能，发布服务器可以将脚本标识为 2.5.0-alpha 版，随后可发布用于取代预发行版本的 2.5.0 生产就绪版。</span><span class="sxs-lookup"><span data-stu-id="7b33a-109">Using these features, publishers can identify a script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="7b33a-110">在高级别中，预发行版脚本功的能包括：</span><span class="sxs-lookup"><span data-stu-id="7b33a-110">At a high level, the prerelease script features include:</span></span>

- <span data-ttu-id="7b33a-111">将预发行版字符串后缀添加到脚本清单中的版本字符串。</span><span class="sxs-lookup"><span data-stu-id="7b33a-111">Adding a PrereleaseString suffix to the version string in the script manifest.</span></span> <span data-ttu-id="7b33a-112">当脚本发布到 PowerShell 库后，会从清单中提取此数据，用于标识预发行包。</span><span class="sxs-lookup"><span data-stu-id="7b33a-112">When the scripts is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease packages.</span></span>
- <span data-ttu-id="7b33a-113">获取预发行包要求将 -AllowPrerelease 标记添加到 PowerShellGet 命令 Find-Script、Install-Script、Update-Script 和 Save-Script。</span><span class="sxs-lookup"><span data-stu-id="7b33a-113">Acquiring prerelease packages requires adding -AllowPrerelease flag to the PowerShellGet commands Find-Script, Install-Script, Update-Script, and Save-Script.</span></span> <span data-ttu-id="7b33a-114">如果未指定标记，则不会显示预发行包。</span><span class="sxs-lookup"><span data-stu-id="7b33a-114">If the flag is not specified, prerelease packages will not be shown.</span></span>
- <span data-ttu-id="7b33a-115">Find-Script、Get-InstalledScript 显示的脚本版本，以及在 PowerShell 库中显示的脚本版本在显示时会附加预发行版字符串，如 2.5.0-alpha。</span><span class="sxs-lookup"><span data-stu-id="7b33a-115">Script versions displayed by Find-Script, Get-InstalledScript, and in the PowerShell Gallery will be displayed with the PrereleaseString, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="7b33a-116">以下介绍了这些功能的详细信息。</span><span class="sxs-lookup"><span data-stu-id="7b33a-116">Details for the features are included below.</span></span>

## <a name="identifying-a-script-version-as-a-prerelease"></a><span data-ttu-id="7b33a-117">将脚本版本标识为预发行版</span><span class="sxs-lookup"><span data-stu-id="7b33a-117">Identifying a script version as a prerelease</span></span>

<span data-ttu-id="7b33a-118">PowerShellGet 对脚本的预发行版本的支持比模块更容易。</span><span class="sxs-lookup"><span data-stu-id="7b33a-118">PowerShellGet support for prerelease versions is easier for scripts than modules.</span></span> <span data-ttu-id="7b33a-119">仅 PowerShellGet 支持脚本版本控制，因此添加预发行字符串不会引起兼容性问题。</span><span class="sxs-lookup"><span data-stu-id="7b33a-119">Script versioning is only supported by PowerShellGet, so there are no compatibility issues caused by adding the prerelease string.</span></span> <span data-ttu-id="7b33a-120">要将 PowerShell 库中的脚本标识为预发行版，请将预发行后缀添加到脚本元数据中格式正确的版本字符串中。</span><span class="sxs-lookup"><span data-stu-id="7b33a-120">To identify a script in the PowerShell Gallery as a prerelease, add a prerelease suffix to a properly-formatted version string in the script metadata.</span></span>

<span data-ttu-id="7b33a-121">具有预发行版本的脚本清单的示例部分如下所示：</span><span class="sxs-lookup"><span data-stu-id="7b33a-121">An example section of a script manifest with a prerelease version would look like the following:</span></span>

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>
```

<span data-ttu-id="7b33a-122">要使用预发行后缀，版本字符串必须满足以下要求：</span><span class="sxs-lookup"><span data-stu-id="7b33a-122">To use a prerelease suffix, the version string must meet the following requirements:</span></span>

- <span data-ttu-id="7b33a-123">版本为 3 段式的 Major.Minor.Build 时，只能指定预发行后缀。</span><span class="sxs-lookup"><span data-stu-id="7b33a-123">A prerelease suffix may only be specified when the Version is 3 segments for Major.Minor.Build.</span></span>
  <span data-ttu-id="7b33a-124">这符合 SemVer v1.0.0 的要求</span><span class="sxs-lookup"><span data-stu-id="7b33a-124">This aligns with SemVer v1.0.0</span></span>
- <span data-ttu-id="7b33a-125">预发行后缀是以连字符开头的字符串，并且可能包含 ASCII 字母数字 [0-9A-Za-z-]</span><span class="sxs-lookup"><span data-stu-id="7b33a-125">The prerelease suffix is a string which begins with a hyphen, and may contain ASCII alphanumerics [0-9A-Za-z-]</span></span>
- <span data-ttu-id="7b33a-126">此时仅支持 SemVer v1.0.0 预发行字符串，因此预发行后缀不得包含句点或 + [.+]，而在 SemVer 2.0 中允许包含</span><span class="sxs-lookup"><span data-stu-id="7b33a-126">Only SemVer v1.0.0 prerelease strings are supported at this time, so the prerelease suffix **must not** contain either period or + [.+], which are allowed in SemVer 2.0</span></span>
- <span data-ttu-id="7b33a-127">支持的预发行版字符串的示例包括：-alpha、-alpha1、-BETA、-update20171020</span><span class="sxs-lookup"><span data-stu-id="7b33a-127">Examples of supported PrereleaseString strings are: -alpha, -alpha1, -BETA, -update20171020</span></span>

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a><span data-ttu-id="7b33a-128">预发行版本控制对排序顺序和安装文件夹的影响</span><span class="sxs-lookup"><span data-stu-id="7b33a-128">Prerelease versioning impact on sort order and installation folders</span></span>

<span data-ttu-id="7b33a-129">使用预发行版本时，排序顺序会发生更改，这在发布到 PowerShell 库时，以及使用 PowerShellGet 命令安装脚本时非常重要。</span><span class="sxs-lookup"><span data-stu-id="7b33a-129">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing scripts using PowerShellGet commands.</span></span> <span data-ttu-id="7b33a-130">如果两个脚本版本都具有该版本号，则排序顺序基于连字符后面的字符串部分。</span><span class="sxs-lookup"><span data-stu-id="7b33a-130">If two scripts versions with the version number exist, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="7b33a-131">因此，2.5.0-alpha 版低于 2.5.0-beta 版，而 2.5.0-beta 版低于 2.5.0-gamma 版。</span><span class="sxs-lookup"><span data-stu-id="7b33a-131">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="7b33a-132">如果两个脚本具有相同的版本号，并且只有一个脚本具有预发行版字符串，则不具有预发行版后缀的脚本会假定为生产就绪版本，在排序时的版本要比预发行版本高。</span><span class="sxs-lookup"><span data-stu-id="7b33a-132">If two scripts have the same version number, and only one has a PrereleaseString, the script **without** the prerelease suffix is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version.</span></span> <span data-ttu-id="7b33a-133">例如，在比较 2.5.0 和 2.5.0-beta 版本时，2.5.0 版本会视为两者中更高的版本。</span><span class="sxs-lookup"><span data-stu-id="7b33a-133">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="7b33a-134">在发布到 PowerShell 库时，默认情况下，发布的脚本版本必须高于 PowerShell 库中以前发布的任何版本。</span><span class="sxs-lookup"><span data-stu-id="7b33a-134">When publishing to the PowerShell Gallery, by default the version of the script being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span> <span data-ttu-id="7b33a-135">发布服务器可能会使用 2.5.0-beta 或不具有预发行版后缀的 2.5.0 更新版本 2.5.0-alpha。</span><span class="sxs-lookup"><span data-stu-id="7b33a-135">A publisher may update version 2.5.0-alpha with 2.5.0-beta, or with 2.5.0 (with no prerelease suffix).</span></span>

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a><span data-ttu-id="7b33a-136">使用 PowerShellGet 命令查找和获取预发行包</span><span class="sxs-lookup"><span data-stu-id="7b33a-136">Finding and acquiring prerelease packages using PowerShellGet commands</span></span>

<span data-ttu-id="7b33a-137">使用 PowerShellGet Find-Script、Install-Script、Update-Script 和 Save-Script 命令处理预发行包需要添加 -AllowPrerelease 标记。</span><span class="sxs-lookup"><span data-stu-id="7b33a-137">Dealing with prerelease packages using PowerShellGet Find-Script, Install-Script, Update-Script, and Save-Script commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="7b33a-138">如果已指定 -AllowPrerelease，则会包括预发行包（如存在）。</span><span class="sxs-lookup"><span data-stu-id="7b33a-138">If -AllowPrerelease is specified, prerelease packages will be included if they are present.</span></span> <span data-ttu-id="7b33a-139">如果未指定 -AllowPrerelease 标记，则不会显示预发行包。</span><span class="sxs-lookup"><span data-stu-id="7b33a-139">If -AllowPrerelease flag is not specified, prerelease packages will not be shown.</span></span>

<span data-ttu-id="7b33a-140">PowerShellGet 脚本命令中这种情况的唯一例外是 Get-InstalledScript，以及某些情况下的 Uninstall-Script。</span><span class="sxs-lookup"><span data-stu-id="7b33a-140">The only exceptions to this in the PowerShellGet script commands are Get-InstalledScript, and some cases with Uninstall-Script.</span></span>

- <span data-ttu-id="7b33a-141">Get-InstalledScript 始终在版本字符串中自动显示预发行信息（如存在）。</span><span class="sxs-lookup"><span data-stu-id="7b33a-141">Get-InstalledScript always will automatically show the prerelease information in the version string if it is present.</span></span>
- <span data-ttu-id="7b33a-142">Uninstall-Script 在未指定任何版本时默认卸载最新版本的脚本。</span><span class="sxs-lookup"><span data-stu-id="7b33a-142">Uninstall-Script will by default uninstall the most recent version of a script, if **no version** is specified.</span></span> <span data-ttu-id="7b33a-143">该行为尚未更改。</span><span class="sxs-lookup"><span data-stu-id="7b33a-143">That behavior has not changed.</span></span> <span data-ttu-id="7b33a-144">但是，如果预发行版本是使用 `-RequiredVersion` 指定的，则需要 `-AllowPrerelease`。</span><span class="sxs-lookup"><span data-stu-id="7b33a-144">However, if a prerelease version is specified using `-RequiredVersion`, `-AllowPrerelease` will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="7b33a-145">示例</span><span class="sxs-lookup"><span data-stu-id="7b33a-145">Examples</span></span>

```powershell
# Assume the PowerShell Gallery has TestPackage versions 1.8.0 and 1.9.0-alpha.
# If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
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
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage)[Find-Package], Exception
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

<span data-ttu-id="7b33a-146">如果未提供 -RequiredVersion，Uninstall-Script 会删除最新版本的脚本。</span><span class="sxs-lookup"><span data-stu-id="7b33a-146">Uninstall-Script will remove the current version of a script when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="7b33a-147">如果已指定 -RequiredVersion，并且是预发行版，则必须将 -AllowPrerelease 添加到命令中。</span><span class="sxs-lookup"><span data-stu-id="7b33a-147">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

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

## <a name="more-details"></a><span data-ttu-id="7b33a-148">详细信息</span><span class="sxs-lookup"><span data-stu-id="7b33a-148">More details</span></span>

- [<span data-ttu-id="7b33a-149">预发行模块版本</span><span class="sxs-lookup"><span data-stu-id="7b33a-149">Prerelease Module Versions</span></span>](module-prerelease-support.md)
- [<span data-ttu-id="7b33a-150">Find-script</span><span class="sxs-lookup"><span data-stu-id="7b33a-150">Find-script</span></span>](/powershell/module/powershellget/find-script)
- [<span data-ttu-id="7b33a-151">Install-script</span><span class="sxs-lookup"><span data-stu-id="7b33a-151">Install-script</span></span>](/powershell/module/powershellget/install-script)
- [<span data-ttu-id="7b33a-152">Save-script</span><span class="sxs-lookup"><span data-stu-id="7b33a-152">Save-script</span></span>](/powershell/module/powershellget/save-script)
- [<span data-ttu-id="7b33a-153">Update-script</span><span class="sxs-lookup"><span data-stu-id="7b33a-153">Update-script</span></span>](/powershell/module/powershellget/update-script)
- [<span data-ttu-id="7b33a-154">Get-Installedscript</span><span class="sxs-lookup"><span data-stu-id="7b33a-154">Get-Installedscript</span></span>](/powershell/module/powershellget/get-installedscript)
- [<span data-ttu-id="7b33a-155">UnInstall-script</span><span class="sxs-lookup"><span data-stu-id="7b33a-155">UnInstall-script</span></span>](/powershell/module/powershellget/uninstall-script)
