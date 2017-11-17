---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "库,powershell,cmdlet,psget"
title: Find-Script
ms.openlocfilehash: 15bf23b803250c7893fe970c2580592ea7c0a4b6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="find-script"></a><span data-ttu-id="1091e-103">Find-Script</span><span class="sxs-lookup"><span data-stu-id="1091e-103">Find-Script</span></span>

<span data-ttu-id="1091e-104">查找联机库中与指定条件相匹配的 PowerShell 脚本文件。</span><span class="sxs-lookup"><span data-stu-id="1091e-104">Finds the PowerShell script files from an online gallery that match specified criteria.</span></span>

## <a name="description"></a><span data-ttu-id="1091e-105">说明</span><span class="sxs-lookup"><span data-stu-id="1091e-105">Description</span></span>

<span data-ttu-id="1091e-106">Find-Script 在已注册存储库中发现了与指定条件相匹配的脚本文件。</span><span class="sxs-lookup"><span data-stu-id="1091e-106">Find-Script discovers the script files from registered repositories that matches the specified criteria.</span></span>
<span data-ttu-id="1091e-107">对于每个已发现的脚本，Find-Script 将返回 PSRepositoryItemInfo 对象，可根据需要将其通过管道传递到 Install-Script 以安装该脚本。</span><span class="sxs-lookup"><span data-stu-id="1091e-107">For each script found, Find-Script returns a PSRepositoryItemInfo object which can optionally be piped to Install-Script for installing the scripts.</span></span>
<span data-ttu-id="1091e-108">Find-Script cmdlet 可使用不同的搜索条件（如名称、标记、筛选器、命令名、版本范围、确切版本、所有版本及其依赖项和来自特定的或所有已注册的存储库）来发现脚本文件。</span><span class="sxs-lookup"><span data-stu-id="1091e-108">Find-Script cmdlet lets you to discover the script files with different search criteria like name, tag, filter, command name, version range, exact version, all versions, including its dependencies and from specific or all registered repositories.</span></span>

- <span data-ttu-id="1091e-109">Find-Script 可使用 -Command 和 -Includes 参数根据模块内容进行筛选。</span><span class="sxs-lookup"><span data-stu-id="1091e-109">Find-Script can filter based on script contents with the -Command and -Includes parameters.</span></span>
- <span data-ttu-id="1091e-110">Find-Script 可使用版本参数进行筛选：MinimumVersion、MaximumVersion、RequiredVersion、AllVersions。</span><span class="sxs-lookup"><span data-stu-id="1091e-110">Find-Script can filter with version parameters: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="1091e-111">这些参数彼此排斥，但 MinmimumVersion 和 MaximumVersion 除外。</span><span class="sxs-lookup"><span data-stu-id="1091e-111">These parameters are mutually exclusive, except MinmimumVersion and MaximumVersion.</span></span>
  - <span data-ttu-id="1091e-112">这些版本参数只允许具有单个脚本名称，而不能具有任何通配符。</span><span class="sxs-lookup"><span data-stu-id="1091e-112">These version parameters are allowed only with the single script name without any wildcards.</span></span>
  - <span data-ttu-id="1091e-113">如果未指定 RequiredVersion 参数，Find-Script 将返回等于或高于指定最低版本的脚本的最新版本，若未指定最低版本，则返回脚本的最新版本。</span><span class="sxs-lookup"><span data-stu-id="1091e-113">If the RequiredVersion parameter is not specified, Find-Script returns the latest version of the script that is equal to or greater than the minimum version specified or the latest version of the script if no minimum version is specified.</span></span> 
  - <span data-ttu-id="1091e-114">如果指定了 RequiredVersion 参数，Find-Script 仅返回与指定版本完全匹配的脚本版本。</span><span class="sxs-lookup"><span data-stu-id="1091e-114">If the RequiredVersion parameter is specified, Find-Script only returns the version of script that exactly matches the specified version.</span></span>
- <span data-ttu-id="1091e-115">Find-Script 可使用 -Tag 参数对脚本元数据进行筛选。</span><span class="sxs-lookup"><span data-stu-id="1091e-115">Find-Script can filter on script metadata with the -Tag parameter.</span></span>
- <span data-ttu-id="1091e-116">Find-Script 可使用 -Filter 参数对存储库特定搜索语言进行筛选。</span><span class="sxs-lookup"><span data-stu-id="1091e-116">Find-Script can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="1091e-117">Find-Script 可从所有或少数已注册存储库中对脚本进行筛选。</span><span class="sxs-lookup"><span data-stu-id="1091e-117">Find-Script can filter on scripts from all or few of the registered repositories.</span></span>

