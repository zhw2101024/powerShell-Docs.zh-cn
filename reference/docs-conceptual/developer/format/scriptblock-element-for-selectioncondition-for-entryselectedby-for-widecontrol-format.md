---
title: 用于 WideControl 的 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec68309-7826-4643-a521-e29c996663fb
caps.latest.revision: 11
ms.openlocfilehash: 649a978e21e9421a3f3e953261e1d309e23c3f9c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368556"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="3d23e-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3d23e-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="3d23e-103">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="3d23e-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="3d23e-104">如果此脚本的计算结果为 `true`，则满足条件，并使用宽输入定义。</span><span class="sxs-lookup"><span data-stu-id="3d23e-104">When this script is evaluated to `true`, the condition is met, and the wide entry definition is used.</span></span>

<span data-ttu-id="3d23e-105">配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（format） EntrySelectedBy 元素 for WideEntry （Format） SelectionCondition 元素 forEntrySelectedBy for WideEntry （Format） ScriptBlock 元素 for SelectionCondition for EntrySelectedBy for WideEntry （Format）</span><span class="sxs-lookup"><span data-stu-id="3d23e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3d23e-106">语法</span><span class="sxs-lookup"><span data-stu-id="3d23e-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3d23e-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="3d23e-107">Attributes and Elements</span></span>

<span data-ttu-id="3d23e-108">以下各节介绍了 `ScriptBlock` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3d23e-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3d23e-109">属性</span><span class="sxs-lookup"><span data-stu-id="3d23e-109">Attributes</span></span>

<span data-ttu-id="3d23e-110">无。</span><span class="sxs-lookup"><span data-stu-id="3d23e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3d23e-111">子元素</span><span class="sxs-lookup"><span data-stu-id="3d23e-111">Child Elements</span></span>

<span data-ttu-id="3d23e-112">无。</span><span class="sxs-lookup"><span data-stu-id="3d23e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3d23e-113">父元素</span><span class="sxs-lookup"><span data-stu-id="3d23e-113">Parent Elements</span></span>

|<span data-ttu-id="3d23e-114">元素</span><span class="sxs-lookup"><span data-stu-id="3d23e-114">Element</span></span>|<span data-ttu-id="3d23e-115">描述</span><span class="sxs-lookup"><span data-stu-id="3d23e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3d23e-116">WideEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="3d23e-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="3d23e-117">定义要使用此定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="3d23e-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3d23e-118">文本值</span><span class="sxs-lookup"><span data-stu-id="3d23e-118">Text Value</span></span>

<span data-ttu-id="3d23e-119">指定要评估的脚本。</span><span class="sxs-lookup"><span data-stu-id="3d23e-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="3d23e-120">备注</span><span class="sxs-lookup"><span data-stu-id="3d23e-120">Remarks</span></span>

<span data-ttu-id="3d23e-121">选择条件必须指定至少一个要计算的脚本或属性名称，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="3d23e-121">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="3d23e-122">有关如何使用选择条件的详细信息，请参阅为[数据显示定义条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="3d23e-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="3d23e-123">有关大视图的其他组件的详细信息，请参阅[宽视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="3d23e-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3d23e-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3d23e-124">See Also</span></span>

[<span data-ttu-id="3d23e-125">创建宽视图</span><span class="sxs-lookup"><span data-stu-id="3d23e-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="3d23e-126">定义显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="3d23e-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="3d23e-127">WideEntry 的 SelectionCondition for EntrySelectedBy 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="3d23e-127">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="3d23e-128">WideEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="3d23e-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="3d23e-129">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="3d23e-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
