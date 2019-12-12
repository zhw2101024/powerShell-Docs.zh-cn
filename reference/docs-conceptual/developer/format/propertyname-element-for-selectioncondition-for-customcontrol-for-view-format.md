---
title: View 的 SelectionCondition for CustomControl 的 PropertyName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc48a417-2083-46d4-ac38-16c12e65b6b9
caps.latest.revision: 7
ms.openlocfilehash: e08037d5d051d3be51e90193c7e87cc2e738f78a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362346"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="dacf8-102">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="dacf8-102">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="dacf8-103">指定触发条件的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="dacf8-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="dacf8-104">如果该属性存在或其计算结果为 `true`，则满足条件，并使用定义。</span><span class="sxs-lookup"><span data-stu-id="dacf8-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="dacf8-105">定义自定义控件视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="dacf8-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="dacf8-106">Configuration Element （Format） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素 for View （format） CustomEntries 元素 for CustomControl for CustomEntry for CustomEntries for View （Format） CustomControl 元素 for view （Format） CustomItem 元素 for CustomEntry for CustomControl for CustomEntry for CustomControl for SelectionCondition for EntrySelectedBy for view （format） PropertyName 的 CustomControl 元素View 的 SelectionCondition for CustomControl 的元素（格式）</span><span class="sxs-lookup"><span data-stu-id="dacf8-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dacf8-107">语法</span><span class="sxs-lookup"><span data-stu-id="dacf8-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dacf8-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="dacf8-108">Attributes and Elements</span></span>

<span data-ttu-id="dacf8-109">以下各节介绍了 `PropertyName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="dacf8-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dacf8-110">属性</span><span class="sxs-lookup"><span data-stu-id="dacf8-110">Attributes</span></span>

<span data-ttu-id="dacf8-111">无。</span><span class="sxs-lookup"><span data-stu-id="dacf8-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dacf8-112">子元素</span><span class="sxs-lookup"><span data-stu-id="dacf8-112">Child Elements</span></span>

<span data-ttu-id="dacf8-113">无。</span><span class="sxs-lookup"><span data-stu-id="dacf8-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dacf8-114">父元素</span><span class="sxs-lookup"><span data-stu-id="dacf8-114">Parent Elements</span></span>

|<span data-ttu-id="dacf8-115">元素</span><span class="sxs-lookup"><span data-stu-id="dacf8-115">Element</span></span>|<span data-ttu-id="dacf8-116">描述</span><span class="sxs-lookup"><span data-stu-id="dacf8-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dacf8-117">用于 View 的 CustomControl 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="dacf8-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="dacf8-118">定义要使用的控件定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="dacf8-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="dacf8-119">文本值</span><span class="sxs-lookup"><span data-stu-id="dacf8-119">Text Value</span></span>

<span data-ttu-id="dacf8-120">指定 .NET 属性名称。</span><span class="sxs-lookup"><span data-stu-id="dacf8-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="dacf8-121">备注</span><span class="sxs-lookup"><span data-stu-id="dacf8-121">Remarks</span></span>

<span data-ttu-id="dacf8-122">选择条件必须指定至少一个属性名称或脚本，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="dacf8-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="dacf8-123">有关如何使用选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="dacf8-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dacf8-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dacf8-124">See Also</span></span>

[<span data-ttu-id="dacf8-125">用于 View 的 CustomControl 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="dacf8-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="dacf8-126">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="dacf8-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
