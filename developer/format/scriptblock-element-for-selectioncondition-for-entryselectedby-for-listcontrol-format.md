---
title: 脚本块元素的 ListControl （格式） 的 EntrySelectedBy SelectionCondition |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: fd708473d04a76bcf6cf3a8f8278e1d15fb9addf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858653"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="d4639-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d4639-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="d4639-103">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="d4639-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="d4639-104">当此脚本的计算结果为`true`、 满足该条件，以及使用列表项。</span><span class="sxs-lookup"><span data-stu-id="d4639-104">When this script is evaluated to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="d4639-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素 （格式） ListEntry 元素 （格式） EntrySelectedBy 元素 ListEntry （格式） SelectionCondition 元素EntrySelectedBy ListEntry （格式） 的 EntrySelectedBy 的 SelectionCondition ListEntry （格式） 脚本块元素</span><span class="sxs-lookup"><span data-stu-id="d4639-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d4639-106">语法</span><span class="sxs-lookup"><span data-stu-id="d4639-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d4639-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="d4639-107">Attributes and Elements</span></span>

<span data-ttu-id="d4639-108">以下各节描述了特性、 子元素和父元素的`ScriptBlock`元素。</span><span class="sxs-lookup"><span data-stu-id="d4639-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d4639-109">属性</span><span class="sxs-lookup"><span data-stu-id="d4639-109">Attributes</span></span>

<span data-ttu-id="d4639-110">无。</span><span class="sxs-lookup"><span data-stu-id="d4639-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d4639-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d4639-111">Child Elements</span></span>

<span data-ttu-id="d4639-112">无。</span><span class="sxs-lookup"><span data-stu-id="d4639-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d4639-113">父元素</span><span class="sxs-lookup"><span data-stu-id="d4639-113">Parent Elements</span></span>

|<span data-ttu-id="d4639-114">元素</span><span class="sxs-lookup"><span data-stu-id="d4639-114">Element</span></span>|<span data-ttu-id="d4639-115">说明</span><span class="sxs-lookup"><span data-stu-id="d4639-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d4639-116">ListEntry （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="d4639-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="d4639-117">定义要使用此列表项中必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="d4639-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d4639-118">文本值</span><span class="sxs-lookup"><span data-stu-id="d4639-118">Text Value</span></span>

<span data-ttu-id="d4639-119">指定计算的脚本。</span><span class="sxs-lookup"><span data-stu-id="d4639-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="d4639-120">备注</span><span class="sxs-lookup"><span data-stu-id="d4639-120">Remarks</span></span>

<span data-ttu-id="d4639-121">选择条件必须指定至少一个脚本或属性名称来评估，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="d4639-121">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="d4639-122">(有关如何使用选择条件的详细信息，请参阅[时视图条目定义条件或使用项](./defining-conditions-for-displaying-data.md)。)</span><span class="sxs-lookup"><span data-stu-id="d4639-122">(For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).)</span></span>

<span data-ttu-id="d4639-123">列表视图的其他组件的详细信息，请参阅[列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="d4639-123">For more information about the other components of a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d4639-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d4639-124">See Also</span></span>

[<span data-ttu-id="d4639-125">ListEntry 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="d4639-125">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="d4639-126">有关 ListEntry （格式） 的 EmtrySelectedBy SelectionCondition PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="d4639-126">PropertyName Element for SelectionCondition for EmtrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="d4639-127">ListEntry （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="d4639-127">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="d4639-128">列表视图</span><span class="sxs-lookup"><span data-stu-id="d4639-128">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="d4639-129">使用视图条目或项时定义的条件</span><span class="sxs-lookup"><span data-stu-id="d4639-129">Defining Conditions for when a View Entry or Item is Used</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="d4639-130">编写 Windows PowerShell 格式设置和文件类型</span><span class="sxs-lookup"><span data-stu-id="d4639-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
