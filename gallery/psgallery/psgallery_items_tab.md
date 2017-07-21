---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: "库,powershell,cmdlet,psgallery"
title: psgallery_items_tab
ms.openlocfilehash: 8424c4729436a78fec3fdbb405591fcd3c6bc6a6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
<a name="items-tab"></a><span data-ttu-id="ef09a-103">“项”选项卡</span><span class="sxs-lookup"><span data-stu-id="ef09a-103">Items Tab</span></span>
==========

<span data-ttu-id="ef09a-104">“项”选项卡显示 PowerShell 库中的所有可用项。</span><span class="sxs-lookup"><span data-stu-id="ef09a-104">The Items Tab displays all available items in the PowerShell Gallery.</span></span>

<span data-ttu-id="ef09a-105">若要仅查看 PowerShell 库中的模块，请在“项”选项卡下拉框中单击“模块”。</span><span class="sxs-lookup"><span data-stu-id="ef09a-105">To see only Modules in the PowerShell Gallery, click Modules in the Items Tab drop down.</span></span>  <span data-ttu-id="ef09a-106">同样，若要仅查看 PowerShell 库中的脚本，请在“项”选项卡下拉框中单击“脚本”。</span><span class="sxs-lookup"><span data-stu-id="ef09a-106">Similarly, to see only Scripts in the PowerShell Gallery, click Scripts in the Items Tab drop down.</span></span>  

<span data-ttu-id="ef09a-107">若要查看某个特定项的详细信息，请单击该项。</span><span class="sxs-lookup"><span data-stu-id="ef09a-107">To see more details about a particular item, click the item.</span></span>

<span data-ttu-id="ef09a-108">对项进行排序的几种方法：</span><span class="sxs-lookup"><span data-stu-id="ef09a-108">There are several ways to sort the items:</span></span>

##<a name="filter-by"></a><span data-ttu-id="ef09a-109">筛选依据##</span><span class="sxs-lookup"><span data-stu-id="ef09a-109">Filter By##</span></span>
<span data-ttu-id="ef09a-110">“筛选依据”部分允许用户根据以下内容筛选结果：</span><span class="sxs-lookup"><span data-stu-id="ef09a-110">The Filter By section allows users to filter the results by:</span></span>
* <span data-ttu-id="ef09a-111">项类型：</span><span class="sxs-lookup"><span data-stu-id="ef09a-111">Item Type:</span></span>
    * <span data-ttu-id="ef09a-112">模块</span><span class="sxs-lookup"><span data-stu-id="ef09a-112">Modules</span></span>
    * <span data-ttu-id="ef09a-113">脚本</span><span class="sxs-lookup"><span data-stu-id="ef09a-113">Scripts</span></span>
* <span data-ttu-id="ef09a-114">类别：</span><span class="sxs-lookup"><span data-stu-id="ef09a-114">Category:</span></span>
    * <span data-ttu-id="ef09a-115">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ef09a-115">Cmdlet</span></span>
    * <span data-ttu-id="ef09a-116">DSC 资源</span><span class="sxs-lookup"><span data-stu-id="ef09a-116">DSC Resource</span></span>
    * <span data-ttu-id="ef09a-117">功能</span><span class="sxs-lookup"><span data-stu-id="ef09a-117">Function</span></span>
    * <span data-ttu-id="ef09a-118">工作流</span><span class="sxs-lookup"><span data-stu-id="ef09a-118">Workflow</span></span>

<span data-ttu-id="ef09a-119">注意：包含筛选器。</span><span class="sxs-lookup"><span data-stu-id="ef09a-119">Note: Filters are inclusive.</span></span>  
<span data-ttu-id="ef09a-120">示例：如果选中 Cmdlet 或 Function（或两者），将显示包含 Cmdlet 和 Function 二者的项。</span><span class="sxs-lookup"><span data-stu-id="ef09a-120">Example: An item containing both Cmdlets and Functions will appear if either Cmdlet or Function (or both) are checked.</span></span>  <span data-ttu-id="ef09a-121">如果未选中任何一个，则不会显示项。</span><span class="sxs-lookup"><span data-stu-id="ef09a-121">If neither are selected, the item will not appear.</span></span>  
<span data-ttu-id="ef09a-122">同样，如果选择了所有类别，将仅显示包含这些类别之一的项。</span><span class="sxs-lookup"><span data-stu-id="ef09a-122">Similarly, if all categories are selected, only items containing one of those categories will appear.</span></span> <span data-ttu-id="ef09a-123">**不会显示不属于任何这些类别的项。**</span><span class="sxs-lookup"><span data-stu-id="ef09a-123">**Items that do not belong to any of those categories will not appear.**</span></span>

##<a name="sort-by"></a><span data-ttu-id="ef09a-124">排序依据##</span><span class="sxs-lookup"><span data-stu-id="ef09a-124">Sort By##</span></span> 
<span data-ttu-id="ef09a-125">“排序依据”下拉框允许用户根据以下内容筛选结果：</span><span class="sxs-lookup"><span data-stu-id="ef09a-125">The Sort By drop down allows users to sort the results by:</span></span>
* <span data-ttu-id="ef09a-126">热门程度 - 热门程度取决于下载计数。</span><span class="sxs-lookup"><span data-stu-id="ef09a-126">Popularity - Popularity is determined by Download Count.</span></span>
* <span data-ttu-id="ef09a-127">A-Z - 按项名称的字母顺序排序。</span><span class="sxs-lookup"><span data-stu-id="ef09a-127">A-Z - Alphabetically by item name.</span></span>
* <span data-ttu-id="ef09a-128">最近 - 按发布日期的顺序显示项。</span><span class="sxs-lookup"><span data-stu-id="ef09a-128">Recent - Items appear in order of publish date.</span></span>


##<a name="search-box"></a><span data-ttu-id="ef09a-129">搜索框##</span><span class="sxs-lookup"><span data-stu-id="ef09a-129">Search Box##</span></span>
<span data-ttu-id="ef09a-130">搜索框允许用户通过关键字来搜索项。</span><span class="sxs-lookup"><span data-stu-id="ef09a-130">The Search Box allows users to search the items on keywords.</span></span>  
<span data-ttu-id="ef09a-131">有关详细信息，请参阅[搜索语法](./psgallery_search_syntax.md)。</span><span class="sxs-lookup"><span data-stu-id="ef09a-131">See [Search Syntax](./psgallery_search_syntax.md) for more details.</span></span>

