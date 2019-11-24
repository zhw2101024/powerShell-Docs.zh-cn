---
title: WideControl （Format）的 EntrySelectedBy 的 SelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364776"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="2ab1d-102">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="2ab1d-102">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="2ab1d-103">定义要使用此定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-103">Defines the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="2ab1d-104">对于可为宽输入定义指定的选择条件数没有限制。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-104">There is no limit to the number of selection conditions that can be specified for a wide entry definition.</span></span>

<span data-ttu-id="2ab1d-105">配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（format） EntrySelectedBy 元素 for WideEntry （Format） SelectionCondition 元素 forEntrySelectedBy for WideEntry （Format）</span><span class="sxs-lookup"><span data-stu-id="2ab1d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2ab1d-106">语法</span><span class="sxs-lookup"><span data-stu-id="2ab1d-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2ab1d-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="2ab1d-107">Attributes and Elements</span></span>

<span data-ttu-id="2ab1d-108">以下各节介绍了 `SelectionCondition` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="2ab1d-109">必须指定单个 `PropertyName` 或 `ScriptBlock` 元素。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-109">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="2ab1d-110">`SelectionSetName` 和 `TypeName` 元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-110">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="2ab1d-111">可以指定任一元素中的一个。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-111">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2ab1d-112">特性</span><span class="sxs-lookup"><span data-stu-id="2ab1d-112">Attributes</span></span>

<span data-ttu-id="2ab1d-113">无。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2ab1d-114">子元素</span><span class="sxs-lookup"><span data-stu-id="2ab1d-114">Child Elements</span></span>

|<span data-ttu-id="2ab1d-115">元素</span><span class="sxs-lookup"><span data-stu-id="2ab1d-115">Element</span></span>|<span data-ttu-id="2ab1d-116">描述</span><span class="sxs-lookup"><span data-stu-id="2ab1d-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2ab1d-117">WideEntry 的 SelectionCondition for EntrySelectedBy 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="2ab1d-117">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="2ab1d-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-118">Optional element.</span></span><br /><br /> <span data-ttu-id="2ab1d-119">指定触发条件的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-119">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="2ab1d-120">WideEntry 的 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2ab1d-120">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="2ab1d-121">可选元素。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-121">Optional element.</span></span><br /><br /> <span data-ttu-id="2ab1d-122">指定触发条件的脚本块。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-122">Specifies the script block that triggers the condition.</span></span>|
|[<span data-ttu-id="2ab1d-123">WideEntry 的 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="2ab1d-123">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="2ab1d-124">可选元素。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-124">Optional element.</span></span><br /><br /> <span data-ttu-id="2ab1d-125">指定触发条件的 .NET 类型集。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-125">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="2ab1d-126">WideEntry 的 SelectionCondition for EntrySelectedBy 的 TypeName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="2ab1d-126">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="2ab1d-127">可选元素。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-127">Optional element.</span></span><br /><br /> <span data-ttu-id="2ab1d-128">指定触发条件的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-128">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2ab1d-129">父元素</span><span class="sxs-lookup"><span data-stu-id="2ab1d-129">Parent Elements</span></span>

|<span data-ttu-id="2ab1d-130">元素</span><span class="sxs-lookup"><span data-stu-id="2ab1d-130">Element</span></span>|<span data-ttu-id="2ab1d-131">描述</span><span class="sxs-lookup"><span data-stu-id="2ab1d-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2ab1d-132">WideEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2ab1d-132">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="2ab1d-133">定义使用此宽项的 .NET 类型或此项要使用的条件。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-133">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2ab1d-134">备注</span><span class="sxs-lookup"><span data-stu-id="2ab1d-134">Remarks</span></span>

<span data-ttu-id="2ab1d-135">每个宽条目都必须定义至少一个类型名称、选择集或选择条件。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-135">Each wide entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="2ab1d-136">定义选择条件时，需要满足以下要求：</span><span class="sxs-lookup"><span data-stu-id="2ab1d-136">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="2ab1d-137">选择条件必须指定至少一个属性名称或脚本块，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-137">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="2ab1d-138">选择条件可以指定任意数量的 .NET 类型或选择集，但是不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-138">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="2ab1d-139">有关如何使用选择条件的详细信息，请参阅[定义使用视图条目或项的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-139">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="2ab1d-140">有关大视图的其他组件的详细信息，请参阅[创建宽视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-140">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2ab1d-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2ab1d-141">See Also</span></span>

[<span data-ttu-id="2ab1d-142">创建宽视图</span><span class="sxs-lookup"><span data-stu-id="2ab1d-142">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="2ab1d-143">定义显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="2ab1d-143">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="2ab1d-144">WideEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2ab1d-144">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="2ab1d-145">WideEntry 的 SelectionCondition for EntrySelectedBy 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="2ab1d-145">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="2ab1d-146">WideEntry 的 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2ab1d-146">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="2ab1d-147">WideEntry 的 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="2ab1d-147">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="2ab1d-148">WideEntry 的 SelectionCondition for EntrySelectedBy 的 TypeName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="2ab1d-148">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="2ab1d-149">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="2ab1d-149">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
