---
title: CustomControl （格式） 的 EntrySelectedBy SelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075743"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a><span data-ttu-id="7eb4d-102">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7eb4d-102">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>

<span data-ttu-id="7eb4d-103">定义必须存在要使用的控件定义的条件。</span><span class="sxs-lookup"><span data-stu-id="7eb4d-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="7eb4d-104">定义自定义控件视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="7eb4d-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="7eb4d-105">视图 （格式） 的视图 （格式） 的视图 (CustomControl CustomEntries CustomEntry 元素 CustomControl CustomEntries 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素格式） 的视图 （格式） 的视图 （格式） 的视图 （格式） 的 CustomControl EntrySelectedBy SelectionCondition 元素 CustomControl CustomEntry EntrySelectedBy 元素 CustomControl CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="7eb4d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7eb4d-106">语法</span><span class="sxs-lookup"><span data-stu-id="7eb4d-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7eb4d-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="7eb4d-107">Attributes and Elements</span></span>

<span data-ttu-id="7eb4d-108">以下各节描述了特性、 子元素和父元素的`SelectionCondition`元素。</span><span class="sxs-lookup"><span data-stu-id="7eb4d-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7eb4d-109">属性</span><span class="sxs-lookup"><span data-stu-id="7eb4d-109">Attributes</span></span>

<span data-ttu-id="7eb4d-110">无。</span><span class="sxs-lookup"><span data-stu-id="7eb4d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7eb4d-111">子元素</span><span class="sxs-lookup"><span data-stu-id="7eb4d-111">Child Elements</span></span>

|<span data-ttu-id="7eb4d-112">元素</span><span class="sxs-lookup"><span data-stu-id="7eb4d-112">Element</span></span>|<span data-ttu-id="7eb4d-113">说明</span><span class="sxs-lookup"><span data-stu-id="7eb4d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7eb4d-114">属性名称的视图 （格式） 的 CustomControl SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="7eb4d-114">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="7eb4d-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="7eb4d-115">Optional element.</span></span><br /><br /> <span data-ttu-id="7eb4d-116">指定触发条件的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="7eb4d-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="7eb4d-117">为视图 （格式） 的 CustomControl SelectionCondition 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="7eb4d-117">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="7eb4d-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="7eb4d-118">Optional element.</span></span><br /><br /> <span data-ttu-id="7eb4d-119">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="7eb4d-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="7eb4d-120">自定义控件的视图 （格式） 的 SelectionCondition SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="7eb4d-120">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="7eb4d-121">可选元素。</span><span class="sxs-lookup"><span data-stu-id="7eb4d-121">Optional element.</span></span><br /><br /> <span data-ttu-id="7eb4d-122">指定触发条件的.NET 类型集。</span><span class="sxs-lookup"><span data-stu-id="7eb4d-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="7eb4d-123">为视图 （格式） 的 CustomControl SelectionCondition 的 TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="7eb4d-123">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="7eb4d-124">可选元素。</span><span class="sxs-lookup"><span data-stu-id="7eb4d-124">Optional element.</span></span><br /><br /> <span data-ttu-id="7eb4d-125">指定触发条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="7eb4d-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7eb4d-126">父元素</span><span class="sxs-lookup"><span data-stu-id="7eb4d-126">Parent Elements</span></span>

|<span data-ttu-id="7eb4d-127">元素</span><span class="sxs-lookup"><span data-stu-id="7eb4d-127">Element</span></span>|<span data-ttu-id="7eb4d-128">说明</span><span class="sxs-lookup"><span data-stu-id="7eb4d-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7eb4d-129">为视图 （格式） 的 CustomControl CustomEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="7eb4d-129">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="7eb4d-130">定义使用此控件定义或要使用此定义中必须存在的条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="7eb4d-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7eb4d-131">备注</span><span class="sxs-lookup"><span data-stu-id="7eb4d-131">Remarks</span></span>

<span data-ttu-id="7eb4d-132">在定义的选择条件时，必须满足以下要求：</span><span class="sxs-lookup"><span data-stu-id="7eb4d-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="7eb4d-133">选择条件必须指定至少一个属性名或脚本块，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="7eb4d-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="7eb4d-134">选择条件可以指定任意数量的.NET 类型，或者选择设置，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="7eb4d-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="7eb4d-135">有关如何使用选择条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="7eb4d-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7eb4d-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7eb4d-136">See Also</span></span>

[<span data-ttu-id="7eb4d-137">属性名称的视图 （格式） 的 CustomControl SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="7eb4d-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="7eb4d-138">为视图 （格式） 的 CustomControl SelectionCondition 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="7eb4d-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="7eb4d-139">自定义控件的视图 （格式） 的 SelectionCondition SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="7eb4d-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="7eb4d-140">为视图 （格式） 的 CustomControl SelectionCondition 的 TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="7eb4d-140">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="7eb4d-141">为视图 （格式） 的 CustomControl CustomEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="7eb4d-141">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="7eb4d-142">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="7eb4d-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
