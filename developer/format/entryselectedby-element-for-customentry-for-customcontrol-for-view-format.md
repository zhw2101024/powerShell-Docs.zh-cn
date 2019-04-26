---
title: EntrySelectedBy 元素的视图 （格式） 的 CustomControl CustomEntry |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066271"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="65e46-102">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="65e46-102">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="65e46-103">定义使用此自定义项或要使用此项必须存在的条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="65e46-103">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>

<span data-ttu-id="65e46-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素 （格式） CustomEntries 元素 CustomControl 视图 （格式） 的视图 （格式） EntrySelectedBy CustomEntries CustomEntry 元素CustomEntry 视图 （格式） 的元素</span><span class="sxs-lookup"><span data-stu-id="65e46-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="65e46-105">语法</span><span class="sxs-lookup"><span data-stu-id="65e46-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="65e46-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="65e46-106">Attributes and Elements</span></span>

<span data-ttu-id="65e46-107">以下各节描述了特性、 子元素和父元素的`EntrySelectedBy`元素。</span><span class="sxs-lookup"><span data-stu-id="65e46-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="65e46-108">属性</span><span class="sxs-lookup"><span data-stu-id="65e46-108">Attributes</span></span>

<span data-ttu-id="65e46-109">无。</span><span class="sxs-lookup"><span data-stu-id="65e46-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="65e46-110">子元素</span><span class="sxs-lookup"><span data-stu-id="65e46-110">Child Elements</span></span>

|<span data-ttu-id="65e46-111">元素</span><span class="sxs-lookup"><span data-stu-id="65e46-111">Element</span></span>|<span data-ttu-id="65e46-112">说明</span><span class="sxs-lookup"><span data-stu-id="65e46-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="65e46-113">CustomEntry （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="65e46-113">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="65e46-114">可选元素。</span><span class="sxs-lookup"><span data-stu-id="65e46-114">Optional element.</span></span><br /><br /> <span data-ttu-id="65e46-115">定义必须存在要使用此定义的条件。</span><span class="sxs-lookup"><span data-stu-id="65e46-115">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="65e46-116">CustomEntry （格式） 的 EntrySelectedBy SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="65e46-116">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|<span data-ttu-id="65e46-117">可选元素。</span><span class="sxs-lookup"><span data-stu-id="65e46-117">Optional element.</span></span><br /><br /> <span data-ttu-id="65e46-118">指定一组使用的控件视图此定义的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="65e46-118">Specifies a set of .NET types that use this definition of the control view.</span></span>|
|[<span data-ttu-id="65e46-119">CustomEntry （格式） 的 EntrySelectedBy 的 TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="65e46-119">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="65e46-120">可选元素。</span><span class="sxs-lookup"><span data-stu-id="65e46-120">Optional element.</span></span><br /><br /> <span data-ttu-id="65e46-121">指定将使用此定义的控件视图的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="65e46-121">Specifies a .NET type that uses this definition of the control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="65e46-122">父元素</span><span class="sxs-lookup"><span data-stu-id="65e46-122">Parent Elements</span></span>

|<span data-ttu-id="65e46-123">元素</span><span class="sxs-lookup"><span data-stu-id="65e46-123">Element</span></span>|<span data-ttu-id="65e46-124">说明</span><span class="sxs-lookup"><span data-stu-id="65e46-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="65e46-125">视图 （格式） 的 CustomEntries CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="65e46-125">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="65e46-126">定义特定的.NET 对象所使用的控件。</span><span class="sxs-lookup"><span data-stu-id="65e46-126">Defines the controls used by specific .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="65e46-127">备注</span><span class="sxs-lookup"><span data-stu-id="65e46-127">Remarks</span></span>

<span data-ttu-id="65e46-128">必须指定至少一个类型、 选择集或选择条件的条目。</span><span class="sxs-lookup"><span data-stu-id="65e46-128">You must specify at least one type, selection set, or selection condition for an entry.</span></span> <span data-ttu-id="65e46-129">可以使用的子元素的数目没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="65e46-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="65e46-130">使用选择条件来定义的条件必须存在要使用的项，例如当一个对象具有特定属性时，或者特定属性值或脚本的计算结果为`true`。</span><span class="sxs-lookup"><span data-stu-id="65e46-130">Selection conditions are used to define a condition that must exist for the entry to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="65e46-131">有关选择条件的详细信息，请参阅[时视图条目定义条件或使用项](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="65e46-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="65e46-132">有关组件的自定义控件视图的详细信息，请参阅[自定义控件视图](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="65e46-132">For more information about the components of a custom control view, see [Custom Control View](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="65e46-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="65e46-133">See Also</span></span>

[<span data-ttu-id="65e46-134">CustomEntry （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="65e46-134">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="65e46-135">CustomEntry （格式） 的 EntrySelectedBy SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="65e46-135">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[<span data-ttu-id="65e46-136">CustomEntry （格式） 的 EntrySelectedBy 的 TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="65e46-136">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="65e46-137">视图 （格式） 的 CustomEntries CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="65e46-137">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="65e46-138">自定义控件视图</span><span class="sxs-lookup"><span data-stu-id="65e46-138">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="65e46-139">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="65e46-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
