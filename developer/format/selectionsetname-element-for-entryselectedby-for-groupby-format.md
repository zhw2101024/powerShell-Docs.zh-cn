---
title: GroupBy （格式） 的 EntrySelectedBy SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569c623-2277-49e3-933e-c26262b91cd5
caps.latest.revision: 6
ms.openlocfilehash: 69cd113c444b4e3c5dceabcdfddb439cd1376f6b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858853"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="8b6d8-102">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="8b6d8-102">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="8b6d8-103">指定一组.NET 对象列表项。</span><span class="sxs-lookup"><span data-stu-id="8b6d8-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="8b6d8-104">可以为一个条目指定的所选内容集的数量没有限制。</span><span class="sxs-lookup"><span data-stu-id="8b6d8-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span> <span data-ttu-id="8b6d8-105">定义如何显示一组新对象时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="8b6d8-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="8b6d8-106">GroupBy （格式） 的 GroupBy （格式） CustomEntry 元素 CustomControl CustomEntries 元素的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素CustomControl GroupBy （格式） 的 GroupBy （格式） 的 GroupBy （格式） 的 EntrySelectedBy SelectionSetName 元素 CustomEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="8b6d8-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8b6d8-107">语法</span><span class="sxs-lookup"><span data-stu-id="8b6d8-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8b6d8-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="8b6d8-108">Attributes and Elements</span></span>

<span data-ttu-id="8b6d8-109">以下各节描述了特性、 子元素和父元素的`SelectionSetName`元素。</span><span class="sxs-lookup"><span data-stu-id="8b6d8-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8b6d8-110">特性</span><span class="sxs-lookup"><span data-stu-id="8b6d8-110">Attributes</span></span>

<span data-ttu-id="8b6d8-111">无。</span><span class="sxs-lookup"><span data-stu-id="8b6d8-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8b6d8-112">子元素</span><span class="sxs-lookup"><span data-stu-id="8b6d8-112">Child Elements</span></span>

<span data-ttu-id="8b6d8-113">无。</span><span class="sxs-lookup"><span data-stu-id="8b6d8-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8b6d8-114">父元素</span><span class="sxs-lookup"><span data-stu-id="8b6d8-114">Parent Elements</span></span>

|<span data-ttu-id="8b6d8-115">元素</span><span class="sxs-lookup"><span data-stu-id="8b6d8-115">Element</span></span>|<span data-ttu-id="8b6d8-116">描述</span><span class="sxs-lookup"><span data-stu-id="8b6d8-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8b6d8-117">GroupBy （格式） 的 CustomEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="8b6d8-117">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="8b6d8-118">定义使用此自定义项或要使用此项必须存在的条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="8b6d8-118">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8b6d8-119">文本值</span><span class="sxs-lookup"><span data-stu-id="8b6d8-119">Text Value</span></span>

<span data-ttu-id="8b6d8-120">指定所选内容集的名称。</span><span class="sxs-lookup"><span data-stu-id="8b6d8-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="8b6d8-121">备注</span><span class="sxs-lookup"><span data-stu-id="8b6d8-121">Remarks</span></span>

<span data-ttu-id="8b6d8-122">每个自定义控件定义必须至少一个类型名称、 选择集或定义的选择条件。</span><span class="sxs-lookup"><span data-stu-id="8b6d8-122">Each custom control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="8b6d8-123">当你想要在多个视图中定义的一组使用的对象时通常使用的选项集。</span><span class="sxs-lookup"><span data-stu-id="8b6d8-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="8b6d8-124">例如，你可能想要创建的表视图和同一组对象的列表视图。</span><span class="sxs-lookup"><span data-stu-id="8b6d8-124">For example, you may want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="8b6d8-125">有关定义的选项集的详细信息，请参阅[定义所选内容设置](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="8b6d8-125">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="8b6d8-126">有关组件的自定义控件视图的详细信息，请参阅[创建自定义控件](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="8b6d8-126">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8b6d8-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8b6d8-127">See Also</span></span>

[<span data-ttu-id="8b6d8-128">GroupBy （格式） 的 CustomEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="8b6d8-128">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="8b6d8-129">创建自定义控件</span><span class="sxs-lookup"><span data-stu-id="8b6d8-129">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="8b6d8-130">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="8b6d8-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
