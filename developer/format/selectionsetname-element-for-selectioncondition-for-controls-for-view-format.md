---
title: 视图 （格式） 的控件的 SelectionCondition SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: daea8c6f-873a-4639-9eee-599642822958
caps.latest.revision: 6
ms.openlocfilehash: 697f2ea284393ebddd77a862c408f27f3d332900
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063881"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="94300-102">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="94300-102">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="94300-103">指定.NET 类型的触发器条件的集。</span><span class="sxs-lookup"><span data-stu-id="94300-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="94300-104">当存在任何此集中的类型时，满足条件，并且使用此控件显示该对象。</span><span class="sxs-lookup"><span data-stu-id="94300-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="94300-105">定义一个视图，可以使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="94300-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="94300-106">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 控件元素 （格式） 控制元素的控件的视图 （格式） CustomEntries 元素的控件的控件的视图 （格式） CustomControl 元素CustomControl CustomEntries CustomEntry EntrySelectedBy 视图 （控件的视图 （格式） SelectionCondition 元素的控件的视图 （格式） EntrySelectedBy 元素的控件的视图 （格式） CustomEntry 元素的控件SelectionCondition 视图 （格式） 的控件的格式） SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="94300-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="94300-107">语法</span><span class="sxs-lookup"><span data-stu-id="94300-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="94300-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="94300-108">Attributes and Elements</span></span>

<span data-ttu-id="94300-109">以下各节描述了特性、 子元素和父元素的`SelectionSetName`元素。</span><span class="sxs-lookup"><span data-stu-id="94300-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="94300-110">属性</span><span class="sxs-lookup"><span data-stu-id="94300-110">Attributes</span></span>

<span data-ttu-id="94300-111">无。</span><span class="sxs-lookup"><span data-stu-id="94300-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="94300-112">子元素</span><span class="sxs-lookup"><span data-stu-id="94300-112">Child Elements</span></span>

<span data-ttu-id="94300-113">无。</span><span class="sxs-lookup"><span data-stu-id="94300-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="94300-114">父元素</span><span class="sxs-lookup"><span data-stu-id="94300-114">Parent Elements</span></span>

|<span data-ttu-id="94300-115">元素</span><span class="sxs-lookup"><span data-stu-id="94300-115">Element</span></span>|<span data-ttu-id="94300-116">说明</span><span class="sxs-lookup"><span data-stu-id="94300-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="94300-117">视图 （格式） 的控件的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="94300-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="94300-118">定义必须存在要使用的控件定义的条件。</span><span class="sxs-lookup"><span data-stu-id="94300-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="94300-119">文本值</span><span class="sxs-lookup"><span data-stu-id="94300-119">Text Value</span></span>

<span data-ttu-id="94300-120">指定所选内容集的名称。</span><span class="sxs-lookup"><span data-stu-id="94300-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="94300-121">备注</span><span class="sxs-lookup"><span data-stu-id="94300-121">Remarks</span></span>

<span data-ttu-id="94300-122">所选内容集是常见的可以使用的格式设置文件定义任何视图的.NET 对象分组。</span><span class="sxs-lookup"><span data-stu-id="94300-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="94300-123">有关创建和引用所选内容集的详细信息，请参阅[定义所选内容设置](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="94300-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="94300-124">选择条件可以指定所选内容集或.NET 类型，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="94300-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="94300-125">有关如何使用选择条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="94300-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="94300-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="94300-126">See Also</span></span>

[<span data-ttu-id="94300-127">视图 （格式） 的控件的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="94300-127">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="94300-128">定义何时显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="94300-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="94300-129">定义的选项集</span><span class="sxs-lookup"><span data-stu-id="94300-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="94300-130">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="94300-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
