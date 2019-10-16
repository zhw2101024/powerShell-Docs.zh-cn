---
title: CustomControl （Format）的 ExpressionBinding 的 ItemSelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362906"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="2482d-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="2482d-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="2482d-103">定义要使用此控件必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="2482d-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="2482d-104">对于可为控件项指定的选择条件数没有限制。</span><span class="sxs-lookup"><span data-stu-id="2482d-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="2482d-105">定义自定义控件视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="2482d-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="2482d-106">用于 CustomEntry 的 CustomControl for view （format） CustomEntries 元素的 ViewDefinitions 元素（format） View 元素（format） CustomControl 元素（format） CustomEntries 元素CustomEntry for View （Format） ExpressionBinding 元素 for CustomItem for CustomControl for view （Format） ItemSelectionCondition 元素 for CustomControl for View （Format）的表达式绑定</span><span class="sxs-lookup"><span data-stu-id="2482d-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2482d-107">语法</span><span class="sxs-lookup"><span data-stu-id="2482d-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2482d-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="2482d-108">Attributes and Elements</span></span>

<span data-ttu-id="2482d-109">以下各节介绍了 `ItemSelectionCondition` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2482d-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2482d-110">属性</span><span class="sxs-lookup"><span data-stu-id="2482d-110">Attributes</span></span>

<span data-ttu-id="2482d-111">无。</span><span class="sxs-lookup"><span data-stu-id="2482d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2482d-112">子元素</span><span class="sxs-lookup"><span data-stu-id="2482d-112">Child Elements</span></span>

|<span data-ttu-id="2482d-113">元素</span><span class="sxs-lookup"><span data-stu-id="2482d-113">Element</span></span>|<span data-ttu-id="2482d-114">描述</span><span class="sxs-lookup"><span data-stu-id="2482d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2482d-115">View 的 ItemSelectionCondition for CustomControl 的 PropertyName 元素（格式</span><span class="sxs-lookup"><span data-stu-id="2482d-115">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="2482d-116">可选元素。</span><span class="sxs-lookup"><span data-stu-id="2482d-116">Optional element.</span></span><br /><br /> <span data-ttu-id="2482d-117">指定触发条件的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="2482d-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="2482d-118">用于 View 的 ItemSelectionCondition for CustomControl 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2482d-118">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="2482d-119">可选元素。</span><span class="sxs-lookup"><span data-stu-id="2482d-119">Optional element.</span></span><br /><br /> <span data-ttu-id="2482d-120">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="2482d-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2482d-121">父元素</span><span class="sxs-lookup"><span data-stu-id="2482d-121">Parent Elements</span></span>

|<span data-ttu-id="2482d-122">元素</span><span class="sxs-lookup"><span data-stu-id="2482d-122">Element</span></span>|<span data-ttu-id="2482d-123">描述</span><span class="sxs-lookup"><span data-stu-id="2482d-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2482d-124">用于 View 的 CustomControl 的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2482d-124">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="2482d-125">定义控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="2482d-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2482d-126">备注</span><span class="sxs-lookup"><span data-stu-id="2482d-126">Remarks</span></span>

<span data-ttu-id="2482d-127">您可以为此条件指定一个属性名称或脚本，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="2482d-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="2482d-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2482d-128">See Also</span></span>

[<span data-ttu-id="2482d-129">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="2482d-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="2482d-130">用于 View 的 CustomControl 的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2482d-130">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
