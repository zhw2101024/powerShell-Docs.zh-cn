---
title: GroupBy （格式） 的 ItemSelectionCondition PropertyName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 221cbdc2-f794-4f3a-9d40-bfdd8cba1013
caps.latest.revision: 6
ms.openlocfilehash: aae65789cf5572cbcc9251eca802a2d43065e49f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064758"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="a1cfd-102">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a1cfd-102">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="a1cfd-103">指定触发条件的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="a1cfd-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="a1cfd-104">存在此属性时或当计算结果为`true`、 满足该条件，并使用该控件。</span><span class="sxs-lookup"><span data-stu-id="a1cfd-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="a1cfd-105">定义如何显示一组新对象时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="a1cfd-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="a1cfd-106">GroupBy （格式） 的 GroupBy （格式） CustomEntry 元素 CustomControl CustomEntries 元素的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素CustomControl GroupBy （格式） 的 GroupBy （格式） 的 GroupBy （格式） 的 GroupBy （格式） PropertyName 元素 ExpressionBinding ItemSelectionCondition 元素 CustomItem ExpressionBinding 元素 CustomEntry CustomItem 元素GroupBy （格式） 的 ItemSelectionCondition</span><span class="sxs-lookup"><span data-stu-id="a1cfd-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a1cfd-107">语法</span><span class="sxs-lookup"><span data-stu-id="a1cfd-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a1cfd-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="a1cfd-108">Attributes and Elements</span></span>

<span data-ttu-id="a1cfd-109">以下各节描述了特性、 子元素和父元素的`PropertyName`元素。</span><span class="sxs-lookup"><span data-stu-id="a1cfd-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a1cfd-110">属性</span><span class="sxs-lookup"><span data-stu-id="a1cfd-110">Attributes</span></span>

<span data-ttu-id="a1cfd-111">无。</span><span class="sxs-lookup"><span data-stu-id="a1cfd-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a1cfd-112">子元素</span><span class="sxs-lookup"><span data-stu-id="a1cfd-112">Child Elements</span></span>

<span data-ttu-id="a1cfd-113">无。</span><span class="sxs-lookup"><span data-stu-id="a1cfd-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a1cfd-114">父元素</span><span class="sxs-lookup"><span data-stu-id="a1cfd-114">Parent Elements</span></span>

|<span data-ttu-id="a1cfd-115">元素</span><span class="sxs-lookup"><span data-stu-id="a1cfd-115">Element</span></span>|<span data-ttu-id="a1cfd-116">说明</span><span class="sxs-lookup"><span data-stu-id="a1cfd-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a1cfd-117">GroupBy （格式） 的 ExpressionBinding 的 ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="a1cfd-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="a1cfd-118">定义要在使用此控件中必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="a1cfd-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a1cfd-119">文本值</span><span class="sxs-lookup"><span data-stu-id="a1cfd-119">Text Value</span></span>

<span data-ttu-id="a1cfd-120">指定触发条件的.NET 属性的名称。</span><span class="sxs-lookup"><span data-stu-id="a1cfd-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="a1cfd-121">备注</span><span class="sxs-lookup"><span data-stu-id="a1cfd-121">Remarks</span></span>

<span data-ttu-id="a1cfd-122">如果使用此元素时，不能指定[ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)元素定义的选择条件时。</span><span class="sxs-lookup"><span data-stu-id="a1cfd-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1cfd-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a1cfd-123">See Also</span></span>

[<span data-ttu-id="a1cfd-124">GroupBy （格式） 的 ItemSelectionCondition 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="a1cfd-124">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="a1cfd-125">GroupBy （格式） 的 ExpressionBinding 的 ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="a1cfd-125">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="a1cfd-126">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="a1cfd-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
