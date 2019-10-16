---
title: WideEntry 的 SelectionCondition for EntrySelectedBy 的 PropertyName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 340abb12-6df1-42f4-bdae-b0509c90952c
caps.latest.revision: 11
ms.openlocfilehash: 196877b97db9ed0592e357486c1318dc1e7efd31
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362236"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="4c64d-102">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="4c64d-102">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="4c64d-103">指定触发条件的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="4c64d-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="4c64d-104">如果存在此属性，或者其计算结果为 `true`，则满足条件，并使用定义。</span><span class="sxs-lookup"><span data-stu-id="4c64d-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="4c64d-105">配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（format） EntrySelectedBy 元素 for WideEntry （Format） SelectionCondition 元素 forSelectionCondition for EntrySelectedBy for WideEntry 的 WideEntry （Format） PropertyName 元素的 EntrySelectedBy （Format）</span><span class="sxs-lookup"><span data-stu-id="4c64d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4c64d-106">语法</span><span class="sxs-lookup"><span data-stu-id="4c64d-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a><span data-ttu-id="4c64d-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="4c64d-107">Attributes and Elements</span></span>

<span data-ttu-id="4c64d-108">以下各节介绍了 `PropertyName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4c64d-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4c64d-109">属性</span><span class="sxs-lookup"><span data-stu-id="4c64d-109">Attributes</span></span>

<span data-ttu-id="4c64d-110">无。</span><span class="sxs-lookup"><span data-stu-id="4c64d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4c64d-111">子元素</span><span class="sxs-lookup"><span data-stu-id="4c64d-111">Child Elements</span></span>

<span data-ttu-id="4c64d-112">无。</span><span class="sxs-lookup"><span data-stu-id="4c64d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4c64d-113">父元素</span><span class="sxs-lookup"><span data-stu-id="4c64d-113">Parent Elements</span></span>

|<span data-ttu-id="4c64d-114">元素</span><span class="sxs-lookup"><span data-stu-id="4c64d-114">Element</span></span>|<span data-ttu-id="4c64d-115">描述</span><span class="sxs-lookup"><span data-stu-id="4c64d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4c64d-116">WideEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4c64d-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="4c64d-117">定义要使用此定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="4c64d-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4c64d-118">文本值</span><span class="sxs-lookup"><span data-stu-id="4c64d-118">Text Value</span></span>

<span data-ttu-id="4c64d-119">指定 .NET 属性名称。</span><span class="sxs-lookup"><span data-stu-id="4c64d-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="4c64d-120">备注</span><span class="sxs-lookup"><span data-stu-id="4c64d-120">Remarks</span></span>

<span data-ttu-id="4c64d-121">选择条件必须指定至少一个要计算的属性名称或脚本，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="4c64d-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="4c64d-122">有关如何使用选择条件的详细信息，请参阅为[数据显示定义条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="4c64d-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="4c64d-123">有关大视图的其他组件的详细信息，请参阅[宽视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="4c64d-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4c64d-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4c64d-124">See Also</span></span>

[<span data-ttu-id="4c64d-125">创建宽视图</span><span class="sxs-lookup"><span data-stu-id="4c64d-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="4c64d-126">定义显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="4c64d-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="4c64d-127">WideEntry 的 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4c64d-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="4c64d-128">WideEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4c64d-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="4c64d-129">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="4c64d-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
