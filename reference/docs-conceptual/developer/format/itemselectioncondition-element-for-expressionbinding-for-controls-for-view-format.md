---
title: 用于视图（格式）的 ExpressionBinding 的 ItemSelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362936"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="7d113-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="7d113-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="7d113-103">定义要使用此控件必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="7d113-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="7d113-104">定义可由视图使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="7d113-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="7d113-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 元素（format） Control 元素 for View （format） CustomControl 元素的控件元素，用于控件的 View （format） CustomEntries 元素CustomControl for view （Format） CustomEntry 元素 for CustomEntries for view （format） CustomItem 元素 for CustomEntry for view （format）元素 for ExpressionBinding for view （format）的控件用于视图的控件的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7d113-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7d113-106">语法</span><span class="sxs-lookup"><span data-stu-id="7d113-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7d113-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="7d113-107">Attributes and Elements</span></span>

<span data-ttu-id="7d113-108">以下各节介绍了 `ItemSelectionCondition` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7d113-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7d113-109">属性</span><span class="sxs-lookup"><span data-stu-id="7d113-109">Attributes</span></span>

<span data-ttu-id="7d113-110">无。</span><span class="sxs-lookup"><span data-stu-id="7d113-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7d113-111">子元素</span><span class="sxs-lookup"><span data-stu-id="7d113-111">Child Elements</span></span>

|<span data-ttu-id="7d113-112">元素</span><span class="sxs-lookup"><span data-stu-id="7d113-112">Element</span></span>|<span data-ttu-id="7d113-113">描述</span><span class="sxs-lookup"><span data-stu-id="7d113-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7d113-114">View 的 ItemSelectionCondition for Controls 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="7d113-114">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="7d113-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="7d113-115">Optional element.</span></span><br /><br /> <span data-ttu-id="7d113-116">指定触发条件的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="7d113-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="7d113-117">用于视图的控件的 ItemSelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7d113-117">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="7d113-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="7d113-118">Optional element.</span></span><br /><br /> <span data-ttu-id="7d113-119">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="7d113-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7d113-120">父元素</span><span class="sxs-lookup"><span data-stu-id="7d113-120">Parent Elements</span></span>

|<span data-ttu-id="7d113-121">元素</span><span class="sxs-lookup"><span data-stu-id="7d113-121">Element</span></span>|<span data-ttu-id="7d113-122">描述</span><span class="sxs-lookup"><span data-stu-id="7d113-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7d113-123">用于视图的控件的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7d113-123">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="7d113-124">定义控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="7d113-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7d113-125">备注</span><span class="sxs-lookup"><span data-stu-id="7d113-125">Remarks</span></span>

<span data-ttu-id="7d113-126">您可以为此条件指定一个属性名称或脚本，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="7d113-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d113-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7d113-127">See Also</span></span>

[<span data-ttu-id="7d113-128">View 的 ItemSelectionCondition for Controls 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="7d113-128">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="7d113-129">用于视图的控件的 ItemSelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7d113-129">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="7d113-130">用于视图的控件的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7d113-130">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="7d113-131">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="7d113-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