<span data-ttu-id="1091e-118">**注意：**已注册的 PSRepository 应具有有效的 ScriptSourceLocation。</span><span class="sxs-lookup"><span data-stu-id="1091e-118">**NOTE:** Registered PSRepository should have a valid ScriptSourceLocation.</span></span> <span data-ttu-id="1091e-119">可使用 Set-PSRepository 设置 ScriptSourceLocation 值。</span><span class="sxs-lookup"><span data-stu-id="1091e-119">You can use the Set-PSRepository to set ScriptSourceLocation value.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="1091e-120">Cmdlet 语法</span><span class="sxs-lookup"><span data-stu-id="1091e-120">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Find-Script -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="1091e-121">Cmdlet 联机帮助参考</span><span class="sxs-lookup"><span data-stu-id="1091e-121">Cmdlet online help reference</span></span>

[<span data-ttu-id="1091e-122">Find-Script</span><span class="sxs-lookup"><span data-stu-id="1091e-122">Find-Script</span></span>](http://go.microsoft.com/fwlink/?LinkId=619785)

## <a name="example-commands"></a><span data-ttu-id="1091e-123">示例命令</span><span class="sxs-lookup"><span data-stu-id="1091e-123">Example commands</span></span>

```powershell
# Find a script from the registered repository with ScriptSourceLocation
Find-Script Connect-AzureVM

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        Connect-AzureVM                     PSGallery            This runbook sets up a connection to an Azure vi...

# Find multiple scripts
Find-Script -Name Connect-AzureVM, Show-Tree, Connect-O365

# Find scripts with wildcards in -Name
Find-Script -Name *Azure*

# Find all versions of a script
Find-Script -Name Connect-O365 -AllVersions

# Find a script with -MinimumVersion. 
# With MinimumVersion we can find a script whose version is greate than or equal to the specified MinimumVersion value.
Find-Script Connect-O365 -MinimumVersion 1.4

# Find a script with MaximumVersion
Find-Script -Name Connect-O365 -MaximumVersion 1.6.2

# Find a script with both MinimumVersion and MaximumVersion range.
Find-Script -Name Connect-O365 -MinimumVersion 1.1 -MaximumVersion 1.6.2

# Find a script with exact version
Find-Script -Name Connect-O365 -RequiredVersion 1.5.7

# Find a script from the specified repository
Find-Script -Name Fabrikam-ServerScript -Repository MyLocalRepo

# Find available scripts from all registered repositories
Find-Script

# Find available scripts from few registered repositories
Find-Script -Repository PSGallery, PrivatePSGallery

# Find a script along with its dependent modules and scripts
Find-Script -Name Connect-AzureVM -IncludeDependencies

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        Connect-AzureVM                     PSGallery            This runbook sets up a connection to an Azure vi...
1.4.0      Azure                               PSGallery            Microsoft Azure PowerShell - Service Management
1.1.2      Azure.Storage                       PSGallery            Microsoft Azure PowerShell - Storage service cmd...
1.0.8      AzureRM.profile                     PSGallery            Microsoft Azure PowerShell - Profile credential ...

# Find all scripts with workflows
Find-Script -Includes Workflow

# Find all scripts with functions
Find-Script -Includes Function

# Find scripts with specific commands
Find-Script -Command Log-Message
Find-Script -Command Log-Message, Show-Tree -Includes Function
Find-Script -Command Connect-AzureVM -Includes Workflow

# Find scripts with -Filter based search. -Filter searches in description and names
Find-Script -Filter Windows
Find-Script -Filter Azure

# Find all scripts with tags O365 or Nano
Find-Script -Tag O365, Nano

# Properties of Find-Script returned object
Find-Script Show-Tree | Format-List * -Force
Name                       : Show-Tree
Version                    : 1.0.0
Type                       : Script
Description                : Script to show the layout of PowerShell namespaces (Trees) using ASCII
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 10:15:35 PM
InstalledDate              :
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
AdditionalMetadata         : {versionDownloadCount, ItemType, copyright, PackageManagementProvider...}


# Includes property on PSRepositoryItemInfo object
$t = Find-Script -Includes Workflow -Repository INT -Name Fabrikam-ClientScript
$t.Includes

Name                           Value
----                           -----
Function                       {Test-FunctionFromScript_Fabrikam-ClientScript}
RoleCapability                 {}
Command                        {Test-FunctionFromScript_Fabrikam-ClientScript, Test-WorkflowFromScript_Fabrikam-Clie...
DscResource                    {}
Workflow                       {Test-WorkflowFromScript_Fabrikam-ClientScript}
Cmdlet                         {}


```

