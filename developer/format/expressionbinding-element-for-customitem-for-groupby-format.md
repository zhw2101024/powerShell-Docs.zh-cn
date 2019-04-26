---
title: GroupBy （格式） 的 CustomItem ExpressionBinding 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065897"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a><span data-ttu-id="9450a-102">ExpressionBinding Element for CustomItem for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9450a-102">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="9450a-103">定义由控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="9450a-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="9450a-104">定义如何显示一组新对象时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="9450a-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="9450a-105">GroupBy （格式） 的 GroupBy （格式） CustomEntry 元素 CustomControl CustomEntries 元素的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素CustomControl GroupBy （格式） 的 GroupBy （格式） 的 GroupBy （格式） 的 CustomItem ExpressionBinding 元素 CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="9450a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9450a-106">语法</span><span class="sxs-lookup"><span data-stu-id="9450a-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="9450a-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="9450a-107">Attributes and Elements</span></span>

<span data-ttu-id="9450a-108">以下各节描述了特性、 子元素和父元素的`ExpressionBinding`元素。</span><span class="sxs-lookup"><span data-stu-id="9450a-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9450a-109">属性</span><span class="sxs-lookup"><span data-stu-id="9450a-109">Attributes</span></span>

<span data-ttu-id="9450a-110">无。</span><span class="sxs-lookup"><span data-stu-id="9450a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9450a-111">子元素</span><span class="sxs-lookup"><span data-stu-id="9450a-111">Child Elements</span></span>

|<span data-ttu-id="9450a-112">元素</span><span class="sxs-lookup"><span data-stu-id="9450a-112">Element</span></span>|<span data-ttu-id="9450a-113">说明</span><span class="sxs-lookup"><span data-stu-id="9450a-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="9450a-114">可选元素。</span><span class="sxs-lookup"><span data-stu-id="9450a-114">Optional element.</span></span><br /><br /> <span data-ttu-id="9450a-115">定义此控件使用的控件。</span><span class="sxs-lookup"><span data-stu-id="9450a-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="9450a-116">GroupBy （格式） 的 ExpressionBinding 的 CustomControlName 元素</span><span class="sxs-lookup"><span data-stu-id="9450a-116">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="9450a-117">可选元素。</span><span class="sxs-lookup"><span data-stu-id="9450a-117">Optional element.</span></span><br /><br /> <span data-ttu-id="9450a-118">指定公共控件或视图控件的名称。</span><span class="sxs-lookup"><span data-stu-id="9450a-118">Specifies the name of a common control or a view control.</span></span>|
|<span data-ttu-id="9450a-119">[GroupBy （格式） 的 ExpressionBinding 的 EnumerateCollection 元素](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)GroupBy （格式） 的 ExpressionBinding 的 EnumerateCollection 元素</span><span class="sxs-lookup"><span data-stu-id="9450a-119">[EnumerateCollection Element for ExpressionBinding for GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>|<span data-ttu-id="9450a-120">可选元素。</span><span class="sxs-lookup"><span data-stu-id="9450a-120">Optional element.</span></span><br /><br /> <span data-ttu-id="9450a-121">指定显示的元素的集合。</span><span class="sxs-lookup"><span data-stu-id="9450a-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="9450a-122">GroupBy （格式） 的 ExpressionBinding 的 ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="9450a-122">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="9450a-123">可选元素。</span><span class="sxs-lookup"><span data-stu-id="9450a-123">Optional element.</span></span><br /><br /> <span data-ttu-id="9450a-124">定义要在使用此控件中必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="9450a-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="9450a-125">GroupBy （格式） 的 ExpressionBinding 的 PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="9450a-125">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="9450a-126">可选元素。</span><span class="sxs-lookup"><span data-stu-id="9450a-126">Optional element.</span></span><br /><br /> <span data-ttu-id="9450a-127">指定控件显示其值的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="9450a-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="9450a-128">ExpressionBinding 的 GroupBy （格式） 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="9450a-128">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="9450a-129">可选元素。</span><span class="sxs-lookup"><span data-stu-id="9450a-129">Optional element.</span></span><br /><br /> <span data-ttu-id="9450a-130">指定控件显示其值的脚本。</span><span class="sxs-lookup"><span data-stu-id="9450a-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9450a-131">父元素</span><span class="sxs-lookup"><span data-stu-id="9450a-131">Parent Elements</span></span>

|<span data-ttu-id="9450a-132">元素</span><span class="sxs-lookup"><span data-stu-id="9450a-132">Element</span></span>|<span data-ttu-id="9450a-133">说明</span><span class="sxs-lookup"><span data-stu-id="9450a-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9450a-134">GroupBy （格式） 的 CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="9450a-134">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="9450a-135">定义由自定义控件视图中显示的数据和显示方式。</span><span class="sxs-lookup"><span data-stu-id="9450a-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="9450a-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9450a-136">See Also</span></span>

[<span data-ttu-id="9450a-137">GroupBy （格式） 的 ExpressionBinding 的 CustomControlName 元素</span><span class="sxs-lookup"><span data-stu-id="9450a-137">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="9450a-138">GroupBy （格式） 的 ExpressionBinding 的 EnumerateCollection 元素</span><span class="sxs-lookup"><span data-stu-id="9450a-138">EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="9450a-139">GroupBy （格式） 的 ExpressionBinding 的 ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="9450a-139">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="9450a-140">GroupBy （格式） 的 ExpressionBinding 的 PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="9450a-140">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="9450a-141">ExpressionBinding 的 GroupBy （格式） 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="9450a-141">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="9450a-142">GroupBy （格式） 的 CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="9450a-142">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="9450a-143">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="9450a-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
