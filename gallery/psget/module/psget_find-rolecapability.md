---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "库,powershell,cmdlet,psget"
title: Find-RoleCapability
ms.openlocfilehash: 77c5b492d9681fa05315401fba410c508af1d13b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="find-rolecapability"></a><span data-ttu-id="70103-103">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="70103-103">Find-RoleCapability</span></span>

<span data-ttu-id="70103-104">在模块中查找角色功能。</span><span class="sxs-lookup"><span data-stu-id="70103-104">Finds role capabilities in modules.</span></span>

## <a name="description"></a><span data-ttu-id="70103-105">说明</span><span class="sxs-lookup"><span data-stu-id="70103-105">Description</span></span>
<span data-ttu-id="70103-106">Find-RoleCapability cmdlet 查找模块中的 PowerShell 角色功能。</span><span class="sxs-lookup"><span data-stu-id="70103-106">The Find-RoleCapability cmdlet finds PowerShell role capabilities in modules.</span></span> <span data-ttu-id="70103-107">Find-RoleCapability 在已注册的存储库中搜索模块。</span><span class="sxs-lookup"><span data-stu-id="70103-107">Find-RoleCapability searches modules in registered repositories.</span></span> <span data-ttu-id="70103-108">对于此 cmdlet 查找的每个角色功能，它将返回 PSGetRoleCapabilityInfo 对象。</span><span class="sxs-lookup"><span data-stu-id="70103-108">For each role capability that this cmdlet finds, it returns a PSGetRoleCapabilityInfo object.</span></span> <span data-ttu-id="70103-109">可以将 PSGetRoleCapabilityInfo 对象传递给 Install-Module cmdlet 以安装包含角色功能的模块。</span><span class="sxs-lookup"><span data-stu-id="70103-109">You can pass a PSGetRoleCapabilityInfo object to the Install-Module cmdlet to install the module that contains the role capability.</span></span>
<span data-ttu-id="70103-110">PowerShell 角色功能定义在 Just Enough Administration (JEA) 终结点中可供用户使用的命令、应用程序等。</span><span class="sxs-lookup"><span data-stu-id="70103-110">PowerShell role capabilities define which commands, applications, and so on are available to a user at a Just Enough Administration (JEA) endpoint.</span></span> <span data-ttu-id="70103-111">角色功能由扩展名为“.psrc”的文件定义。</span><span class="sxs-lookup"><span data-stu-id="70103-111">Role capabilities are defined by files with a .psrc extension.</span></span>

- <span data-ttu-id="70103-112">Find-RoleCapability 可使用版本参数 MinimumVersion、RequiredVersion、AllVersions 进行筛选。</span><span class="sxs-lookup"><span data-stu-id="70103-112">Find-RoleCapability can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="70103-113">这些参数彼此排斥。</span><span class="sxs-lookup"><span data-stu-id="70103-113">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="70103-114">这些版本参数只允许具有单个模块名称，而不能具有任何通配符。</span><span class="sxs-lookup"><span data-stu-id="70103-114">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="70103-115">如果未指定 RequiredVersion 参数，Find-RoleCapability 将返回等于或高于指定的最低版本的最新版本的模块或最新版本的模块（若未指定最低版本）。</span><span class="sxs-lookup"><span data-stu-id="70103-115">If the RequiredVersion parameter is not specified, Find-RoleCapability returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="70103-116">如果指定了 RequiredVersion 参数，Find-RoleCapability 仅返回与指定版本完全匹配的模块。</span><span class="sxs-lookup"><span data-stu-id="70103-116">If the RequiredVersion parameter is specified, Find-RoleCapability only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="70103-117">Find-RoleCapability 可使用 -Tag 参数对模块元数据进行筛选</span><span class="sxs-lookup"><span data-stu-id="70103-117">Find-RoleCapability can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="70103-118">Find-RoleCapability 可使用 -Filter 参数对存储库特定搜索语言进行筛选。</span><span class="sxs-lookup"><span data-stu-id="70103-118">Find-RoleCapability can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="70103-119">Find-RoleCapability 可以从所有或少数已注册存储库中对模块进行筛选。</span><span class="sxs-lookup"><span data-stu-id="70103-119">Find-RoleCapability can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="70103-120">Cmdlet 语法</span><span class="sxs-lookup"><span data-stu-id="70103-120">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-RoleCapability -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="70103-121">Cmdlet 联机帮助参考</span><span class="sxs-lookup"><span data-stu-id="70103-121">Cmdlet online help reference</span></span>

[<span data-ttu-id="70103-122">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="70103-122">Find-RoleCapability</span></span>](http://go.microsoft.com/fwlink/?LinkId=718029)

## <a name="example-commands"></a><span data-ttu-id="70103-123">示例命令</span><span class="sxs-lookup"><span data-stu-id="70103-123">Example commands</span></span>
```powershell

# Find a specific role capability
Find-RoleCapability -Name Maintenance

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Maintenance                         1.5.0      RoleCapModule                       PrivatePSGallery

# Find multiple role capabilities
Find-RoleCapability -Name MyJeaRole, Maintenance

# Find all available role capabilities from all registered repositories
Find-RoleCapability

# Find available role capabilities from few registered repositories
Find-RoleCapability -Repository PSGallery,PrivatePSGallery

# Find all role capabilities in a specified repository
Find-RoleCapability -Repository PSGallery

# Find a role capability defined in a specific module
Find-RoleCapability -Name Maintenance -ModuleName RoleCapModule

# Find role capabilities from all versions of a module
Find-RoleCapability -ModuleName RoleCapModule -AllVersions

# Find role capabilities with module name and MinimumVersion.
Find-RoleCapability -ModuleName RoleCapModule -MinimumVersion 1.1

# Find role capabilities with module name and exact version
Find-RoleCapability -ModuleName RoleCapModule -RequiredVersion 1.4.0

# Find role capabilities defined modules with -Filter based search. -Filter searches in description and module names
Find-RoleCapability -Filter Cookbook
Find-RoleCapability -Filter RBAC

# Find all role capabilities with tags Azure or DSC in module metadata
Find-RoleCapability -Tag Azure, DSC

```

