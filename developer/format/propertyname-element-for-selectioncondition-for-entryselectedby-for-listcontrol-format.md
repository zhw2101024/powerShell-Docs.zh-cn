---
title: PropertyName 元素的 ListControl （格式） 的 EntrySelectedBy SelectionCondition |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71c3f1f6-6fe2-42f1-8260-6974d3871748
caps.latest.revision: 11
ms.openlocfilehash: 7d526372cf80327b3fb9b79b6e83429c57780183
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064877"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="475fc-102">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="475fc-102">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="475fc-103">指定触发条件的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="475fc-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="475fc-104">存在此属性时或当计算结果为`true`、 满足该条件，以及使用列表项。</span><span class="sxs-lookup"><span data-stu-id="475fc-104">When this property is present or when it evaluates to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="475fc-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素 （格式） ListEntry 元素 （格式） EntrySelectedBy 元素 ListEntry （格式） SelectionCondition 元素EntrySelectedBy ListEntry （格式） 的 ListEntry （格式） 的 EntrySelectedBy SelectionCondition PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="475fc-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="475fc-106">语法</span><span class="sxs-lookup"><span data-stu-id="475fc-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="475fc-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="475fc-107">Attributes and Elements</span></span>

<span data-ttu-id="475fc-108">以下各节描述了特性、 子元素和父元素的`PropertyName`元素。</span><span class="sxs-lookup"><span data-stu-id="475fc-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="475fc-109">属性</span><span class="sxs-lookup"><span data-stu-id="475fc-109">Attributes</span></span>

<span data-ttu-id="475fc-110">无。</span><span class="sxs-lookup"><span data-stu-id="475fc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="475fc-111">子元素</span><span class="sxs-lookup"><span data-stu-id="475fc-111">Child Elements</span></span>

<span data-ttu-id="475fc-112">无。</span><span class="sxs-lookup"><span data-stu-id="475fc-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="475fc-113">父元素</span><span class="sxs-lookup"><span data-stu-id="475fc-113">Parent Elements</span></span>

|<span data-ttu-id="475fc-114">元素</span><span class="sxs-lookup"><span data-stu-id="475fc-114">Element</span></span>|<span data-ttu-id="475fc-115">说明</span><span class="sxs-lookup"><span data-stu-id="475fc-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="475fc-116">ListEntry （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="475fc-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="475fc-117">定义要使用此列表项中必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="475fc-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="475fc-118">文本值</span><span class="sxs-lookup"><span data-stu-id="475fc-118">Text Value</span></span>

<span data-ttu-id="475fc-119">指定.NET 属性名称。</span><span class="sxs-lookup"><span data-stu-id="475fc-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="475fc-120">备注</span><span class="sxs-lookup"><span data-stu-id="475fc-120">Remarks</span></span>

<span data-ttu-id="475fc-121">选择条件必须指定至少一个属性名称或脚本块，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="475fc-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="475fc-122">有关如何使用选择条件的详细信息，请参阅[时视图条目定义条件或使用项](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="475fc-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="475fc-123">列表视图的其他组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="475fc-123">For more information about other components of a list view, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="475fc-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="475fc-124">See Also</span></span>

[<span data-ttu-id="475fc-125">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="475fc-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="475fc-126">定义条件的数据时显示</span><span class="sxs-lookup"><span data-stu-id="475fc-126">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="475fc-127">ListEntry 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="475fc-127">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="475fc-128">有关 ListEntry （格式） 的 EntrySelectedBy SelectionCondition 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="475fc-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="475fc-129">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="475fc-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
