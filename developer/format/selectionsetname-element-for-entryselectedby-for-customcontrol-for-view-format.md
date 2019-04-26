---
title: SelectionSetName 元素的视图 （格式） 的 CustomControl EntrySelectedBy |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063960"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a><span data-ttu-id="7d4aa-102">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="7d4aa-102">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

<span data-ttu-id="7d4aa-103">指定一组.NET 对象列表项。</span><span class="sxs-lookup"><span data-stu-id="7d4aa-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="7d4aa-104">可以为一个条目指定的所选内容集的数量没有限制。</span><span class="sxs-lookup"><span data-stu-id="7d4aa-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="7d4aa-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素 （格式） CustomEntries 元素 CustomControl 视图 （格式） 的视图 （格式） EntrySelectedBy CustomEntries CustomEntry 元素CustomEntry EntrySelectedBy CustomEntry （格式） 的视图 （格式） SelectionSetName 元素的元素</span><span class="sxs-lookup"><span data-stu-id="7d4aa-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7d4aa-106">语法</span><span class="sxs-lookup"><span data-stu-id="7d4aa-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7d4aa-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="7d4aa-107">Attributes and Elements</span></span>

<span data-ttu-id="7d4aa-108">以下各节描述了特性、 子元素和父元素的`SelectionSetName`元素。</span><span class="sxs-lookup"><span data-stu-id="7d4aa-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7d4aa-109">属性</span><span class="sxs-lookup"><span data-stu-id="7d4aa-109">Attributes</span></span>

<span data-ttu-id="7d4aa-110">无。</span><span class="sxs-lookup"><span data-stu-id="7d4aa-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7d4aa-111">子元素</span><span class="sxs-lookup"><span data-stu-id="7d4aa-111">Child Elements</span></span>

<span data-ttu-id="7d4aa-112">无。</span><span class="sxs-lookup"><span data-stu-id="7d4aa-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7d4aa-113">父元素</span><span class="sxs-lookup"><span data-stu-id="7d4aa-113">Parent Elements</span></span>

|<span data-ttu-id="7d4aa-114">元素</span><span class="sxs-lookup"><span data-stu-id="7d4aa-114">Element</span></span>|<span data-ttu-id="7d4aa-115">说明</span><span class="sxs-lookup"><span data-stu-id="7d4aa-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7d4aa-116">视图 （格式） 的 CustomEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="7d4aa-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="7d4aa-117">定义使用此自定义项或要使用此项必须存在的条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="7d4aa-117">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7d4aa-118">文本值</span><span class="sxs-lookup"><span data-stu-id="7d4aa-118">Text Value</span></span>

<span data-ttu-id="7d4aa-119">指定所选内容集的名称。</span><span class="sxs-lookup"><span data-stu-id="7d4aa-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="7d4aa-120">备注</span><span class="sxs-lookup"><span data-stu-id="7d4aa-120">Remarks</span></span>

<span data-ttu-id="7d4aa-121">自定义控件的每个条目必须具有至少一个类型名称、 选择集或定义的选择条件。</span><span class="sxs-lookup"><span data-stu-id="7d4aa-121">Each custom control entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="7d4aa-122">当你想要在多个视图中定义的一组使用的对象时通常使用的选项集。</span><span class="sxs-lookup"><span data-stu-id="7d4aa-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="7d4aa-123">例如，你可能想要创建的表视图和同一组对象的列表视图。</span><span class="sxs-lookup"><span data-stu-id="7d4aa-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="7d4aa-124">有关定义的选项集的详细信息，请参阅[定义所选内容设置](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="7d4aa-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="7d4aa-125">有关组件的自定义控件视图的详细信息，请参阅[创建自定义控件](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="7d4aa-125">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7d4aa-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7d4aa-126">See Also</span></span>

[<span data-ttu-id="7d4aa-127">视图 （格式） 的 CustomEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="7d4aa-127">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="7d4aa-128">自定义控件视图</span><span class="sxs-lookup"><span data-stu-id="7d4aa-128">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="7d4aa-129">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="7d4aa-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
