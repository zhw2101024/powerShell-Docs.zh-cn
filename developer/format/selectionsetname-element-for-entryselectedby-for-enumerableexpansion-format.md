---
title: EnumerableExpansion （格式） 的 EntrySelectedBy SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 936d09f2-2c48-49e8-ab2d-0c8729199a2e
caps.latest.revision: 8
ms.openlocfilehash: 8ba8931ea5e34f610878351396cad42023393ad6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862743"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="9e154-102">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="9e154-102">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="9e154-103">指定.NET 类型的情况下此定义展开的组。</span><span class="sxs-lookup"><span data-stu-id="9e154-103">Specifies the set of .NET types that are expanded by this definition.</span></span>

<span data-ttu-id="9e154-104">用于为 EntrySelectedBy EnumerableExpansion （格式） SelectionSetName 元素的配置元素 （格式） DefaultSettings 元素 （格式） EnumerableExpansions 元素 （格式） EnumerableExpansion 元素 （格式） EntrySelectedBy 元素EnumerableExpansion （格式）</span><span class="sxs-lookup"><span data-stu-id="9e154-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9e154-105">语法</span><span class="sxs-lookup"><span data-stu-id="9e154-105">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="9e154-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="9e154-106">Attributes and Elements</span></span>

<span data-ttu-id="9e154-107">以下各节描述了特性、 子元素和父元素的`SelectionSetName`元素。</span><span class="sxs-lookup"><span data-stu-id="9e154-107">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9e154-108">特性</span><span class="sxs-lookup"><span data-stu-id="9e154-108">Attributes</span></span>

<span data-ttu-id="9e154-109">无。</span><span class="sxs-lookup"><span data-stu-id="9e154-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9e154-110">子元素</span><span class="sxs-lookup"><span data-stu-id="9e154-110">Child Elements</span></span>

<span data-ttu-id="9e154-111">无。</span><span class="sxs-lookup"><span data-stu-id="9e154-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9e154-112">父元素</span><span class="sxs-lookup"><span data-stu-id="9e154-112">Parent Elements</span></span>

|<span data-ttu-id="9e154-113">元素</span><span class="sxs-lookup"><span data-stu-id="9e154-113">Element</span></span>|<span data-ttu-id="9e154-114">描述</span><span class="sxs-lookup"><span data-stu-id="9e154-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9e154-115">EnumerableExpansion （格式） 的 EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="9e154-115">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="9e154-116">定义此定义的扩展的.NET 集合对象。</span><span class="sxs-lookup"><span data-stu-id="9e154-116">Defines the .NET collection objects that are expanded by this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9e154-117">文本值</span><span class="sxs-lookup"><span data-stu-id="9e154-117">Text Value</span></span>

<span data-ttu-id="9e154-118">指定所选内容集的名称。</span><span class="sxs-lookup"><span data-stu-id="9e154-118">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="9e154-119">备注</span><span class="sxs-lookup"><span data-stu-id="9e154-119">Remarks</span></span>

<span data-ttu-id="9e154-120">每个定义必须指定一个或多个类型名称、 一个选择集或选择条件。</span><span class="sxs-lookup"><span data-stu-id="9e154-120">Each definition must specify one or more type names, a selection set, or a selection condition.</span></span>

<span data-ttu-id="9e154-121">当你想要在多个视图中定义的一组使用的对象时通常使用的选项集。</span><span class="sxs-lookup"><span data-stu-id="9e154-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="9e154-122">例如，你可能想要创建的表视图和同一组对象的列表视图。</span><span class="sxs-lookup"><span data-stu-id="9e154-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="9e154-123">有关定义的选项集的详细信息，请参阅[定义设置的对象图](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="9e154-123">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9e154-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9e154-124">See Also</span></span>

[<span data-ttu-id="9e154-125">定义的选项集</span><span class="sxs-lookup"><span data-stu-id="9e154-125">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="9e154-126">EnumerableExpansion （格式） 的 EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="9e154-126">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)

[<span data-ttu-id="9e154-127">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="9e154-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
