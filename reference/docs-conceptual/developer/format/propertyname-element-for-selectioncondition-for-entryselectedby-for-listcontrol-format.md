---
title: ListControl 的 SelectionCondition for EntrySelectedBy 的 PropertyName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71c3f1f6-6fe2-42f1-8260-6974d3871748
caps.latest.revision: 11
ms.openlocfilehash: 7d526372cf80327b3fb9b79b6e83429c57780183
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362286"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="c9705-102">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c9705-102">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="c9705-103">指定触发条件的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="c9705-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="c9705-104">如果该属性存在或其计算结果为 `true`，则满足条件，并使用列表项。</span><span class="sxs-lookup"><span data-stu-id="c9705-104">When this property is present or when it evaluates to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="c9705-105">配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） ListControl 元素（格式） ListEntries 元素（格式） ListEntry 元素（format） EntrySelectedBy 元素 for ListEntry （Format） SelectionCondition 元素 forSelectionCondition for EntrySelectedBy for ListEntry 的 ListEntry （Format） PropertyName 元素的 EntrySelectedBy （Format）</span><span class="sxs-lookup"><span data-stu-id="c9705-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c9705-106">语法</span><span class="sxs-lookup"><span data-stu-id="c9705-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c9705-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="c9705-107">Attributes and Elements</span></span>

<span data-ttu-id="c9705-108">以下各节介绍了 `PropertyName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c9705-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c9705-109">属性</span><span class="sxs-lookup"><span data-stu-id="c9705-109">Attributes</span></span>

<span data-ttu-id="c9705-110">无。</span><span class="sxs-lookup"><span data-stu-id="c9705-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c9705-111">子元素</span><span class="sxs-lookup"><span data-stu-id="c9705-111">Child Elements</span></span>

<span data-ttu-id="c9705-112">无。</span><span class="sxs-lookup"><span data-stu-id="c9705-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c9705-113">父元素</span><span class="sxs-lookup"><span data-stu-id="c9705-113">Parent Elements</span></span>

|<span data-ttu-id="c9705-114">元素</span><span class="sxs-lookup"><span data-stu-id="c9705-114">Element</span></span>|<span data-ttu-id="c9705-115">描述</span><span class="sxs-lookup"><span data-stu-id="c9705-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c9705-116">ListEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c9705-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="c9705-117">定义要使用此列表项必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="c9705-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c9705-118">文本值</span><span class="sxs-lookup"><span data-stu-id="c9705-118">Text Value</span></span>

<span data-ttu-id="c9705-119">指定 .NET 属性名称。</span><span class="sxs-lookup"><span data-stu-id="c9705-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="c9705-120">备注</span><span class="sxs-lookup"><span data-stu-id="c9705-120">Remarks</span></span>

<span data-ttu-id="c9705-121">选择条件必须指定至少一个属性名称或脚本块，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="c9705-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="c9705-122">有关如何使用选择条件的详细信息，请参阅[定义使用视图条目或项的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="c9705-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="c9705-123">有关列表视图的其他组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="c9705-123">For more information about other components of a list view, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c9705-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c9705-124">See Also</span></span>

[<span data-ttu-id="c9705-125">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="c9705-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="c9705-126">定义显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="c9705-126">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="c9705-127">ListEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c9705-127">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="c9705-128">ListEntry 的 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c9705-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="c9705-129">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="c9705-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
