---
title: SelectionCondition 配置 （格式） 的控件的属性名称元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec048408-e1c6-41ef-b39b-72f4c2dcf2ac
caps.latest.revision: 6
ms.openlocfilehash: b4b2440fdb7171d09fdc16ac7cc4f25ed1a4bb78
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064721"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="54b1e-102">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="54b1e-102">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="54b1e-103">指定触发条件的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="54b1e-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="54b1e-104">存在此属性时或当计算结果为`true`、 满足该条件，和使用的项。</span><span class="sxs-lookup"><span data-stu-id="54b1e-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="54b1e-105">定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。</span><span class="sxs-lookup"><span data-stu-id="54b1e-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="54b1e-106">配置 （格式） 的配置 （格式） 的配置 （CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素CustomControl CustomEntry 的 Controls 的配置 （格式） 的配置 （CustomEntry 的 EntrySelectedBy SelectionCondition 元素的配置 （格式） EntrySelectedBy 元素的控件的格式） CustomEntry 元素格式） 的 ListEntry （格式） 的 EntrySelectedBy SelectionCondition PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="54b1e-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="54b1e-107">语法</span><span class="sxs-lookup"><span data-stu-id="54b1e-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="54b1e-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="54b1e-108">Attributes and Elements</span></span>

<span data-ttu-id="54b1e-109">以下各节描述了特性、 子元素和父元素的`PropertyName`元素。</span><span class="sxs-lookup"><span data-stu-id="54b1e-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="54b1e-110">属性</span><span class="sxs-lookup"><span data-stu-id="54b1e-110">Attributes</span></span>

<span data-ttu-id="54b1e-111">无。</span><span class="sxs-lookup"><span data-stu-id="54b1e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="54b1e-112">子元素</span><span class="sxs-lookup"><span data-stu-id="54b1e-112">Child Elements</span></span>

<span data-ttu-id="54b1e-113">无。</span><span class="sxs-lookup"><span data-stu-id="54b1e-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="54b1e-114">父元素</span><span class="sxs-lookup"><span data-stu-id="54b1e-114">Parent Elements</span></span>

|<span data-ttu-id="54b1e-115">元素</span><span class="sxs-lookup"><span data-stu-id="54b1e-115">Element</span></span>|<span data-ttu-id="54b1e-116">说明</span><span class="sxs-lookup"><span data-stu-id="54b1e-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="54b1e-117">配置 （格式） 的控件的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="54b1e-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="54b1e-118">定义必须存在要使用的常见控件定义的条件。</span><span class="sxs-lookup"><span data-stu-id="54b1e-118">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="54b1e-119">文本值</span><span class="sxs-lookup"><span data-stu-id="54b1e-119">Text Value</span></span>

<span data-ttu-id="54b1e-120">指定.NET 属性名称。</span><span class="sxs-lookup"><span data-stu-id="54b1e-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="54b1e-121">备注</span><span class="sxs-lookup"><span data-stu-id="54b1e-121">Remarks</span></span>

<span data-ttu-id="54b1e-122">选择条件必须指定至少一个属性名或脚本，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="54b1e-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="54b1e-123">有关如何使用选择条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="54b1e-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="54b1e-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="54b1e-124">See Also</span></span>

[<span data-ttu-id="54b1e-125">配置 （格式） 的控件的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="54b1e-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="54b1e-126">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="54b1e-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
