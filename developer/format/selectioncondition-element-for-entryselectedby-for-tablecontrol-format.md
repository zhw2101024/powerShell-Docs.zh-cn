---
title: TableControl （格式） 的 EntrySelectedBy SelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 912f3e63-e4d5-41ce-8710-6dfd8c885dc2
caps.latest.revision: 12
ms.openlocfilehash: 2faca6021dc26878869bdd2d35bc4ffc64d0fe7b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861233"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="2e677-102">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="2e677-102">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="2e677-103">定义必须存在要用于此定义的表视图的条件。</span><span class="sxs-lookup"><span data-stu-id="2e677-103">Defines the condition that must exist to use for this definition of the table view.</span></span> <span data-ttu-id="2e677-104">可以为表定义指定的选择条件数目没有限制。</span><span class="sxs-lookup"><span data-stu-id="2e677-104">There is no limit to the number of selection conditions that can be specified for a table definition.</span></span>

<span data-ttu-id="2e677-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableRowEntries 元素 （格式） TableRowEntry 元素 （格式） EntrySelectedBy 元素 TableRowEntry （格式）TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="2e677-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2e677-106">语法</span><span class="sxs-lookup"><span data-stu-id="2e677-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2e677-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="2e677-107">Attributes and Elements</span></span>

<span data-ttu-id="2e677-108">以下各节描述了特性、 子元素和 SelectionCondition 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="2e677-108">The following sections describe attributes, child elements, and the parent element of the SelectionCondition element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2e677-109">特性</span><span class="sxs-lookup"><span data-stu-id="2e677-109">Attributes</span></span>

<span data-ttu-id="2e677-110">无。</span><span class="sxs-lookup"><span data-stu-id="2e677-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2e677-111">子元素</span><span class="sxs-lookup"><span data-stu-id="2e677-111">Child Elements</span></span>

|<span data-ttu-id="2e677-112">元素</span><span class="sxs-lookup"><span data-stu-id="2e677-112">Element</span></span>|<span data-ttu-id="2e677-113">描述</span><span class="sxs-lookup"><span data-stu-id="2e677-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2e677-114">有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="2e677-114">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|<span data-ttu-id="2e677-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="2e677-115">Optional element.</span></span><br /><br /> <span data-ttu-id="2e677-116">指定触发条件的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="2e677-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="2e677-117">有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="2e677-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="2e677-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="2e677-118">Optional element.</span></span><br /><br /> <span data-ttu-id="2e677-119">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="2e677-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="2e677-120">有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="2e677-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="2e677-121">可选元素。</span><span class="sxs-lookup"><span data-stu-id="2e677-121">Optional element.</span></span><br /><br /> <span data-ttu-id="2e677-122">指定.NET 类型的触发器条件的集。</span><span class="sxs-lookup"><span data-stu-id="2e677-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="2e677-123">有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 的 TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="2e677-123">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="2e677-124">可选元素。</span><span class="sxs-lookup"><span data-stu-id="2e677-124">Optional element.</span></span><br /><br /> <span data-ttu-id="2e677-125">指定触发条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="2e677-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2e677-126">父元素</span><span class="sxs-lookup"><span data-stu-id="2e677-126">Parent Elements</span></span>

|<span data-ttu-id="2e677-127">元素</span><span class="sxs-lookup"><span data-stu-id="2e677-127">Element</span></span>|<span data-ttu-id="2e677-128">描述</span><span class="sxs-lookup"><span data-stu-id="2e677-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2e677-129">TableRowEntry （格式） 的 EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="2e677-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="2e677-130">定义使用此表项或要使用此项必须存在的条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="2e677-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2e677-131">备注</span><span class="sxs-lookup"><span data-stu-id="2e677-131">Remarks</span></span>

<span data-ttu-id="2e677-132">每个列表项必须具有至少一个类型名称、 选择集或定义的选择条件。</span><span class="sxs-lookup"><span data-stu-id="2e677-132">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="2e677-133">在定义的选择条件时，必须满足以下要求：</span><span class="sxs-lookup"><span data-stu-id="2e677-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="2e677-134">选择条件必须指定至少一个属性名或脚本块，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="2e677-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="2e677-135">选择条件可以指定任意数量的.NET 类型，或者选择设置，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="2e677-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="2e677-136">有关如何使用选择条件的详细信息，请参阅[时视图条目定义条件或使用项](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="2e677-136">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="2e677-137">表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="2e677-137">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2e677-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2e677-138">See Also</span></span>

[<span data-ttu-id="2e677-139">创建表视图</span><span class="sxs-lookup"><span data-stu-id="2e677-139">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="2e677-140">定义何时显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="2e677-140">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="2e677-141">EntrySelectedBy 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="2e677-141">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="2e677-142">有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="2e677-142">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="2e677-143">有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="2e677-143">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="2e677-144">有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="2e677-144">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="2e677-145">有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 的 TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="2e677-145">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="2e677-146">编写 Windows PowerShell 格式设置和文件类型</span><span class="sxs-lookup"><span data-stu-id="2e677-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
