---
title: 配置 （格式） 的控件的 EntrySelectedBy SelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075760"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="ef102-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="ef102-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="ef102-103">定义必须存在要使用的常见控件定义的条件。</span><span class="sxs-lookup"><span data-stu-id="ef102-103">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="ef102-104">定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。</span><span class="sxs-lookup"><span data-stu-id="ef102-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="ef102-105">配置 （格式） 的配置 （格式） 的 Controls 的 CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素配置 （格式） 的 Controls 的配置 （格式） 的 Controls 的配置 （格式） SelectionCondition 元素，用于为 CustomEntry 的 EntrySelectedBy CustomEntry EntrySelectedBy 元素 CustomControl CustomEntry 元素配置 （格式）</span><span class="sxs-lookup"><span data-stu-id="ef102-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ef102-106">语法</span><span class="sxs-lookup"><span data-stu-id="ef102-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ef102-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="ef102-107">Attributes and Elements</span></span>

<span data-ttu-id="ef102-108">以下各节描述了特性、 子元素和父元素的`SelectionCondition`元素。</span><span class="sxs-lookup"><span data-stu-id="ef102-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ef102-109">属性</span><span class="sxs-lookup"><span data-stu-id="ef102-109">Attributes</span></span>

<span data-ttu-id="ef102-110">无。</span><span class="sxs-lookup"><span data-stu-id="ef102-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ef102-111">子元素</span><span class="sxs-lookup"><span data-stu-id="ef102-111">Child Elements</span></span>

|<span data-ttu-id="ef102-112">元素</span><span class="sxs-lookup"><span data-stu-id="ef102-112">Element</span></span>|<span data-ttu-id="ef102-113">说明</span><span class="sxs-lookup"><span data-stu-id="ef102-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef102-114">SelectionCondition 配置 （格式） 的控件的属性名称元素</span><span class="sxs-lookup"><span data-stu-id="ef102-114">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="ef102-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="ef102-115">Optional element.</span></span><br /><br /> <span data-ttu-id="ef102-116">指定触发条件的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="ef102-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="ef102-117">SelectionCondition 的 Controls 的配置 （格式） 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="ef102-117">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="ef102-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="ef102-118">Optional element.</span></span><br /><br /> <span data-ttu-id="ef102-119">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="ef102-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="ef102-120">配置 （格式） 的控件的 SelectionCondition SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="ef102-120">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="ef102-121">可选元素。</span><span class="sxs-lookup"><span data-stu-id="ef102-121">Optional element.</span></span><br /><br /> <span data-ttu-id="ef102-122">指定触发条件的.NET 类型集。</span><span class="sxs-lookup"><span data-stu-id="ef102-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="ef102-123">SelectionCondition 配置 （格式） 的控件的类型名称元素</span><span class="sxs-lookup"><span data-stu-id="ef102-123">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="ef102-124">可选元素。</span><span class="sxs-lookup"><span data-stu-id="ef102-124">Optional element.</span></span><br /><br /> <span data-ttu-id="ef102-125">指定触发条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="ef102-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ef102-126">父元素</span><span class="sxs-lookup"><span data-stu-id="ef102-126">Parent Elements</span></span>

|<span data-ttu-id="ef102-127">元素</span><span class="sxs-lookup"><span data-stu-id="ef102-127">Element</span></span>|<span data-ttu-id="ef102-128">说明</span><span class="sxs-lookup"><span data-stu-id="ef102-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef102-129">配置 （格式） 的控件的 CustomEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="ef102-129">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="ef102-130">定义使用常见的控件定义的此项的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="ef102-130">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ef102-131">备注</span><span class="sxs-lookup"><span data-stu-id="ef102-131">Remarks</span></span>

<span data-ttu-id="ef102-132">定义选择条件时，必须遵循以下准则：</span><span class="sxs-lookup"><span data-stu-id="ef102-132">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="ef102-133">选择条件必须指定至少一个属性名或脚本块，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="ef102-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="ef102-134">选择条件可以指定任意数量的.NET 类型，或者选择设置，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="ef102-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="ef102-135">有关如何使用选择条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="ef102-135">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ef102-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ef102-136">See Also</span></span>

[<span data-ttu-id="ef102-137">SelectionCondition 配置 （格式） 的控件的属性名称元素</span><span class="sxs-lookup"><span data-stu-id="ef102-137">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="ef102-138">SelectionCondition 的 Controls 的配置 （格式） 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="ef102-138">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="ef102-139">配置 （格式） 的控件的 SelectionCondition SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="ef102-139">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="ef102-140">SelectionCondition 配置 （格式） 的控件的类型名称元素</span><span class="sxs-lookup"><span data-stu-id="ef102-140">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="ef102-141">配置 （格式） 的控件的 CustomEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="ef102-141">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="ef102-142">编写 Windows PowerShell 格式设置和文件类型</span><span class="sxs-lookup"><span data-stu-id="ef102-142">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
