---
title: CustomControl 的 SelectionCondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368636"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="36ef0-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="36ef0-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="36ef0-103">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="36ef0-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="36ef0-104">如果此脚本的计算结果为 `true`，则满足条件，并使用定义。</span><span class="sxs-lookup"><span data-stu-id="36ef0-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="36ef0-105">定义自定义控件视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="36ef0-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="36ef0-106">Configuration Element （Format） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素 for View （format） CustomEntries 元素 for CustomControl for CustomEntry for CustomEntries for View （Format） CustomControl 元素 for view （Format） CustomItem 元素 for CustomEntry for CustomControl for EntrySelectedBy for CustomControl for SelectionCondition for CustomControl for view （format） ScriptBlock 元素 for for view （Format）</span><span class="sxs-lookup"><span data-stu-id="36ef0-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="36ef0-107">语法</span><span class="sxs-lookup"><span data-stu-id="36ef0-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="36ef0-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="36ef0-108">Attributes and Elements</span></span>

<span data-ttu-id="36ef0-109">以下各节介绍了 `ScriptBlock` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="36ef0-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="36ef0-110">属性</span><span class="sxs-lookup"><span data-stu-id="36ef0-110">Attributes</span></span>

<span data-ttu-id="36ef0-111">无。</span><span class="sxs-lookup"><span data-stu-id="36ef0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="36ef0-112">子元素</span><span class="sxs-lookup"><span data-stu-id="36ef0-112">Child Elements</span></span>

<span data-ttu-id="36ef0-113">无。</span><span class="sxs-lookup"><span data-stu-id="36ef0-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="36ef0-114">父元素</span><span class="sxs-lookup"><span data-stu-id="36ef0-114">Parent Elements</span></span>

|<span data-ttu-id="36ef0-115">元素</span><span class="sxs-lookup"><span data-stu-id="36ef0-115">Element</span></span>|<span data-ttu-id="36ef0-116">描述</span><span class="sxs-lookup"><span data-stu-id="36ef0-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="36ef0-117">用于 View 的 CustomControl 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="36ef0-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="36ef0-118">定义要使用的控件定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="36ef0-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="36ef0-119">文本值</span><span class="sxs-lookup"><span data-stu-id="36ef0-119">Text Value</span></span>

<span data-ttu-id="36ef0-120">指定要评估的脚本。</span><span class="sxs-lookup"><span data-stu-id="36ef0-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="36ef0-121">备注</span><span class="sxs-lookup"><span data-stu-id="36ef0-121">Remarks</span></span>

<span data-ttu-id="36ef0-122">选择条件必须指定至少一个要计算的脚本或属性名称，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="36ef0-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="36ef0-123">有关如何使用选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="36ef0-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="36ef0-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="36ef0-124">See Also</span></span>

[<span data-ttu-id="36ef0-125">用于 View 的 CustomControl 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="36ef0-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="36ef0-126">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="36ef0-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
