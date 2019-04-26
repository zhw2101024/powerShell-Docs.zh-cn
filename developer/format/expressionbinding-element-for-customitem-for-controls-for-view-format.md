---
title: ExpressionBinding 元素视图 （格式） 的控件的 CustomItem |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065933"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="490ec-102">ExpressionBinding Element for CustomItem for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="490ec-102">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="490ec-103">定义由控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="490ec-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="490ec-104">定义一个视图，可以使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="490ec-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="490ec-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 控件元素 （格式） 控制元素的控件的视图 （格式） CustomEntries 元素的控件的控件的视图 （格式） CustomControl 元素CustomControl CustomEntries CustomEntry CustomItem 视图 （格式） 的控件的视图 （格式） ExpressionBinding 元素的控件的视图 （格式） CustomItem 元素的控件的视图 （格式） CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="490ec-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="490ec-106">语法</span><span class="sxs-lookup"><span data-stu-id="490ec-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="490ec-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="490ec-107">Attributes and Elements</span></span>

<span data-ttu-id="490ec-108">以下各节描述了特性、 子元素和父元素的`ExpressionBinding`元素。</span><span class="sxs-lookup"><span data-stu-id="490ec-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="490ec-109">属性</span><span class="sxs-lookup"><span data-stu-id="490ec-109">Attributes</span></span>

<span data-ttu-id="490ec-110">无。</span><span class="sxs-lookup"><span data-stu-id="490ec-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="490ec-111">子元素</span><span class="sxs-lookup"><span data-stu-id="490ec-111">Child Elements</span></span>

|<span data-ttu-id="490ec-112">元素</span><span class="sxs-lookup"><span data-stu-id="490ec-112">Element</span></span>|<span data-ttu-id="490ec-113">说明</span><span class="sxs-lookup"><span data-stu-id="490ec-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="490ec-114">可选元素。</span><span class="sxs-lookup"><span data-stu-id="490ec-114">Optional element.</span></span><br /><br /> <span data-ttu-id="490ec-115">定义此控件使用的控件。</span><span class="sxs-lookup"><span data-stu-id="490ec-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="490ec-116">ExpressionBinding 的 Controls 的视图 （格式） 的 CustomControlName 元素</span><span class="sxs-lookup"><span data-stu-id="490ec-116">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="490ec-117">可选元素。</span><span class="sxs-lookup"><span data-stu-id="490ec-117">Optional element.</span></span><br /><br /> <span data-ttu-id="490ec-118">指定公共控件或视图控件的名称。</span><span class="sxs-lookup"><span data-stu-id="490ec-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="490ec-119">ExpressionBinding 的 Controls 的视图 （格式） 的 EnumerateCollection 元素</span><span class="sxs-lookup"><span data-stu-id="490ec-119">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="490ec-120">可选元素。</span><span class="sxs-lookup"><span data-stu-id="490ec-120">Optional element.</span></span><br /><br /> <span data-ttu-id="490ec-121">指定显示的元素的集合。</span><span class="sxs-lookup"><span data-stu-id="490ec-121">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="490ec-122">ExpressionBinding 的 Controls 的视图 （格式） 的 ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="490ec-122">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="490ec-123">可选元素。</span><span class="sxs-lookup"><span data-stu-id="490ec-123">Optional element.</span></span><br /><br /> <span data-ttu-id="490ec-124">定义要在使用此控件中必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="490ec-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="490ec-125">ExpressionBinding 的视图 （格式） 的控件的属性名称元素</span><span class="sxs-lookup"><span data-stu-id="490ec-125">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="490ec-126">可选元素。</span><span class="sxs-lookup"><span data-stu-id="490ec-126">Optional element.</span></span><br /><br /> <span data-ttu-id="490ec-127">指定控件显示其值的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="490ec-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="490ec-128">ExpressionBinding 的 Controls 的视图 （格式） 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="490ec-128">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="490ec-129">可选元素。</span><span class="sxs-lookup"><span data-stu-id="490ec-129">Optional element.</span></span><br /><br /> <span data-ttu-id="490ec-130">指定控件显示其值的脚本。</span><span class="sxs-lookup"><span data-stu-id="490ec-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="490ec-131">父元素</span><span class="sxs-lookup"><span data-stu-id="490ec-131">Parent Elements</span></span>

|<span data-ttu-id="490ec-132">元素</span><span class="sxs-lookup"><span data-stu-id="490ec-132">Element</span></span>|<span data-ttu-id="490ec-133">说明</span><span class="sxs-lookup"><span data-stu-id="490ec-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="490ec-134">视图 （格式） 的控件的 CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="490ec-134">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="490ec-135">定义由控件显示的数据和显示方式。</span><span class="sxs-lookup"><span data-stu-id="490ec-135">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="490ec-136">备注</span><span class="sxs-lookup"><span data-stu-id="490ec-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="490ec-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="490ec-137">See Also</span></span>

[<span data-ttu-id="490ec-138">视图 （格式） 的控件的 CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="490ec-138">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="490ec-139">ExpressionBinding 的 Controls 的视图 （格式） 的 CustomControlName 元素</span><span class="sxs-lookup"><span data-stu-id="490ec-139">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="490ec-140">ExpressionBinding 的 Controls 的视图 （格式） 的 EnumerateCollection 元素</span><span class="sxs-lookup"><span data-stu-id="490ec-140">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="490ec-141">ExpressionBinding 的 Controls 的视图 （格式） 的 ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="490ec-141">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="490ec-142">ExpressionBinding 的视图 （格式） 的控件的属性名称元素</span><span class="sxs-lookup"><span data-stu-id="490ec-142">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="490ec-143">ExpressionBinding 的 Controls 的视图 （格式） 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="490ec-143">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="490ec-144">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="490ec-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
