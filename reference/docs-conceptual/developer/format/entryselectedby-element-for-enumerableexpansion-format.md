---
title: EnumerableExpansion 的 EntrySelectedBy 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368796"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a><span data-ttu-id="90c6a-102">EntrySelectedBy Element for EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="90c6a-102">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="90c6a-103">定义使用此定义的 .NET 类型或要使用此定义时必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="90c6a-103">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="90c6a-104">EnumerableExpansion 的配置元素（格式） DefaultSettings 元素（格式） EnumerableExpansions 元素（格式） EnumerableExpansion 元素（格式） EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="90c6a-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="90c6a-105">语法</span><span class="sxs-lookup"><span data-stu-id="90c6a-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="90c6a-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="90c6a-106">Attributes and Elements</span></span>

<span data-ttu-id="90c6a-107">以下各节介绍了 `EntrySelectedBy` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="90c6a-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="90c6a-108">属性</span><span class="sxs-lookup"><span data-stu-id="90c6a-108">Attributes</span></span>

<span data-ttu-id="90c6a-109">无。</span><span class="sxs-lookup"><span data-stu-id="90c6a-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="90c6a-110">子元素</span><span class="sxs-lookup"><span data-stu-id="90c6a-110">Child Elements</span></span>

|<span data-ttu-id="90c6a-111">元素</span><span class="sxs-lookup"><span data-stu-id="90c6a-111">Element</span></span>|<span data-ttu-id="90c6a-112">描述</span><span class="sxs-lookup"><span data-stu-id="90c6a-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="90c6a-113">EnumerableExpansion 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="90c6a-113">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="90c6a-114">可选元素。</span><span class="sxs-lookup"><span data-stu-id="90c6a-114">Optional element.</span></span><br /><br /> <span data-ttu-id="90c6a-115">定义扩展此定义的集合对象时必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="90c6a-115">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|
|[<span data-ttu-id="90c6a-116">EnumerableExpansion 的 EntrySelectedBy 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="90c6a-116">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="90c6a-117">可选元素。</span><span class="sxs-lookup"><span data-stu-id="90c6a-117">Optional element.</span></span><br /><br /> <span data-ttu-id="90c6a-118">指定一组使用此定义如何扩展集合对象的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="90c6a-118">Specifies a set of .NET types that use this definition of how collection objects are expanded.</span></span>|
|[<span data-ttu-id="90c6a-119">EnumerableExpansion 的 EntrySelectedBy 的 TypeName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="90c6a-119">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="90c6a-120">可选元素。</span><span class="sxs-lookup"><span data-stu-id="90c6a-120">Optional element.</span></span><br /><br /> <span data-ttu-id="90c6a-121">指定使用此定义如何扩展集合对象的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="90c6a-121">Specifies a .NET type that uses this definition of how collection objects are expanded.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="90c6a-122">父元素</span><span class="sxs-lookup"><span data-stu-id="90c6a-122">Parent Elements</span></span>

|<span data-ttu-id="90c6a-123">元素</span><span class="sxs-lookup"><span data-stu-id="90c6a-123">Element</span></span>|<span data-ttu-id="90c6a-124">描述</span><span class="sxs-lookup"><span data-stu-id="90c6a-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="90c6a-125">EnumerableExpansion 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="90c6a-125">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="90c6a-126">定义特定 .NET 集合对象在视图中显示的方式。</span><span class="sxs-lookup"><span data-stu-id="90c6a-126">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="90c6a-127">备注</span><span class="sxs-lookup"><span data-stu-id="90c6a-127">Remarks</span></span>

<span data-ttu-id="90c6a-128">必须为定义条目指定至少一个类型、选择集或选择条件。</span><span class="sxs-lookup"><span data-stu-id="90c6a-128">You must specify at least one type, selection set, or selection condition for a definition entry.</span></span> <span data-ttu-id="90c6a-129">您可以使用的子元素数没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="90c6a-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="90c6a-130">选择条件用于定义要使用的定义必须存在的条件，例如当对象具有特定属性或特定属性值或脚本计算结果为 `true`时。</span><span class="sxs-lookup"><span data-stu-id="90c6a-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="90c6a-131">有关选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="90c6a-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="90c6a-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="90c6a-132">See Also</span></span>

[<span data-ttu-id="90c6a-133">定义显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="90c6a-133">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="90c6a-134">EnumerableExpansion 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="90c6a-134">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)

[<span data-ttu-id="90c6a-135">EnumerableExpansion 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="90c6a-135">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="90c6a-136">EnumerableExpansion 的 EntrySelectedBy 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="90c6a-136">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="90c6a-137">EnumerableExpansion 的 EntrySelectedBy 的 TypeName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="90c6a-137">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="90c6a-138">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="90c6a-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
