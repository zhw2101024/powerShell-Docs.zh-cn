---
title: 有关 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7af0b2-68e6-43c3-adcc-7c58007fced8
caps.latest.revision: 13
ms.openlocfilehash: 6f7c8d9af3c1c2fbda0208148b0088161701fdbe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063854"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="dee2c-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="dee2c-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="dee2c-103">指定.NET 类型的触发器条件的集。</span><span class="sxs-lookup"><span data-stu-id="dee2c-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="dee2c-104">当存在任何此集中的类型时，是满足的条件。</span><span class="sxs-lookup"><span data-stu-id="dee2c-104">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="dee2c-105">用于为 EntrySelectedBy EnumerableExpansion （格式） SelectionCondition 元素的配置元素 DefaultSettings 元素 （格式） EnumerableExpansions 元素 （格式） EnumerableExpansions 元素 （格式） EntrySelectedBy 元素有关 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition EnumerableExpansion （格式） SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="dee2c-105">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dee2c-106">语法</span><span class="sxs-lookup"><span data-stu-id="dee2c-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dee2c-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="dee2c-107">Attributes and Elements</span></span>

<span data-ttu-id="dee2c-108">以下各节描述了特性、 子元素和父元素的`SelectionSetName`元素。</span><span class="sxs-lookup"><span data-stu-id="dee2c-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dee2c-109">属性</span><span class="sxs-lookup"><span data-stu-id="dee2c-109">Attributes</span></span>

<span data-ttu-id="dee2c-110">无。</span><span class="sxs-lookup"><span data-stu-id="dee2c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dee2c-111">子元素</span><span class="sxs-lookup"><span data-stu-id="dee2c-111">Child Elements</span></span>

<span data-ttu-id="dee2c-112">无。</span><span class="sxs-lookup"><span data-stu-id="dee2c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dee2c-113">父元素</span><span class="sxs-lookup"><span data-stu-id="dee2c-113">Parent Elements</span></span>

|<span data-ttu-id="dee2c-114">元素</span><span class="sxs-lookup"><span data-stu-id="dee2c-114">Element</span></span>|<span data-ttu-id="dee2c-115">说明</span><span class="sxs-lookup"><span data-stu-id="dee2c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dee2c-116">EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="dee2c-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="dee2c-117">定义要展开此定义的集合对象必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="dee2c-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="dee2c-118">文本值</span><span class="sxs-lookup"><span data-stu-id="dee2c-118">Text Value</span></span>

<span data-ttu-id="dee2c-119">指定所选内容集的名称。</span><span class="sxs-lookup"><span data-stu-id="dee2c-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="dee2c-120">备注</span><span class="sxs-lookup"><span data-stu-id="dee2c-120">Remarks</span></span>

<span data-ttu-id="dee2c-121">选择条件可以指定所选内容集或.NET 类型，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="dee2c-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="dee2c-122">有关如何使用选择条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="dee2c-122">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="dee2c-123">所选内容集是常见的可以使用的格式设置文件定义任何视图的.NET 对象分组。</span><span class="sxs-lookup"><span data-stu-id="dee2c-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="dee2c-124">有关创建和引用所选内容集的详细信息，请参阅[定义所选内容设置](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="dee2c-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dee2c-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dee2c-125">See Also</span></span>

[<span data-ttu-id="dee2c-126">定义的选项集</span><span class="sxs-lookup"><span data-stu-id="dee2c-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="dee2c-127">EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="dee2c-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="dee2c-128">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="dee2c-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
