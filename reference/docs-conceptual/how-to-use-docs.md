---
ms.date: 09/25/2019
keywords: powershell,cmdlet
title: 如何使用 PowerShell 文档
ms.openlocfilehash: 9e3d5828d6bdb4ef14701994f146354a041efaea
ms.sourcegitcommit: a80bb79b85deab8ae3c21de56d1ee432fdd92628
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72281652"
---
# <a name="how-to-use-the-powershell-documentation"></a><span data-ttu-id="486cb-103">如何使用 PowerShell 文档</span><span class="sxs-lookup"><span data-stu-id="486cb-103">How to use the PowerShell documentation</span></span>

<span data-ttu-id="486cb-104">欢迎使用 PowerShell 联机文档。</span><span class="sxs-lookup"><span data-stu-id="486cb-104">Welcome to the PowerShell online documentation.</span></span> <span data-ttu-id="486cb-105">此站点包含以下 PowerShell 版本的 cmdlet 参考：</span><span class="sxs-lookup"><span data-stu-id="486cb-105">This site contains cmdlet reference for the following versions of PowerShell:</span></span>

- <span data-ttu-id="486cb-106">PowerShell 7（预览版）</span><span class="sxs-lookup"><span data-stu-id="486cb-106">PowerShell 7 (preview)</span></span>
- <span data-ttu-id="486cb-107">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="486cb-107">PowerShell 6</span></span>
- <span data-ttu-id="486cb-108">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="486cb-108">PowerShell 5.1</span></span>
- <span data-ttu-id="486cb-109">PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="486cb-109">PowerShell 5.0</span></span>
- <span data-ttu-id="486cb-110">PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="486cb-110">PowerShell 4.0</span></span>
- <span data-ttu-id="486cb-111">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="486cb-111">PowerShell 3.0</span></span>

## <a name="selecting-your-version"></a><span data-ttu-id="486cb-112">选择你的版本</span><span class="sxs-lookup"><span data-stu-id="486cb-112">Selecting your version</span></span>

<span data-ttu-id="486cb-113">默认情况下，此站点显示最新版本的 PowerShell 的文档。</span><span class="sxs-lookup"><span data-stu-id="486cb-113">By default, this site displays documentation for the latest released version of PowerShell.</span></span> <span data-ttu-id="486cb-114">一些 cmdlet 在不同版本的 PowerShell 中的工作方式有所不同。</span><span class="sxs-lookup"><span data-stu-id="486cb-114">Some cmdlets work differently in various versions of PowerShell.</span></span> <span data-ttu-id="486cb-115">确保查看所使用的 PowerShell 版本的文档。</span><span class="sxs-lookup"><span data-stu-id="486cb-115">Be sure you are viewing the documentation for the version of PowerShell you are using.</span></span>

<span data-ttu-id="486cb-116">使用页面顶部的版本选取器来选择所需的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="486cb-116">Use the version picker at the top of the page to select the version of PowerShell you want.</span></span>

![版本选取器](images/how-to-use-docs/picker-vall.gif)

<span data-ttu-id="486cb-118">可以通过查看 `$PSversionTable.PSVersion` 值来验证所使用的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="486cb-118">You can verify the version of PowerShell you are using by inspecting the `$PSversionTable.PSVersion` value.</span></span> <span data-ttu-id="486cb-119">下面的示例演示 Windows PowerShell v5.1 的输出。</span><span class="sxs-lookup"><span data-stu-id="486cb-119">The following example shows the output for Windows PowerShell v5.1.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```

## <a name="searching-for-articles"></a><span data-ttu-id="486cb-120">搜索文章</span><span class="sxs-lookup"><span data-stu-id="486cb-120">Searching for articles</span></span>

<span data-ttu-id="486cb-121">有两种方法可以搜索 Docs 中的内容。最简单的方法是使用版本选取器下的筛选器框。</span><span class="sxs-lookup"><span data-stu-id="486cb-121">There are two ways to search for content in Docs. The simplest way is to use the filter box under the version selector.</span></span> <span data-ttu-id="486cb-122">只需输入文章标题中出现的字词即可。</span><span class="sxs-lookup"><span data-stu-id="486cb-122">Just enter a word that appears in the title of an article.</span></span> <span data-ttu-id="486cb-123">该页面显示匹配文章的列表。</span><span class="sxs-lookup"><span data-stu-id="486cb-123">The page displays a list of matching articles.</span></span> <span data-ttu-id="486cb-124">还可以从该列表中选择用于搜索整个站点的选项。</span><span class="sxs-lookup"><span data-stu-id="486cb-124">You can also select the option to search the entire site from that list.</span></span>

![筛选器框](images/how-to-use-docs/filter-search.gif)
