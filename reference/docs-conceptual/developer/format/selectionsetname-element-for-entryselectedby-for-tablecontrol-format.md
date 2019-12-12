---
title: TableControl （Format）的 EntrySelectedBy 的 SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368316"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="19198-102">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="19198-102">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="19198-103">指定使用此表视图项的一组 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="19198-103">Specifies a set of .NET types the use this entry of the table view.</span></span> <span data-ttu-id="19198-104">对于可为条目指定的选项集数没有限制。</span><span class="sxs-lookup"><span data-stu-id="19198-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="19198-105">配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） TableControl 元素（格式） TableRowEntries 元素（格式） TableRowEntry 元素（格式） EntrySelectedBy 元素（格式） SelectionSetName 元素EntrySelectedBy for TableRowEntry （Format）</span><span class="sxs-lookup"><span data-stu-id="19198-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) SelectionSetName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="19198-106">语法</span><span class="sxs-lookup"><span data-stu-id="19198-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="19198-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="19198-107">Attributes and Elements</span></span>

<span data-ttu-id="19198-108">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="19198-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="19198-109">属性</span><span class="sxs-lookup"><span data-stu-id="19198-109">Attributes</span></span>

<span data-ttu-id="19198-110">无。</span><span class="sxs-lookup"><span data-stu-id="19198-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="19198-111">子元素</span><span class="sxs-lookup"><span data-stu-id="19198-111">Child Elements</span></span>

<span data-ttu-id="19198-112">无。</span><span class="sxs-lookup"><span data-stu-id="19198-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="19198-113">父元素</span><span class="sxs-lookup"><span data-stu-id="19198-113">Parent Elements</span></span>

|<span data-ttu-id="19198-114">元素</span><span class="sxs-lookup"><span data-stu-id="19198-114">Element</span></span>|<span data-ttu-id="19198-115">描述</span><span class="sxs-lookup"><span data-stu-id="19198-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="19198-116">EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="19198-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="19198-117">定义使用此项的 .NET 类型或此项要使用的条件。</span><span class="sxs-lookup"><span data-stu-id="19198-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="19198-118">文本值</span><span class="sxs-lookup"><span data-stu-id="19198-118">Text Value</span></span>

<span data-ttu-id="19198-119">指定选择集的名称。</span><span class="sxs-lookup"><span data-stu-id="19198-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="19198-120">备注</span><span class="sxs-lookup"><span data-stu-id="19198-120">Remarks</span></span>

<span data-ttu-id="19198-121">当要定义在多个视图中使用的一组对象时，通常使用选择集。</span><span class="sxs-lookup"><span data-stu-id="19198-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="19198-122">例如，您可能希望为同一组对象创建表视图和列表视图。</span><span class="sxs-lookup"><span data-stu-id="19198-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="19198-123">有关定义选择集的详细信息，请参阅为[视图定义对象集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="19198-123">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="19198-124">如果为某个条目指定了选择集，则无法指定类型名称。</span><span class="sxs-lookup"><span data-stu-id="19198-124">If you specify a selection set for an entry, you cannot specify a type name.</span></span> <span data-ttu-id="19198-125">有关如何指定 .NET 类型的详细信息，请参阅[EntrySelectedBy For TableRowEntry （Format）的 TypeName 元素](./typename-element-for-entryselectedby-for-tablecontrol-format.md)。</span><span class="sxs-lookup"><span data-stu-id="19198-125">For more information about how to specify a .NET type, see [TypeName Element for EntrySelectedBy for TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span></span>

<span data-ttu-id="19198-126">有关表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="19198-126">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="19198-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="19198-127">See Also</span></span>

[<span data-ttu-id="19198-128">EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="19198-128">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="19198-129">为视图定义对象集</span><span class="sxs-lookup"><span data-stu-id="19198-129">Defining Sets of objects for a View</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="19198-130">创建表视图</span><span class="sxs-lookup"><span data-stu-id="19198-130">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="19198-131">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="19198-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
