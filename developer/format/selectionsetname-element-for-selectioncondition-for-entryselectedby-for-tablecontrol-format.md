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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064044"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="426de-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="426de-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="426de-103">指定.NET 类型的触发器条件的集。</span><span class="sxs-lookup"><span data-stu-id="426de-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="426de-104">当存在任何此集中的类型时，满足该条件，并通过使用此定义的表视图中显示该对象。</span><span class="sxs-lookup"><span data-stu-id="426de-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the table view.</span></span>

<span data-ttu-id="426de-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableRowEntries 元素 （格式） TableRowEntry 元素 （格式） EntrySelectedBy 元素 TableRowEntry （格式）有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition TableRowEntry （格式） SelectionSetName 元素 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="426de-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="426de-106">语法</span><span class="sxs-lookup"><span data-stu-id="426de-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="426de-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="426de-107">Attributes and Elements</span></span>

<span data-ttu-id="426de-108">以下各节描述了特性、 子元素和父元素的`SelectionSetName`元素。</span><span class="sxs-lookup"><span data-stu-id="426de-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="426de-109">属性</span><span class="sxs-lookup"><span data-stu-id="426de-109">Attributes</span></span>

<span data-ttu-id="426de-110">无。</span><span class="sxs-lookup"><span data-stu-id="426de-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="426de-111">子元素</span><span class="sxs-lookup"><span data-stu-id="426de-111">Child Elements</span></span>

<span data-ttu-id="426de-112">无。</span><span class="sxs-lookup"><span data-stu-id="426de-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="426de-113">父元素</span><span class="sxs-lookup"><span data-stu-id="426de-113">Parent Elements</span></span>

|<span data-ttu-id="426de-114">元素</span><span class="sxs-lookup"><span data-stu-id="426de-114">Element</span></span>|<span data-ttu-id="426de-115">说明</span><span class="sxs-lookup"><span data-stu-id="426de-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="426de-116">TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="426de-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="426de-117">定义必须存在要用于此定义的表视图的条件。</span><span class="sxs-lookup"><span data-stu-id="426de-117">Defines the condition that must exist to use for this definition of the table view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="426de-118">文本值</span><span class="sxs-lookup"><span data-stu-id="426de-118">Text Value</span></span>

<span data-ttu-id="426de-119">指定所选内容集的名称。</span><span class="sxs-lookup"><span data-stu-id="426de-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="426de-120">备注</span><span class="sxs-lookup"><span data-stu-id="426de-120">Remarks</span></span>

<span data-ttu-id="426de-121">选择条件可以指定所选内容集或.NET 类型，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="426de-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="426de-122">有关如何使用选择条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="426de-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="426de-123">所选内容集是常见的可以使用的格式设置文件定义任何视图的.NET 对象分组。</span><span class="sxs-lookup"><span data-stu-id="426de-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="426de-124">有关创建和引用所选内容集的详细信息，请参阅[定义设置的对象](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="426de-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="426de-125">有关较宽的视图的其他组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="426de-125">For more information about other components of a wide view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="426de-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="426de-126">See Also</span></span>

[<span data-ttu-id="426de-127">创建表视图</span><span class="sxs-lookup"><span data-stu-id="426de-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="426de-128">定义何时显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="426de-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="426de-129">有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 的 TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="426de-129">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="426de-130">TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="426de-130">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="426de-131">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="426de-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
