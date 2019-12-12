---
title: 用于视图（格式）的控件的 SelectionCondition 的 PropertyName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92c4237d-c2b2-4908-82ac-f36070f89d26
caps.latest.revision: 6
ms.openlocfilehash: 79859bed3d762948182e03babf71d4270278bae7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362356"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="517ed-102">PropertyName Element for SelectionCondition for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="517ed-102">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="517ed-103">指定触发条件的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="517ed-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="517ed-104">如果该属性存在或其计算结果为 `true`，则满足条件，并使用该条目。</span><span class="sxs-lookup"><span data-stu-id="517ed-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="517ed-105">定义可由视图使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="517ed-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="517ed-106">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 元素（format） Control 元素 for View （format） CustomControl 元素的控件元素，用于控件的 View （format） CustomEntries 元素CustomControl for view （format） CustomEntry 元素 for view （format）元素 for CustomEntries for view （format） EntrySelectedBy 元素 for view （format）元素 for CustomEntry for view （format） SelectionCondition 元素 for view （Format）用于视图的控件的 SelectionCondition 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="517ed-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="517ed-107">语法</span><span class="sxs-lookup"><span data-stu-id="517ed-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="517ed-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="517ed-108">Attributes and Elements</span></span>

<span data-ttu-id="517ed-109">以下各节介绍了 `PropertyName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="517ed-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="517ed-110">属性</span><span class="sxs-lookup"><span data-stu-id="517ed-110">Attributes</span></span>

<span data-ttu-id="517ed-111">无。</span><span class="sxs-lookup"><span data-stu-id="517ed-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="517ed-112">子元素</span><span class="sxs-lookup"><span data-stu-id="517ed-112">Child Elements</span></span>

<span data-ttu-id="517ed-113">无。</span><span class="sxs-lookup"><span data-stu-id="517ed-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="517ed-114">父元素</span><span class="sxs-lookup"><span data-stu-id="517ed-114">Parent Elements</span></span>

|<span data-ttu-id="517ed-115">元素</span><span class="sxs-lookup"><span data-stu-id="517ed-115">Element</span></span>|<span data-ttu-id="517ed-116">描述</span><span class="sxs-lookup"><span data-stu-id="517ed-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="517ed-117">用于视图的控件的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="517ed-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="517ed-118">定义要使用的控件定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="517ed-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="517ed-119">文本值</span><span class="sxs-lookup"><span data-stu-id="517ed-119">Text Value</span></span>

<span data-ttu-id="517ed-120">指定 .NET 属性名称。</span><span class="sxs-lookup"><span data-stu-id="517ed-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="517ed-121">备注</span><span class="sxs-lookup"><span data-stu-id="517ed-121">Remarks</span></span>

<span data-ttu-id="517ed-122">选择条件必须指定至少一个属性名称或脚本，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="517ed-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="517ed-123">有关如何使用选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="517ed-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="517ed-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="517ed-124">See Also</span></span>

[<span data-ttu-id="517ed-125">用于视图的控件的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="517ed-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="517ed-126">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="517ed-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
