---
title: 有关 ListEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eae67e47-6c60-4741-8430-78d2cb6067b1
caps.latest.revision: 10
ms.openlocfilehash: ccfc0b772ad3b2d1979c7c832a5153de870035d7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862193"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a><span data-ttu-id="eeae3-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="eeae3-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

<span data-ttu-id="eeae3-103">指定.NET 类型的触发器条件的集。</span><span class="sxs-lookup"><span data-stu-id="eeae3-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="eeae3-104">当存在任何此集中的类型时，满足该条件，并通过使用此定义列表视图显示该对象。</span><span class="sxs-lookup"><span data-stu-id="eeae3-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the list view.</span></span>

<span data-ttu-id="eeae3-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素 （格式） ListEntry 元素 （格式） EntrySelectedBy 元素 ListEntry （格式） SelectionCondition 元素EntrySelectedBy ListEntry （格式） 的 ListEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="eeae3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="eeae3-106">语法</span><span class="sxs-lookup"><span data-stu-id="eeae3-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="eeae3-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="eeae3-107">Attributes and Elements</span></span>

<span data-ttu-id="eeae3-108">以下各节描述了特性、 子元素和父元素的`SelectionSetName`元素。</span><span class="sxs-lookup"><span data-stu-id="eeae3-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="eeae3-109">特性</span><span class="sxs-lookup"><span data-stu-id="eeae3-109">Attributes</span></span>

<span data-ttu-id="eeae3-110">无。</span><span class="sxs-lookup"><span data-stu-id="eeae3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="eeae3-111">子元素</span><span class="sxs-lookup"><span data-stu-id="eeae3-111">Child Elements</span></span>

<span data-ttu-id="eeae3-112">无。</span><span class="sxs-lookup"><span data-stu-id="eeae3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="eeae3-113">父元素</span><span class="sxs-lookup"><span data-stu-id="eeae3-113">Parent Elements</span></span>

|<span data-ttu-id="eeae3-114">元素</span><span class="sxs-lookup"><span data-stu-id="eeae3-114">Element</span></span>|<span data-ttu-id="eeae3-115">描述</span><span class="sxs-lookup"><span data-stu-id="eeae3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="eeae3-116">ListEntry （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="eeae3-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="eeae3-117">定义要使用此列表视图的定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="eeae3-117">Defines the condition that must exist to use this definition of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="eeae3-118">文本值</span><span class="sxs-lookup"><span data-stu-id="eeae3-118">Text Value</span></span>

<span data-ttu-id="eeae3-119">指定所选内容集的名称。</span><span class="sxs-lookup"><span data-stu-id="eeae3-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="eeae3-120">备注</span><span class="sxs-lookup"><span data-stu-id="eeae3-120">Remarks</span></span>

<span data-ttu-id="eeae3-121">选择条件可以指定所选内容集或.NET 类型，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="eeae3-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="eeae3-122">有关如何使用选择条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="eeae3-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="eeae3-123">所选内容集是常见的可以使用的格式设置文件定义任何视图的.NET 对象分组。</span><span class="sxs-lookup"><span data-stu-id="eeae3-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="eeae3-124">有关创建和引用所选内容集的详细信息，请参阅[定义设置的对象](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="eeae3-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="eeae3-125">列表视图的其他组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="eeae3-125">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eeae3-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eeae3-126">See Also</span></span>

[<span data-ttu-id="eeae3-127">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="eeae3-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="eeae3-128">定义何时显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="eeae3-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="eeae3-129">ListEntry （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="eeae3-129">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="eeae3-130">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="eeae3-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
