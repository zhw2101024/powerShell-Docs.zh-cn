---
title: 脚本块元素的 GroupBy （格式） 的 EntrySelectedBy SelectionCondition |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e01344bd-ad69-4789-8e9f-2e79880c3a33
caps.latest.revision: 6
ms.openlocfilehash: cb79fb942111cee89c6b2abba75de4c494082b7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064333"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="1f823-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1f823-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="1f823-103">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="1f823-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="1f823-104">当此脚本的计算结果为`true`、 满足该条件，以及使用该定义。</span><span class="sxs-lookup"><span data-stu-id="1f823-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="1f823-105">定义如何显示一组新对象时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="1f823-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="1f823-106">GroupBy （格式） 的 GroupBy （格式） CustomEntry 元素 CustomControl CustomEntries 元素的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素CustomControl EntrySelectedBy SelectionCondition 为 GroupBy （格式） 的 GroupBy （格式） 脚本块元素的 GroupBy （格式） SelectionCondition 元素 CustomEntry GroupBy （格式） EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="1f823-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1f823-107">语法</span><span class="sxs-lookup"><span data-stu-id="1f823-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1f823-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="1f823-108">Attributes and Elements</span></span>

<span data-ttu-id="1f823-109">以下各节描述了特性、 子元素和父元素的`ScriptBlock`元素。</span><span class="sxs-lookup"><span data-stu-id="1f823-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1f823-110">属性</span><span class="sxs-lookup"><span data-stu-id="1f823-110">Attributes</span></span>

<span data-ttu-id="1f823-111">无。</span><span class="sxs-lookup"><span data-stu-id="1f823-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1f823-112">子元素</span><span class="sxs-lookup"><span data-stu-id="1f823-112">Child Elements</span></span>

<span data-ttu-id="1f823-113">无。</span><span class="sxs-lookup"><span data-stu-id="1f823-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1f823-114">父元素</span><span class="sxs-lookup"><span data-stu-id="1f823-114">Parent Elements</span></span>

|<span data-ttu-id="1f823-115">元素</span><span class="sxs-lookup"><span data-stu-id="1f823-115">Element</span></span>|<span data-ttu-id="1f823-116">说明</span><span class="sxs-lookup"><span data-stu-id="1f823-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f823-117">GroupBy （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="1f823-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="1f823-118">定义必须存在要使用的控件定义的条件。</span><span class="sxs-lookup"><span data-stu-id="1f823-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1f823-119">文本值</span><span class="sxs-lookup"><span data-stu-id="1f823-119">Text Value</span></span>

<span data-ttu-id="1f823-120">指定计算的脚本。</span><span class="sxs-lookup"><span data-stu-id="1f823-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="1f823-121">备注</span><span class="sxs-lookup"><span data-stu-id="1f823-121">Remarks</span></span>

<span data-ttu-id="1f823-122">选择条件必须指定至少一个脚本或属性名称来评估，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="1f823-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="1f823-123">有关如何使用选择条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="1f823-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1f823-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1f823-124">See Also</span></span>

[<span data-ttu-id="1f823-125">GroupBy （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="1f823-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="1f823-126">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="1f823-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
