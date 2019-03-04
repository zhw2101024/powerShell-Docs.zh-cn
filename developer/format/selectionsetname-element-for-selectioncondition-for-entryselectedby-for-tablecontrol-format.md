---
title: TableControl （格式） 的 EntrySelectedBy 的 SelectionCondition SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ae4d6b-dc95-4a1d-8e32-31ff084a951f
caps.latest.revision: 10
ms.openlocfilehash: edb163f2b0b5129bd741677dce882888d9bbfd89
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863273"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="c55a6-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c55a6-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="c55a6-103">指定.NET 类型的触发器条件的集。</span><span class="sxs-lookup"><span data-stu-id="c55a6-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="c55a6-104">当存在任何此集中的类型时，满足该条件，并通过使用此定义的表视图中显示该对象。</span><span class="sxs-lookup"><span data-stu-id="c55a6-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the table view.</span></span>

<span data-ttu-id="c55a6-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableRowEntries 元素 （格式） TableRowEntry 元素 （格式） EntrySelectedBy 元素 TableRowEntry （格式）有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition TableRowEntry （格式） SelectionSetName 元素 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="c55a6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c55a6-106">语法</span><span class="sxs-lookup"><span data-stu-id="c55a6-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c55a6-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="c55a6-107">Attributes and Elements</span></span>

<span data-ttu-id="c55a6-108">以下各节描述了特性、 子元素和父元素的`SelectionSetName`元素。</span><span class="sxs-lookup"><span data-stu-id="c55a6-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c55a6-109">特性</span><span class="sxs-lookup"><span data-stu-id="c55a6-109">Attributes</span></span>

<span data-ttu-id="c55a6-110">无。</span><span class="sxs-lookup"><span data-stu-id="c55a6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c55a6-111">子元素</span><span class="sxs-lookup"><span data-stu-id="c55a6-111">Child Elements</span></span>

<span data-ttu-id="c55a6-112">无。</span><span class="sxs-lookup"><span data-stu-id="c55a6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c55a6-113">父元素</span><span class="sxs-lookup"><span data-stu-id="c55a6-113">Parent Elements</span></span>

|<span data-ttu-id="c55a6-114">元素</span><span class="sxs-lookup"><span data-stu-id="c55a6-114">Element</span></span>|<span data-ttu-id="c55a6-115">描述</span><span class="sxs-lookup"><span data-stu-id="c55a6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c55a6-116">TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="c55a6-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="c55a6-117">定义必须存在要用于此定义的表视图的条件。</span><span class="sxs-lookup"><span data-stu-id="c55a6-117">Defines the condition that must exist to use for this definition of the table view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c55a6-118">文本值</span><span class="sxs-lookup"><span data-stu-id="c55a6-118">Text Value</span></span>

<span data-ttu-id="c55a6-119">指定所选内容集的名称。</span><span class="sxs-lookup"><span data-stu-id="c55a6-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="c55a6-120">备注</span><span class="sxs-lookup"><span data-stu-id="c55a6-120">Remarks</span></span>

<span data-ttu-id="c55a6-121">选择条件可以指定所选内容集或.NET 类型，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="c55a6-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="c55a6-122">有关如何使用选择条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="c55a6-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="c55a6-123">所选内容集是常见的可以使用的格式设置文件定义任何视图的.NET 对象分组。</span><span class="sxs-lookup"><span data-stu-id="c55a6-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="c55a6-124">有关创建和引用所选内容集的详细信息，请参阅[定义设置的对象](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="c55a6-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="c55a6-125">有关较宽的视图的其他组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="c55a6-125">For more information about other components of a wide view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c55a6-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c55a6-126">See Also</span></span>

[<span data-ttu-id="c55a6-127">创建表视图</span><span class="sxs-lookup"><span data-stu-id="c55a6-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="c55a6-128">定义何时显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="c55a6-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="c55a6-129">有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 的 TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="c55a6-129">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="c55a6-130">TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="c55a6-130">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="c55a6-131">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="c55a6-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
