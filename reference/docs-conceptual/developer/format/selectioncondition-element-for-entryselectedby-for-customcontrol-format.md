---
title: CustomControl （Format）的 EntrySelectedBy 的 SelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368436"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a><span data-ttu-id="510e4-102">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="510e4-102">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>

<span data-ttu-id="510e4-103">定义要使用的控件定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="510e4-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="510e4-104">定义自定义控件视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="510e4-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="510e4-105">Configuration Element （Format） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素 for View （format） CustomEntries 元素 for CustomControl for CustomEntry for CustomEntries for View （Format） CustomControl 元素 for view （Format） CustomItem 元素 for CustomEntry for CustomControl for for view （format） EntrySelectedBy 元素 for CustomEntry for CustomControl for SelectionCondition for view （format） EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="510e4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="510e4-106">语法</span><span class="sxs-lookup"><span data-stu-id="510e4-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="510e4-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="510e4-107">Attributes and Elements</span></span>

<span data-ttu-id="510e4-108">以下各节介绍了 `SelectionCondition` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="510e4-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="510e4-109">属性</span><span class="sxs-lookup"><span data-stu-id="510e4-109">Attributes</span></span>

<span data-ttu-id="510e4-110">无。</span><span class="sxs-lookup"><span data-stu-id="510e4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="510e4-111">子元素</span><span class="sxs-lookup"><span data-stu-id="510e4-111">Child Elements</span></span>

|<span data-ttu-id="510e4-112">元素</span><span class="sxs-lookup"><span data-stu-id="510e4-112">Element</span></span>|<span data-ttu-id="510e4-113">描述</span><span class="sxs-lookup"><span data-stu-id="510e4-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="510e4-114">View 的 SelectionCondition for CustomControl 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="510e4-114">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="510e4-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="510e4-115">Optional element.</span></span><br /><br /> <span data-ttu-id="510e4-116">指定触发条件的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="510e4-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="510e4-117">用于 View 的 SelectionCondition for CustomControl 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="510e4-117">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="510e4-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="510e4-118">Optional element.</span></span><br /><br /> <span data-ttu-id="510e4-119">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="510e4-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="510e4-120">用于视图的自定义控件的 SelectionCondition 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="510e4-120">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="510e4-121">可选元素。</span><span class="sxs-lookup"><span data-stu-id="510e4-121">Optional element.</span></span><br /><br /> <span data-ttu-id="510e4-122">指定触发条件的 .NET 类型集。</span><span class="sxs-lookup"><span data-stu-id="510e4-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="510e4-123">用于 View 的 SelectionCondition for CustomControl 的 TypeName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="510e4-123">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="510e4-124">可选元素。</span><span class="sxs-lookup"><span data-stu-id="510e4-124">Optional element.</span></span><br /><br /> <span data-ttu-id="510e4-125">指定触发条件的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="510e4-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="510e4-126">父元素</span><span class="sxs-lookup"><span data-stu-id="510e4-126">Parent Elements</span></span>

|<span data-ttu-id="510e4-127">元素</span><span class="sxs-lookup"><span data-stu-id="510e4-127">Element</span></span>|<span data-ttu-id="510e4-128">描述</span><span class="sxs-lookup"><span data-stu-id="510e4-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="510e4-129">用于 View 的 CustomControl 的 CustomEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="510e4-129">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="510e4-130">定义使用此控件定义的 .NET 类型或要使用此定义时必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="510e4-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="510e4-131">备注</span><span class="sxs-lookup"><span data-stu-id="510e4-131">Remarks</span></span>

<span data-ttu-id="510e4-132">定义选择条件时，需要满足以下要求：</span><span class="sxs-lookup"><span data-stu-id="510e4-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="510e4-133">选择条件必须指定至少一个属性名称或脚本块，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="510e4-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="510e4-134">选择条件可以指定任意数量的 .NET 类型或选择集，但是不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="510e4-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="510e4-135">有关如何使用选择条件的详细信息，请参阅为[数据显示定义条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="510e4-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="510e4-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="510e4-136">See Also</span></span>

[<span data-ttu-id="510e4-137">View 的 SelectionCondition for CustomControl 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="510e4-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="510e4-138">用于 View 的 SelectionCondition for CustomControl 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="510e4-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="510e4-139">用于视图的自定义控件的 SelectionCondition 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="510e4-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="510e4-140">用于 View 的 SelectionCondition for CustomControl 的 TypeName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="510e4-140">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="510e4-141">用于 View 的 CustomControl 的 CustomEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="510e4-141">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="510e4-142">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="510e4-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
