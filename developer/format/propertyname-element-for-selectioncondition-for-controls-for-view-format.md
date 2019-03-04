---
title: SelectionCondition 视图 （格式） 的控件的属性名称元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92c4237d-c2b2-4908-82ac-f36070f89d26
caps.latest.revision: 6
ms.openlocfilehash: 79859bed3d762948182e03babf71d4270278bae7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853523"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="1b624-102">PropertyName Element for SelectionCondition for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="1b624-102">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="1b624-103">指定触发条件的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="1b624-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="1b624-104">存在此属性时或当计算结果为`true`、 满足该条件，和使用的项。</span><span class="sxs-lookup"><span data-stu-id="1b624-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="1b624-105">定义一个视图，可以使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="1b624-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="1b624-106">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 控件元素 （格式） 控制元素的控件的视图 （格式） CustomEntries 元素的控件的控件的视图 （格式） CustomControl 元素CustomControl CustomEntries CustomEntry EntrySelectedBy 视图 （控件的视图 （格式） SelectionCondition 元素的控件的视图 （格式） EntrySelectedBy 元素的控件的视图 （格式） CustomEntry 元素的控件SelectionCondition 视图 （格式） 的控件的格式） PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="1b624-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1b624-107">语法</span><span class="sxs-lookup"><span data-stu-id="1b624-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1b624-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="1b624-108">Attributes and Elements</span></span>

<span data-ttu-id="1b624-109">以下各节描述了特性、 子元素和父元素的`PropertyName`元素。</span><span class="sxs-lookup"><span data-stu-id="1b624-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1b624-110">特性</span><span class="sxs-lookup"><span data-stu-id="1b624-110">Attributes</span></span>

<span data-ttu-id="1b624-111">无。</span><span class="sxs-lookup"><span data-stu-id="1b624-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1b624-112">子元素</span><span class="sxs-lookup"><span data-stu-id="1b624-112">Child Elements</span></span>

<span data-ttu-id="1b624-113">无。</span><span class="sxs-lookup"><span data-stu-id="1b624-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1b624-114">父元素</span><span class="sxs-lookup"><span data-stu-id="1b624-114">Parent Elements</span></span>

|<span data-ttu-id="1b624-115">元素</span><span class="sxs-lookup"><span data-stu-id="1b624-115">Element</span></span>|<span data-ttu-id="1b624-116">描述</span><span class="sxs-lookup"><span data-stu-id="1b624-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1b624-117">视图 （格式） 的控件的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="1b624-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="1b624-118">定义必须存在要使用的控件定义的条件。</span><span class="sxs-lookup"><span data-stu-id="1b624-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1b624-119">文本值</span><span class="sxs-lookup"><span data-stu-id="1b624-119">Text Value</span></span>

<span data-ttu-id="1b624-120">指定.NET 属性名称。</span><span class="sxs-lookup"><span data-stu-id="1b624-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="1b624-121">备注</span><span class="sxs-lookup"><span data-stu-id="1b624-121">Remarks</span></span>

<span data-ttu-id="1b624-122">选择条件必须指定至少一个属性名或脚本，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="1b624-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="1b624-123">有关如何使用选择条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="1b624-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1b624-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1b624-124">See Also</span></span>

[<span data-ttu-id="1b624-125">视图 （格式） 的控件的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="1b624-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="1b624-126">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="1b624-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
