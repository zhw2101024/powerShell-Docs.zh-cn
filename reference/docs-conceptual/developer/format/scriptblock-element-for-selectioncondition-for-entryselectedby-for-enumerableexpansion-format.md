---
title: 用于 EnumerableExpansion 的 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4126b799-c43d-4175-8513-6d761c65437e
caps.latest.revision: 9
ms.openlocfilehash: a51d8d22fa8b0c7f303a5e8f37edcc5e57724063
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368606"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="19a7f-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="19a7f-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="19a7f-103">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="19a7f-103">Specifies the script that triggers the condition.</span></span>

<span data-ttu-id="19a7f-104">用于 EnumerableExpansion 的 SelectionCondition （Format） EntrySelectedBy 元素的配置元素（格式） DefaultSettings 元素（format） EnumerableExpansions 元素（format） EntrySelectedBy 元素用于 EntrySelectedBy for EnumerableExpansion （Format）的 SelectionCondition 的 EnumerableExpansion （格式） ScriptBlock 元素</span><span class="sxs-lookup"><span data-stu-id="19a7f-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="19a7f-105">语法</span><span class="sxs-lookup"><span data-stu-id="19a7f-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="19a7f-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="19a7f-106">Attributes and Elements</span></span>

<span data-ttu-id="19a7f-107">以下各节介绍了 `ScriptBlock` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="19a7f-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="19a7f-108">属性</span><span class="sxs-lookup"><span data-stu-id="19a7f-108">Attributes</span></span>

<span data-ttu-id="19a7f-109">无。</span><span class="sxs-lookup"><span data-stu-id="19a7f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="19a7f-110">子元素</span><span class="sxs-lookup"><span data-stu-id="19a7f-110">Child Elements</span></span>

<span data-ttu-id="19a7f-111">无。</span><span class="sxs-lookup"><span data-stu-id="19a7f-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="19a7f-112">父元素</span><span class="sxs-lookup"><span data-stu-id="19a7f-112">Parent Elements</span></span>

|<span data-ttu-id="19a7f-113">元素</span><span class="sxs-lookup"><span data-stu-id="19a7f-113">Element</span></span>|<span data-ttu-id="19a7f-114">描述</span><span class="sxs-lookup"><span data-stu-id="19a7f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="19a7f-115">EnumerableExpansion 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="19a7f-115">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="19a7f-116">定义扩展此定义的集合对象时必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="19a7f-116">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="19a7f-117">文本值</span><span class="sxs-lookup"><span data-stu-id="19a7f-117">Text Value</span></span>

<span data-ttu-id="19a7f-118">指定要评估的脚本。</span><span class="sxs-lookup"><span data-stu-id="19a7f-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="19a7f-119">备注</span><span class="sxs-lookup"><span data-stu-id="19a7f-119">Remarks</span></span>

<span data-ttu-id="19a7f-120">选择条件必须指定至少一个要计算的脚本或属性名称，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="19a7f-120">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="19a7f-121">有关如何使用选择条件的详细信息，请参阅为[数据显示定义条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="19a7f-121">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="19a7f-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="19a7f-122">See Also</span></span>

[<span data-ttu-id="19a7f-123">定义显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="19a7f-123">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="19a7f-124">EnumerableExpansion 的 SelectionCondition for EntrySelectedBy 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="19a7f-124">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="19a7f-125">EnumerableExpansion 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="19a7f-125">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="19a7f-126">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="19a7f-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
