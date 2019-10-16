---
title: 用于视图（格式）的 EntrySelectedBy 的 SelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362046"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="a5903-102">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="a5903-102">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="a5903-103">定义要使用的控件定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="a5903-103">Defines a condition that must exist for the control definition to be used.</span></span> <span data-ttu-id="a5903-104">定义可由视图使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="a5903-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="a5903-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 元素（format） Control 元素 for View （format） CustomControl 元素的控件元素，用于控件的 View （format） CustomEntries 元素CustomControl for view （format） CustomEntry 元素 for view （format）元素 for CustomEntries for view （format） EntrySelectedBy 元素 for view （format）元素 for CustomEntry for view （format） SelectionCondition 元素 for view （形式</span><span class="sxs-lookup"><span data-stu-id="a5903-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a5903-106">语法</span><span class="sxs-lookup"><span data-stu-id="a5903-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a5903-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="a5903-107">Attributes and Elements</span></span>

<span data-ttu-id="a5903-108">以下各节介绍了 `SelectionCondition` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a5903-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a5903-109">属性</span><span class="sxs-lookup"><span data-stu-id="a5903-109">Attributes</span></span>

<span data-ttu-id="a5903-110">无。</span><span class="sxs-lookup"><span data-stu-id="a5903-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a5903-111">子元素</span><span class="sxs-lookup"><span data-stu-id="a5903-111">Child Elements</span></span>

|<span data-ttu-id="a5903-112">元素</span><span class="sxs-lookup"><span data-stu-id="a5903-112">Element</span></span>|<span data-ttu-id="a5903-113">描述</span><span class="sxs-lookup"><span data-stu-id="a5903-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a5903-114">View 的 SelectionCondition for Controls 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="a5903-114">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="a5903-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="a5903-115">Optional element.</span></span><br /><br /> <span data-ttu-id="a5903-116">指定触发条件的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="a5903-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="a5903-117">用于视图的控件的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a5903-117">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="a5903-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="a5903-118">Optional element.</span></span><br /><br /> <span data-ttu-id="a5903-119">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="a5903-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="a5903-120">用于视图的控件的 SelectionCondition 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a5903-120">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="a5903-121">可选元素。</span><span class="sxs-lookup"><span data-stu-id="a5903-121">Optional element.</span></span><br /><br /> <span data-ttu-id="a5903-122">指定触发条件的 .NET 类型集。</span><span class="sxs-lookup"><span data-stu-id="a5903-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="a5903-123">用于视图的控件的 SelectionCondition 的 TypeName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="a5903-123">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="a5903-124">可选元素。</span><span class="sxs-lookup"><span data-stu-id="a5903-124">Optional element.</span></span><br /><br /> <span data-ttu-id="a5903-125">指定触发条件的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="a5903-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a5903-126">父元素</span><span class="sxs-lookup"><span data-stu-id="a5903-126">Parent Elements</span></span>

|<span data-ttu-id="a5903-127">元素</span><span class="sxs-lookup"><span data-stu-id="a5903-127">Element</span></span>|<span data-ttu-id="a5903-128">描述</span><span class="sxs-lookup"><span data-stu-id="a5903-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a5903-129">用于视图的控件的 CustomEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a5903-129">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="a5903-130">定义使用此控件定义的 .NET 类型或要使用此定义时必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="a5903-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a5903-131">备注</span><span class="sxs-lookup"><span data-stu-id="a5903-131">Remarks</span></span>

<span data-ttu-id="a5903-132">定义选择条件时，需要满足以下要求：</span><span class="sxs-lookup"><span data-stu-id="a5903-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="a5903-133">选择条件必须指定至少一个属性名称或脚本块，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="a5903-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="a5903-134">选择条件可以指定任意数量的 .NET 类型或选择集，但是不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="a5903-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="a5903-135">有关如何使用选择条件的详细信息，请参阅为[数据显示定义条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="a5903-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a5903-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a5903-136">See Also</span></span>

[<span data-ttu-id="a5903-137">View 的 SelectionCondition for Controls 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="a5903-137">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="a5903-138">用于视图的控件的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a5903-138">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="a5903-139">用于视图的控件的 SelectionCondition 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a5903-139">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="a5903-140">用于视图的控件的 SelectionCondition 的 TypeName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="a5903-140">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="a5903-141">用于视图的控件的 CustomEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a5903-141">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="a5903-142">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="a5903-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
