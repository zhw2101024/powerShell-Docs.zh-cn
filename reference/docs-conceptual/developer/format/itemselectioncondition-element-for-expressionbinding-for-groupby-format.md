---
title: GroupBy （Format）的 ExpressionBinding 的 ItemSelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365286"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="6b631-102">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="6b631-102">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="6b631-103">定义要使用此控件必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="6b631-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="6b631-104">对于可为控件项指定的选择条件数没有限制。</span><span class="sxs-lookup"><span data-stu-id="6b631-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="6b631-105">此元素在定义如何显示新的对象组时使用。</span><span class="sxs-lookup"><span data-stu-id="6b631-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="6b631-106">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format）对于 GroupBy （format） CustomEntries 元素，用于元素的 CustomControl 元素（format）CustomControl for groupby （format） CustomItem 元素 for CustomEntry for groupby （format） ExpressionBinding 元素 for CustomItem for groupby （format） ItemSelectionCondition 元素 for groupby （Format）</span><span class="sxs-lookup"><span data-stu-id="6b631-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6b631-107">语法</span><span class="sxs-lookup"><span data-stu-id="6b631-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6b631-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="6b631-108">Attributes and Elements</span></span>

<span data-ttu-id="6b631-109">以下各节介绍了 `ItemSelectionCondition` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6b631-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6b631-110">属性</span><span class="sxs-lookup"><span data-stu-id="6b631-110">Attributes</span></span>

<span data-ttu-id="6b631-111">无。</span><span class="sxs-lookup"><span data-stu-id="6b631-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6b631-112">子元素</span><span class="sxs-lookup"><span data-stu-id="6b631-112">Child Elements</span></span>

|<span data-ttu-id="6b631-113">元素</span><span class="sxs-lookup"><span data-stu-id="6b631-113">Element</span></span>|<span data-ttu-id="6b631-114">描述</span><span class="sxs-lookup"><span data-stu-id="6b631-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6b631-115">GroupBy 的 ItemSelectionCondition 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="6b631-115">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="6b631-116">可选元素。</span><span class="sxs-lookup"><span data-stu-id="6b631-116">Optional element.</span></span><br /><br /> <span data-ttu-id="6b631-117">指定触发条件的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="6b631-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="6b631-118">GroupBy 的 ItemSelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6b631-118">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="6b631-119">可选元素。</span><span class="sxs-lookup"><span data-stu-id="6b631-119">Optional element.</span></span><br /><br /> <span data-ttu-id="6b631-120">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="6b631-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6b631-121">父元素</span><span class="sxs-lookup"><span data-stu-id="6b631-121">Parent Elements</span></span>

|<span data-ttu-id="6b631-122">元素</span><span class="sxs-lookup"><span data-stu-id="6b631-122">Element</span></span>|<span data-ttu-id="6b631-123">描述</span><span class="sxs-lookup"><span data-stu-id="6b631-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6b631-124">GroupBy 的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6b631-124">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="6b631-125">定义控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="6b631-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6b631-126">备注</span><span class="sxs-lookup"><span data-stu-id="6b631-126">Remarks</span></span>

<span data-ttu-id="6b631-127">您可以为此条件指定一个属性名称或脚本，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="6b631-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="6b631-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6b631-128">See Also</span></span>

[<span data-ttu-id="6b631-129">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="6b631-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="6b631-130">GroupBy 的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6b631-130">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
