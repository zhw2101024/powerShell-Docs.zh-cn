---
title: EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858283"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="a349a-102">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="a349a-102">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="a349a-103">定义要展开此定义的集合对象必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="a349a-103">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="a349a-104">用于为 EntrySelectedBy EnumerableExpansion （格式） SelectionCondition 元素的配置元素 （格式） DefaultSettings 元素 （格式） EnumerableExpansions 元素 （格式） EnumerableExpansion 元素 （格式） EntrySelectedBy 元素EnumerableExpansion （格式）</span><span class="sxs-lookup"><span data-stu-id="a349a-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a349a-105">语法</span><span class="sxs-lookup"><span data-stu-id="a349a-105">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a349a-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="a349a-106">Attributes and Elements</span></span>

<span data-ttu-id="a349a-107">以下各节描述了特性、 子元素和父元素的`SelectionCondition`元素。</span><span class="sxs-lookup"><span data-stu-id="a349a-107">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="a349a-108">必须指定单个`PropertyName`或`ScriptBlock`元素。</span><span class="sxs-lookup"><span data-stu-id="a349a-108">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="a349a-109">`SelectionSetName`和`TypeName`元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="a349a-109">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="a349a-110">您可以指定一个其中一个元素。</span><span class="sxs-lookup"><span data-stu-id="a349a-110">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a349a-111">特性</span><span class="sxs-lookup"><span data-stu-id="a349a-111">Attributes</span></span>

<span data-ttu-id="a349a-112">无。</span><span class="sxs-lookup"><span data-stu-id="a349a-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a349a-113">子元素</span><span class="sxs-lookup"><span data-stu-id="a349a-113">Child Elements</span></span>

|<span data-ttu-id="a349a-114">元素</span><span class="sxs-lookup"><span data-stu-id="a349a-114">Element</span></span>|<span data-ttu-id="a349a-115">描述</span><span class="sxs-lookup"><span data-stu-id="a349a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a349a-116">有关 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="a349a-116">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="a349a-117">可选元素。</span><span class="sxs-lookup"><span data-stu-id="a349a-117">Optional element.</span></span><br /><br /> <span data-ttu-id="a349a-118">指定触发条件的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="a349a-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="a349a-119">有关 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="a349a-119">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="a349a-120">可选元素。</span><span class="sxs-lookup"><span data-stu-id="a349a-120">Optional element.</span></span><br /><br /> <span data-ttu-id="a349a-121">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="a349a-121">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="a349a-122">有关 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="a349a-122">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="a349a-123">可选元素。</span><span class="sxs-lookup"><span data-stu-id="a349a-123">Optional element.</span></span><br /><br /> <span data-ttu-id="a349a-124">指定触发条件的.NET 类型集。</span><span class="sxs-lookup"><span data-stu-id="a349a-124">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="a349a-125">有关 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 的 TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="a349a-125">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="a349a-126">可选元素。</span><span class="sxs-lookup"><span data-stu-id="a349a-126">Optional element.</span></span><br /><br /> <span data-ttu-id="a349a-127">指定触发条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="a349a-127">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a349a-128">父元素</span><span class="sxs-lookup"><span data-stu-id="a349a-128">Parent Elements</span></span>

|<span data-ttu-id="a349a-129">元素</span><span class="sxs-lookup"><span data-stu-id="a349a-129">Element</span></span>|<span data-ttu-id="a349a-130">描述</span><span class="sxs-lookup"><span data-stu-id="a349a-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a349a-131">EnumerableExpansion （格式） 的 EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="a349a-131">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="a349a-132">定义此定义的扩展的.NET 集合对象。</span><span class="sxs-lookup"><span data-stu-id="a349a-132">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a349a-133">备注</span><span class="sxs-lookup"><span data-stu-id="a349a-133">Remarks</span></span>

<span data-ttu-id="a349a-134">每个定义必须至少一个类型名称、 选择集或定义的选择条件。</span><span class="sxs-lookup"><span data-stu-id="a349a-134">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="a349a-135">在定义的选择条件时，必须满足以下要求：</span><span class="sxs-lookup"><span data-stu-id="a349a-135">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="a349a-136">选择条件必须指定至少一个属性名或脚本块，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="a349a-136">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="a349a-137">选择条件可以指定任意数量的.NET 类型，或者选择设置，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="a349a-137">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="a349a-138">有关如何使用选择条件的详细信息，请参阅[Diplaying 数据定义条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="a349a-138">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="a349a-139">有关较宽的视图的其他组件的详细信息，请参阅[宽视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="a349a-139">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a349a-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a349a-140">See Also</span></span>

[<span data-ttu-id="a349a-141">定义何时显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="a349a-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="a349a-142">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="a349a-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
