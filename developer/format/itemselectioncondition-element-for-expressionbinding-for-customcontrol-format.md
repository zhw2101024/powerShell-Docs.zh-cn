---
title: CustomControl （格式） 的 ExpressionBinding 的 ItemSelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065806"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="ce34c-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ce34c-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="ce34c-103">定义要在使用此控件中必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="ce34c-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="ce34c-104">可以为控件项指定的选择条件数目没有限制。</span><span class="sxs-lookup"><span data-stu-id="ce34c-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="ce34c-105">定义自定义控件视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="ce34c-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="ce34c-106">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素 （格式） CustomEntries 元素 CustomControl 视图 （格式） 的视图 （格式） CustomItem 元素 CustomEntries CustomEntry 元素CustomEntry CustomItem CustomControl CustomControl 视图 （格式） 的表达式绑定的视图 （格式） ItemSelectionCondition 元素的视图 （格式） ExpressionBinding 元素</span><span class="sxs-lookup"><span data-stu-id="ce34c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ce34c-107">语法</span><span class="sxs-lookup"><span data-stu-id="ce34c-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ce34c-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="ce34c-108">Attributes and Elements</span></span>

<span data-ttu-id="ce34c-109">以下各节描述了特性、 子元素和父元素的`ItemSelectionCondition`元素。</span><span class="sxs-lookup"><span data-stu-id="ce34c-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ce34c-110">属性</span><span class="sxs-lookup"><span data-stu-id="ce34c-110">Attributes</span></span>

<span data-ttu-id="ce34c-111">无。</span><span class="sxs-lookup"><span data-stu-id="ce34c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ce34c-112">子元素</span><span class="sxs-lookup"><span data-stu-id="ce34c-112">Child Elements</span></span>

|<span data-ttu-id="ce34c-113">元素</span><span class="sxs-lookup"><span data-stu-id="ce34c-113">Element</span></span>|<span data-ttu-id="ce34c-114">说明</span><span class="sxs-lookup"><span data-stu-id="ce34c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ce34c-115">为视图 （格式为 CustomControl ItemSelectionCondition PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="ce34c-115">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="ce34c-116">可选元素。</span><span class="sxs-lookup"><span data-stu-id="ce34c-116">Optional element.</span></span><br /><br /> <span data-ttu-id="ce34c-117">指定触发条件的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="ce34c-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="ce34c-118">为视图 （格式） 的 CustomControl ItemSelectionCondition 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="ce34c-118">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="ce34c-119">可选元素。</span><span class="sxs-lookup"><span data-stu-id="ce34c-119">Optional element.</span></span><br /><br /> <span data-ttu-id="ce34c-120">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="ce34c-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ce34c-121">父元素</span><span class="sxs-lookup"><span data-stu-id="ce34c-121">Parent Elements</span></span>

|<span data-ttu-id="ce34c-122">元素</span><span class="sxs-lookup"><span data-stu-id="ce34c-122">Element</span></span>|<span data-ttu-id="ce34c-123">说明</span><span class="sxs-lookup"><span data-stu-id="ce34c-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ce34c-124">为视图 （格式） 的 CustomControl CustomItem ExpressionBinding 元素</span><span class="sxs-lookup"><span data-stu-id="ce34c-124">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="ce34c-125">定义由控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="ce34c-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ce34c-126">备注</span><span class="sxs-lookup"><span data-stu-id="ce34c-126">Remarks</span></span>

<span data-ttu-id="ce34c-127">您可以指定一个属性名称或用于这种情况的脚本，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="ce34c-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="ce34c-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ce34c-128">See Also</span></span>

[<span data-ttu-id="ce34c-129">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="ce34c-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="ce34c-130">为视图 （格式） 的 CustomControl CustomItem ExpressionBinding 元素</span><span class="sxs-lookup"><span data-stu-id="ce34c-130">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
