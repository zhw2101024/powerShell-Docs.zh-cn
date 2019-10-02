---
ms.date: 06/12/2017
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery
title: 筛选搜索结果
ms.openlocfilehash: 13270a310613a974e1588a9f56d443a936cfebb8
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328038"
---
# <a name="filtering-search-results"></a><span data-ttu-id="86287-103">筛选搜索结果</span><span class="sxs-lookup"><span data-stu-id="86287-103">Filtering search results</span></span>

<span data-ttu-id="86287-104">[“包”选项卡](https://www.powershellgallery.com/packages)显示 PowerShell 库中所有可用的包。</span><span class="sxs-lookup"><span data-stu-id="86287-104">The [Packages tab](https://www.powershellgallery.com/packages) displays all available packages in the PowerShell Gallery.</span></span>

<span data-ttu-id="86287-105">可通过多种方法筛选、排序和搜索这些包。</span><span class="sxs-lookup"><span data-stu-id="86287-105">There are several ways to filter, sort, and search the packages.</span></span>
<span data-ttu-id="86287-106">若要查看某个特定包的详细信息，请单击该包。</span><span class="sxs-lookup"><span data-stu-id="86287-106">To see more details about a particular package, click the package.</span></span>

## <a name="filter-by"></a><span data-ttu-id="86287-107">筛选依据</span><span class="sxs-lookup"><span data-stu-id="86287-107">Filter By</span></span>

<span data-ttu-id="86287-108">使用“筛选依据”下拉列表，用户可以按下列依据筛选结果：</span><span class="sxs-lookup"><span data-stu-id="86287-108">The drop-down under "Filter By" allows users to filter the results by:</span></span>
- <span data-ttu-id="86287-109">包括预发行版</span><span class="sxs-lookup"><span data-stu-id="86287-109">Include Prerelease</span></span>
- <span data-ttu-id="86287-110">仅稳定版</span><span class="sxs-lookup"><span data-stu-id="86287-110">Stable Only</span></span>

<span data-ttu-id="86287-111">若要了解“预发行版”和“稳定版”，请参阅 PowerShell 团队博客中的[在 PowerShellGet 和 PowerShell 库中添加的预发行版版本控制](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/)。</span><span class="sxs-lookup"><span data-stu-id="86287-111">For information about "Prerelease" and "Stable", see [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in the PowerShell Team Blog.</span></span>

<span data-ttu-id="86287-112">使用下拉列表下的复选框，用户可以按下列依据筛选结果：</span><span class="sxs-lookup"><span data-stu-id="86287-112">The checkboxes under the drop-down allow users to filter the results by:</span></span>
- <span data-ttu-id="86287-113">包类型</span><span class="sxs-lookup"><span data-stu-id="86287-113">Package Types</span></span>
  - <span data-ttu-id="86287-114">模块</span><span class="sxs-lookup"><span data-stu-id="86287-114">Module</span></span>
  - <span data-ttu-id="86287-115">脚本</span><span class="sxs-lookup"><span data-stu-id="86287-115">Script</span></span>
- <span data-ttu-id="86287-116">类别</span><span class="sxs-lookup"><span data-stu-id="86287-116">Categories</span></span>
  - <span data-ttu-id="86287-117">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="86287-117">Cmdlet</span></span>
  - <span data-ttu-id="86287-118">DSC 资源</span><span class="sxs-lookup"><span data-stu-id="86287-118">DSC Resource</span></span>
  - <span data-ttu-id="86287-119">功能</span><span class="sxs-lookup"><span data-stu-id="86287-119">Function</span></span>
  - <span data-ttu-id="86287-120">角色功能</span><span class="sxs-lookup"><span data-stu-id="86287-120">Role Capability</span></span>
  - <span data-ttu-id="86287-121">工作流</span><span class="sxs-lookup"><span data-stu-id="86287-121">Workflow</span></span>

<span data-ttu-id="86287-122">若要仅查看 PowerShell 库中的模块，请选中“包类型”中的“模块”。</span><span class="sxs-lookup"><span data-stu-id="86287-122">To see only modules in the PowerShell Gallery, check Module in the Package Types.</span></span>
<span data-ttu-id="86287-123">同样，若要仅查看 PowerShell 库中的脚本，请选中“包类型”中的“脚本”。</span><span class="sxs-lookup"><span data-stu-id="86287-123">Similarly, to see only scripts in the PowerShell Gallery, check Script in the Package Types.</span></span>

> [!NOTE]
> <span data-ttu-id="86287-124">筛选器为包含式。</span><span class="sxs-lookup"><span data-stu-id="86287-124">Filters are inclusive.</span></span>
> <span data-ttu-id="86287-125">例如：如果选中“Cmdlet”和/或“函数”，将显示包含 cmdlet 和函数的包。</span><span class="sxs-lookup"><span data-stu-id="86287-125">Example: A package containing both cmdlets and functions will appear if either Cmdlet or Function (or both) are checked.</span></span>
> <span data-ttu-id="86287-126">如果未选中任何一个，则不会显示包。</span><span class="sxs-lookup"><span data-stu-id="86287-126">If neither are selected, the package will not appear.</span></span>
> <span data-ttu-id="86287-127">同样，如果选择了所有类别，将仅显示包含这些类别之一的包。</span><span class="sxs-lookup"><span data-stu-id="86287-127">Similarly, if all categories are selected, only packages containing one of those categories will appear.</span></span>
> <span data-ttu-id="86287-128">不会显示不属于任何这些类别的包。 </span><span class="sxs-lookup"><span data-stu-id="86287-128">**Packages that do not belong to any of those categories will not appear.**</span></span>

## <a name="sort-by"></a><span data-ttu-id="86287-129">排序依据</span><span class="sxs-lookup"><span data-stu-id="86287-129">Sort By</span></span>

<span data-ttu-id="86287-130">使用“排序依据”下拉列表，用户可以按下列依据排序结果：</span><span class="sxs-lookup"><span data-stu-id="86287-130">The Sort By drop-down allows users to sort the results by:</span></span>
- <span data-ttu-id="86287-131">热门程度 - 热门程度取决于下载次数</span><span class="sxs-lookup"><span data-stu-id="86287-131">Popularity - Popularity is determined by Download Count</span></span>
- <span data-ttu-id="86287-132">A-Z - 按包名称的字母顺序排序</span><span class="sxs-lookup"><span data-stu-id="86287-132">A-Z - Alphabetically by package name</span></span>
- <span data-ttu-id="86287-133">最新 - 按发布日期顺序显示各包</span><span class="sxs-lookup"><span data-stu-id="86287-133">Recent - Packages appear in order of publish date</span></span>

## <a name="search-box"></a><span data-ttu-id="86287-134">搜索框</span><span class="sxs-lookup"><span data-stu-id="86287-134">Search Box</span></span>

<span data-ttu-id="86287-135">使用搜索框，用户可以通过关键字来搜索包。</span><span class="sxs-lookup"><span data-stu-id="86287-135">The Search Box allows users to search the packages on keywords.</span></span>
<span data-ttu-id="86287-136">有关详细信息，请参阅[库搜索语法](search-syntax.md)。</span><span class="sxs-lookup"><span data-stu-id="86287-136">For more information, see [Gallery Search Syntax](search-syntax.md).</span></span>
