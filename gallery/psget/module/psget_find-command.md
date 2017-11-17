---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "库,powershell,cmdlet,psget"
title: Find-Command
ms.openlocfilehash: f867f12b1c6efad30a04581c6f36c5a77a2fb2ae
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="find-command"></a><span data-ttu-id="b2483-103">Find-Command</span><span class="sxs-lookup"><span data-stu-id="b2483-103">Find-Command</span></span>

<span data-ttu-id="b2483-104">查找模块中的 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="b2483-104">Finds PowerShell commands in modules.</span></span>

## <a name="description"></a><span data-ttu-id="b2483-105">说明</span><span class="sxs-lookup"><span data-stu-id="b2483-105">Description</span></span>
<span data-ttu-id="b2483-106">Find-Command cmdlet 会查找 cmdlet、别名、函数和工作流等 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="b2483-106">The Find-Command cmdlet finds PowerShell commands such as cmdlets, aliases, functions, and workflows.</span></span> <span data-ttu-id="b2483-107">Find-Command 搜索已注册存储库中的模块。</span><span class="sxs-lookup"><span data-stu-id="b2483-107">Find-Command searches modules in registered repositories.</span></span>
<span data-ttu-id="b2483-108">对于此 cmdlet 找到的每个命令，将返回一个 PSGetCommandInfo 对象。</span><span class="sxs-lookup"><span data-stu-id="b2483-108">For each command that this cmdlet finds, it returns a PSGetCommandInfo object.</span></span> <span data-ttu-id="b2483-109">可将 PSGetCommandInfo 对象传递给 Install-Module cmdlet 以安装包含此命令的模块。</span><span class="sxs-lookup"><span data-stu-id="b2483-109">You can pass a PSGetCommandInfo object to the Install-Module cmdlet to install the module that contains the command.</span></span>

- <span data-ttu-id="b2483-110">Find-Command 可使用版本参数 MinimumVersion、RequiredVersion、AllVersions 进行筛选。</span><span class="sxs-lookup"><span data-stu-id="b2483-110">Find-Command can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="b2483-111">这些参数彼此排斥。</span><span class="sxs-lookup"><span data-stu-id="b2483-111">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="b2483-112">这些版本参数只允许具有单个模块名称，而不能具有任何通配符。</span><span class="sxs-lookup"><span data-stu-id="b2483-112">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="b2483-113">如果未指定 RequiredVersion 参数，Find-Command 将返回等于或高于指定的最低版本的最新版本的模块或最新版本的模块（若未指定最低版本）。</span><span class="sxs-lookup"><span data-stu-id="b2483-113">If the RequiredVersion parameter is not specified, Find-Command returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="b2483-114">如果指定了 RequiredVersion 参数，Find-Command 仅返回与指定版本完全匹配的模块。</span><span class="sxs-lookup"><span data-stu-id="b2483-114">If the RequiredVersion parameter is specified, Find-Command only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="b2483-115">Find-Command 可使用 -Tag 参数对模块元数据进行筛选</span><span class="sxs-lookup"><span data-stu-id="b2483-115">Find-Command can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="b2483-116">Find-Command 可使用 -Filter 参数对存储库特定搜索语言进行筛选。</span><span class="sxs-lookup"><span data-stu-id="b2483-116">Find-Command can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="b2483-117">Find-Command 可从所有或少数的已注册的存储库中对模块进行筛选。</span><span class="sxs-lookup"><span data-stu-id="b2483-117">Find-Command can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="b2483-118">Cmdlet 语法</span><span class="sxs-lookup"><span data-stu-id="b2483-118">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-Command -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="b2483-119">Cmdlet 联机帮助参考</span><span class="sxs-lookup"><span data-stu-id="b2483-119">Cmdlet online help reference</span></span>

[<span data-ttu-id="b2483-120">Find-Command</span><span class="sxs-lookup"><span data-stu-id="b2483-120">Find-Command</span></span>](http://go.microsoft.com/fwlink/?LinkId=733636)

## <a name="example-commands"></a><span data-ttu-id="b2483-121">示例命令</span><span class="sxs-lookup"><span data-stu-id="b2483-121">Example commands</span></span>
```powershell

# Find a specific command
Find-Command -Name Get-ScriptAnalyzerRule

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Get-ScriptAnalyzerRule              1.5.0      PSScriptAnalyzer                    PSGallery

# Find multiple commands
Find-Command -Name Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

# Find all available commands from all registered repositories
Find-Command

# Find available commands from few registered repositories
Find-Command -Repository PSGallery,PrivatePSGallery

# Find all commands in a specified repository
Find-Command -Repository PSGallery

# Find a command defined in a specific module
Find-Command -Name Get-ScriptAnalyzerRule -Module PSScriptAnalyzer

# Find commands from all versions of a module
Find-Command -ModuleName PSReadline -AllVersions

# Find commands with module name and MinimumVersion.
Find-Command -ModuleName PSReadline -MinimumVersion 1.1

# Find commands with module name and exact version
Find-Command -ModuleName AzureRM -RequiredVersion 1.4.0

# Find commands defined modules with -Filter based search. -Filter searches in description and module names
Find-Command -Filter Cookbook
Find-Command -Filter RBAC

# Find all commands with tags Azure or DSC in module metadata
Find-Command -Tag Azure, DSC

```

