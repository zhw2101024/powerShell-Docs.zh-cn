---
title: EnumerableExpansion （Format）的 EntrySelectedBy 的 SelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362006"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="049d7-102">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="049d7-102">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="049d7-103">定义扩展此定义的集合对象时必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="049d7-103">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="049d7-104">用于 EnumerableExpansion 的 SelectionCondition （Format） EntrySelectedBy 元素的配置元素（格式） DefaultSettings 元素（format） EnumerableExpansions 元素（format） EntrySelectedBy 元素EnumerableExpansion （格式）</span><span class="sxs-lookup"><span data-stu-id="049d7-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="049d7-105">语法</span><span class="sxs-lookup"><span data-stu-id="049d7-105">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="049d7-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="049d7-106">Attributes and Elements</span></span>

<span data-ttu-id="049d7-107">以下各节介绍了 `SelectionCondition` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="049d7-107">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="049d7-108">必须指定单个 `PropertyName` 或 `ScriptBlock` 元素。</span><span class="sxs-lookup"><span data-stu-id="049d7-108">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="049d7-109">`SelectionSetName` 和 `TypeName` 元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="049d7-109">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="049d7-110">可以指定任一元素中的一个。</span><span class="sxs-lookup"><span data-stu-id="049d7-110">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="049d7-111">特性</span><span class="sxs-lookup"><span data-stu-id="049d7-111">Attributes</span></span>

<span data-ttu-id="049d7-112">无。</span><span class="sxs-lookup"><span data-stu-id="049d7-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="049d7-113">子元素</span><span class="sxs-lookup"><span data-stu-id="049d7-113">Child Elements</span></span>

|<span data-ttu-id="049d7-114">元素</span><span class="sxs-lookup"><span data-stu-id="049d7-114">Element</span></span>|<span data-ttu-id="049d7-115">描述</span><span class="sxs-lookup"><span data-stu-id="049d7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="049d7-116">EnumerableExpansion 的 SelectionCondition for EntrySelectedBy 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="049d7-116">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="049d7-117">可选元素。</span><span class="sxs-lookup"><span data-stu-id="049d7-117">Optional element.</span></span><br /><br /> <span data-ttu-id="049d7-118">指定触发条件的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="049d7-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="049d7-119">EnumerableExpansion 的 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="049d7-119">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="049d7-120">可选元素。</span><span class="sxs-lookup"><span data-stu-id="049d7-120">Optional element.</span></span><br /><br /> <span data-ttu-id="049d7-121">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="049d7-121">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="049d7-122">EnumerableExpansion 的 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="049d7-122">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="049d7-123">可选元素。</span><span class="sxs-lookup"><span data-stu-id="049d7-123">Optional element.</span></span><br /><br /> <span data-ttu-id="049d7-124">指定触发条件的 .NET 类型集。</span><span class="sxs-lookup"><span data-stu-id="049d7-124">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="049d7-125">EnumerableExpansion 的 SelectionCondition for EntrySelectedBy 的 TypeName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="049d7-125">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="049d7-126">可选元素。</span><span class="sxs-lookup"><span data-stu-id="049d7-126">Optional element.</span></span><br /><br /> <span data-ttu-id="049d7-127">指定触发条件的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="049d7-127">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="049d7-128">父元素</span><span class="sxs-lookup"><span data-stu-id="049d7-128">Parent Elements</span></span>

|<span data-ttu-id="049d7-129">元素</span><span class="sxs-lookup"><span data-stu-id="049d7-129">Element</span></span>|<span data-ttu-id="049d7-130">描述</span><span class="sxs-lookup"><span data-stu-id="049d7-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="049d7-131">EnumerableExpansion 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="049d7-131">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="049d7-132">定义通过此定义扩展哪些 .NET 集合对象。</span><span class="sxs-lookup"><span data-stu-id="049d7-132">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="049d7-133">备注</span><span class="sxs-lookup"><span data-stu-id="049d7-133">Remarks</span></span>

<span data-ttu-id="049d7-134">每个定义都必须定义至少一个类型名称、选择集或选择条件。</span><span class="sxs-lookup"><span data-stu-id="049d7-134">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="049d7-135">定义选择条件时，需要满足以下要求：</span><span class="sxs-lookup"><span data-stu-id="049d7-135">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="049d7-136">选择条件必须指定至少一个属性名称或脚本块，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="049d7-136">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="049d7-137">选择条件可以指定任意数量的 .NET 类型或选择集，但是不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="049d7-137">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="049d7-138">有关如何使用选择条件的详细信息，请参阅[定义 Diplaying 数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="049d7-138">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="049d7-139">有关大视图的其他组件的详细信息，请参阅[宽视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="049d7-139">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="049d7-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="049d7-140">See Also</span></span>

[<span data-ttu-id="049d7-141">定义显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="049d7-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="049d7-142">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="049d7-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
