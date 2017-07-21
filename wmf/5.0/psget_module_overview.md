---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,安装程序"
ms.openlocfilehash: 2c7e718bc518b332cb4303ef73b1bf5c924ca471
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a><span data-ttu-id="088d5-102">使用 PowerShellGet 进行 PowerShell 模块发现、安装和盘存</span><span class="sxs-lookup"><span data-stu-id="088d5-102">PowerShell Module Discovery, Install and Inventory with PowerShellGet</span></span>
 
<span data-ttu-id="088d5-103">此版本的 WMF 中包括了 PowerShellGet：</span><span class="sxs-lookup"><span data-stu-id="088d5-103">PowerShellGet is included in this release of WMF:</span></span>
-   <span data-ttu-id="088d5-104">Find-Module 可以使用 -Tag 参数对模块元数据进行筛选</span><span class="sxs-lookup"><span data-stu-id="088d5-104">Find-Module can filter on module metadata with the -Tag parameter</span></span>
-   <span data-ttu-id="088d5-105">Find-Module 可以使用 -Filter 参数对存储库特定搜索语言进行筛选</span><span class="sxs-lookup"><span data-stu-id="088d5-105">Find-Module can filter on repository-specific search language with the -Filter parameter</span></span>
-   <span data-ttu-id="088d5-106">Find-Module 可以使用 -Command、-DscResource 和 -Includes 参数根据模块内容进行筛选</span><span class="sxs-lookup"><span data-stu-id="088d5-106">Find-Module can filter based on module contents with the -Command, -DscResource, and -Includes parameters</span></span>
-   <span data-ttu-id="088d5-107">Find-DscResource 可以发现存储库中的单个 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="088d5-107">Find-DscResource allows discovery of individual DSC resources in repositories</span></span>
-   <span data-ttu-id="088d5-108">支持使用 NuGet 从文件共享安装，且支持发布到文件共享</span><span class="sxs-lookup"><span data-stu-id="088d5-108">Support for installing from and publishing to file shares with NuGet</span></span>

## <a name="example-commands"></a><span data-ttu-id="088d5-109">示例命令</span><span class="sxs-lookup"><span data-stu-id="088d5-109">Example commands</span></span>
```powershell
\# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

\# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

\#Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

\# Find all modules with Dsc resources
Find-Module -Includes DscResource

\# Find all modules with cmdlets
Find-Module -Includes Cmdlet

\# Find all modules with functions
Find-Module -Includes Function

\# Find all DSC resources
Find-DscResource

\# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking

\# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

\# Find modules using -Filter parameter
\# Specified filter value is searched in Name and Description properties
Find-Module -Filter Cookbook -Repository PSGallery
Find-Module -Filter RBAC -Repository PSGallery
```

## <a name="new-features-in-powershellget"></a><span data-ttu-id="088d5-110">PowerShellGet 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="088d5-110">New features in PowerShellGet</span></span>
-   <span data-ttu-id="088d5-111">PowerShell 5.0 或更高版本上的并行版本支持</span><span class="sxs-lookup"><span data-stu-id="088d5-111">Side-by-side version support on Windows PowerShell 5.0 or newer</span></span>
-   <span data-ttu-id="088d5-112">模块依赖项安装支持</span><span class="sxs-lookup"><span data-stu-id="088d5-112">Module dependency installation support</span></span>
-   <span data-ttu-id="088d5-113">三个新的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="088d5-113">Three new cmdlets</span></span>
    -   <span data-ttu-id="088d5-114">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="088d5-114">Get-InstalledModule</span></span>
    -   <span data-ttu-id="088d5-115">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="088d5-115">Uninstall-Module</span></span>
    -   <span data-ttu-id="088d5-116">Save-Module</span><span class="sxs-lookup"><span data-stu-id="088d5-116">Save-Module</span></span>
    
