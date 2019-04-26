---
title: 脚本块元素的视图 （格式） 的 CustomControl SelectionCondition |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064554"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="d8d69-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="d8d69-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="d8d69-103">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="d8d69-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="d8d69-104">当此脚本的计算结果为`true`、 满足该条件，以及使用该定义。</span><span class="sxs-lookup"><span data-stu-id="d8d69-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="d8d69-105">定义自定义控件视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="d8d69-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="d8d69-106">视图 （格式） 的视图 （格式） 的视图 (CustomControl CustomEntries CustomEntry 元素 CustomControl CustomEntries 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素格式） 的视图 （格式） 的视图 （格式） 的视图 （格式） 的 CustomControl SelectionCondition ScriptBlock 元素 CustomControl EntrySelectedBy SelectionCondition 元素 CustomControl CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="d8d69-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d8d69-107">语法</span><span class="sxs-lookup"><span data-stu-id="d8d69-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d8d69-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="d8d69-108">Attributes and Elements</span></span>

<span data-ttu-id="d8d69-109">以下各节描述了特性、 子元素和父元素的`ScriptBlock`元素。</span><span class="sxs-lookup"><span data-stu-id="d8d69-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d8d69-110">属性</span><span class="sxs-lookup"><span data-stu-id="d8d69-110">Attributes</span></span>

<span data-ttu-id="d8d69-111">无。</span><span class="sxs-lookup"><span data-stu-id="d8d69-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d8d69-112">子元素</span><span class="sxs-lookup"><span data-stu-id="d8d69-112">Child Elements</span></span>

<span data-ttu-id="d8d69-113">无。</span><span class="sxs-lookup"><span data-stu-id="d8d69-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d8d69-114">父元素</span><span class="sxs-lookup"><span data-stu-id="d8d69-114">Parent Elements</span></span>

|<span data-ttu-id="d8d69-115">元素</span><span class="sxs-lookup"><span data-stu-id="d8d69-115">Element</span></span>|<span data-ttu-id="d8d69-116">说明</span><span class="sxs-lookup"><span data-stu-id="d8d69-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d8d69-117">为视图 （格式） 的 CustomControl EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="d8d69-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="d8d69-118">定义必须存在要使用的控件定义的条件。</span><span class="sxs-lookup"><span data-stu-id="d8d69-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d8d69-119">文本值</span><span class="sxs-lookup"><span data-stu-id="d8d69-119">Text Value</span></span>

<span data-ttu-id="d8d69-120">指定计算的脚本。</span><span class="sxs-lookup"><span data-stu-id="d8d69-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="d8d69-121">备注</span><span class="sxs-lookup"><span data-stu-id="d8d69-121">Remarks</span></span>

<span data-ttu-id="d8d69-122">选择条件必须指定至少一个脚本或属性名称来评估，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="d8d69-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="d8d69-123">有关如何使用选择条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="d8d69-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d8d69-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d8d69-124">See Also</span></span>

[<span data-ttu-id="d8d69-125">为视图 （格式） 的 CustomControl EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="d8d69-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="d8d69-126">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="d8d69-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
