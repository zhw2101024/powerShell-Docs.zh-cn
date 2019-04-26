---
title: 有关 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 的脚本块元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4126b799-c43d-4175-8513-6d761c65437e
caps.latest.revision: 9
ms.openlocfilehash: a51d8d22fa8b0c7f303a5e8f37edcc5e57724063
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064367"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="a85a6-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="a85a6-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="a85a6-103">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="a85a6-103">Specifies the script that triggers the condition.</span></span>

<span data-ttu-id="a85a6-104">用于为 EntrySelectedBy EnumerableExpansion （格式） SelectionCondition 元素的配置元素 （格式） DefaultSettings 元素 （格式） EnumerableExpansions 元素 （格式） EnumerableExpansion 元素 （格式） EntrySelectedBy 元素有关 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition EnumerableExpansion （格式） 脚本块元素</span><span class="sxs-lookup"><span data-stu-id="a85a6-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a85a6-105">语法</span><span class="sxs-lookup"><span data-stu-id="a85a6-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a85a6-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="a85a6-106">Attributes and Elements</span></span>

<span data-ttu-id="a85a6-107">以下各节描述了特性、 子元素和父元素的`ScriptBlock`元素。</span><span class="sxs-lookup"><span data-stu-id="a85a6-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a85a6-108">属性</span><span class="sxs-lookup"><span data-stu-id="a85a6-108">Attributes</span></span>

<span data-ttu-id="a85a6-109">无。</span><span class="sxs-lookup"><span data-stu-id="a85a6-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a85a6-110">子元素</span><span class="sxs-lookup"><span data-stu-id="a85a6-110">Child Elements</span></span>

<span data-ttu-id="a85a6-111">无。</span><span class="sxs-lookup"><span data-stu-id="a85a6-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a85a6-112">父元素</span><span class="sxs-lookup"><span data-stu-id="a85a6-112">Parent Elements</span></span>

|<span data-ttu-id="a85a6-113">元素</span><span class="sxs-lookup"><span data-stu-id="a85a6-113">Element</span></span>|<span data-ttu-id="a85a6-114">说明</span><span class="sxs-lookup"><span data-stu-id="a85a6-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a85a6-115">EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="a85a6-115">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="a85a6-116">定义要展开此定义的集合对象必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="a85a6-116">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a85a6-117">文本值</span><span class="sxs-lookup"><span data-stu-id="a85a6-117">Text Value</span></span>

<span data-ttu-id="a85a6-118">指定计算的脚本。</span><span class="sxs-lookup"><span data-stu-id="a85a6-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="a85a6-119">备注</span><span class="sxs-lookup"><span data-stu-id="a85a6-119">Remarks</span></span>

<span data-ttu-id="a85a6-120">选择条件必须指定至少一个脚本或属性名称，若要评估，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="a85a6-120">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="a85a6-121">有关如何使用选择条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="a85a6-121">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a85a6-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a85a6-122">See Also</span></span>

[<span data-ttu-id="a85a6-123">定义何时显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="a85a6-123">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="a85a6-124">有关 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="a85a6-124">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="a85a6-125">EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="a85a6-125">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="a85a6-126">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="a85a6-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
