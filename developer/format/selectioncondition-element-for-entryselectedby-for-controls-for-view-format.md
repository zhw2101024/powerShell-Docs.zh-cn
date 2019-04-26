---
title: 视图 （格式） 的控件的 EntrySelectedBy SelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064217"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="f2310-102">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="f2310-102">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="f2310-103">定义必须存在要使用的控件定义的条件。</span><span class="sxs-lookup"><span data-stu-id="f2310-103">Defines a condition that must exist for the control definition to be used.</span></span> <span data-ttu-id="f2310-104">定义一个视图，可以使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="f2310-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="f2310-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 控件元素 （格式） 控制元素的控件的视图 （格式） CustomEntries 元素的控件的控件的视图 （格式） CustomControl 元素CustomControl CustomEntries CustomEntry EntrySelectedBy 视图 （控件的视图 （格式） SelectionCondition 元素的控件的视图 （格式） EntrySelectedBy 元素的控件的视图 （格式） CustomEntry 元素的控件格式）</span><span class="sxs-lookup"><span data-stu-id="f2310-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f2310-106">语法</span><span class="sxs-lookup"><span data-stu-id="f2310-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f2310-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="f2310-107">Attributes and Elements</span></span>

<span data-ttu-id="f2310-108">以下各节描述了特性、 子元素和父元素的`SelectionCondition`元素。</span><span class="sxs-lookup"><span data-stu-id="f2310-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f2310-109">属性</span><span class="sxs-lookup"><span data-stu-id="f2310-109">Attributes</span></span>

<span data-ttu-id="f2310-110">无。</span><span class="sxs-lookup"><span data-stu-id="f2310-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f2310-111">子元素</span><span class="sxs-lookup"><span data-stu-id="f2310-111">Child Elements</span></span>

|<span data-ttu-id="f2310-112">元素</span><span class="sxs-lookup"><span data-stu-id="f2310-112">Element</span></span>|<span data-ttu-id="f2310-113">说明</span><span class="sxs-lookup"><span data-stu-id="f2310-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f2310-114">SelectionCondition 视图 （格式） 的控件的属性名称元素</span><span class="sxs-lookup"><span data-stu-id="f2310-114">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="f2310-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="f2310-115">Optional element.</span></span><br /><br /> <span data-ttu-id="f2310-116">指定触发条件的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="f2310-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="f2310-117">SelectionCondition 的 Controls 的视图 （格式） 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="f2310-117">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="f2310-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="f2310-118">Optional element.</span></span><br /><br /> <span data-ttu-id="f2310-119">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="f2310-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="f2310-120">视图 （格式） 的控件的 SelectionCondition SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="f2310-120">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="f2310-121">可选元素。</span><span class="sxs-lookup"><span data-stu-id="f2310-121">Optional element.</span></span><br /><br /> <span data-ttu-id="f2310-122">指定触发条件的.NET 类型集。</span><span class="sxs-lookup"><span data-stu-id="f2310-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="f2310-123">SelectionCondition 视图 （格式） 的控件的类型名称元素</span><span class="sxs-lookup"><span data-stu-id="f2310-123">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="f2310-124">可选元素。</span><span class="sxs-lookup"><span data-stu-id="f2310-124">Optional element.</span></span><br /><br /> <span data-ttu-id="f2310-125">指定触发条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="f2310-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f2310-126">父元素</span><span class="sxs-lookup"><span data-stu-id="f2310-126">Parent Elements</span></span>

|<span data-ttu-id="f2310-127">元素</span><span class="sxs-lookup"><span data-stu-id="f2310-127">Element</span></span>|<span data-ttu-id="f2310-128">说明</span><span class="sxs-lookup"><span data-stu-id="f2310-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f2310-129">视图 （格式） 的控件的 CustomEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="f2310-129">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="f2310-130">定义使用此控件定义或要使用此定义中必须存在的条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="f2310-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f2310-131">备注</span><span class="sxs-lookup"><span data-stu-id="f2310-131">Remarks</span></span>

<span data-ttu-id="f2310-132">在定义的选择条件时，必须满足以下要求：</span><span class="sxs-lookup"><span data-stu-id="f2310-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="f2310-133">选择条件必须指定至少一个属性名或脚本块，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="f2310-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="f2310-134">选择条件可以指定任意数量的.NET 类型，或者选择设置，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="f2310-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="f2310-135">有关如何使用选择条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="f2310-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f2310-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f2310-136">See Also</span></span>

[<span data-ttu-id="f2310-137">SelectionCondition 视图 （格式） 的控件的属性名称元素</span><span class="sxs-lookup"><span data-stu-id="f2310-137">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="f2310-138">SelectionCondition 的 Controls 的视图 （格式） 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="f2310-138">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="f2310-139">视图 （格式） 的控件的 SelectionCondition SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="f2310-139">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="f2310-140">SelectionCondition 视图 （格式） 的控件的类型名称元素</span><span class="sxs-lookup"><span data-stu-id="f2310-140">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="f2310-141">视图 （格式） 的控件的 CustomEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="f2310-141">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="f2310-142">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="f2310-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
