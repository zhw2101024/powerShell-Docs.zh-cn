---
title: 用于视图（格式）的 CustomItem 的 ExpressionBinding 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363776"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="cda2a-102">ExpressionBinding Element for CustomItem for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="cda2a-102">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="cda2a-103">定义控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="cda2a-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="cda2a-104">定义可由视图使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="cda2a-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="cda2a-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 元素（format） Control 元素 for View （format） CustomControl 元素的控件元素，用于控件的 View （format） CustomEntries 元素CustomControl for view （Format） CustomEntry 元素 for CustomEntries for view （format） CustomItem 元素 for CustomEntry for view （format）元素 for ExpressionBinding for view （format）的控件</span><span class="sxs-lookup"><span data-stu-id="cda2a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cda2a-106">语法</span><span class="sxs-lookup"><span data-stu-id="cda2a-106">Syntax</span></span>

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cda2a-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="cda2a-107">Attributes and Elements</span></span>

<span data-ttu-id="cda2a-108">以下各节介绍了 `ExpressionBinding` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cda2a-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cda2a-109">属性</span><span class="sxs-lookup"><span data-stu-id="cda2a-109">Attributes</span></span>

<span data-ttu-id="cda2a-110">无。</span><span class="sxs-lookup"><span data-stu-id="cda2a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cda2a-111">子元素</span><span class="sxs-lookup"><span data-stu-id="cda2a-111">Child Elements</span></span>

|<span data-ttu-id="cda2a-112">元素</span><span class="sxs-lookup"><span data-stu-id="cda2a-112">Element</span></span>|<span data-ttu-id="cda2a-113">描述</span><span class="sxs-lookup"><span data-stu-id="cda2a-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="cda2a-114">可选元素。</span><span class="sxs-lookup"><span data-stu-id="cda2a-114">Optional element.</span></span><br /><br /> <span data-ttu-id="cda2a-115">定义此控件使用的控件。</span><span class="sxs-lookup"><span data-stu-id="cda2a-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="cda2a-116">用于视图的控件的 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cda2a-116">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="cda2a-117">可选元素。</span><span class="sxs-lookup"><span data-stu-id="cda2a-117">Optional element.</span></span><br /><br /> <span data-ttu-id="cda2a-118">指定公共控件或视图控件的名称。</span><span class="sxs-lookup"><span data-stu-id="cda2a-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="cda2a-119">用于视图的控件的 ExpressionBinding 的 EnumerateCollection 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cda2a-119">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="cda2a-120">可选元素。</span><span class="sxs-lookup"><span data-stu-id="cda2a-120">Optional element.</span></span><br /><br /> <span data-ttu-id="cda2a-121">指定显示集合的元素。</span><span class="sxs-lookup"><span data-stu-id="cda2a-121">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="cda2a-122">用于视图的控件的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cda2a-122">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="cda2a-123">可选元素。</span><span class="sxs-lookup"><span data-stu-id="cda2a-123">Optional element.</span></span><br /><br /> <span data-ttu-id="cda2a-124">定义要使用此控件必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="cda2a-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="cda2a-125">View 的 ExpressionBinding for Controls 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="cda2a-125">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="cda2a-126">可选元素。</span><span class="sxs-lookup"><span data-stu-id="cda2a-126">Optional element.</span></span><br /><br /> <span data-ttu-id="cda2a-127">指定其值由控件显示的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="cda2a-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="cda2a-128">用于视图的控件的 ExpressionBinding 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cda2a-128">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="cda2a-129">可选元素。</span><span class="sxs-lookup"><span data-stu-id="cda2a-129">Optional element.</span></span><br /><br /> <span data-ttu-id="cda2a-130">指定其值由控件显示的脚本。</span><span class="sxs-lookup"><span data-stu-id="cda2a-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cda2a-131">父元素</span><span class="sxs-lookup"><span data-stu-id="cda2a-131">Parent Elements</span></span>

|<span data-ttu-id="cda2a-132">元素</span><span class="sxs-lookup"><span data-stu-id="cda2a-132">Element</span></span>|<span data-ttu-id="cda2a-133">描述</span><span class="sxs-lookup"><span data-stu-id="cda2a-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cda2a-134">用于视图的控件的 CustomEntry 的 CustomItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cda2a-134">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="cda2a-135">定义控件显示的数据及其显示方式。</span><span class="sxs-lookup"><span data-stu-id="cda2a-135">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cda2a-136">备注</span><span class="sxs-lookup"><span data-stu-id="cda2a-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="cda2a-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cda2a-137">See Also</span></span>

[<span data-ttu-id="cda2a-138">用于视图的控件的 CustomEntry 的 CustomItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cda2a-138">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="cda2a-139">用于视图的控件的 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cda2a-139">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="cda2a-140">用于视图的控件的 ExpressionBinding 的 EnumerateCollection 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cda2a-140">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="cda2a-141">用于视图的控件的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cda2a-141">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="cda2a-142">View 的 ExpressionBinding for Controls 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="cda2a-142">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="cda2a-143">用于视图的控件的 ExpressionBinding 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cda2a-143">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="cda2a-144">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="cda2a-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
