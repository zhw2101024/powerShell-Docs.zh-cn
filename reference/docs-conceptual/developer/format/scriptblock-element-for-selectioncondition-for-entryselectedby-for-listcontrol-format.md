---
title: 用于 ListControl 的 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: b65d953169f6daf15fb617ce4d0303cf4cb584ee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368586"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="3cb66-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3cb66-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="3cb66-103">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="3cb66-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="3cb66-104">如果此脚本的计算结果为 `true`，则满足条件，并使用列表项。</span><span class="sxs-lookup"><span data-stu-id="3cb66-104">When this script is evaluated to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="3cb66-105">配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） ListControl 元素（格式） ListEntries 元素（格式） ListEntry 元素（format） EntrySelectedBy 元素 for ListEntry （Format） SelectionCondition 元素 forEntrySelectedBy for ListEntry （Format） ScriptBlock 元素 for SelectionCondition for EntrySelectedBy for ListEntry （Format）</span><span class="sxs-lookup"><span data-stu-id="3cb66-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3cb66-106">语法</span><span class="sxs-lookup"><span data-stu-id="3cb66-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3cb66-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="3cb66-107">Attributes and Elements</span></span>

<span data-ttu-id="3cb66-108">以下各节介绍了 `ScriptBlock` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3cb66-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3cb66-109">属性</span><span class="sxs-lookup"><span data-stu-id="3cb66-109">Attributes</span></span>

<span data-ttu-id="3cb66-110">无。</span><span class="sxs-lookup"><span data-stu-id="3cb66-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3cb66-111">子元素</span><span class="sxs-lookup"><span data-stu-id="3cb66-111">Child Elements</span></span>

<span data-ttu-id="3cb66-112">无。</span><span class="sxs-lookup"><span data-stu-id="3cb66-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3cb66-113">父元素</span><span class="sxs-lookup"><span data-stu-id="3cb66-113">Parent Elements</span></span>

|<span data-ttu-id="3cb66-114">元素</span><span class="sxs-lookup"><span data-stu-id="3cb66-114">Element</span></span>|<span data-ttu-id="3cb66-115">描述</span><span class="sxs-lookup"><span data-stu-id="3cb66-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3cb66-116">ListEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="3cb66-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="3cb66-117">定义要使用此列表项必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="3cb66-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3cb66-118">文本值</span><span class="sxs-lookup"><span data-stu-id="3cb66-118">Text Value</span></span>

<span data-ttu-id="3cb66-119">指定要评估的脚本。</span><span class="sxs-lookup"><span data-stu-id="3cb66-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="3cb66-120">备注</span><span class="sxs-lookup"><span data-stu-id="3cb66-120">Remarks</span></span>

<span data-ttu-id="3cb66-121">选择条件必须指定至少一个要计算的脚本或属性名称，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="3cb66-121">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="3cb66-122">（有关如何使用选择条件的详细信息，请参阅[定义使用视图条目或项的条件](./defining-conditions-for-displaying-data.md)。）</span><span class="sxs-lookup"><span data-stu-id="3cb66-122">(For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).)</span></span>

<span data-ttu-id="3cb66-123">有关列表视图的其他组件的详细信息，请参阅[列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="3cb66-123">For more information about the other components of a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3cb66-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3cb66-124">See Also</span></span>

[<span data-ttu-id="3cb66-125">ListEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="3cb66-125">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="3cb66-126">ListEntry 的 SelectionCondition for EntrySelectedBy 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="3cb66-126">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="3cb66-127">ListEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="3cb66-127">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="3cb66-128">列表视图</span><span class="sxs-lookup"><span data-stu-id="3cb66-128">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="3cb66-129">定义使用视图条目或项的条件</span><span class="sxs-lookup"><span data-stu-id="3cb66-129">Defining Conditions for when a View Entry or Item is Used</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="3cb66-130">编写 Windows PowerShell 格式设置和类型文件</span><span class="sxs-lookup"><span data-stu-id="3cb66-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
