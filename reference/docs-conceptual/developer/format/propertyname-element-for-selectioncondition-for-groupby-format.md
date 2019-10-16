---
title: GroupBy （Format）的 SelectionCondition 的 PropertyName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1707317-6c26-4866-bcc1-8924103c9014
caps.latest.revision: 6
ms.openlocfilehash: 7241ea0ea364befa7ad4ab0af4c4209be72214a7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364946"
---
# <a name="propertyname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="3c10c-102">PropertyName Element for SelectionCondition for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3c10c-102">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="3c10c-103">指定触发条件的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="3c10c-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="3c10c-104">如果存在此属性，或者其计算结果为 `true`，则满足条件，并使用定义。</span><span class="sxs-lookup"><span data-stu-id="3c10c-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="3c10c-105">此元素在定义如何显示新的对象组时使用。</span><span class="sxs-lookup"><span data-stu-id="3c10c-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="3c10c-106">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format）对于 GroupBy （format） CustomEntries 元素，用于元素的 CustomControl 元素（format）CustomControl for groupby （format） EntrySelectedBy 元素 for CustomEntry for groupby （format） SelectionCondition 元素 for EntrySelectedBy for groupby （format） PropertyName 元素 for GroupBy （Format）</span><span class="sxs-lookup"><span data-stu-id="3c10c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3c10c-107">语法</span><span class="sxs-lookup"><span data-stu-id="3c10c-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3c10c-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="3c10c-108">Attributes and Elements</span></span>

<span data-ttu-id="3c10c-109">以下各节介绍了 `PropertyName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3c10c-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3c10c-110">属性</span><span class="sxs-lookup"><span data-stu-id="3c10c-110">Attributes</span></span>

<span data-ttu-id="3c10c-111">无。</span><span class="sxs-lookup"><span data-stu-id="3c10c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3c10c-112">子元素</span><span class="sxs-lookup"><span data-stu-id="3c10c-112">Child Elements</span></span>

<span data-ttu-id="3c10c-113">无。</span><span class="sxs-lookup"><span data-stu-id="3c10c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3c10c-114">父元素</span><span class="sxs-lookup"><span data-stu-id="3c10c-114">Parent Elements</span></span>

|<span data-ttu-id="3c10c-115">元素</span><span class="sxs-lookup"><span data-stu-id="3c10c-115">Element</span></span>|<span data-ttu-id="3c10c-116">描述</span><span class="sxs-lookup"><span data-stu-id="3c10c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3c10c-117">GroupBy 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="3c10c-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="3c10c-118">定义要使用的控件定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="3c10c-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3c10c-119">文本值</span><span class="sxs-lookup"><span data-stu-id="3c10c-119">Text Value</span></span>

<span data-ttu-id="3c10c-120">指定 .NET 属性名称。</span><span class="sxs-lookup"><span data-stu-id="3c10c-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="3c10c-121">备注</span><span class="sxs-lookup"><span data-stu-id="3c10c-121">Remarks</span></span>

<span data-ttu-id="3c10c-122">选择条件必须指定至少一个属性名称或脚本，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="3c10c-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="3c10c-123">有关如何使用选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="3c10c-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3c10c-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3c10c-124">See Also</span></span>

[<span data-ttu-id="3c10c-125">GroupBy 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="3c10c-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="3c10c-126">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="3c10c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
