---
title: 用于配置的控件（格式）的 SelectionCondition 的 SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7dcaeadb-4e79-47a0-96e2-8952af26abbe
caps.latest.revision: 7
ms.openlocfilehash: 5db35a8094ea2bb966c8d6a96802c72f64c05c17
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368276"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="064a7-102">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="064a7-102">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="064a7-103">指定触发条件的 .NET 类型集。</span><span class="sxs-lookup"><span data-stu-id="064a7-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="064a7-104">如果此集中的任何类型存在，则满足条件，并使用此控件显示该对象。</span><span class="sxs-lookup"><span data-stu-id="064a7-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="064a7-105">此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。</span><span class="sxs-lookup"><span data-stu-id="064a7-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="064a7-106">Configuration 元素（格式）控制配置（format） CustomControl 元素的控件的配置（Format）控件元素的元素，用于控件的配置（format） CustomEntries 元素，用于 CustomControl 的控件配置（format） CustomEntry 元素 for CustomControl for EntrySelectedBy 元素 for CustomEntry for 元素 for for 的控件配置（format）用于控件的 SelectionCondition 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="064a7-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="064a7-107">语法</span><span class="sxs-lookup"><span data-stu-id="064a7-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="064a7-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="064a7-108">Attributes and Elements</span></span>

<span data-ttu-id="064a7-109">以下各节介绍了 `SelectionSetName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="064a7-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="064a7-110">属性</span><span class="sxs-lookup"><span data-stu-id="064a7-110">Attributes</span></span>

<span data-ttu-id="064a7-111">无。</span><span class="sxs-lookup"><span data-stu-id="064a7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="064a7-112">子元素</span><span class="sxs-lookup"><span data-stu-id="064a7-112">Child Elements</span></span>

<span data-ttu-id="064a7-113">无。</span><span class="sxs-lookup"><span data-stu-id="064a7-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="064a7-114">父元素</span><span class="sxs-lookup"><span data-stu-id="064a7-114">Parent Elements</span></span>

|<span data-ttu-id="064a7-115">元素</span><span class="sxs-lookup"><span data-stu-id="064a7-115">Element</span></span>|<span data-ttu-id="064a7-116">描述</span><span class="sxs-lookup"><span data-stu-id="064a7-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="064a7-117">用于配置的控件的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="064a7-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="064a7-118">定义要使用的控件定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="064a7-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="064a7-119">文本值</span><span class="sxs-lookup"><span data-stu-id="064a7-119">Text Value</span></span>

<span data-ttu-id="064a7-120">指定选择集的名称。</span><span class="sxs-lookup"><span data-stu-id="064a7-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="064a7-121">备注</span><span class="sxs-lookup"><span data-stu-id="064a7-121">Remarks</span></span>

<span data-ttu-id="064a7-122">选择集是可由格式设置文件所定义的任何视图使用的常用 .NET 对象组。</span><span class="sxs-lookup"><span data-stu-id="064a7-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="064a7-123">有关创建和引用选项集的详细信息，请参阅[定义对象集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="064a7-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="064a7-124">选择条件可以指定选择集或 .NET 类型，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="064a7-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="064a7-125">有关如何使用选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="064a7-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="064a7-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="064a7-126">See Also</span></span>

[<span data-ttu-id="064a7-127">用于配置的控件的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="064a7-127">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="064a7-128">定义显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="064a7-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="064a7-129">定义选择集</span><span class="sxs-lookup"><span data-stu-id="064a7-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="064a7-130">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="064a7-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
