---
title: GroupBy （格式） 的 EntrySelectedBy SelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc2093a-dc54-42c4-ada3-c8d089ba1e8e
caps.latest.revision: 6
ms.openlocfilehash: a6738a7c4c934b2d6a16695a711f7c6c80afdd2d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855163"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="a62dd-102">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a62dd-102">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="a62dd-103">定义必须存在要使用的控件定义的条件。</span><span class="sxs-lookup"><span data-stu-id="a62dd-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="a62dd-104">定义如何显示一组新对象时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="a62dd-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="a62dd-105">GroupBy （格式） 的 GroupBy （格式） CustomEntry 元素 CustomControl CustomEntries 元素的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素CustomControl GroupBy （格式） 的 GroupBy （格式） 的 GroupBy （格式） 的 EntrySelectedBy SelectionCondition 元素 CustomEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="a62dd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a62dd-106">语法</span><span class="sxs-lookup"><span data-stu-id="a62dd-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a62dd-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="a62dd-107">Attributes and Elements</span></span>

<span data-ttu-id="a62dd-108">以下各节描述了特性、 子元素和父元素的`SelectionCondition`元素。</span><span class="sxs-lookup"><span data-stu-id="a62dd-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a62dd-109">特性</span><span class="sxs-lookup"><span data-stu-id="a62dd-109">Attributes</span></span>

<span data-ttu-id="a62dd-110">无。</span><span class="sxs-lookup"><span data-stu-id="a62dd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a62dd-111">子元素</span><span class="sxs-lookup"><span data-stu-id="a62dd-111">Child Elements</span></span>

|<span data-ttu-id="a62dd-112">元素</span><span class="sxs-lookup"><span data-stu-id="a62dd-112">Element</span></span>|<span data-ttu-id="a62dd-113">描述</span><span class="sxs-lookup"><span data-stu-id="a62dd-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a62dd-114">GroupBy （格式） 的 SelectionCondition PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="a62dd-114">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="a62dd-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="a62dd-115">Optional element.</span></span><br /><br /> <span data-ttu-id="a62dd-116">指定触发条件的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="a62dd-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="a62dd-117">GroupBy （格式） 的 SelectionCondition 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="a62dd-117">ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="a62dd-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="a62dd-118">Optional element.</span></span><br /><br /> <span data-ttu-id="a62dd-119">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="a62dd-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="a62dd-120">GroupBy （格式） 的 SelectionCondition SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="a62dd-120">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="a62dd-121">可选元素。</span><span class="sxs-lookup"><span data-stu-id="a62dd-121">Optional element.</span></span><br /><br /> <span data-ttu-id="a62dd-122">指定触发条件的.NET 类型集。</span><span class="sxs-lookup"><span data-stu-id="a62dd-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="a62dd-123">GroupBy （格式） 的 SelectionCondition 的 TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="a62dd-123">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="a62dd-124">可选元素。</span><span class="sxs-lookup"><span data-stu-id="a62dd-124">Optional element.</span></span><br /><br /> <span data-ttu-id="a62dd-125">指定触发条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="a62dd-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a62dd-126">父元素</span><span class="sxs-lookup"><span data-stu-id="a62dd-126">Parent Elements</span></span>

|<span data-ttu-id="a62dd-127">元素</span><span class="sxs-lookup"><span data-stu-id="a62dd-127">Element</span></span>|<span data-ttu-id="a62dd-128">描述</span><span class="sxs-lookup"><span data-stu-id="a62dd-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a62dd-129">GroupBy （格式） 的 CustomEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="a62dd-129">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="a62dd-130">定义使用此控件定义或要使用此定义中必须存在的条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="a62dd-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a62dd-131">备注</span><span class="sxs-lookup"><span data-stu-id="a62dd-131">Remarks</span></span>

<span data-ttu-id="a62dd-132">在定义的选择条件时，必须满足以下要求：</span><span class="sxs-lookup"><span data-stu-id="a62dd-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="a62dd-133">选择条件必须指定至少一个属性名或脚本块，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="a62dd-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="a62dd-134">选择条件可以指定任意数量的.NET 类型，或者选择设置，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="a62dd-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="a62dd-135">有关如何使用选择条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="a62dd-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a62dd-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a62dd-136">See Also</span></span>

[<span data-ttu-id="a62dd-137">属性名称的视图 （格式） 的 CustomControl SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="a62dd-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a62dd-138">为视图 （格式） 的 CustomControl SelectionCondition 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="a62dd-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a62dd-139">自定义控件的视图 （格式） 的 SelectionCondition SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="a62dd-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a62dd-140">GroupBy （格式） 的 SelectionCondition 的 TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="a62dd-140">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="a62dd-141">GroupBy （格式） 的 CustomEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="a62dd-141">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="a62dd-142">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="a62dd-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
