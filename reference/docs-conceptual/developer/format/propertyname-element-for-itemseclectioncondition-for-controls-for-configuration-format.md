---
title: 用于配置（格式）的控件的 ItemSeclectionCondition 的 PropertyName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad8ab181-c559-492e-a0cf-299e381fdcc3
caps.latest.revision: 6
ms.openlocfilehash: ce25789bdfc2679372ca9e42f99dcc6a30ae2def
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362526"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="f2494-102">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="f2494-102">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="f2494-103">指定触发条件的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="f2494-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="f2494-104">如果该属性存在，或其计算结果为 `true`，则满足条件，并使用控件。</span><span class="sxs-lookup"><span data-stu-id="f2494-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="f2494-105">此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。</span><span class="sxs-lookup"><span data-stu-id="f2494-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="f2494-106">Configuration 元素（格式）控制配置（format） CustomControl 元素的控件的配置（Format）控件元素的元素，以控制 CustomControl for configuration （Format） CustomEntries 元素的配置（Format） CustomEntry 元素 for CustomControl for CustomItem 元素 for CustomEntry for 元素 for for ExpressionBinding for configuration CustomItem 元素 for for controlExpressionBinding 的 ItemSelectionCondition 元素，用于配置的控件的 ItemSeclectionCondition 的的属性名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f2494-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f2494-107">语法</span><span class="sxs-lookup"><span data-stu-id="f2494-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f2494-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="f2494-108">Attributes and Elements</span></span>

<span data-ttu-id="f2494-109">以下各节介绍了 `PropertyName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f2494-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f2494-110">属性</span><span class="sxs-lookup"><span data-stu-id="f2494-110">Attributes</span></span>

<span data-ttu-id="f2494-111">无。</span><span class="sxs-lookup"><span data-stu-id="f2494-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f2494-112">子元素</span><span class="sxs-lookup"><span data-stu-id="f2494-112">Child Elements</span></span>

<span data-ttu-id="f2494-113">无。</span><span class="sxs-lookup"><span data-stu-id="f2494-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f2494-114">父元素</span><span class="sxs-lookup"><span data-stu-id="f2494-114">Parent Elements</span></span>

|<span data-ttu-id="f2494-115">元素</span><span class="sxs-lookup"><span data-stu-id="f2494-115">Element</span></span>|<span data-ttu-id="f2494-116">描述</span><span class="sxs-lookup"><span data-stu-id="f2494-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f2494-117">用于配置的控件的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f2494-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="f2494-118">定义要使用此控件必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="f2494-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f2494-119">文本值</span><span class="sxs-lookup"><span data-stu-id="f2494-119">Text Value</span></span>

<span data-ttu-id="f2494-120">指定触发条件的 .NET 属性的名称。</span><span class="sxs-lookup"><span data-stu-id="f2494-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="f2494-121">备注</span><span class="sxs-lookup"><span data-stu-id="f2494-121">Remarks</span></span>

<span data-ttu-id="f2494-122">如果使用此元素，则在定义选择条件时，不能指定[ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="f2494-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2494-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f2494-123">See Also</span></span>

[<span data-ttu-id="f2494-124">用于配置的控件的 ItemSeclectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f2494-124">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="f2494-125">用于配置的控件的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f2494-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="f2494-126">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="f2494-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
