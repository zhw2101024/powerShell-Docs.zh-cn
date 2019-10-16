---
title: WideEntry 的 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a13a429c-a31b-4e29-828c-c0c0917b5415
caps.latest.revision: 11
ms.openlocfilehash: baea89e4b259611dfa45b6bcf94fa0bf2df6b9de
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368406"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="67300-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="67300-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="67300-103">指定触发条件的 .NET 类型集。</span><span class="sxs-lookup"><span data-stu-id="67300-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="67300-104">如果此集中的任何类型存在，则满足条件，并使用此大视图的定义显示该对象。</span><span class="sxs-lookup"><span data-stu-id="67300-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the wide view.</span></span>

<span data-ttu-id="67300-105">配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（format） EntrySelectedBy 元素 for WideEntry （Format） SelectionCondition 元素 forEntrySelectedBy for WideEntry （Format） SelectionSetName 元素 for SelectionCondition for EntrySelectedBy for WideEntry （Format）</span><span class="sxs-lookup"><span data-stu-id="67300-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="67300-106">语法</span><span class="sxs-lookup"><span data-stu-id="67300-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="67300-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="67300-107">Attributes and Elements</span></span>

<span data-ttu-id="67300-108">以下各节介绍了 `SelectionSetName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="67300-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="67300-109">属性</span><span class="sxs-lookup"><span data-stu-id="67300-109">Attributes</span></span>

<span data-ttu-id="67300-110">无。</span><span class="sxs-lookup"><span data-stu-id="67300-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="67300-111">子元素</span><span class="sxs-lookup"><span data-stu-id="67300-111">Child Elements</span></span>

<span data-ttu-id="67300-112">无。</span><span class="sxs-lookup"><span data-stu-id="67300-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="67300-113">父元素</span><span class="sxs-lookup"><span data-stu-id="67300-113">Parent Elements</span></span>

|<span data-ttu-id="67300-114">元素</span><span class="sxs-lookup"><span data-stu-id="67300-114">Element</span></span>|<span data-ttu-id="67300-115">描述</span><span class="sxs-lookup"><span data-stu-id="67300-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="67300-116">WideEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="67300-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="67300-117">定义要使用此定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="67300-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="67300-118">文本值</span><span class="sxs-lookup"><span data-stu-id="67300-118">Text Value</span></span>

<span data-ttu-id="67300-119">指定选择集的名称。</span><span class="sxs-lookup"><span data-stu-id="67300-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="67300-120">备注</span><span class="sxs-lookup"><span data-stu-id="67300-120">Remarks</span></span>

<span data-ttu-id="67300-121">选择条件可以指定选择集或 .NET 类型，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="67300-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="67300-122">有关如何使用选择条件的详细信息，请参阅为[数据显示定义条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="67300-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="67300-123">选择集是可由格式设置文件所定义的任何视图使用的常用 .NET 对象组。</span><span class="sxs-lookup"><span data-stu-id="67300-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="67300-124">有关创建和引用选项集的详细信息，请参阅[定义对象集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="67300-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="67300-125">有关大视图的其他组件的详细信息，请参阅[创建宽视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="67300-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="67300-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="67300-126">See Also</span></span>

[<span data-ttu-id="67300-127">创建宽视图</span><span class="sxs-lookup"><span data-stu-id="67300-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="67300-128">定义显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="67300-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="67300-129">定义选择集</span><span class="sxs-lookup"><span data-stu-id="67300-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="67300-130">WideEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="67300-130">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="67300-131">WideEntry 的 SelectionCondition for EntrySelectedBy 的 TypeName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="67300-131">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="67300-132">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="67300-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
