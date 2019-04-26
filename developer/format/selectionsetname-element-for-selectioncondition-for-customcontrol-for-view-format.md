---
title: SelectionSetName 元素的视图 （格式） 的 CustomControl SelectionCondition |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52b05a9-762e-4f1c-ad57-9d1710149722
caps.latest.revision: 10
ms.openlocfilehash: 25d46665ca5df3ddf49af5718d513b84c77988c8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075573"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="33452-102">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="33452-102">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="33452-103">指定.NET 类型的触发器条件的集。</span><span class="sxs-lookup"><span data-stu-id="33452-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="33452-104">当存在任何此集中的类型时，满足条件，并且使用此控件显示该对象。</span><span class="sxs-lookup"><span data-stu-id="33452-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="33452-105">定义自定义控件视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="33452-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="33452-106">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素 （格式） CustomEntries 元素 CustomControl 视图 （格式） 的视图 （格式） EntrySelectedBy CustomEntries CustomEntry 元素CustomEntry 视图 （格式） 的元素</span><span class="sxs-lookup"><span data-stu-id="33452-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="33452-107">语法</span><span class="sxs-lookup"><span data-stu-id="33452-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="33452-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="33452-108">Attributes and Elements</span></span>

<span data-ttu-id="33452-109">以下各节描述了特性、 子元素和父元素的`SelectionSetName`元素。</span><span class="sxs-lookup"><span data-stu-id="33452-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="33452-110">属性</span><span class="sxs-lookup"><span data-stu-id="33452-110">Attributes</span></span>

<span data-ttu-id="33452-111">无。</span><span class="sxs-lookup"><span data-stu-id="33452-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="33452-112">子元素</span><span class="sxs-lookup"><span data-stu-id="33452-112">Child Elements</span></span>

<span data-ttu-id="33452-113">无。</span><span class="sxs-lookup"><span data-stu-id="33452-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="33452-114">父元素</span><span class="sxs-lookup"><span data-stu-id="33452-114">Parent Elements</span></span>

|<span data-ttu-id="33452-115">元素</span><span class="sxs-lookup"><span data-stu-id="33452-115">Element</span></span>|<span data-ttu-id="33452-116">说明</span><span class="sxs-lookup"><span data-stu-id="33452-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="33452-117">为视图 （格式） 的 CustomControl EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="33452-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="33452-118">定义必须存在要使用的控件定义的条件。</span><span class="sxs-lookup"><span data-stu-id="33452-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="33452-119">文本值</span><span class="sxs-lookup"><span data-stu-id="33452-119">Text Value</span></span>

<span data-ttu-id="33452-120">指定所选内容集的名称。</span><span class="sxs-lookup"><span data-stu-id="33452-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="33452-121">备注</span><span class="sxs-lookup"><span data-stu-id="33452-121">Remarks</span></span>

<span data-ttu-id="33452-122">所选内容集是常见的可以使用的格式设置文件定义任何视图的.NET 对象分组。</span><span class="sxs-lookup"><span data-stu-id="33452-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="33452-123">有关创建和引用所选内容集的详细信息，请参阅[定义设置的对象](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="33452-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="33452-124">选择条件可以指定所选内容集或.NET 类型，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="33452-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="33452-125">有关如何使用选择条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="33452-125">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="33452-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="33452-126">See Also</span></span>

[<span data-ttu-id="33452-127">为视图 （格式） 的 CustomControl EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="33452-127">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="33452-128">定义何时显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="33452-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="33452-129">定义的选项集</span><span class="sxs-lookup"><span data-stu-id="33452-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="33452-130">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="33452-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
