---
title: GroupBy （Format）的 CustomEntry 的 EntrySelectedBy 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363856"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a><span data-ttu-id="bedad-102">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bedad-102">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="bedad-103">定义使用此控件定义的 .NET 类型或要使用此定义时必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="bedad-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="bedad-104">此元素在定义如何显示新的对象组时使用。</span><span class="sxs-lookup"><span data-stu-id="bedad-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="bedad-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format）对于 GroupBy （format） CustomEntries 元素，用于元素的 CustomControl 元素（format）CustomControl for GroupBy （Format） EntrySelectedBy 元素 for CustomEntry for GroupBy （Format）</span><span class="sxs-lookup"><span data-stu-id="bedad-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bedad-106">语法</span><span class="sxs-lookup"><span data-stu-id="bedad-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bedad-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="bedad-107">Attributes and Elements</span></span>

<span data-ttu-id="bedad-108">以下各节介绍 `EntrySelectedBy` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="bedad-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="bedad-109">必须为定义至少指定一个类型、选择集或选择条件。</span><span class="sxs-lookup"><span data-stu-id="bedad-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="bedad-110">您可以使用的子元素数没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="bedad-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="bedad-111">属性</span><span class="sxs-lookup"><span data-stu-id="bedad-111">Attributes</span></span>

<span data-ttu-id="bedad-112">无。</span><span class="sxs-lookup"><span data-stu-id="bedad-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bedad-113">子元素</span><span class="sxs-lookup"><span data-stu-id="bedad-113">Child Elements</span></span>

|<span data-ttu-id="bedad-114">元素</span><span class="sxs-lookup"><span data-stu-id="bedad-114">Element</span></span>|<span data-ttu-id="bedad-115">描述</span><span class="sxs-lookup"><span data-stu-id="bedad-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bedad-116">GroupBy 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="bedad-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="bedad-117">可选元素。</span><span class="sxs-lookup"><span data-stu-id="bedad-117">Optional element.</span></span><br /><br /> <span data-ttu-id="bedad-118">定义要使用此定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="bedad-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="bedad-119">GroupBy 的 EntrySelectedBy 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="bedad-119">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="bedad-120">可选元素。</span><span class="sxs-lookup"><span data-stu-id="bedad-120">Optional element.</span></span><br /><br /> <span data-ttu-id="bedad-121">指定一组使用此控件定义的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="bedad-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="bedad-122">GroupBy 的 EntrySelectedBy 的 TypeName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="bedad-122">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="bedad-123">可选元素。</span><span class="sxs-lookup"><span data-stu-id="bedad-123">Optional element.</span></span><br /><br /> <span data-ttu-id="bedad-124">指定使用控件的此定义的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="bedad-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bedad-125">父元素</span><span class="sxs-lookup"><span data-stu-id="bedad-125">Parent Elements</span></span>

|<span data-ttu-id="bedad-126">元素</span><span class="sxs-lookup"><span data-stu-id="bedad-126">Element</span></span>|<span data-ttu-id="bedad-127">描述</span><span class="sxs-lookup"><span data-stu-id="bedad-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bedad-128">GroupBy 的 CustomControl 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="bedad-128">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="bedad-129">提供控件的定义。</span><span class="sxs-lookup"><span data-stu-id="bedad-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bedad-130">备注</span><span class="sxs-lookup"><span data-stu-id="bedad-130">Remarks</span></span>

<span data-ttu-id="bedad-131">选择条件用于定义要使用的定义必须存在的条件，例如当对象具有特定属性或特定属性值或脚本计算结果为 `true` 时。</span><span class="sxs-lookup"><span data-stu-id="bedad-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="bedad-132">有关选择条件的详细信息，请参阅[定义使用视图条目或项的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="bedad-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bedad-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bedad-133">See Also</span></span>

[<span data-ttu-id="bedad-134">GroupBy 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="bedad-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="bedad-135">GroupBy 的 EntrySelectedBy 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="bedad-135">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="bedad-136">GroupBy 的 EntrySelectedBy 的 TypeName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="bedad-136">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="bedad-137">用于视图的控件的 CustomEntries 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="bedad-137">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="bedad-138">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="bedad-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
