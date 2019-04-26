---
title: PropertyName 元素为 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ae11924-0072-451e-bf70-c5ffb25dccc0
caps.latest.revision: 13
ms.openlocfilehash: 0c20512e660c8d2b61d063dbd7078b55b23efeb8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064945"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="aefa8-102">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="aefa8-102">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="aefa8-103">指定触发条件的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="aefa8-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="aefa8-104">存在此属性时或当计算结果为`true`、 满足该条件，以及使用该定义。</span><span class="sxs-lookup"><span data-stu-id="aefa8-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="aefa8-105">用于为 EntrySelectedBy EnumerableExpansion （格式） SelectionCondition 元素的配置元素 （格式） DefaultSettings 元素 （格式） EnumerableExpansions 元素 （格式） EnumerableExpansion 元素 （格式） EntrySelectedBy 元素有关 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition EnumerableExpansion （格式） PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="aefa8-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="aefa8-106">语法</span><span class="sxs-lookup"><span data-stu-id="aefa8-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="aefa8-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="aefa8-107">Attributes and Elements</span></span>

<span data-ttu-id="aefa8-108">以下各节描述了特性、 子元素和父元素的`PropertyName`元素。</span><span class="sxs-lookup"><span data-stu-id="aefa8-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="aefa8-109">属性</span><span class="sxs-lookup"><span data-stu-id="aefa8-109">Attributes</span></span>

<span data-ttu-id="aefa8-110">无。</span><span class="sxs-lookup"><span data-stu-id="aefa8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="aefa8-111">子元素</span><span class="sxs-lookup"><span data-stu-id="aefa8-111">Child Elements</span></span>

<span data-ttu-id="aefa8-112">无。</span><span class="sxs-lookup"><span data-stu-id="aefa8-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="aefa8-113">父元素</span><span class="sxs-lookup"><span data-stu-id="aefa8-113">Parent Elements</span></span>

|<span data-ttu-id="aefa8-114">元素</span><span class="sxs-lookup"><span data-stu-id="aefa8-114">Element</span></span>|<span data-ttu-id="aefa8-115">说明</span><span class="sxs-lookup"><span data-stu-id="aefa8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aefa8-116">EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="aefa8-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="aefa8-117">定义要展开此定义的集合对象必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="aefa8-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="aefa8-118">文本值</span><span class="sxs-lookup"><span data-stu-id="aefa8-118">Text Value</span></span>

<span data-ttu-id="aefa8-119">指定.NET 属性名称。</span><span class="sxs-lookup"><span data-stu-id="aefa8-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="aefa8-120">备注</span><span class="sxs-lookup"><span data-stu-id="aefa8-120">Remarks</span></span>

<span data-ttu-id="aefa8-121">选择条件必须指定至少一个属性名称或脚本来评估，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="aefa8-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="aefa8-122">有关如何使用选择条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="aefa8-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aefa8-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aefa8-123">See Also</span></span>

[<span data-ttu-id="aefa8-124">定义条件的数据时显示</span><span class="sxs-lookup"><span data-stu-id="aefa8-124">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="aefa8-125">有关 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="aefa8-125">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="aefa8-126">EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="aefa8-126">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="aefa8-127">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="aefa8-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
