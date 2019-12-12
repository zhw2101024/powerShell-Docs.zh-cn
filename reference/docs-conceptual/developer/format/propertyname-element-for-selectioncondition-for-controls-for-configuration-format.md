---
title: 用于配置（格式）的控件的 SelectionCondition 的 PropertyName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec048408-e1c6-41ef-b39b-72f4c2dcf2ac
caps.latest.revision: 6
ms.openlocfilehash: b4b2440fdb7171d09fdc16ac7cc4f25ed1a4bb78
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362396"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="baba3-102">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="baba3-102">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="baba3-103">指定触发条件的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="baba3-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="baba3-104">如果该属性存在或其计算结果为 `true`，则满足条件，并使用该条目。</span><span class="sxs-lookup"><span data-stu-id="baba3-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="baba3-105">此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。</span><span class="sxs-lookup"><span data-stu-id="baba3-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="baba3-106">Configuration 元素（格式）控制配置（format） CustomControl 元素的控件的配置（Format）控件元素的元素，以控制 CustomControl for configuration （Format） CustomEntries 元素的配置（Format） CustomEntry 的 CustomControl 的元素，用于配置（Format） EntrySelectedBy 元素 for CustomEntry 的控件（format）元素 for for SelectionCondition for EntrySelectedBy 的控件（Format）用于 ListEntry 的 SelectionCondition for EntrySelectedBy 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="baba3-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="baba3-107">语法</span><span class="sxs-lookup"><span data-stu-id="baba3-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="baba3-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="baba3-108">Attributes and Elements</span></span>

<span data-ttu-id="baba3-109">以下各节介绍了 `PropertyName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="baba3-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="baba3-110">属性</span><span class="sxs-lookup"><span data-stu-id="baba3-110">Attributes</span></span>

<span data-ttu-id="baba3-111">无。</span><span class="sxs-lookup"><span data-stu-id="baba3-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="baba3-112">子元素</span><span class="sxs-lookup"><span data-stu-id="baba3-112">Child Elements</span></span>

<span data-ttu-id="baba3-113">无。</span><span class="sxs-lookup"><span data-stu-id="baba3-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="baba3-114">父元素</span><span class="sxs-lookup"><span data-stu-id="baba3-114">Parent Elements</span></span>

|<span data-ttu-id="baba3-115">元素</span><span class="sxs-lookup"><span data-stu-id="baba3-115">Element</span></span>|<span data-ttu-id="baba3-116">描述</span><span class="sxs-lookup"><span data-stu-id="baba3-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="baba3-117">用于配置的控件的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="baba3-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="baba3-118">定义要使用的公共控件定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="baba3-118">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="baba3-119">文本值</span><span class="sxs-lookup"><span data-stu-id="baba3-119">Text Value</span></span>

<span data-ttu-id="baba3-120">指定 .NET 属性名称。</span><span class="sxs-lookup"><span data-stu-id="baba3-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="baba3-121">备注</span><span class="sxs-lookup"><span data-stu-id="baba3-121">Remarks</span></span>

<span data-ttu-id="baba3-122">选择条件必须指定至少一个属性名称或脚本，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="baba3-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="baba3-123">有关如何使用选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="baba3-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="baba3-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="baba3-124">See Also</span></span>

[<span data-ttu-id="baba3-125">用于配置的控件的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="baba3-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="baba3-126">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="baba3-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
