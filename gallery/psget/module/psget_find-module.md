---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "库,powershell,cmdlet,psget"
title: Find-Module
ms.openlocfilehash: 5c878a04d186f7f5970fba9e7f3cdb480cef21f6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="find-module"></a><span data-ttu-id="22c66-103">Find-Module</span><span class="sxs-lookup"><span data-stu-id="22c66-103">Find-Module</span></span>
<span data-ttu-id="22c66-104">查找联机库中与指定条件相匹配的模块。</span><span class="sxs-lookup"><span data-stu-id="22c66-104">Finds modules from an online gallery that match specified criteria.</span></span>

## <a name="description"></a><span data-ttu-id="22c66-105">说明</span><span class="sxs-lookup"><span data-stu-id="22c66-105">Description</span></span>
<span data-ttu-id="22c66-106">Find-Module 在已注册存储库中发现与指定条件相匹配的模块。</span><span class="sxs-lookup"><span data-stu-id="22c66-106">Find-Module discovers the modules from registered repositories that matches the specified criteria.</span></span>
<span data-ttu-id="22c66-107">对于每个找到的模块，Find-Module 将返回 PSRepositoryItemInfo 对象，可根据需要将其通过管道传递到 Install-Module 以安装该模块。</span><span class="sxs-lookup"><span data-stu-id="22c66-107">For each module found, Find-Module returns a PSRepositoryItemInfo object which can optionally be piped to Install-Module for installing the modules.</span></span>

- <span data-ttu-id="22c66-108">Find-Module 可使用 -Command、-DscResource、 -RoleCapability 和 -Includes 参数根据模块内容进行筛选。</span><span class="sxs-lookup"><span data-stu-id="22c66-108">Find-Module can filter based on module contents with the -Command, -DscResource, -RoleCapability and -Includes parameters.</span></span>
- <span data-ttu-id="22c66-109">Find-Module 可使用版本参数 MinimumVersion、MaximumVersion、RequiredVersion、AllVersions 进行筛选。</span><span class="sxs-lookup"><span data-stu-id="22c66-109">Find-Module can filter with version parameters: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="22c66-110">这些参数彼此排斥，但 MinmimumVersion 和 MaximumVersion 除外。</span><span class="sxs-lookup"><span data-stu-id="22c66-110">These parameters are mutually exclusive, except MinmimumVersion and MaximumVersion.</span></span>
  - <span data-ttu-id="22c66-111">这些版本参数只允许具有单个模块名称，而不能具有任何通配符。</span><span class="sxs-lookup"><span data-stu-id="22c66-111">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="22c66-112">如果未指定 RequiredVersion 参数，Find-Module 将返回等于或高于指定的最低版本的最新版本的模块或最新版本的模块（若未指定最低版本）。</span><span class="sxs-lookup"><span data-stu-id="22c66-112">If the RequiredVersion parameter is not specified, Find-Module returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span> 
  - <span data-ttu-id="22c66-113">如果已指定 RequiredVersion 参数，则 Find-Module 只返回完全匹配指定版本的模块。</span><span class="sxs-lookup"><span data-stu-id="22c66-113">If the RequiredVersion parameter is specified, Find-Module only returns the version of module that exactly matches the specified version.</span></span>
- <span data-ttu-id="22c66-114">Find-Module 可以使用 -Tag 参数对模块元数据进行筛选</span><span class="sxs-lookup"><span data-stu-id="22c66-114">Find-Module can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="22c66-115">Find-Module 可使用 -Filter 参数对存储库特定搜索语言进行筛选。</span><span class="sxs-lookup"><span data-stu-id="22c66-115">Find-Module can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="22c66-116">Find-Module 可从所有或少数的已注册的存储库中对模块进行筛选。</span><span class="sxs-lookup"><span data-stu-id="22c66-116">Find-Module can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="22c66-117">Cmdlet 语法</span><span class="sxs-lookup"><span data-stu-id="22c66-117">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="22c66-118">Cmdlet 联机帮助参考</span><span class="sxs-lookup"><span data-stu-id="22c66-118">Cmdlet online help reference</span></span>

[<span data-ttu-id="22c66-119">Find-Module</span><span class="sxs-lookup"><span data-stu-id="22c66-119">Find-Module</span></span>](http://go.microsoft.com/fwlink/?LinkID=398574)

## <a name="example-commands"></a><span data-ttu-id="22c66-120">示例命令</span><span class="sxs-lookup"><span data-stu-id="22c66-120">Example commands</span></span>
```powershell
# Find a specific module
Find-Module Azure

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.3.2      Azure                               PSGallery            Microsoft Azure PowerShell - Service Management

# Find multiple modules
Find-Module Azure,AzureRM

# Find modules with wildcards in -Name
Find-Module -Name AzureRM*

# Find all versions of a module
Find-Module -Name PSReadline -AllVersions

# Find a module with -MinimumVersion. 
# With MinimumVersion we can find a module whose version is greate than or equal to the specified MinimumVersion value.
Find-Module -Name PSReadline -MinimumVersion 1.0.0.12

# Find a module with MaximumVersion
Find-Module -Name PSReadline -MaximumVersion 1.0.0.13

# Find a module with both MinimumVersion and MaximumVersion range.
Find-Module -Name PSReadline -MinimumVersion 1.0.0.12 -MaximumVersion 1.0.0.13

# Find a module with exact version
Find-Module -Name AzureRM -RequiredVersion 1.3.2

# Find a module from the specified repository
Find-Module -Name Contoso -Repository MyLocalRepo

# Find available modules from all registered repositories
Find-Module

# Find available modules from few registered repositories
Find-Module -Repository PSGallery,PrivatePSGallery

# Find a module along with its dependencies
Find-Module -Name AzureRM -IncludeDependencies

# Find all modules with Dsc resources
Find-Module -Includes DscResource

# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

# Find all modules with cmdlets
Find-Module -Includes Cmdlet

# Find all modules with functions
Find-Module -Includes Function

# Find all modules with Role Capabilities
Find-Module -Includes RoleCapability

# Find all modules with the specified Role Capability name
Find-Module -RoleCapability RoleCap1
Find-Module -RoleCapability RoleCap2 -Includes RoleCapability

# Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer -Includes Cmdlet
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer -Includes Function

# Find modules with -Filter based search. -Filter searches in description and names
Find-Module -Filter Cookbook
Find-Module -Filter RBAC
Find-Module -Filter 'App Domain' -Includes 'DscResource'

# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

# Properties of Find-Module returned object
Find-Module AzureRM.Profile | Format-List * -Force

Name                       : AzureRM.profile
Version                    : 1.0.8
Type                       : Module
Description                : Microsoft Azure PowerShell - Profile credential management cmdlets for Azure Resource
                             Manager
Author                     : Microsoft Corporation
CompanyName                : {elogeel, azure-sdk}
Copyright                  : Microsoft Corporation. All rights reserved.
PublishedDate              : 5/4/2016 9:40:33 PM
InstalledDate              :
UpdatedDate                :
LicenseUri                 : https://raw.githubusercontent.com/Azure/azure-powershell/dev/LICENSE.txt
ProjectUri                 : https://github.com/Azure/azure-powershell
IconUri                    :
Tags                       : {PSModule}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               : https://github.com/Azure/azure-powershell/blob/dev/ChangeLog.md
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {downloadCount, description, copyright, FileList...}

```

