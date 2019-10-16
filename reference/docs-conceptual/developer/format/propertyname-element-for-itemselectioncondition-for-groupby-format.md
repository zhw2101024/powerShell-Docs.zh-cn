---
title: GroupBy （Format）的 ItemSelectionCondition 的 PropertyName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 221cbdc2-f794-4f3a-9d40-bfdd8cba1013
caps.latest.revision: 6
ms.openlocfilehash: aae65789cf5572cbcc9251eca802a2d43065e49f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362406"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="ce72d-102">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="ce72d-102">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="ce72d-103">指定触发条件的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="ce72d-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="ce72d-104">如果该属性存在，或其计算结果为 `true`，则满足条件，并使用控件。</span><span class="sxs-lookup"><span data-stu-id="ce72d-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="ce72d-105">此元素在定义如何显示新的对象组时使用。</span><span class="sxs-lookup"><span data-stu-id="ce72d-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="ce72d-106">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format）对于 GroupBy （format） CustomEntries 元素，用于元素的 CustomControl 元素（format）CustomControl for GroupBy （format） CustomItem 元素 for CustomEntry for groupby （format） ExpressionBinding 元素 for CustomItem for groupby （format） PropertyName 元素 for ItemSelectionConditionItemSelectionCondition for GroupBy （Format）</span><span class="sxs-lookup"><span data-stu-id="ce72d-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ce72d-107">语法</span><span class="sxs-lookup"><span data-stu-id="ce72d-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ce72d-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="ce72d-108">Attributes and Elements</span></span>

<span data-ttu-id="ce72d-109">以下各节介绍了 `PropertyName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ce72d-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ce72d-110">属性</span><span class="sxs-lookup"><span data-stu-id="ce72d-110">Attributes</span></span>

<span data-ttu-id="ce72d-111">无。</span><span class="sxs-lookup"><span data-stu-id="ce72d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ce72d-112">子元素</span><span class="sxs-lookup"><span data-stu-id="ce72d-112">Child Elements</span></span>

<span data-ttu-id="ce72d-113">无。</span><span class="sxs-lookup"><span data-stu-id="ce72d-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ce72d-114">父元素</span><span class="sxs-lookup"><span data-stu-id="ce72d-114">Parent Elements</span></span>

|<span data-ttu-id="ce72d-115">元素</span><span class="sxs-lookup"><span data-stu-id="ce72d-115">Element</span></span>|<span data-ttu-id="ce72d-116">描述</span><span class="sxs-lookup"><span data-stu-id="ce72d-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ce72d-117">GroupBy 的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ce72d-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="ce72d-118">定义要使用此控件必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="ce72d-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ce72d-119">文本值</span><span class="sxs-lookup"><span data-stu-id="ce72d-119">Text Value</span></span>

<span data-ttu-id="ce72d-120">指定触发条件的 .NET 属性的名称。</span><span class="sxs-lookup"><span data-stu-id="ce72d-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="ce72d-121">备注</span><span class="sxs-lookup"><span data-stu-id="ce72d-121">Remarks</span></span>

<span data-ttu-id="ce72d-122">如果使用此元素，则在定义选择条件时，不能指定[ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="ce72d-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="ce72d-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ce72d-123">See Also</span></span>

[<span data-ttu-id="ce72d-124">GroupBy 的 ItemSelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ce72d-124">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="ce72d-125">GroupBy 的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ce72d-125">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="ce72d-126">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="ce72d-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
