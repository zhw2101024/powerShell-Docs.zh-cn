---
title: 用于配置（格式）的控件的 SelectionCondition 的 ScriptBlock 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb032dfc-9ef6-403c-b557-5858617e3483
caps.latest.revision: 6
ms.openlocfilehash: 102987970152420896a0c986f0973280ae209623
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368616"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="7c10e-102">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="7c10e-102">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="7c10e-103">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="7c10e-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="7c10e-104">如果此脚本的计算结果为 `true`，则满足条件，并使用定义。</span><span class="sxs-lookup"><span data-stu-id="7c10e-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="7c10e-105">此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。</span><span class="sxs-lookup"><span data-stu-id="7c10e-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="7c10e-106">Configuration 元素（格式）控制配置（format） CustomControl 元素的控件的配置（Format）控件元素的元素，以控制 CustomControl for configuration （Format） CustomEntries 元素的配置（Format） CustomEntry 元素 for CustomControl for EntrySelectedBy 元素 for CustomEntry for 元素 for for 元素 for for SelectionCondition for control for control （Format）用于配置的控件的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7c10e-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7c10e-107">语法</span><span class="sxs-lookup"><span data-stu-id="7c10e-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7c10e-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="7c10e-108">Attributes and Elements</span></span>

<span data-ttu-id="7c10e-109">以下各节介绍了 `ScriptBlock` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7c10e-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7c10e-110">属性</span><span class="sxs-lookup"><span data-stu-id="7c10e-110">Attributes</span></span>

<span data-ttu-id="7c10e-111">无。</span><span class="sxs-lookup"><span data-stu-id="7c10e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7c10e-112">子元素</span><span class="sxs-lookup"><span data-stu-id="7c10e-112">Child Elements</span></span>

<span data-ttu-id="7c10e-113">无。</span><span class="sxs-lookup"><span data-stu-id="7c10e-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7c10e-114">父元素</span><span class="sxs-lookup"><span data-stu-id="7c10e-114">Parent Elements</span></span>

|<span data-ttu-id="7c10e-115">元素</span><span class="sxs-lookup"><span data-stu-id="7c10e-115">Element</span></span>|<span data-ttu-id="7c10e-116">描述</span><span class="sxs-lookup"><span data-stu-id="7c10e-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7c10e-117">用于配置的控件的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7c10e-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="7c10e-118">定义要使用的公共控件定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="7c10e-118">Defines a condition that must exist for the common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7c10e-119">文本值</span><span class="sxs-lookup"><span data-stu-id="7c10e-119">Text Value</span></span>

<span data-ttu-id="7c10e-120">指定要评估的脚本。</span><span class="sxs-lookup"><span data-stu-id="7c10e-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="7c10e-121">备注</span><span class="sxs-lookup"><span data-stu-id="7c10e-121">Remarks</span></span>

<span data-ttu-id="7c10e-122">选择条件必须指定至少一个要计算的脚本或属性名称，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="7c10e-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="7c10e-123">有关如何使用选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="7c10e-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7c10e-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7c10e-124">See Also</span></span>

[<span data-ttu-id="7c10e-125">用于配置的控件的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7c10e-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="7c10e-126">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="7c10e-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
