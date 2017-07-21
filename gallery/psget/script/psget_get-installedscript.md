---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "库,powershell,cmdlet,psget"
title: Get-InstalledScript
ms.openlocfilehash: f35e57cdadd1448bd9032ab007d692003c4cf4a2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="get-installedscript"></a><span data-ttu-id="1df74-103">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="1df74-103">Get-InstalledScript</span></span>

<span data-ttu-id="1df74-104">获取计算机上的已安装脚本。</span><span class="sxs-lookup"><span data-stu-id="1df74-104">Gets installed scripts on a computer.</span></span>

## <a name="description"></a><span data-ttu-id="1df74-105">说明</span><span class="sxs-lookup"><span data-stu-id="1df74-105">Description</span></span>

<span data-ttu-id="1df74-106">Get-InstalledScript cmdlet 获取计算机上的已安装 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="1df74-106">The Get-InstalledScript cmdlet gets installed PowerShell scripts on a computer.</span></span>

<span data-ttu-id="1df74-107">对于每个已安装脚本，Get-InstalledScript 将返回 PSRepositoryItemInfo 对象，可根据需要将其通过管道传递到 Uninstall-Script 以卸载已安装的脚本。</span><span class="sxs-lookup"><span data-stu-id="1df74-107">For each installed script, Get-InstalledScript returns a PSRepositoryItemInfo object which can optionally be piped to Uninstall-Script for uninstalling the installed scripts.</span></span>

- <span data-ttu-id="1df74-108">Get-InstalledScript 可根据名称、版本参数筛选已安装的脚本。</span><span class="sxs-lookup"><span data-stu-id="1df74-108">Get-InstalledScript can filter installed scripts based on name, version parameters.</span></span>
- <span data-ttu-id="1df74-109">Get-InstalledScript 可使用版本参数进行筛选：MinimumVersion、MaximumVersion、RequiredVersion、AllVersions。</span><span class="sxs-lookup"><span data-stu-id="1df74-109">Get-InstalledScript can filter with version parameters: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="1df74-110">这些参数彼此排斥，但 MinmimumVersion 和 MaximumVersion 除外。</span><span class="sxs-lookup"><span data-stu-id="1df74-110">These parameters are mutually exclusive, except MinmimumVersion and MaximumVersion.</span></span>
  - <span data-ttu-id="1df74-111">这些版本参数只允许具有单个脚本名称，而不能具有任何通配符。</span><span class="sxs-lookup"><span data-stu-id="1df74-111">These version parameters are allowed only with the single script name without any wildcards.</span></span>
  - <span data-ttu-id="1df74-112">如果未指定 RequiredVersion 参数，Get-InstalledScript 将返回等于或高于指定最低版本的已安装脚本的最新版本，若未指定最低版本，则返回脚本的最新版本。</span><span class="sxs-lookup"><span data-stu-id="1df74-112">If the RequiredVersion parameter is not specified, Get-InstalledScript returns the latest version of the installed script that is equal to or greater than the minimum version specified or the latest version of the script if no minimum version is specified.</span></span> 
  - <span data-ttu-id="1df74-113">如果指定了 RequiredVersion 参数，Get-InstalledScript 仅返回与指定版本完全匹配的已安装脚本版本。</span><span class="sxs-lookup"><span data-stu-id="1df74-113">If the RequiredVersion parameter is specified, Get-InstalledScript only returns the version of installed script that exactly matches the specified version.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="1df74-114">Cmdlet 语法</span><span class="sxs-lookup"><span data-stu-id="1df74-114">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Get-InstalledScript -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="1df74-115">Cmdlet 联机帮助参考</span><span class="sxs-lookup"><span data-stu-id="1df74-115">Cmdlet online help reference</span></span>

[<span data-ttu-id="1df74-116">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="1df74-116">Get-InstalledScript</span></span>](http://go.microsoft.com/fwlink/?LinkId=619790)

## <a name="example-commands"></a><span data-ttu-id="1df74-117">示例命令</span><span class="sxs-lookup"><span data-stu-id="1df74-117">Example commands</span></span>

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

