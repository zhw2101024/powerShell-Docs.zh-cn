---
title: 用于 CustomControl for View （Format）的 SelectionCondition 的 SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52b05a9-762e-4f1c-ad57-9d1710149722
caps.latest.revision: 10
ms.openlocfilehash: 25d46665ca5df3ddf49af5718d513b84c77988c8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368266"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="ca285-102">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="ca285-102">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="ca285-103">指定触发条件的 .NET 类型集。</span><span class="sxs-lookup"><span data-stu-id="ca285-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="ca285-104">如果此集中的任何类型存在，则满足条件，并使用此控件显示该对象。</span><span class="sxs-lookup"><span data-stu-id="ca285-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="ca285-105">定义自定义控件视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="ca285-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="ca285-106">用于 CustomEntry 的 CustomControl for view （format） CustomEntries 元素的配置元素（格式） ViewDefinitions 元素（格式） CustomControl 元素（format） CustomEntries 元素 EntrySelectedByView 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ca285-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ca285-107">语法</span><span class="sxs-lookup"><span data-stu-id="ca285-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ca285-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="ca285-108">Attributes and Elements</span></span>

<span data-ttu-id="ca285-109">以下各节介绍了 `SelectionSetName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ca285-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ca285-110">属性</span><span class="sxs-lookup"><span data-stu-id="ca285-110">Attributes</span></span>

<span data-ttu-id="ca285-111">无。</span><span class="sxs-lookup"><span data-stu-id="ca285-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ca285-112">子元素</span><span class="sxs-lookup"><span data-stu-id="ca285-112">Child Elements</span></span>

<span data-ttu-id="ca285-113">无。</span><span class="sxs-lookup"><span data-stu-id="ca285-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ca285-114">父元素</span><span class="sxs-lookup"><span data-stu-id="ca285-114">Parent Elements</span></span>

|<span data-ttu-id="ca285-115">元素</span><span class="sxs-lookup"><span data-stu-id="ca285-115">Element</span></span>|<span data-ttu-id="ca285-116">描述</span><span class="sxs-lookup"><span data-stu-id="ca285-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ca285-117">用于 View 的 CustomControl 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ca285-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="ca285-118">定义要使用的控件定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="ca285-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ca285-119">文本值</span><span class="sxs-lookup"><span data-stu-id="ca285-119">Text Value</span></span>

<span data-ttu-id="ca285-120">指定选择集的名称。</span><span class="sxs-lookup"><span data-stu-id="ca285-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="ca285-121">备注</span><span class="sxs-lookup"><span data-stu-id="ca285-121">Remarks</span></span>

<span data-ttu-id="ca285-122">选择集是可由格式设置文件所定义的任何视图使用的常用 .NET 对象组。</span><span class="sxs-lookup"><span data-stu-id="ca285-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="ca285-123">有关创建和引用选项集的详细信息，请参阅[定义对象集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="ca285-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="ca285-124">选择条件可以指定选择集或 .NET 类型，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="ca285-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="ca285-125">有关如何使用选择条件的详细信息，请参阅为[数据显示定义条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="ca285-125">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ca285-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ca285-126">See Also</span></span>

[<span data-ttu-id="ca285-127">用于 View 的 CustomControl 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ca285-127">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="ca285-128">定义显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="ca285-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="ca285-129">定义选择集</span><span class="sxs-lookup"><span data-stu-id="ca285-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="ca285-130">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="ca285-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
