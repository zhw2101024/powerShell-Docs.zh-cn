---
title: EnumerableExpansion 的 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7af0b2-68e6-43c3-adcc-7c58007fced8
caps.latest.revision: 13
ms.openlocfilehash: 6f7c8d9af3c1c2fbda0208148b0088161701fdbe
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361986"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="c7c32-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="c7c32-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="c7c32-103">指定触发条件的 .NET 类型集。</span><span class="sxs-lookup"><span data-stu-id="c7c32-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="c7c32-104">如果此集中的任何类型存在，则满足条件。</span><span class="sxs-lookup"><span data-stu-id="c7c32-104">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="c7c32-105">用于 EnumerableExpansion 的 DefaultSettings 元素（format） EnumerableExpansions 元素（format） EnumerableExpansions 元素（format） EntrySelectedBy 元素EnumerableExpansion （Format） SelectionSetName 元素 for SelectionCondition for EntrySelectedBy for EnumerableExpansion （Format）</span><span class="sxs-lookup"><span data-stu-id="c7c32-105">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c7c32-106">语法</span><span class="sxs-lookup"><span data-stu-id="c7c32-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c7c32-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="c7c32-107">Attributes and Elements</span></span>

<span data-ttu-id="c7c32-108">以下各节介绍 `SelectionSetName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c7c32-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c7c32-109">属性</span><span class="sxs-lookup"><span data-stu-id="c7c32-109">Attributes</span></span>

<span data-ttu-id="c7c32-110">无。</span><span class="sxs-lookup"><span data-stu-id="c7c32-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c7c32-111">子元素</span><span class="sxs-lookup"><span data-stu-id="c7c32-111">Child Elements</span></span>

<span data-ttu-id="c7c32-112">无。</span><span class="sxs-lookup"><span data-stu-id="c7c32-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c7c32-113">父元素</span><span class="sxs-lookup"><span data-stu-id="c7c32-113">Parent Elements</span></span>

|<span data-ttu-id="c7c32-114">元素</span><span class="sxs-lookup"><span data-stu-id="c7c32-114">Element</span></span>|<span data-ttu-id="c7c32-115">描述</span><span class="sxs-lookup"><span data-stu-id="c7c32-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c7c32-116">EnumerableExpansion 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c7c32-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="c7c32-117">定义扩展此定义的集合对象时必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="c7c32-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c7c32-118">文本值</span><span class="sxs-lookup"><span data-stu-id="c7c32-118">Text Value</span></span>

<span data-ttu-id="c7c32-119">指定选择集的名称。</span><span class="sxs-lookup"><span data-stu-id="c7c32-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="c7c32-120">备注</span><span class="sxs-lookup"><span data-stu-id="c7c32-120">Remarks</span></span>

<span data-ttu-id="c7c32-121">选择条件可以指定选择集或 .NET 类型，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="c7c32-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="c7c32-122">有关如何使用选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="c7c32-122">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="c7c32-123">选择集是可由格式设置文件所定义的任何视图使用的常用 .NET 对象组。</span><span class="sxs-lookup"><span data-stu-id="c7c32-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="c7c32-124">有关创建和引用选项集的详细信息，请参阅[定义选择集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="c7c32-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c7c32-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c7c32-125">See Also</span></span>

[<span data-ttu-id="c7c32-126">定义选择集</span><span class="sxs-lookup"><span data-stu-id="c7c32-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="c7c32-127">EnumerableExpansion 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c7c32-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="c7c32-128">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="c7c32-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
