---
title: GroupBy （格式） 的 ExpressionBinding 的 ItemSelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853133"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="bd874-102">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bd874-102">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="bd874-103">定义要在使用此控件中必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="bd874-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="bd874-104">可以为控件项指定的选择条件数目没有限制。</span><span class="sxs-lookup"><span data-stu-id="bd874-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="bd874-105">定义如何显示一组新对象时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="bd874-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="bd874-106">GroupBy （格式） 的 GroupBy （格式） CustomEntry 元素 CustomControl CustomEntries 元素的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素CustomControl ExpressionBinding 的 GroupBy （格式） 的 GroupBy （格式） ItemSelectionCondition 元素 CustomItem GroupBy （格式） ExpressionBinding 元素 CustomEntry GroupBy （格式） CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="bd874-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bd874-107">语法</span><span class="sxs-lookup"><span data-stu-id="bd874-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bd874-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="bd874-108">Attributes and Elements</span></span>

<span data-ttu-id="bd874-109">以下各节描述了特性、 子元素和父元素的`ItemSelectionCondition`元素。</span><span class="sxs-lookup"><span data-stu-id="bd874-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bd874-110">特性</span><span class="sxs-lookup"><span data-stu-id="bd874-110">Attributes</span></span>

<span data-ttu-id="bd874-111">无。</span><span class="sxs-lookup"><span data-stu-id="bd874-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bd874-112">子元素</span><span class="sxs-lookup"><span data-stu-id="bd874-112">Child Elements</span></span>

|<span data-ttu-id="bd874-113">元素</span><span class="sxs-lookup"><span data-stu-id="bd874-113">Element</span></span>|<span data-ttu-id="bd874-114">描述</span><span class="sxs-lookup"><span data-stu-id="bd874-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bd874-115">GroupBy （格式） 的 ItemSelectionCondition PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="bd874-115">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="bd874-116">可选元素。</span><span class="sxs-lookup"><span data-stu-id="bd874-116">Optional element.</span></span><br /><br /> <span data-ttu-id="bd874-117">指定触发条件的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="bd874-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="bd874-118">GroupBy （格式） 的 ItemSelectionCondition 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="bd874-118">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="bd874-119">可选元素。</span><span class="sxs-lookup"><span data-stu-id="bd874-119">Optional element.</span></span><br /><br /> <span data-ttu-id="bd874-120">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="bd874-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bd874-121">父元素</span><span class="sxs-lookup"><span data-stu-id="bd874-121">Parent Elements</span></span>

|<span data-ttu-id="bd874-122">元素</span><span class="sxs-lookup"><span data-stu-id="bd874-122">Element</span></span>|<span data-ttu-id="bd874-123">描述</span><span class="sxs-lookup"><span data-stu-id="bd874-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bd874-124">GroupBy （格式） 的 CustomItem ExpressionBinding 元素</span><span class="sxs-lookup"><span data-stu-id="bd874-124">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="bd874-125">定义由控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="bd874-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bd874-126">备注</span><span class="sxs-lookup"><span data-stu-id="bd874-126">Remarks</span></span>

<span data-ttu-id="bd874-127">您可以指定一个属性名称或用于这种情况的脚本，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="bd874-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="bd874-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bd874-128">See Also</span></span>

[<span data-ttu-id="bd874-129">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="bd874-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="bd874-130">GroupBy （格式） 的 CustomItem ExpressionBinding 元素</span><span class="sxs-lookup"><span data-stu-id="bd874-130">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
