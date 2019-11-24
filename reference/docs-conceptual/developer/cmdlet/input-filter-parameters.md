---
title: 输入筛选器参数 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364386"
---
# <a name="input-filter-parameters"></a><span data-ttu-id="36a67-102">输入筛选参数</span><span class="sxs-lookup"><span data-stu-id="36a67-102">Input Filter Parameters</span></span>

<span data-ttu-id="36a67-103">Cmdlet 可定义 `Filter`、`Include`和 `Exclude` 参数，这些参数可筛选 cmdlet 影响的输入对象集。</span><span class="sxs-lookup"><span data-stu-id="36a67-103">A cmdlet can define `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

<span data-ttu-id="36a67-104">通常，输入对象集由 `InputObject`、`Path`或 `Name` 参数指定。</span><span class="sxs-lookup"><span data-stu-id="36a67-104">Typically, the set of input objects is specified by an `InputObject`, `Path`, or `Name` parameter.</span></span> <span data-ttu-id="36a67-105">例如，一个 cmdlet 可以有一个 `Path` 参数，该参数使用通配符接受多个路径，并且每个路径指向一个输入对象。</span><span class="sxs-lookup"><span data-stu-id="36a67-105">For example, a cmdlet can have a `Path` parameter that accepts multiple paths by using wildcard characters, and each path points to an input object.</span></span> <span data-ttu-id="36a67-106">一起使用时，`Filter`、`Include`和 `Exclude` 参数进一步限定了 cmdlet 在每次调用时所起的作用。</span><span class="sxs-lookup"><span data-stu-id="36a67-106">Used together, the `Filter`, `Include`, and `Exclude` parameters further qualify the paths the cmdlet works on each time it is invoked.</span></span>

## <a name="include-and-exclude-parameters"></a><span data-ttu-id="36a67-107">包括和排除参数</span><span class="sxs-lookup"><span data-stu-id="36a67-107">Include and Exclude Parameters</span></span>

<span data-ttu-id="36a67-108">`Include` 和 `Exclude` 参数标识传递到 cmdlet 的输入对象集中包含或排除的对象。</span><span class="sxs-lookup"><span data-stu-id="36a67-108">The `Include` and `Exclude` parameters identify the objects that are included or excluded from the set of input objects passed to the cmdlet.</span></span> <span data-ttu-id="36a67-109">如果筛选器可以用标准通配符语言表示，请使用这些参数。</span><span class="sxs-lookup"><span data-stu-id="36a67-109">Use these parameters when the filter can be expressed in the standard wildcard language.</span></span> <span data-ttu-id="36a67-110">（有关通配符的详细信息，请参阅[在 Cmdlet 参数中支持通配符](./supporting-wildcard-characters-in-cmdlet-parameters.md)。）`Include` 参数包含名称与包含筛选器匹配的所有对象。</span><span class="sxs-lookup"><span data-stu-id="36a67-110">(For more information about wildcard characters, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).) The `Include` parameter includes all the objects whose names match the inclusion filter.</span></span> <span data-ttu-id="36a67-111">`Exclude` 参数会排除名称与筛选器匹配的所有对象。</span><span class="sxs-lookup"><span data-stu-id="36a67-111">The `Exclude` parameter excludes all the objects whose names match the filter.</span></span>

## <a name="filter-parameter"></a><span data-ttu-id="36a67-112">筛选器参数</span><span class="sxs-lookup"><span data-stu-id="36a67-112">Filter Parameter</span></span>

<span data-ttu-id="36a67-113">`Filter` 参数指定了不以标准通配符语言表示的筛选器。</span><span class="sxs-lookup"><span data-stu-id="36a67-113">The `Filter` parameter specifies a filter that is not expressed in the standard wildcard language.</span></span> <span data-ttu-id="36a67-114">例如，Active Directory 服务接口（ADSI）或 SQL 筛选器可以通过其 `Filter` 参数传递给 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="36a67-114">For example, Active Directory Service Interfaces (ADSI) or SQL filters might be passed to the cmdlet through its `Filter` parameter.</span></span> <span data-ttu-id="36a67-115">在 Windows PowerShell 提供的 cmdlet 中，这些筛选器由使用 cmdlet 访问数据存储的 Windows PowerShell 提供程序指定。</span><span class="sxs-lookup"><span data-stu-id="36a67-115">In the cmdlets provided by Windows PowerShell, these filters are specified by the Windows PowerShell providers that use the cmdlet to access a data store.</span></span> <span data-ttu-id="36a67-116">每个提供程序通常定义自己的筛选器。</span><span class="sxs-lookup"><span data-stu-id="36a67-116">Each provider typically defines its own filter.</span></span>

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a><span data-ttu-id="36a67-117">如果未指定任何输入对象集，则进行筛选</span><span class="sxs-lookup"><span data-stu-id="36a67-117">Filtering If No Set of Input Objects Is Specified</span></span>

<span data-ttu-id="36a67-118">如果未指定任何输入对象集，这通常意味着要针对所有对象进行筛选。</span><span class="sxs-lookup"><span data-stu-id="36a67-118">If no set of input objects is specified, this typically means to filter against all objects.</span></span> <span data-ttu-id="36a67-119">有关详细信息，请参阅[获取进程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)。</span><span class="sxs-lookup"><span data-stu-id="36a67-119">For more information, see[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span></span>

## <a name="see-also"></a><span data-ttu-id="36a67-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="36a67-120">See Also</span></span>

[<span data-ttu-id="36a67-121">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="36a67-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)