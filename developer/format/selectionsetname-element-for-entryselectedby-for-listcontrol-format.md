---
title: ListControl （格式） 的 EntrySelectedBy SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff7763c-5ce0-49c1-a480-1249c9f57a13
caps.latest.revision: 11
ms.openlocfilehash: 7fd431b4b1ddecd3a7358c2bf97f299b97162b34
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075556"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="aa511-102">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="aa511-102">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="aa511-103">指定一组.NET 对象列表项。</span><span class="sxs-lookup"><span data-stu-id="aa511-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="aa511-104">可以为一个条目指定的所选内容集的数量没有限制。</span><span class="sxs-lookup"><span data-stu-id="aa511-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="aa511-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素 （格式） ListEntry 元素 （格式） EntrySelectedBy 元素 ListEntry （格式） SelectionSetName 元素EntrySelectedBy 为 ListEntry （格式） 的</span><span class="sxs-lookup"><span data-stu-id="aa511-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="aa511-106">语法</span><span class="sxs-lookup"><span data-stu-id="aa511-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="aa511-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="aa511-107">Attributes and Elements</span></span>

<span data-ttu-id="aa511-108">以下各节描述了特性、 子元素和父元素的`SelectionSetName`元素。</span><span class="sxs-lookup"><span data-stu-id="aa511-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="aa511-109">属性</span><span class="sxs-lookup"><span data-stu-id="aa511-109">Attributes</span></span>

<span data-ttu-id="aa511-110">无。</span><span class="sxs-lookup"><span data-stu-id="aa511-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="aa511-111">子元素</span><span class="sxs-lookup"><span data-stu-id="aa511-111">Child Elements</span></span>

<span data-ttu-id="aa511-112">无。</span><span class="sxs-lookup"><span data-stu-id="aa511-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="aa511-113">父元素</span><span class="sxs-lookup"><span data-stu-id="aa511-113">Parent Elements</span></span>

|<span data-ttu-id="aa511-114">元素</span><span class="sxs-lookup"><span data-stu-id="aa511-114">Element</span></span>|<span data-ttu-id="aa511-115">说明</span><span class="sxs-lookup"><span data-stu-id="aa511-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aa511-116">ListEntry （格式） 的 EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="aa511-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="aa511-117">定义使用此列表项或要使用此项必须存在的条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="aa511-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="aa511-118">文本值</span><span class="sxs-lookup"><span data-stu-id="aa511-118">Text Value</span></span>

<span data-ttu-id="aa511-119">指定所选内容集的名称。</span><span class="sxs-lookup"><span data-stu-id="aa511-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="aa511-120">备注</span><span class="sxs-lookup"><span data-stu-id="aa511-120">Remarks</span></span>

<span data-ttu-id="aa511-121">每个列表项必须具有至少一个类型名称、 选择集或定义的选择条件。</span><span class="sxs-lookup"><span data-stu-id="aa511-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="aa511-122">当你想要在多个视图中定义的一组使用的对象时通常使用的选项集。</span><span class="sxs-lookup"><span data-stu-id="aa511-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="aa511-123">例如，你可能想要创建的表视图和同一组对象的列表视图。</span><span class="sxs-lookup"><span data-stu-id="aa511-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="aa511-124">有关定义的选项集的详细信息，请参阅[定义的视图的对象设置](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="aa511-124">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="aa511-125">列表视图的组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="aa511-125">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="aa511-126">示例</span><span class="sxs-lookup"><span data-stu-id="aa511-126">Example</span></span>

<span data-ttu-id="aa511-127">下面的示例演示如何以指定的选项集列表视图的条目。</span><span class="sxs-lookup"><span data-stu-id="aa511-127">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="aa511-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aa511-128">See Also</span></span>

[<span data-ttu-id="aa511-129">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="aa511-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="aa511-130">ListEntry （格式） 的 EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="aa511-130">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="aa511-131">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="aa511-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
