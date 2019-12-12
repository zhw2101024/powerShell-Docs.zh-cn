---
title: 用于 CustomControl for View （Format）的 EntrySelectedBy 的 SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364746"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a><span data-ttu-id="ad5cd-102">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="ad5cd-102">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

<span data-ttu-id="ad5cd-103">为列表条目指定一组 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="ad5cd-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="ad5cd-104">对于可为条目指定的选项集数没有限制。</span><span class="sxs-lookup"><span data-stu-id="ad5cd-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="ad5cd-105">用于 CustomEntry 的 CustomControl for view （format） CustomEntries 元素的配置元素（格式） ViewDefinitions 元素（格式） CustomControl 元素（format） CustomEntries 元素 EntrySelectedByCustomEntry 的 EntrySelectedBy 的 CustomEntry for View （Format） SelectionSetName 元素的元素</span><span class="sxs-lookup"><span data-stu-id="ad5cd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ad5cd-106">语法</span><span class="sxs-lookup"><span data-stu-id="ad5cd-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ad5cd-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="ad5cd-107">Attributes and Elements</span></span>

<span data-ttu-id="ad5cd-108">以下各节介绍了 `SelectionSetName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ad5cd-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ad5cd-109">属性</span><span class="sxs-lookup"><span data-stu-id="ad5cd-109">Attributes</span></span>

<span data-ttu-id="ad5cd-110">无。</span><span class="sxs-lookup"><span data-stu-id="ad5cd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ad5cd-111">子元素</span><span class="sxs-lookup"><span data-stu-id="ad5cd-111">Child Elements</span></span>

<span data-ttu-id="ad5cd-112">无。</span><span class="sxs-lookup"><span data-stu-id="ad5cd-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ad5cd-113">父元素</span><span class="sxs-lookup"><span data-stu-id="ad5cd-113">Parent Elements</span></span>

|<span data-ttu-id="ad5cd-114">元素</span><span class="sxs-lookup"><span data-stu-id="ad5cd-114">Element</span></span>|<span data-ttu-id="ad5cd-115">描述</span><span class="sxs-lookup"><span data-stu-id="ad5cd-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ad5cd-116">用于视图的 CustomEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ad5cd-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="ad5cd-117">定义使用此自定义项的 .NET 类型或此项要使用的条件。</span><span class="sxs-lookup"><span data-stu-id="ad5cd-117">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ad5cd-118">文本值</span><span class="sxs-lookup"><span data-stu-id="ad5cd-118">Text Value</span></span>

<span data-ttu-id="ad5cd-119">指定选择集的名称。</span><span class="sxs-lookup"><span data-stu-id="ad5cd-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="ad5cd-120">备注</span><span class="sxs-lookup"><span data-stu-id="ad5cd-120">Remarks</span></span>

<span data-ttu-id="ad5cd-121">每个自定义控件项必须至少定义一个类型名称、选择集或选择条件。</span><span class="sxs-lookup"><span data-stu-id="ad5cd-121">Each custom control entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="ad5cd-122">当要定义在多个视图中使用的一组对象时，通常使用选择集。</span><span class="sxs-lookup"><span data-stu-id="ad5cd-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="ad5cd-123">例如，您可能希望为同一组对象创建表视图和列表视图。</span><span class="sxs-lookup"><span data-stu-id="ad5cd-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="ad5cd-124">有关定义选择集的详细信息，请参阅[定义选择集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="ad5cd-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="ad5cd-125">有关自定义控件视图组件的详细信息，请参阅[创建自定义控件](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="ad5cd-125">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ad5cd-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ad5cd-126">See Also</span></span>

[<span data-ttu-id="ad5cd-127">用于视图的 CustomEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ad5cd-127">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ad5cd-128">自定义控件视图</span><span class="sxs-lookup"><span data-stu-id="ad5cd-128">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="ad5cd-129">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="ad5cd-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
