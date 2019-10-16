---
title: 用于配置的控件（格式）的 ExpressionBinding 的 ItemSelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd3ddc33-b21c-4464-b3f2-a78dbe0062a8
caps.latest.revision: 8
ms.openlocfilehash: 4865d716ebe0460b662253a3019e93e82428b882
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362916"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="5ccf4-102">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5ccf4-102">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="5ccf4-103">定义要使用此控件必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="5ccf4-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="5ccf4-104">此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。</span><span class="sxs-lookup"><span data-stu-id="5ccf4-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="5ccf4-105">Configuration 元素（格式）控制配置（format） CustomControl 元素的控件的配置（Format）控件元素的元素，以控制 CustomControl for configuration （Format） CustomEntries 元素的配置（Format） CustomEntry 元素 for CustomControl for CustomItem 元素 for CustomEntry for 元素 for for ExpressionBinding for configuration CustomItem 元素 for for control用于配置的控件的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5ccf4-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5ccf4-106">语法</span><span class="sxs-lookup"><span data-stu-id="5ccf4-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5ccf4-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="5ccf4-107">Attributes and Elements</span></span>

<span data-ttu-id="5ccf4-108">以下各节介绍了 `ItemSelectionCondition` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5ccf4-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5ccf4-109">属性</span><span class="sxs-lookup"><span data-stu-id="5ccf4-109">Attributes</span></span>

<span data-ttu-id="5ccf4-110">无。</span><span class="sxs-lookup"><span data-stu-id="5ccf4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5ccf4-111">子元素</span><span class="sxs-lookup"><span data-stu-id="5ccf4-111">Child Elements</span></span>

|<span data-ttu-id="5ccf4-112">元素</span><span class="sxs-lookup"><span data-stu-id="5ccf4-112">Element</span></span>|<span data-ttu-id="5ccf4-113">描述</span><span class="sxs-lookup"><span data-stu-id="5ccf4-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5ccf4-114">用于配置的控件的 ItemSelectionCondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5ccf4-114">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="5ccf4-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="5ccf4-115">Optional element.</span></span><br /><br /> <span data-ttu-id="5ccf4-116">指定触发条件的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="5ccf4-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="5ccf4-117">用于配置的控件的 ItemSelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5ccf4-117">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="5ccf4-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="5ccf4-118">Optional element.</span></span><br /><br /> <span data-ttu-id="5ccf4-119">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="5ccf4-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5ccf4-120">父元素</span><span class="sxs-lookup"><span data-stu-id="5ccf4-120">Parent Elements</span></span>

|<span data-ttu-id="5ccf4-121">元素</span><span class="sxs-lookup"><span data-stu-id="5ccf4-121">Element</span></span>|<span data-ttu-id="5ccf4-122">描述</span><span class="sxs-lookup"><span data-stu-id="5ccf4-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5ccf4-123">用于配置的控件的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5ccf4-123">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="5ccf4-124">定义控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="5ccf4-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5ccf4-125">备注</span><span class="sxs-lookup"><span data-stu-id="5ccf4-125">Remarks</span></span>

<span data-ttu-id="5ccf4-126">您可以为此条件指定一个属性名称或脚本，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="5ccf4-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ccf4-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5ccf4-127">See Also</span></span>

[<span data-ttu-id="5ccf4-128">用于配置的控件的 ItemSelectionCondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5ccf4-128">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="5ccf4-129">用于配置的控件的 ItemSelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5ccf4-129">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="5ccf4-130">用于配置的控件的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5ccf4-130">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="5ccf4-131">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="5ccf4-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
