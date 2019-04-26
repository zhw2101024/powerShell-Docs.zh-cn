---
title: ExpressionBinding 的 Controls 的视图 （格式） 的 ItemSelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065472"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="37d95-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="37d95-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="37d95-103">定义要在使用此控件中必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="37d95-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="37d95-104">定义一个视图，可以使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="37d95-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="37d95-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 控件元素 （格式） 控制元素的控件的视图 （格式） CustomEntries 元素的控件的控件的视图 （格式） CustomControl 元素CustomControl CustomEntries CustomEntry CustomItem 视图 （格式） 的控件的视图 （格式） ExpressionBinding 元素的控件的视图 （格式） CustomItem 元素的控件的视图 （格式） CustomEntry 元素ExpressionBinding 的 Controls 的视图 （格式） 的 ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="37d95-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="37d95-106">语法</span><span class="sxs-lookup"><span data-stu-id="37d95-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="37d95-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="37d95-107">Attributes and Elements</span></span>

<span data-ttu-id="37d95-108">以下各节描述了特性、 子元素和父元素的`ItemSelectionCondition`元素。</span><span class="sxs-lookup"><span data-stu-id="37d95-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="37d95-109">属性</span><span class="sxs-lookup"><span data-stu-id="37d95-109">Attributes</span></span>

<span data-ttu-id="37d95-110">无。</span><span class="sxs-lookup"><span data-stu-id="37d95-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="37d95-111">子元素</span><span class="sxs-lookup"><span data-stu-id="37d95-111">Child Elements</span></span>

|<span data-ttu-id="37d95-112">元素</span><span class="sxs-lookup"><span data-stu-id="37d95-112">Element</span></span>|<span data-ttu-id="37d95-113">说明</span><span class="sxs-lookup"><span data-stu-id="37d95-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="37d95-114">ItemSelectionCondition 视图 （格式） 的控件的属性名称元素</span><span class="sxs-lookup"><span data-stu-id="37d95-114">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="37d95-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="37d95-115">Optional element.</span></span><br /><br /> <span data-ttu-id="37d95-116">指定触发条件的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="37d95-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="37d95-117">ItemSelectionCondition 的 Controls 的视图 （格式） 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="37d95-117">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="37d95-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="37d95-118">Optional element.</span></span><br /><br /> <span data-ttu-id="37d95-119">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="37d95-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="37d95-120">父元素</span><span class="sxs-lookup"><span data-stu-id="37d95-120">Parent Elements</span></span>

|<span data-ttu-id="37d95-121">元素</span><span class="sxs-lookup"><span data-stu-id="37d95-121">Element</span></span>|<span data-ttu-id="37d95-122">说明</span><span class="sxs-lookup"><span data-stu-id="37d95-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="37d95-123">ExpressionBinding CustomItem 视图 （格式） 的控件元素</span><span class="sxs-lookup"><span data-stu-id="37d95-123">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="37d95-124">定义由控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="37d95-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="37d95-125">备注</span><span class="sxs-lookup"><span data-stu-id="37d95-125">Remarks</span></span>

<span data-ttu-id="37d95-126">您可以指定一个属性名称或用于这种情况的脚本，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="37d95-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="37d95-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="37d95-127">See Also</span></span>

[<span data-ttu-id="37d95-128">ItemSelectionCondition 视图 （格式） 的控件的属性名称元素</span><span class="sxs-lookup"><span data-stu-id="37d95-128">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="37d95-129">ItemSelectionCondition 的 Controls 的视图 （格式） 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="37d95-129">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="37d95-130">ExpressionBinding CustomItem 视图 （格式） 的控件元素</span><span class="sxs-lookup"><span data-stu-id="37d95-130">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="37d95-131">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="37d95-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
