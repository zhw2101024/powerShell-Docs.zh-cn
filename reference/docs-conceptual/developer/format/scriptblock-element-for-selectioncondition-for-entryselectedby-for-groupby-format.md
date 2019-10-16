---
title: 用于 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e01344bd-ad69-4789-8e9f-2e79880c3a33
caps.latest.revision: 6
ms.openlocfilehash: cb79fb942111cee89c6b2abba75de4c494082b7e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368596"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="741f9-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="741f9-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="741f9-103">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="741f9-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="741f9-104">如果此脚本的计算结果为 `true`，则满足条件，并使用定义。</span><span class="sxs-lookup"><span data-stu-id="741f9-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="741f9-105">此元素在定义如何显示新的对象组时使用。</span><span class="sxs-lookup"><span data-stu-id="741f9-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="741f9-106">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format）对于 GroupBy （format） CustomEntries 元素，用于元素的 CustomControl 元素（format）CustomControl for groupby （format） EntrySelectedBy 元素 for CustomEntry for groupby （format）用于 EntrySelectedBy for groupby 的 ScriptBlock 元素的元素（format）</span><span class="sxs-lookup"><span data-stu-id="741f9-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="741f9-107">语法</span><span class="sxs-lookup"><span data-stu-id="741f9-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="741f9-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="741f9-108">Attributes and Elements</span></span>

<span data-ttu-id="741f9-109">以下各节介绍了 `ScriptBlock` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="741f9-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="741f9-110">属性</span><span class="sxs-lookup"><span data-stu-id="741f9-110">Attributes</span></span>

<span data-ttu-id="741f9-111">无。</span><span class="sxs-lookup"><span data-stu-id="741f9-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="741f9-112">子元素</span><span class="sxs-lookup"><span data-stu-id="741f9-112">Child Elements</span></span>

<span data-ttu-id="741f9-113">无。</span><span class="sxs-lookup"><span data-stu-id="741f9-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="741f9-114">父元素</span><span class="sxs-lookup"><span data-stu-id="741f9-114">Parent Elements</span></span>

|<span data-ttu-id="741f9-115">元素</span><span class="sxs-lookup"><span data-stu-id="741f9-115">Element</span></span>|<span data-ttu-id="741f9-116">描述</span><span class="sxs-lookup"><span data-stu-id="741f9-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="741f9-117">GroupBy 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="741f9-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="741f9-118">定义要使用的控件定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="741f9-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="741f9-119">文本值</span><span class="sxs-lookup"><span data-stu-id="741f9-119">Text Value</span></span>

<span data-ttu-id="741f9-120">指定要评估的脚本。</span><span class="sxs-lookup"><span data-stu-id="741f9-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="741f9-121">备注</span><span class="sxs-lookup"><span data-stu-id="741f9-121">Remarks</span></span>

<span data-ttu-id="741f9-122">选择条件必须指定至少一个要计算的脚本或属性名称，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="741f9-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="741f9-123">有关如何使用选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="741f9-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="741f9-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="741f9-124">See Also</span></span>

[<span data-ttu-id="741f9-125">GroupBy 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="741f9-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="741f9-126">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="741f9-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
