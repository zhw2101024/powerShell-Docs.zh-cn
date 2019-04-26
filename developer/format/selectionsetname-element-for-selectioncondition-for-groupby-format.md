---
title: GroupBy （格式） 的 SelectionCondition SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063753"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="29211-102">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="29211-102">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="29211-103">指定.NET 类型的触发器条件的集。</span><span class="sxs-lookup"><span data-stu-id="29211-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="29211-104">当存在任何此集中的类型时，满足该条件，并使用此控件显示该对象。</span><span class="sxs-lookup"><span data-stu-id="29211-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="29211-105">定义如何显示一组新对象时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="29211-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="29211-106">GroupBy （格式） 的 GroupBy （格式） CustomEntry 元素 CustomControl CustomEntries 元素的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素CustomControl GroupBy （格式） 的 GroupBy （格式） 的 GroupBy （格式） 的 GroupBy （格式） 的 SelectionCondition SelectionSetName 元素 EntrySelectedBy SelectionCondition 元素 CustomEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="29211-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="29211-107">语法</span><span class="sxs-lookup"><span data-stu-id="29211-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="29211-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="29211-108">Attributes and Elements</span></span>

<span data-ttu-id="29211-109">以下各节描述了特性、 子元素和父元素的`SelectionSetName`元素。</span><span class="sxs-lookup"><span data-stu-id="29211-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="29211-110">属性</span><span class="sxs-lookup"><span data-stu-id="29211-110">Attributes</span></span>

<span data-ttu-id="29211-111">无。</span><span class="sxs-lookup"><span data-stu-id="29211-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="29211-112">子元素</span><span class="sxs-lookup"><span data-stu-id="29211-112">Child Elements</span></span>

<span data-ttu-id="29211-113">无。</span><span class="sxs-lookup"><span data-stu-id="29211-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="29211-114">父元素</span><span class="sxs-lookup"><span data-stu-id="29211-114">Parent Elements</span></span>

|<span data-ttu-id="29211-115">元素</span><span class="sxs-lookup"><span data-stu-id="29211-115">Element</span></span>|<span data-ttu-id="29211-116">说明</span><span class="sxs-lookup"><span data-stu-id="29211-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="29211-117">GroupBy （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="29211-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="29211-118">定义必须存在要使用的控件定义的条件。</span><span class="sxs-lookup"><span data-stu-id="29211-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="29211-119">文本值</span><span class="sxs-lookup"><span data-stu-id="29211-119">Text Value</span></span>

<span data-ttu-id="29211-120">指定所选内容集的名称。</span><span class="sxs-lookup"><span data-stu-id="29211-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="29211-121">备注</span><span class="sxs-lookup"><span data-stu-id="29211-121">Remarks</span></span>

<span data-ttu-id="29211-122">所选内容集是常见的可以使用的格式设置文件定义任何视图的.NET 对象分组。</span><span class="sxs-lookup"><span data-stu-id="29211-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="29211-123">有关创建和引用所选内容集的详细信息，请参阅[定义所选内容设置](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="29211-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="29211-124">当指定此元素时，不能指定[TypeName](./typename-element-for-selectioncondition-for-groupby-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="29211-124">When this element is specified, you cannot specify the [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) element.</span></span> <span data-ttu-id="29211-125">有关定义选择条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="29211-125">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="29211-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="29211-126">See Also</span></span>

[<span data-ttu-id="29211-127">GroupBy （格式） 的 SelectionCondition 的 TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="29211-127">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="29211-128">GroupBy （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="29211-128">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="29211-129">定义何时显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="29211-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="29211-130">定义的选项集</span><span class="sxs-lookup"><span data-stu-id="29211-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="29211-131">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="29211-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
