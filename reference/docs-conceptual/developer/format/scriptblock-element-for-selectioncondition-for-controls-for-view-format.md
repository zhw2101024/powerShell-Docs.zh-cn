---
title: 用于视图（格式）的控件的 SelectionCondition 的 ScriptBlock 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 08512496-5682-4539-ab56-0c5394ce1f01
caps.latest.revision: 6
ms.openlocfilehash: 0137886437f01518f396613c564517e7910e657a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364796"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="5966b-102">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="5966b-102">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="5966b-103">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="5966b-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="5966b-104">如果此脚本的计算结果为 `true`，则满足条件，并使用定义。</span><span class="sxs-lookup"><span data-stu-id="5966b-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="5966b-105">定义可由视图使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="5966b-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="5966b-106">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 元素（format） Control 元素 for View （format） CustomControl 元素的控件元素，用于控件的 View （format） CustomEntries 元素CustomControl for view （format） CustomEntry 元素 for view （format）元素 for CustomEntries for view （format） EntrySelectedBy 元素 for view （format）元素 for CustomEntry for view （format） SelectionCondition 元素 for view （Format）用于视图的控件的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5966b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5966b-107">语法</span><span class="sxs-lookup"><span data-stu-id="5966b-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5966b-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="5966b-108">Attributes and Elements</span></span>

<span data-ttu-id="5966b-109">以下各节介绍了 `ScriptBlock` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5966b-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5966b-110">属性</span><span class="sxs-lookup"><span data-stu-id="5966b-110">Attributes</span></span>

<span data-ttu-id="5966b-111">无。</span><span class="sxs-lookup"><span data-stu-id="5966b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5966b-112">子元素</span><span class="sxs-lookup"><span data-stu-id="5966b-112">Child Elements</span></span>

<span data-ttu-id="5966b-113">无。</span><span class="sxs-lookup"><span data-stu-id="5966b-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5966b-114">父元素</span><span class="sxs-lookup"><span data-stu-id="5966b-114">Parent Elements</span></span>

|<span data-ttu-id="5966b-115">元素</span><span class="sxs-lookup"><span data-stu-id="5966b-115">Element</span></span>|<span data-ttu-id="5966b-116">描述</span><span class="sxs-lookup"><span data-stu-id="5966b-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5966b-117">用于视图的控件的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5966b-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="5966b-118">定义要使用的控件定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="5966b-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5966b-119">文本值</span><span class="sxs-lookup"><span data-stu-id="5966b-119">Text Value</span></span>

<span data-ttu-id="5966b-120">指定要评估的脚本。</span><span class="sxs-lookup"><span data-stu-id="5966b-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="5966b-121">备注</span><span class="sxs-lookup"><span data-stu-id="5966b-121">Remarks</span></span>

<span data-ttu-id="5966b-122">选择条件必须指定至少一个要计算的脚本或属性名称，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="5966b-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="5966b-123">有关如何使用选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="5966b-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5966b-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5966b-124">See Also</span></span>

[<span data-ttu-id="5966b-125">用于视图的控件的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5966b-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="5966b-126">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="5966b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
