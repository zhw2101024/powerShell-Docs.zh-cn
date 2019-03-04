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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854463"
---
# <a name="input-filter-parameters"></a><span data-ttu-id="479be-102">输入筛选参数</span><span class="sxs-lookup"><span data-stu-id="479be-102">Input Filter Parameters</span></span>

<span data-ttu-id="479be-103">Cmdlet 可以定义`Filter`， `Include`，和`Exclude`筛选会影响该 cmdlet 的输入对象的集合的参数。</span><span class="sxs-lookup"><span data-stu-id="479be-103">A cmdlet can define `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

<span data-ttu-id="479be-104">通常，由指定输入对象的集合`InputObject`， `Path`，或`Name`参数。</span><span class="sxs-lookup"><span data-stu-id="479be-104">Typically, the set of input objects is specified by an `InputObject`, `Path`, or `Name` parameter.</span></span> <span data-ttu-id="479be-105">例如，一个 cmdlet 可以具有`Path`接受多个路径使用通配符字符和每个路径指向输入对象的参数。</span><span class="sxs-lookup"><span data-stu-id="479be-105">For example, a cmdlet can have a `Path` parameter that accepts multiple paths by using wildcard characters, and each path points to an input object.</span></span> <span data-ttu-id="479be-106">一起使用， `Filter`， `Include`，和`Exclude`参数进一步限定 cmdlet 在每次调用它的工作方式的路径。</span><span class="sxs-lookup"><span data-stu-id="479be-106">Used together, the `Filter`, `Include`, and `Exclude` parameters further qualify the paths the cmdlet works on each time it is invoked.</span></span>

## <a name="include-and-exclude-parameters"></a><span data-ttu-id="479be-107">Include 和 Exclude 参数</span><span class="sxs-lookup"><span data-stu-id="479be-107">Include and Exclude Parameters</span></span>

<span data-ttu-id="479be-108">`Include`和`Exclude`参数标识要包含或排除从传递给该 cmdlet 的输入对象的集合的对象。</span><span class="sxs-lookup"><span data-stu-id="479be-108">The `Include` and `Exclude` parameters identify the objects that are included or excluded from the set of input objects passed to the cmdlet.</span></span> <span data-ttu-id="479be-109">可以在标准通配符语言中表示筛选器时，请使用这些参数。</span><span class="sxs-lookup"><span data-stu-id="479be-109">Use these parameters when the filter can be expressed in the standard wildcard language.</span></span> <span data-ttu-id="479be-110">(有关通配符的详细信息，请参阅[中的 Cmdlet 参数支持通配符](./supporting-wildcard-characters-in-cmdlet-parameters.md)。)`Include`参数包括其名称与包含筛选器匹配的所有对象。</span><span class="sxs-lookup"><span data-stu-id="479be-110">(For more information about wildcard characters, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).) The `Include` parameter includes all the objects whose names match the inclusion filter.</span></span> <span data-ttu-id="479be-111">`Exclude`参数不包括其名称的筛选器匹配的所有对象。</span><span class="sxs-lookup"><span data-stu-id="479be-111">The `Exclude` parameter excludes all the objects whose names match the filter.</span></span>

## <a name="filter-parameter"></a><span data-ttu-id="479be-112">筛选器参数</span><span class="sxs-lookup"><span data-stu-id="479be-112">Filter Parameter</span></span>

<span data-ttu-id="479be-113">`Filter`参数指定的标准通配符语言中未表示的筛选器。</span><span class="sxs-lookup"><span data-stu-id="479be-113">The `Filter` parameter specifies a filter that is not expressed in the standard wildcard language.</span></span> <span data-ttu-id="479be-114">例如，Active Directory 服务接口 (ADSI) 或 SQL 筛选器可能会传递给该 cmdlet 通过其`Filter`参数。</span><span class="sxs-lookup"><span data-stu-id="479be-114">For example, Active Directory Service Interfaces (ADSI) or SQL filters might be passed to the cmdlet through its `Filter` parameter.</span></span> <span data-ttu-id="479be-115">在 Windows PowerShell 提供 cmdlet，这些筛选器指定通过使用 cmdlet 来访问数据存储区的 Windows PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="479be-115">In the cmdlets provided by Windows PowerShell, these filters are specified by the Windows PowerShell providers that use the cmdlet to access a data store.</span></span> <span data-ttu-id="479be-116">通常，每个提供程序定义自己的筛选器。</span><span class="sxs-lookup"><span data-stu-id="479be-116">Each provider typically defines its own filter.</span></span>

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a><span data-ttu-id="479be-117">如果不指定了输入对象的任何组筛选</span><span class="sxs-lookup"><span data-stu-id="479be-117">Filtering If No Set of Input Objects Is Specified</span></span>

<span data-ttu-id="479be-118">如果指定的输入对象未设置，则这通常意味着要针对的所有对象进行筛选。</span><span class="sxs-lookup"><span data-stu-id="479be-118">If no set of input objects is specified, this typically means to filter against all objects.</span></span> <span data-ttu-id="479be-119">有关详细信息，请参阅[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)。</span><span class="sxs-lookup"><span data-stu-id="479be-119">For more information, see[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span></span>

## <a name="see-also"></a><span data-ttu-id="479be-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="479be-120">See Also</span></span>

[<span data-ttu-id="479be-121">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="479be-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)