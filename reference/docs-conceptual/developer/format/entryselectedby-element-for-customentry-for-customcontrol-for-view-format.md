---
title: 用于 CustomControl for View （Format）的 CustomEntry 的 EntrySelectedBy 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368776"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="d9ad9-102">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="d9ad9-102">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="d9ad9-103">定义使用此自定义项的 .NET 类型或此项要使用的条件。</span><span class="sxs-lookup"><span data-stu-id="d9ad9-103">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>

<span data-ttu-id="d9ad9-104">用于 CustomEntry 的 CustomControl for view （format） CustomEntries 元素的配置元素（格式） ViewDefinitions 元素（格式） CustomControl 元素（format） CustomEntries 元素 EntrySelectedByView 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d9ad9-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d9ad9-105">语法</span><span class="sxs-lookup"><span data-stu-id="d9ad9-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d9ad9-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="d9ad9-106">Attributes and Elements</span></span>

<span data-ttu-id="d9ad9-107">以下各节介绍了 `EntrySelectedBy` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d9ad9-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d9ad9-108">属性</span><span class="sxs-lookup"><span data-stu-id="d9ad9-108">Attributes</span></span>

<span data-ttu-id="d9ad9-109">无。</span><span class="sxs-lookup"><span data-stu-id="d9ad9-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d9ad9-110">子元素</span><span class="sxs-lookup"><span data-stu-id="d9ad9-110">Child Elements</span></span>

|<span data-ttu-id="d9ad9-111">元素</span><span class="sxs-lookup"><span data-stu-id="d9ad9-111">Element</span></span>|<span data-ttu-id="d9ad9-112">描述</span><span class="sxs-lookup"><span data-stu-id="d9ad9-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d9ad9-113">CustomEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d9ad9-113">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="d9ad9-114">可选元素。</span><span class="sxs-lookup"><span data-stu-id="d9ad9-114">Optional element.</span></span><br /><br /> <span data-ttu-id="d9ad9-115">定义要使用此定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="d9ad9-115">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="d9ad9-116">CustomEntry 的 EntrySelectedBy 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d9ad9-116">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|<span data-ttu-id="d9ad9-117">可选元素。</span><span class="sxs-lookup"><span data-stu-id="d9ad9-117">Optional element.</span></span><br /><br /> <span data-ttu-id="d9ad9-118">指定一组使用控件视图的此定义的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="d9ad9-118">Specifies a set of .NET types that use this definition of the control view.</span></span>|
|[<span data-ttu-id="d9ad9-119">CustomEntry 的 EntrySelectedBy 的 TypeName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="d9ad9-119">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="d9ad9-120">可选元素。</span><span class="sxs-lookup"><span data-stu-id="d9ad9-120">Optional element.</span></span><br /><br /> <span data-ttu-id="d9ad9-121">指定使用控件视图的此定义的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="d9ad9-121">Specifies a .NET type that uses this definition of the control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d9ad9-122">父元素</span><span class="sxs-lookup"><span data-stu-id="d9ad9-122">Parent Elements</span></span>

|<span data-ttu-id="d9ad9-123">元素</span><span class="sxs-lookup"><span data-stu-id="d9ad9-123">Element</span></span>|<span data-ttu-id="d9ad9-124">描述</span><span class="sxs-lookup"><span data-stu-id="d9ad9-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d9ad9-125">用于视图的 CustomEntries 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d9ad9-125">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="d9ad9-126">定义特定 .NET 对象使用的控件。</span><span class="sxs-lookup"><span data-stu-id="d9ad9-126">Defines the controls used by specific .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d9ad9-127">备注</span><span class="sxs-lookup"><span data-stu-id="d9ad9-127">Remarks</span></span>

<span data-ttu-id="d9ad9-128">您必须为某个条目指定至少一个类型、选择集或选择条件。</span><span class="sxs-lookup"><span data-stu-id="d9ad9-128">You must specify at least one type, selection set, or selection condition for an entry.</span></span> <span data-ttu-id="d9ad9-129">您可以使用的子元素数没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="d9ad9-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="d9ad9-130">选择条件用于定义要使用的项必须存在的条件，例如当对象具有特定属性或特定属性值或脚本计算结果为 `true`时。</span><span class="sxs-lookup"><span data-stu-id="d9ad9-130">Selection conditions are used to define a condition that must exist for the entry to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="d9ad9-131">有关选择条件的详细信息，请参阅[定义使用视图条目或项的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="d9ad9-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="d9ad9-132">有关自定义控件视图组件的详细信息，请参阅[自定义控件视图](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="d9ad9-132">For more information about the components of a custom control view, see [Custom Control View](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d9ad9-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d9ad9-133">See Also</span></span>

[<span data-ttu-id="d9ad9-134">CustomEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d9ad9-134">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="d9ad9-135">CustomEntry 的 EntrySelectedBy 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d9ad9-135">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d9ad9-136">CustomEntry 的 EntrySelectedBy 的 TypeName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="d9ad9-136">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d9ad9-137">用于视图的 CustomEntries 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d9ad9-137">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d9ad9-138">自定义控件视图</span><span class="sxs-lookup"><span data-stu-id="d9ad9-138">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="d9ad9-139">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="d9ad9-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
