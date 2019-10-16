---
title: ListEntry 的 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eae67e47-6c60-4741-8430-78d2cb6067b1
caps.latest.revision: 10
ms.openlocfilehash: ccfc0b772ad3b2d1979c7c832a5153de870035d7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368396"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a><span data-ttu-id="f96c5-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="f96c5-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

<span data-ttu-id="f96c5-103">指定触发条件的 .NET 类型集。</span><span class="sxs-lookup"><span data-stu-id="f96c5-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="f96c5-104">如果此集中的任何类型存在，则满足条件，并使用此列表视图的定义显示该对象。</span><span class="sxs-lookup"><span data-stu-id="f96c5-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the list view.</span></span>

<span data-ttu-id="f96c5-105">配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） ListControl 元素（格式） ListEntries 元素（格式） ListEntry 元素（format） EntrySelectedBy 元素 for ListEntry （Format） SelectionCondition 元素 forEntrySelectedBy for ListEntry （Format） SelectionSetName 元素 for SelectionCondition for EntrySelectedBy for ListEntry （Format）</span><span class="sxs-lookup"><span data-stu-id="f96c5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f96c5-106">语法</span><span class="sxs-lookup"><span data-stu-id="f96c5-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f96c5-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="f96c5-107">Attributes and Elements</span></span>

<span data-ttu-id="f96c5-108">以下各节介绍了 `SelectionSetName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f96c5-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f96c5-109">属性</span><span class="sxs-lookup"><span data-stu-id="f96c5-109">Attributes</span></span>

<span data-ttu-id="f96c5-110">无。</span><span class="sxs-lookup"><span data-stu-id="f96c5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f96c5-111">子元素</span><span class="sxs-lookup"><span data-stu-id="f96c5-111">Child Elements</span></span>

<span data-ttu-id="f96c5-112">无。</span><span class="sxs-lookup"><span data-stu-id="f96c5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f96c5-113">父元素</span><span class="sxs-lookup"><span data-stu-id="f96c5-113">Parent Elements</span></span>

|<span data-ttu-id="f96c5-114">元素</span><span class="sxs-lookup"><span data-stu-id="f96c5-114">Element</span></span>|<span data-ttu-id="f96c5-115">描述</span><span class="sxs-lookup"><span data-stu-id="f96c5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f96c5-116">ListEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f96c5-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="f96c5-117">定义使用此列表视图的定义时必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="f96c5-117">Defines the condition that must exist to use this definition of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f96c5-118">文本值</span><span class="sxs-lookup"><span data-stu-id="f96c5-118">Text Value</span></span>

<span data-ttu-id="f96c5-119">指定选择集的名称。</span><span class="sxs-lookup"><span data-stu-id="f96c5-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="f96c5-120">备注</span><span class="sxs-lookup"><span data-stu-id="f96c5-120">Remarks</span></span>

<span data-ttu-id="f96c5-121">选择条件可以指定选择集或 .NET 类型，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="f96c5-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="f96c5-122">有关如何使用选择条件的详细信息，请参阅为[数据显示定义条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="f96c5-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f96c5-123">选择集是可由格式设置文件所定义的任何视图使用的常用 .NET 对象组。</span><span class="sxs-lookup"><span data-stu-id="f96c5-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="f96c5-124">有关创建和引用选项集的详细信息，请参阅[定义对象集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="f96c5-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="f96c5-125">有关列表视图的其他组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="f96c5-125">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f96c5-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f96c5-126">See Also</span></span>

[<span data-ttu-id="f96c5-127">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="f96c5-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="f96c5-128">定义显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="f96c5-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f96c5-129">ListEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f96c5-129">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="f96c5-130">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="f96c5-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
