---
title: GroupBy （格式） 的 SelectionCondition PropertyName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1707317-6c26-4866-bcc1-8924103c9014
caps.latest.revision: 6
ms.openlocfilehash: 7241ea0ea364befa7ad4ab0af4c4209be72214a7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064809"
---
# <a name="propertyname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="daff5-102">PropertyName Element for SelectionCondition for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="daff5-102">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="daff5-103">指定触发条件的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="daff5-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="daff5-104">存在此属性时或当计算结果为`true`、 满足该条件，以及使用该定义。</span><span class="sxs-lookup"><span data-stu-id="daff5-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="daff5-105">定义如何显示一组新对象时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="daff5-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="daff5-106">GroupBy （格式） 的 GroupBy （格式） CustomEntry 元素 CustomControl CustomEntries 元素的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素CustomControl GroupBy （格式） 的 GroupBy （格式） 的 GroupBy （格式） 的 GroupBy （格式） 的 SelectionCondition PropertyName 元素 EntrySelectedBy SelectionCondition 元素 CustomEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="daff5-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="daff5-107">语法</span><span class="sxs-lookup"><span data-stu-id="daff5-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="daff5-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="daff5-108">Attributes and Elements</span></span>

<span data-ttu-id="daff5-109">以下各节描述了特性、 子元素和父元素的`PropertyName`元素。</span><span class="sxs-lookup"><span data-stu-id="daff5-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="daff5-110">属性</span><span class="sxs-lookup"><span data-stu-id="daff5-110">Attributes</span></span>

<span data-ttu-id="daff5-111">无。</span><span class="sxs-lookup"><span data-stu-id="daff5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="daff5-112">子元素</span><span class="sxs-lookup"><span data-stu-id="daff5-112">Child Elements</span></span>

<span data-ttu-id="daff5-113">无。</span><span class="sxs-lookup"><span data-stu-id="daff5-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="daff5-114">父元素</span><span class="sxs-lookup"><span data-stu-id="daff5-114">Parent Elements</span></span>

|<span data-ttu-id="daff5-115">元素</span><span class="sxs-lookup"><span data-stu-id="daff5-115">Element</span></span>|<span data-ttu-id="daff5-116">说明</span><span class="sxs-lookup"><span data-stu-id="daff5-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="daff5-117">GroupBy （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="daff5-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="daff5-118">定义必须存在要使用的控件定义的条件。</span><span class="sxs-lookup"><span data-stu-id="daff5-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="daff5-119">文本值</span><span class="sxs-lookup"><span data-stu-id="daff5-119">Text Value</span></span>

<span data-ttu-id="daff5-120">指定.NET 属性名称。</span><span class="sxs-lookup"><span data-stu-id="daff5-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="daff5-121">备注</span><span class="sxs-lookup"><span data-stu-id="daff5-121">Remarks</span></span>

<span data-ttu-id="daff5-122">选择条件必须指定至少一个属性名或脚本，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="daff5-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="daff5-123">有关如何使用选择条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="daff5-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="daff5-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="daff5-124">See Also</span></span>

[<span data-ttu-id="daff5-125">GroupBy （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="daff5-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="daff5-126">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="daff5-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
