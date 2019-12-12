---
title: 用于配置的控件（格式）的 EntrySelectedBy 的 SelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368446"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="c7a95-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="c7a95-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="c7a95-103">定义要使用的公共控件定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="c7a95-103">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="c7a95-104">此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。</span><span class="sxs-lookup"><span data-stu-id="c7a95-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="c7a95-105">Configuration 元素（格式）控制配置（format） CustomControl 元素的控件的配置（Format）控件元素的元素，用于控件的配置（format） CustomEntries 元素，用于 CustomControl 的控件配置（format） CustomEntry 元素 for CustomControl for EntrySelectedBy 元素 for CustomEntry for 元素 for for SelectionCondition for EntrySelectedBy 的 CustomEntry 元素配置（格式）</span><span class="sxs-lookup"><span data-stu-id="c7a95-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c7a95-106">语法</span><span class="sxs-lookup"><span data-stu-id="c7a95-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c7a95-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="c7a95-107">Attributes and Elements</span></span>

<span data-ttu-id="c7a95-108">以下各节介绍了 `SelectionCondition` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c7a95-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c7a95-109">属性</span><span class="sxs-lookup"><span data-stu-id="c7a95-109">Attributes</span></span>

<span data-ttu-id="c7a95-110">无。</span><span class="sxs-lookup"><span data-stu-id="c7a95-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c7a95-111">子元素</span><span class="sxs-lookup"><span data-stu-id="c7a95-111">Child Elements</span></span>

|<span data-ttu-id="c7a95-112">元素</span><span class="sxs-lookup"><span data-stu-id="c7a95-112">Element</span></span>|<span data-ttu-id="c7a95-113">描述</span><span class="sxs-lookup"><span data-stu-id="c7a95-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c7a95-114">用于配置的控件的 SelectionCondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c7a95-114">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="c7a95-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="c7a95-115">Optional element.</span></span><br /><br /> <span data-ttu-id="c7a95-116">指定触发条件的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="c7a95-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="c7a95-117">用于配置的控件的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c7a95-117">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="c7a95-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="c7a95-118">Optional element.</span></span><br /><br /> <span data-ttu-id="c7a95-119">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="c7a95-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="c7a95-120">用于配置的控件的 SelectionCondition 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c7a95-120">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="c7a95-121">可选元素。</span><span class="sxs-lookup"><span data-stu-id="c7a95-121">Optional element.</span></span><br /><br /> <span data-ttu-id="c7a95-122">指定触发条件的 .NET 类型集。</span><span class="sxs-lookup"><span data-stu-id="c7a95-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="c7a95-123">用于配置的控件的 SelectionCondition 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c7a95-123">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="c7a95-124">可选元素。</span><span class="sxs-lookup"><span data-stu-id="c7a95-124">Optional element.</span></span><br /><br /> <span data-ttu-id="c7a95-125">指定触发条件的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="c7a95-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c7a95-126">父元素</span><span class="sxs-lookup"><span data-stu-id="c7a95-126">Parent Elements</span></span>

|<span data-ttu-id="c7a95-127">元素</span><span class="sxs-lookup"><span data-stu-id="c7a95-127">Element</span></span>|<span data-ttu-id="c7a95-128">描述</span><span class="sxs-lookup"><span data-stu-id="c7a95-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c7a95-129">用于配置的控件的 CustomEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c7a95-129">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="c7a95-130">定义使用此公共控件定义的此项的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="c7a95-130">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c7a95-131">备注</span><span class="sxs-lookup"><span data-stu-id="c7a95-131">Remarks</span></span>

<span data-ttu-id="c7a95-132">定义选择条件时，必须遵循以下准则：</span><span class="sxs-lookup"><span data-stu-id="c7a95-132">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="c7a95-133">选择条件必须指定至少一个属性名称或脚本块，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="c7a95-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="c7a95-134">选择条件可以指定任意数量的 .NET 类型或选择集，但是不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="c7a95-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="c7a95-135">有关如何使用选择条件的详细信息，请参阅为[数据显示定义条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="c7a95-135">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c7a95-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c7a95-136">See Also</span></span>

[<span data-ttu-id="c7a95-137">用于配置的控件的 SelectionCondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c7a95-137">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="c7a95-138">用于配置的控件的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c7a95-138">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="c7a95-139">用于配置的控件的 SelectionCondition 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c7a95-139">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="c7a95-140">用于配置的控件的 SelectionCondition 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c7a95-140">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="c7a95-141">用于配置的控件的 CustomEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c7a95-141">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="c7a95-142">编写 Windows PowerShell 格式设置和类型文件</span><span class="sxs-lookup"><span data-stu-id="c7a95-142">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
