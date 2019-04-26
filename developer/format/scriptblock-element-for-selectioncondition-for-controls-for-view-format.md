---
title: SelectionCondition 的 Controls 的视图 （格式） 的脚本块元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 08512496-5682-4539-ab56-0c5394ce1f01
caps.latest.revision: 6
ms.openlocfilehash: 0137886437f01518f396613c564517e7910e657a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064384"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="b2b73-102">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="b2b73-102">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="b2b73-103">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="b2b73-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="b2b73-104">当此脚本的计算结果为`true`、 满足该条件，以及使用该定义。</span><span class="sxs-lookup"><span data-stu-id="b2b73-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="b2b73-105">定义一个视图，可以使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="b2b73-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="b2b73-106">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 控件元素 （格式） 控制元素的控件的视图 （格式） CustomEntries 元素的控件的控件的视图 （格式） CustomControl 元素CustomControl CustomEntries CustomEntry EntrySelectedBy 视图 （控件的视图 （格式） SelectionCondition 元素的控件的视图 （格式） EntrySelectedBy 元素的控件的视图 （格式） CustomEntry 元素的控件SelectionCondition 视图 （格式） 的控件的格式） 脚本块元素</span><span class="sxs-lookup"><span data-stu-id="b2b73-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b2b73-107">语法</span><span class="sxs-lookup"><span data-stu-id="b2b73-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b2b73-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="b2b73-108">Attributes and Elements</span></span>

<span data-ttu-id="b2b73-109">以下各节描述了特性、 子元素和父元素的`ScriptBlock`元素。</span><span class="sxs-lookup"><span data-stu-id="b2b73-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b2b73-110">属性</span><span class="sxs-lookup"><span data-stu-id="b2b73-110">Attributes</span></span>

<span data-ttu-id="b2b73-111">无。</span><span class="sxs-lookup"><span data-stu-id="b2b73-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b2b73-112">子元素</span><span class="sxs-lookup"><span data-stu-id="b2b73-112">Child Elements</span></span>

<span data-ttu-id="b2b73-113">无。</span><span class="sxs-lookup"><span data-stu-id="b2b73-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b2b73-114">父元素</span><span class="sxs-lookup"><span data-stu-id="b2b73-114">Parent Elements</span></span>

|<span data-ttu-id="b2b73-115">元素</span><span class="sxs-lookup"><span data-stu-id="b2b73-115">Element</span></span>|<span data-ttu-id="b2b73-116">说明</span><span class="sxs-lookup"><span data-stu-id="b2b73-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b2b73-117">视图 （格式） 的控件的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="b2b73-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="b2b73-118">定义必须存在要使用的控件定义的条件。</span><span class="sxs-lookup"><span data-stu-id="b2b73-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b2b73-119">文本值</span><span class="sxs-lookup"><span data-stu-id="b2b73-119">Text Value</span></span>

<span data-ttu-id="b2b73-120">指定计算的脚本。</span><span class="sxs-lookup"><span data-stu-id="b2b73-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="b2b73-121">备注</span><span class="sxs-lookup"><span data-stu-id="b2b73-121">Remarks</span></span>

<span data-ttu-id="b2b73-122">选择条件必须指定至少一个脚本或属性名称来评估，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="b2b73-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="b2b73-123">有关如何使用选择条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="b2b73-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b2b73-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b2b73-124">See Also</span></span>

[<span data-ttu-id="b2b73-125">视图 （格式） 的控件的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="b2b73-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="b2b73-126">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="b2b73-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
