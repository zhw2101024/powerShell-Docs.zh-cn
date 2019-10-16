---
title: ListControl （Format）的 EntrySelectedBy 的 SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff7763c-5ce0-49c1-a480-1249c9f57a13
caps.latest.revision: 11
ms.openlocfilehash: 7fd431b4b1ddecd3a7358c2bf97f299b97162b34
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361996"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="5b9c7-102">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="5b9c7-102">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="5b9c7-103">为列表条目指定一组 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="5b9c7-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="5b9c7-104">对于可为条目指定的选项集数没有限制。</span><span class="sxs-lookup"><span data-stu-id="5b9c7-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="5b9c7-105">配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） ListControl 元素（格式） ListEntries 元素（格式） ListEntry 元素（format） EntrySelectedBy 元素 for ListEntry （Format） SelectionSetName 元素 forEntrySelectedBy for ListEntry （Format）</span><span class="sxs-lookup"><span data-stu-id="5b9c7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5b9c7-106">语法</span><span class="sxs-lookup"><span data-stu-id="5b9c7-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5b9c7-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="5b9c7-107">Attributes and Elements</span></span>

<span data-ttu-id="5b9c7-108">以下各节介绍 `SelectionSetName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5b9c7-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5b9c7-109">属性</span><span class="sxs-lookup"><span data-stu-id="5b9c7-109">Attributes</span></span>

<span data-ttu-id="5b9c7-110">无。</span><span class="sxs-lookup"><span data-stu-id="5b9c7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5b9c7-111">子元素</span><span class="sxs-lookup"><span data-stu-id="5b9c7-111">Child Elements</span></span>

<span data-ttu-id="5b9c7-112">无。</span><span class="sxs-lookup"><span data-stu-id="5b9c7-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5b9c7-113">父元素</span><span class="sxs-lookup"><span data-stu-id="5b9c7-113">Parent Elements</span></span>

|<span data-ttu-id="5b9c7-114">元素</span><span class="sxs-lookup"><span data-stu-id="5b9c7-114">Element</span></span>|<span data-ttu-id="5b9c7-115">描述</span><span class="sxs-lookup"><span data-stu-id="5b9c7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5b9c7-116">ListEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5b9c7-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="5b9c7-117">定义使用此列表项的 .NET 类型或此项要使用的条件。</span><span class="sxs-lookup"><span data-stu-id="5b9c7-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5b9c7-118">文本值</span><span class="sxs-lookup"><span data-stu-id="5b9c7-118">Text Value</span></span>

<span data-ttu-id="5b9c7-119">指定选择集的名称。</span><span class="sxs-lookup"><span data-stu-id="5b9c7-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="5b9c7-120">备注</span><span class="sxs-lookup"><span data-stu-id="5b9c7-120">Remarks</span></span>

<span data-ttu-id="5b9c7-121">每个列表项必须至少定义一个类型名称、选择集或选择条件。</span><span class="sxs-lookup"><span data-stu-id="5b9c7-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="5b9c7-122">当要定义在多个视图中使用的一组对象时，通常使用选择集。</span><span class="sxs-lookup"><span data-stu-id="5b9c7-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="5b9c7-123">例如，您可能希望为同一组对象创建表视图和列表视图。</span><span class="sxs-lookup"><span data-stu-id="5b9c7-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="5b9c7-124">有关定义选择集的详细信息，请参阅为[视图定义对象集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="5b9c7-124">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="5b9c7-125">有关列表视图组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="5b9c7-125">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="5b9c7-126">示例</span><span class="sxs-lookup"><span data-stu-id="5b9c7-126">Example</span></span>

<span data-ttu-id="5b9c7-127">下面的示例演示如何为列表视图的条目指定选择集。</span><span class="sxs-lookup"><span data-stu-id="5b9c7-127">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="5b9c7-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5b9c7-128">See Also</span></span>

[<span data-ttu-id="5b9c7-129">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="5b9c7-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="5b9c7-130">ListEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5b9c7-130">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="5b9c7-131">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="5b9c7-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
