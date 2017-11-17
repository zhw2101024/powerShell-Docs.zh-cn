---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "库,powershell,cmdlet,psget"
title: Find-DscResource
ms.openlocfilehash: 37ba7925d6f73c453126f25e0818b3f8839d3b3b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="find-dscresource"></a><span data-ttu-id="8b33a-103">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="8b33a-103">Find-DscResource</span></span>

<span data-ttu-id="8b33a-104">在模块中查找 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="8b33a-104">Finds DSC Resources in modules.</span></span>

## <a name="description"></a><span data-ttu-id="8b33a-105">说明</span><span class="sxs-lookup"><span data-stu-id="8b33a-105">Description</span></span>

<span data-ttu-id="8b33a-106">Find-DscResource cmdlet 查找已注册的存储库中与指定条件匹配的模块中所包含的[所需状态配置 (DSC)](https://msdn.microsoft.com/en-us/PowerShell/dsc/overview) 资源。</span><span class="sxs-lookup"><span data-stu-id="8b33a-106">The Find-DscResource cmdlet finds [Desired State Configuration (DSC)](https://msdn.microsoft.com/en-us/PowerShell/dsc/overview) resources contained in modules that match the specified criteria from registered repositories.</span></span>
<span data-ttu-id="8b33a-107">对于此 cmdlet 查找的每个模块，Find-DscResource 返回一个 PSGetDscResourceInfo 对象，可以将其通过管道传递到 Install-Module 以安装包含此 cmdlet 返回的资源的模块。</span><span class="sxs-lookup"><span data-stu-id="8b33a-107">For each module that this cmdlet finds, Find-DscResource returns a PSGetDscResourceInfo object that you can pipe to Install-Module to install the modules containing the resources that this cmdlet returns.</span></span>

<span data-ttu-id="8b33a-108">DSC 是 Windows PowerShell 中的新管理平台，可用于部署和管理软件服务的配置数据，并管理这些服务的运行的环境。</span><span class="sxs-lookup"><span data-stu-id="8b33a-108">DSC is a new management platform in Windows PowerShell that enables deploying and managing configuration data for software services and managing the environment in which these services run.</span></span>

<span data-ttu-id="8b33a-109">Desired State Configuration (DSC) 资源为 DSC 配置提供构建基块。</span><span class="sxs-lookup"><span data-stu-id="8b33a-109">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="8b33a-110">资源公开可配置的属性（架构），并包含本地配置管理器 (LCM) 调用以“使其如此”的 PowerShell 脚本函数。</span><span class="sxs-lookup"><span data-stu-id="8b33a-110">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="8b33a-111">资源的建模对象可以是一般的文件或 Windows 进程，也可以是具体的 IIS 服务器设置。</span><span class="sxs-lookup"><span data-stu-id="8b33a-111">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span> <span data-ttu-id="8b33a-112">资源等组被组合成为 DSC 模块，模块将全部所需文件组织成为一个可移植结构，该结构包含标志资源既定用途的元数据。</span><span class="sxs-lookup"><span data-stu-id="8b33a-112">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

- <span data-ttu-id="8b33a-113">Find-DscResource 可使用版本参数 MinimumVersion、RequiredVersion、AllVersions 进行筛选。</span><span class="sxs-lookup"><span data-stu-id="8b33a-113">Find-DscResource can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="8b33a-114">这些参数彼此排斥。</span><span class="sxs-lookup"><span data-stu-id="8b33a-114">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="8b33a-115">这些版本参数只允许具有单个模块名称，而不能具有任何通配符。</span><span class="sxs-lookup"><span data-stu-id="8b33a-115">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="8b33a-116">如果未指定 RequiredVersion 参数，Find-DscResource 将返回等于或高于指定的最低版本的最新版本的模块或最新版本的模块（若未指定最低版本）。</span><span class="sxs-lookup"><span data-stu-id="8b33a-116">If the RequiredVersion parameter is not specified, Find-DscResource returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="8b33a-117">如果指定了 RequiredVersion 参数，Find-DscResource 仅返回与指定版本完全匹配的模块。</span><span class="sxs-lookup"><span data-stu-id="8b33a-117">If the RequiredVersion parameter is specified, Find-DscResource only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="8b33a-118">Find-DscResource 可使用 -Tag 参数对模块元数据进行筛选</span><span class="sxs-lookup"><span data-stu-id="8b33a-118">Find-DscResource can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="8b33a-119">Find-DscResource 可使用 -Filter 参数对存储库特定搜索语言进行筛选。</span><span class="sxs-lookup"><span data-stu-id="8b33a-119">Find-DscResource can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="8b33a-120">Find-DscResource 可从所有或少数已注册存储库中对模块进行筛选。</span><span class="sxs-lookup"><span data-stu-id="8b33a-120">Find-DscResource can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="8b33a-121">Cmdlet 语法</span><span class="sxs-lookup"><span data-stu-id="8b33a-121">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-DscResource -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="8b33a-122">Cmdlet 联机帮助参考</span><span class="sxs-lookup"><span data-stu-id="8b33a-122">Cmdlet online help reference</span></span>

[<span data-ttu-id="8b33a-123">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="8b33a-123">Find-DscResource</span></span>](http://go.microsoft.com/fwlink/?LinkId=517196)

## <a name="example-commands"></a><span data-ttu-id="8b33a-124">示例命令</span><span class="sxs-lookup"><span data-stu-id="8b33a-124">Example commands</span></span>
```powershell

# Find a specific DSC Resource
Find-DscResource -Name xIisFeatureDelegation

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
xIisFeatureDelegation               1.10.0.0   xWebAdministration                  PSGallery

# Find all available DSC Resources from all registered repositories
Find-DscResource

# Find a DSC resource by name
Find-DscResource -Name xWebsite

# Find multiple DSC Resources
Find-DscResource -Name xIisHandler, xFirewall

# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking
Find-DscResource -ModuleName xWebAdministration

# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

# Find available DSC Resources from few registered repositories
Find-DscResource -Repository PSGallery,PrivatePSGallery

# Find all DSC Resources in a specified repository
Find-DscResource -Repository PSGallery

# Find DSC Resources from all versions of a module
Find-DscResource -ModuleName xNetworking -AllVersions

# Find DSC Resources with module name and MinimumVersion.
Find-DscResource -ModuleName xNetworking -MinimumVersion 1.1

# Find DSC Resources with module name and exact version
Find-DscResource -ModuleName xNetworking -RequiredVersion 2.1.1

# Find DSC Resources defined modules with -Filter based search. -Filter searches in description and module names
Find-DscResource -Filter Domain

# Find all DSC Resources with tags Azure or DSC in module metadata
Find-DscResource -Tag Azure, DSC

```

