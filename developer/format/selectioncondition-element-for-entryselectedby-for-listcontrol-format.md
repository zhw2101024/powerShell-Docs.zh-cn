---
title: ListControl （格式） 的 EntrySelectedBy SelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: ec75945c5517c02fa001f0a38573c045ffcdbfd3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857483"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="540f7-102">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="540f7-102">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="540f7-103">定义要使用此列表视图的定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="540f7-103">Defines the condition that must exist to use this definition of the list view.</span></span> <span data-ttu-id="540f7-104">可以为列表定义指定的选择条件数目没有限制。</span><span class="sxs-lookup"><span data-stu-id="540f7-104">There is no limit to the number of selection conditions that can be specified for a list definition.</span></span>

<span data-ttu-id="540f7-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素 （格式） ListEntry 元素 （格式） EntrySelectedBy 元素 ListEntry （格式） SelectionCondition 元素EntrySelectedBy 为 ListEntry （格式） 的</span><span class="sxs-lookup"><span data-stu-id="540f7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="540f7-106">语法</span><span class="sxs-lookup"><span data-stu-id="540f7-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="540f7-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="540f7-107">Attributes and Elements</span></span>

<span data-ttu-id="540f7-108">以下各节描述了特性、 子元素和父元素的`SelectionCondition`元素。</span><span class="sxs-lookup"><span data-stu-id="540f7-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="540f7-109">属性</span><span class="sxs-lookup"><span data-stu-id="540f7-109">Attributes</span></span>

<span data-ttu-id="540f7-110">无。</span><span class="sxs-lookup"><span data-stu-id="540f7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="540f7-111">子元素</span><span class="sxs-lookup"><span data-stu-id="540f7-111">Child Elements</span></span>

|<span data-ttu-id="540f7-112">元素</span><span class="sxs-lookup"><span data-stu-id="540f7-112">Element</span></span>|<span data-ttu-id="540f7-113">说明</span><span class="sxs-lookup"><span data-stu-id="540f7-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="540f7-114">有关 ListEntry （格式） 的 EmtrySelectedBy SelectionCondition PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="540f7-114">PropertyName Element for SelectionCondition for EmtrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="540f7-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="540f7-115">Optional element.</span></span><br /><br /> <span data-ttu-id="540f7-116">指定触发条件的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="540f7-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="540f7-117">有关 ListEntry （格式） 的 EntrySelectedBy SelectionCondition 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="540f7-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="540f7-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="540f7-118">Optional element.</span></span><br /><br /> <span data-ttu-id="540f7-119">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="540f7-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="540f7-120">有关 ListEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="540f7-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|<span data-ttu-id="540f7-121">可选元素。</span><span class="sxs-lookup"><span data-stu-id="540f7-121">Optional element.</span></span><br /><br /> <span data-ttu-id="540f7-122">指定.NET 类型的触发器条件的集。</span><span class="sxs-lookup"><span data-stu-id="540f7-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="540f7-123">有关 ListEntry （格式） 的 EntrySelectedBy SelectionCondition 的 TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="540f7-123">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="540f7-124">可选元素。</span><span class="sxs-lookup"><span data-stu-id="540f7-124">Optional element.</span></span><br /><br /> <span data-ttu-id="540f7-125">指定触发条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="540f7-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="540f7-126">父元素</span><span class="sxs-lookup"><span data-stu-id="540f7-126">Parent Elements</span></span>

|<span data-ttu-id="540f7-127">元素</span><span class="sxs-lookup"><span data-stu-id="540f7-127">Element</span></span>|<span data-ttu-id="540f7-128">说明</span><span class="sxs-lookup"><span data-stu-id="540f7-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="540f7-129">TableRowEntry （格式） 的 EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="540f7-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="540f7-130">定义使用此表项或要使用此项必须存在的条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="540f7-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="540f7-131">备注</span><span class="sxs-lookup"><span data-stu-id="540f7-131">Remarks</span></span>

<span data-ttu-id="540f7-132">lWhen 定义选择条件，必须满足以下要求：</span><span class="sxs-lookup"><span data-stu-id="540f7-132">lWhen you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="540f7-133">选择条件必须指定至少一个属性名或脚本块，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="540f7-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="540f7-134">选择条件可以指定任意数量的.NET 类型，或者选择设置，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="540f7-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="540f7-135">有关如何使用选择条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="540f7-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="540f7-136">列表视图的其他组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="540f7-136">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="540f7-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="540f7-137">See Also</span></span>

[<span data-ttu-id="540f7-138">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="540f7-138">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="540f7-139">定义何时显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="540f7-139">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="540f7-140">ListEntry 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="540f7-140">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="540f7-141">ListEntry （格式） 的 EnrtySelectedBy SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="540f7-141">SelectionSetName Element for EnrtySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="540f7-142">ListEntry （格式） 的 EntrySelectedBy 的 TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="540f7-142">TypeName Element for EntrySelectedBy for ListEntry (Format)</span></span>](http://msdn.microsoft.com/en-us/fcd4daa6-f3fd-43f7-a468-03c582d34533)

[<span data-ttu-id="540f7-143">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="540f7-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
