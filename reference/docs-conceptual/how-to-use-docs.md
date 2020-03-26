---
ms.date: 10/20/2019
keywords: powershell,cmdlet
title: 如何使用 PowerShell 文档
ms.openlocfilehash: 50b054ddc21d55946969414688306fc0d15a5adf
ms.sourcegitcommit: d36db3a1bc44aee6bc97422b557041c3aece4c67
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082836"
---
# <a name="how-to-use-the-powershell-documentation"></a><span data-ttu-id="fdbc8-103">如何使用 PowerShell 文档</span><span class="sxs-lookup"><span data-stu-id="fdbc8-103">How to use the PowerShell documentation</span></span>

<span data-ttu-id="fdbc8-104">欢迎使用 PowerShell 联机文档。</span><span class="sxs-lookup"><span data-stu-id="fdbc8-104">Welcome to the PowerShell online documentation.</span></span> <span data-ttu-id="fdbc8-105">此站点包含以下 PowerShell 版本的 cmdlet 参考：</span><span class="sxs-lookup"><span data-stu-id="fdbc8-105">This site contains cmdlet reference for the following versions of PowerShell:</span></span>

- <span data-ttu-id="fdbc8-106">PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="fdbc8-106">PowerShell 7</span></span>
- <span data-ttu-id="fdbc8-107">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="fdbc8-107">PowerShell 6</span></span>
- <span data-ttu-id="fdbc8-108">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="fdbc8-108">PowerShell 5.1</span></span>

## <a name="finding-articles-and-selecting-a-version"></a><span data-ttu-id="fdbc8-109">查找文章并选择版本</span><span class="sxs-lookup"><span data-stu-id="fdbc8-109">Finding articles and selecting a version</span></span>

<span data-ttu-id="fdbc8-110">有两种方法可以搜索 Docs 中的内容。最简单的方法是使用版本选取器下的筛选器框。</span><span class="sxs-lookup"><span data-stu-id="fdbc8-110">There are two ways to search for content in Docs. The simplest way is to use the filter box under the version selector.</span></span> <span data-ttu-id="fdbc8-111">只需输入文章标题中出现的字词即可。</span><span class="sxs-lookup"><span data-stu-id="fdbc8-111">Just enter a word that appears in the title of an article.</span></span> <span data-ttu-id="fdbc8-112">该页面显示匹配文章的列表。</span><span class="sxs-lookup"><span data-stu-id="fdbc8-112">The page displays a list of matching articles.</span></span> <span data-ttu-id="fdbc8-113">还可以从该列表中选择用于搜索整个站点的选项。</span><span class="sxs-lookup"><span data-stu-id="fdbc8-113">You can also select the option to search the entire site from that list.</span></span>

<span data-ttu-id="fdbc8-114">默认情况下，此站点显示最新版本的 PowerShell 的文档。</span><span class="sxs-lookup"><span data-stu-id="fdbc8-114">By default, this site displays documentation for the latest released version of PowerShell.</span></span> <span data-ttu-id="fdbc8-115">一些 cmdlet 在不同版本的 PowerShell 中的工作方式有所不同。</span><span class="sxs-lookup"><span data-stu-id="fdbc8-115">Some cmdlets work differently in various versions of PowerShell.</span></span> <span data-ttu-id="fdbc8-116">确保查看所使用的 PowerShell 版本的文档。</span><span class="sxs-lookup"><span data-stu-id="fdbc8-116">Be sure you are viewing the documentation for the version of PowerShell you are using.</span></span>

<span data-ttu-id="fdbc8-117">使用页面顶部的版本选取器来选择所需的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="fdbc8-117">Use the version picker at the top of the page to select the version of PowerShell you want.</span></span>

![版本选取器](media/how-to-use-docs/version-search.gif)

<span data-ttu-id="fdbc8-119">可以通过查看 `$PSversionTable.PSVersion` 值来验证所使用的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="fdbc8-119">You can verify the version of PowerShell you are using by inspecting the `$PSversionTable.PSVersion` value.</span></span> <span data-ttu-id="fdbc8-120">下面的示例演示 Windows PowerShell v5.1 的输出。</span><span class="sxs-lookup"><span data-stu-id="fdbc8-120">The following example shows the output for Windows PowerShell v5.1.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```
