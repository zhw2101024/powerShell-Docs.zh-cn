---
title: EnumerableExpansion 的 SelectionCondition for EntrySelectedBy 的 PropertyName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ae11924-0072-451e-bf70-c5ffb25dccc0
caps.latest.revision: 13
ms.openlocfilehash: 0c20512e660c8d2b61d063dbd7078b55b23efeb8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362316"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="893b9-102">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="893b9-102">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="893b9-103">指定触发条件的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="893b9-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="893b9-104">如果存在此属性，或者其计算结果为 `true`，则满足条件，并使用定义。</span><span class="sxs-lookup"><span data-stu-id="893b9-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="893b9-105">用于 EnumerableExpansion 的 SelectionCondition （Format） EntrySelectedBy 元素的配置元素（格式） DefaultSettings 元素（format） EnumerableExpansions 元素（format） EntrySelectedBy 元素EnumerableExpansion 的 EntrySelectedBy 的 SelectionCondition 的 EnumerableExpansion （格式） PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="893b9-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="893b9-106">语法</span><span class="sxs-lookup"><span data-stu-id="893b9-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="893b9-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="893b9-107">Attributes and Elements</span></span>

<span data-ttu-id="893b9-108">以下各节介绍了 `PropertyName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="893b9-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="893b9-109">属性</span><span class="sxs-lookup"><span data-stu-id="893b9-109">Attributes</span></span>

<span data-ttu-id="893b9-110">无。</span><span class="sxs-lookup"><span data-stu-id="893b9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="893b9-111">子元素</span><span class="sxs-lookup"><span data-stu-id="893b9-111">Child Elements</span></span>

<span data-ttu-id="893b9-112">无。</span><span class="sxs-lookup"><span data-stu-id="893b9-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="893b9-113">父元素</span><span class="sxs-lookup"><span data-stu-id="893b9-113">Parent Elements</span></span>

|<span data-ttu-id="893b9-114">元素</span><span class="sxs-lookup"><span data-stu-id="893b9-114">Element</span></span>|<span data-ttu-id="893b9-115">描述</span><span class="sxs-lookup"><span data-stu-id="893b9-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="893b9-116">EnumerableExpansion 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="893b9-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="893b9-117">定义扩展此定义的集合对象时必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="893b9-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="893b9-118">文本值</span><span class="sxs-lookup"><span data-stu-id="893b9-118">Text Value</span></span>

<span data-ttu-id="893b9-119">指定 .NET 属性名称。</span><span class="sxs-lookup"><span data-stu-id="893b9-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="893b9-120">备注</span><span class="sxs-lookup"><span data-stu-id="893b9-120">Remarks</span></span>

<span data-ttu-id="893b9-121">选择条件必须指定至少一个要计算的属性名称或脚本，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="893b9-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="893b9-122">有关如何使用选择条件的详细信息，请参阅为[数据显示定义条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="893b9-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="893b9-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="893b9-123">See Also</span></span>

[<span data-ttu-id="893b9-124">定义显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="893b9-124">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="893b9-125">EnumerableExpansion 的 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="893b9-125">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="893b9-126">EnumerableExpansion 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="893b9-126">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="893b9-127">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="893b9-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
