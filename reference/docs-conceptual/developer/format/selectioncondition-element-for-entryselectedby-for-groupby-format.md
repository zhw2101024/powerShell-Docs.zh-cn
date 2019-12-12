---
title: GroupBy （Format）的 EntrySelectedBy 的 SelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc2093a-dc54-42c4-ada3-c8d089ba1e8e
caps.latest.revision: 6
ms.openlocfilehash: a6738a7c4c934b2d6a16695a711f7c6c80afdd2d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368426"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="5e248-102">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5e248-102">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="5e248-103">定义要使用的控件定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="5e248-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="5e248-104">此元素在定义如何显示新的对象组时使用。</span><span class="sxs-lookup"><span data-stu-id="5e248-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="5e248-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format）对于 GroupBy （format） CustomEntries 元素，用于元素的 CustomControl 元素（format）CustomControl for groupby （format） EntrySelectedBy 元素 for CustomEntry for groupby （format） SelectionCondition 元素 for GroupBy （Format）</span><span class="sxs-lookup"><span data-stu-id="5e248-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5e248-106">语法</span><span class="sxs-lookup"><span data-stu-id="5e248-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5e248-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="5e248-107">Attributes and Elements</span></span>

<span data-ttu-id="5e248-108">以下各节介绍了 `SelectionCondition` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5e248-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5e248-109">属性</span><span class="sxs-lookup"><span data-stu-id="5e248-109">Attributes</span></span>

<span data-ttu-id="5e248-110">无。</span><span class="sxs-lookup"><span data-stu-id="5e248-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5e248-111">子元素</span><span class="sxs-lookup"><span data-stu-id="5e248-111">Child Elements</span></span>

|<span data-ttu-id="5e248-112">元素</span><span class="sxs-lookup"><span data-stu-id="5e248-112">Element</span></span>|<span data-ttu-id="5e248-113">描述</span><span class="sxs-lookup"><span data-stu-id="5e248-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5e248-114">GroupBy 的 SelectionCondition 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="5e248-114">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="5e248-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="5e248-115">Optional element.</span></span><br /><br /> <span data-ttu-id="5e248-116">指定触发条件的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="5e248-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="5e248-117">GroupBy 的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5e248-117">ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="5e248-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="5e248-118">Optional element.</span></span><br /><br /> <span data-ttu-id="5e248-119">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="5e248-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="5e248-120">GroupBy 的 SelectionCondition 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5e248-120">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="5e248-121">可选元素。</span><span class="sxs-lookup"><span data-stu-id="5e248-121">Optional element.</span></span><br /><br /> <span data-ttu-id="5e248-122">指定触发条件的 .NET 类型集。</span><span class="sxs-lookup"><span data-stu-id="5e248-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="5e248-123">GroupBy 的 SelectionCondition 的 TypeName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="5e248-123">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="5e248-124">可选元素。</span><span class="sxs-lookup"><span data-stu-id="5e248-124">Optional element.</span></span><br /><br /> <span data-ttu-id="5e248-125">指定触发条件的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="5e248-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5e248-126">父元素</span><span class="sxs-lookup"><span data-stu-id="5e248-126">Parent Elements</span></span>

|<span data-ttu-id="5e248-127">元素</span><span class="sxs-lookup"><span data-stu-id="5e248-127">Element</span></span>|<span data-ttu-id="5e248-128">描述</span><span class="sxs-lookup"><span data-stu-id="5e248-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5e248-129">GroupBy 的 CustomEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5e248-129">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="5e248-130">定义使用此控件定义的 .NET 类型或要使用此定义时必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="5e248-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5e248-131">备注</span><span class="sxs-lookup"><span data-stu-id="5e248-131">Remarks</span></span>

<span data-ttu-id="5e248-132">定义选择条件时，需要满足以下要求：</span><span class="sxs-lookup"><span data-stu-id="5e248-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="5e248-133">选择条件必须指定至少一个属性名称或脚本块，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="5e248-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="5e248-134">选择条件可以指定任意数量的 .NET 类型或选择集，但是不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="5e248-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="5e248-135">有关如何使用选择条件的详细信息，请参阅为[数据显示定义条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="5e248-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5e248-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5e248-136">See Also</span></span>

[<span data-ttu-id="5e248-137">View 的 SelectionCondition for CustomControl 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="5e248-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5e248-138">用于 View 的 SelectionCondition for CustomControl 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5e248-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5e248-139">用于视图的自定义控件的 SelectionCondition 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5e248-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5e248-140">GroupBy 的 SelectionCondition 的 TypeName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="5e248-140">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="5e248-141">GroupBy 的 CustomEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5e248-141">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="5e248-142">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="5e248-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
