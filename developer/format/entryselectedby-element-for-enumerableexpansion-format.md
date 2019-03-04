---
title: EnumerableExpansion （格式） 的 EntrySelectedBy 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855583"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a><span data-ttu-id="b4c35-102">EntrySelectedBy Element for EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="b4c35-102">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="b4c35-103">定义使用此定义或要使用此定义中必须存在的条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="b4c35-103">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="b4c35-104">配置元素 （格式） DefaultSettings 元素 （格式） EnumerableExpansions 元素 （格式） EnumerableExpansion 元素 （格式） EntrySelectedBy 元素 EnumerableExpansion （格式）</span><span class="sxs-lookup"><span data-stu-id="b4c35-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b4c35-105">语法</span><span class="sxs-lookup"><span data-stu-id="b4c35-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b4c35-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="b4c35-106">Attributes and Elements</span></span>

<span data-ttu-id="b4c35-107">以下各节描述了特性、 子元素和父元素的`EntrySelectedBy`元素。</span><span class="sxs-lookup"><span data-stu-id="b4c35-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b4c35-108">特性</span><span class="sxs-lookup"><span data-stu-id="b4c35-108">Attributes</span></span>

<span data-ttu-id="b4c35-109">无。</span><span class="sxs-lookup"><span data-stu-id="b4c35-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b4c35-110">子元素</span><span class="sxs-lookup"><span data-stu-id="b4c35-110">Child Elements</span></span>

|<span data-ttu-id="b4c35-111">元素</span><span class="sxs-lookup"><span data-stu-id="b4c35-111">Element</span></span>|<span data-ttu-id="b4c35-112">描述</span><span class="sxs-lookup"><span data-stu-id="b4c35-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b4c35-113">EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="b4c35-113">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="b4c35-114">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b4c35-114">Optional element.</span></span><br /><br /> <span data-ttu-id="b4c35-115">定义要展开此定义的集合对象必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="b4c35-115">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|
|[<span data-ttu-id="b4c35-116">EnumerableExpansion （格式） 的 EntrySelectedBy SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="b4c35-116">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="b4c35-117">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b4c35-117">Optional element.</span></span><br /><br /> <span data-ttu-id="b4c35-118">指定一组使用如何扩展的集合对象的此定义的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="b4c35-118">Specifies a set of .NET types that use this definition of how collection objects are expanded.</span></span>|
|[<span data-ttu-id="b4c35-119">EnumerableExpansion （格式） 的 EntrySelectedBy 的 TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="b4c35-119">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="b4c35-120">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b4c35-120">Optional element.</span></span><br /><br /> <span data-ttu-id="b4c35-121">指定将使用如何扩展的集合对象的此定义的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="b4c35-121">Specifies a .NET type that uses this definition of how collection objects are expanded.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b4c35-122">父元素</span><span class="sxs-lookup"><span data-stu-id="b4c35-122">Parent Elements</span></span>

|<span data-ttu-id="b4c35-123">元素</span><span class="sxs-lookup"><span data-stu-id="b4c35-123">Element</span></span>|<span data-ttu-id="b4c35-124">描述</span><span class="sxs-lookup"><span data-stu-id="b4c35-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b4c35-125">EnumerableExpansion 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b4c35-125">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="b4c35-126">定义如何特定对象在视图中显示时进行扩展的.NET 集合。</span><span class="sxs-lookup"><span data-stu-id="b4c35-126">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b4c35-127">备注</span><span class="sxs-lookup"><span data-stu-id="b4c35-127">Remarks</span></span>

<span data-ttu-id="b4c35-128">必须指定至少一个类型、 所选内容集或定义项的选择条件。</span><span class="sxs-lookup"><span data-stu-id="b4c35-128">You must specify at least one type, selection set, or selection condition for a definition entry.</span></span> <span data-ttu-id="b4c35-129">可以使用的子元素的数目没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="b4c35-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="b4c35-130">使用选择条件来定义要使用，例如当一个对象具有特定属性的定义中必须存在一个条件或特定属性值或脚本的计算结果为`true`。</span><span class="sxs-lookup"><span data-stu-id="b4c35-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="b4c35-131">有关选择条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="b4c35-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b4c35-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b4c35-132">See Also</span></span>

[<span data-ttu-id="b4c35-133">定义用于显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="b4c35-133">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b4c35-134">EnumerableExpansion 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b4c35-134">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)

[<span data-ttu-id="b4c35-135">EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="b4c35-135">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="b4c35-136">EnumerableExpansion （格式） 的 EntrySelectedBy SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="b4c35-136">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="b4c35-137">EnumerableExpansion （格式） 的 EntrySelectedBy 的 TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="b4c35-137">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="b4c35-138">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="b4c35-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
