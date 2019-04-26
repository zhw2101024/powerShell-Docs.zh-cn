---
title: PropertyName 元素为 WideEntry （格式） 的 EntrySelectedBy SelectionCondition |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 340abb12-6df1-42f4-bdae-b0509c90952c
caps.latest.revision: 11
ms.openlocfilehash: 196877b97db9ed0592e357486c1318dc1e7efd31
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064673"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="7e3ee-102">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="7e3ee-102">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="7e3ee-103">指定触发条件的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="7e3ee-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="7e3ee-104">存在此属性时或当计算结果为`true`、 满足该条件，以及使用该定义。</span><span class="sxs-lookup"><span data-stu-id="7e3ee-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="7e3ee-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） WideControl 元素 （格式） WideEntries 元素 （格式） WideEntry 元素 （格式） EntrySelectedBy 元素 WideEntry （格式） SelectionCondition 元素EntrySelectedBy WideEntry （格式） 的 WideEntry （格式） 的 EntrySelectedBy SelectionCondition PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="7e3ee-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7e3ee-106">语法</span><span class="sxs-lookup"><span data-stu-id="7e3ee-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a><span data-ttu-id="7e3ee-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="7e3ee-107">Attributes and Elements</span></span>

<span data-ttu-id="7e3ee-108">以下各节描述了特性、 子元素和父元素的`PropertyName`元素。</span><span class="sxs-lookup"><span data-stu-id="7e3ee-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7e3ee-109">属性</span><span class="sxs-lookup"><span data-stu-id="7e3ee-109">Attributes</span></span>

<span data-ttu-id="7e3ee-110">无。</span><span class="sxs-lookup"><span data-stu-id="7e3ee-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7e3ee-111">子元素</span><span class="sxs-lookup"><span data-stu-id="7e3ee-111">Child Elements</span></span>

<span data-ttu-id="7e3ee-112">无。</span><span class="sxs-lookup"><span data-stu-id="7e3ee-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7e3ee-113">父元素</span><span class="sxs-lookup"><span data-stu-id="7e3ee-113">Parent Elements</span></span>

|<span data-ttu-id="7e3ee-114">元素</span><span class="sxs-lookup"><span data-stu-id="7e3ee-114">Element</span></span>|<span data-ttu-id="7e3ee-115">说明</span><span class="sxs-lookup"><span data-stu-id="7e3ee-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7e3ee-116">WideEntry （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="7e3ee-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="7e3ee-117">定义必须存在要使用此定义的条件。</span><span class="sxs-lookup"><span data-stu-id="7e3ee-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7e3ee-118">文本值</span><span class="sxs-lookup"><span data-stu-id="7e3ee-118">Text Value</span></span>

<span data-ttu-id="7e3ee-119">指定.NET 属性名称。</span><span class="sxs-lookup"><span data-stu-id="7e3ee-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="7e3ee-120">备注</span><span class="sxs-lookup"><span data-stu-id="7e3ee-120">Remarks</span></span>

<span data-ttu-id="7e3ee-121">选择条件必须指定至少一个属性名称或脚本来评估，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="7e3ee-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="7e3ee-122">有关如何使用选择条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="7e3ee-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="7e3ee-123">有关较宽的视图的其他组件的详细信息，请参阅[宽视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="7e3ee-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7e3ee-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7e3ee-124">See Also</span></span>

[<span data-ttu-id="7e3ee-125">创建较宽的视图</span><span class="sxs-lookup"><span data-stu-id="7e3ee-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="7e3ee-126">定义何时显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="7e3ee-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="7e3ee-127">有关 WideEntry （格式） 的 EntrySelectedBy SelectionCondition 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="7e3ee-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="7e3ee-128">WideEntry （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="7e3ee-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="7e3ee-129">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="7e3ee-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
