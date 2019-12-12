---
title: GroupBy （Format）的 CustomItem 的 ExpressionBinding 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368626"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a><span data-ttu-id="4d822-102">ExpressionBinding Element for CustomItem for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4d822-102">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="4d822-103">定义控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="4d822-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="4d822-104">此元素在定义如何显示新的对象组时使用。</span><span class="sxs-lookup"><span data-stu-id="4d822-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="4d822-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format）对于 GroupBy （format） CustomEntries 元素，用于元素的 CustomControl 元素（format）CustomControl for groupby （format） CustomItem 元素 for CustomEntry for groupby （format） ExpressionBinding 元素 for GroupBy （Format）</span><span class="sxs-lookup"><span data-stu-id="4d822-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4d822-106">语法</span><span class="sxs-lookup"><span data-stu-id="4d822-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="4d822-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="4d822-107">Attributes and Elements</span></span>

<span data-ttu-id="4d822-108">以下各节介绍了 `ExpressionBinding` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4d822-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4d822-109">属性</span><span class="sxs-lookup"><span data-stu-id="4d822-109">Attributes</span></span>

<span data-ttu-id="4d822-110">无。</span><span class="sxs-lookup"><span data-stu-id="4d822-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4d822-111">子元素</span><span class="sxs-lookup"><span data-stu-id="4d822-111">Child Elements</span></span>

|<span data-ttu-id="4d822-112">元素</span><span class="sxs-lookup"><span data-stu-id="4d822-112">Element</span></span>|<span data-ttu-id="4d822-113">描述</span><span class="sxs-lookup"><span data-stu-id="4d822-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="4d822-114">可选元素。</span><span class="sxs-lookup"><span data-stu-id="4d822-114">Optional element.</span></span><br /><br /> <span data-ttu-id="4d822-115">定义此控件使用的控件。</span><span class="sxs-lookup"><span data-stu-id="4d822-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="4d822-116">GroupBy 的 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4d822-116">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="4d822-117">可选元素。</span><span class="sxs-lookup"><span data-stu-id="4d822-117">Optional element.</span></span><br /><br /> <span data-ttu-id="4d822-118">指定公共控件或视图控件的名称。</span><span class="sxs-lookup"><span data-stu-id="4d822-118">Specifies the name of a common control or a view control.</span></span>|
|<span data-ttu-id="4d822-119">[GroupBy 的 ExpressionBinding 的 EnumerateCollection 元素（格式）](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)GroupBy 的 ExpressionBinding 的 EnumerateCollection 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4d822-119">[EnumerateCollection Element for ExpressionBinding for GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>|<span data-ttu-id="4d822-120">可选元素。</span><span class="sxs-lookup"><span data-stu-id="4d822-120">Optional element.</span></span><br /><br /> <span data-ttu-id="4d822-121">指定显示集合的元素。</span><span class="sxs-lookup"><span data-stu-id="4d822-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="4d822-122">GroupBy 的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4d822-122">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="4d822-123">可选元素。</span><span class="sxs-lookup"><span data-stu-id="4d822-123">Optional element.</span></span><br /><br /> <span data-ttu-id="4d822-124">定义要使用此控件必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="4d822-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="4d822-125">GroupBy 的 ExpressionBinding 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="4d822-125">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="4d822-126">可选元素。</span><span class="sxs-lookup"><span data-stu-id="4d822-126">Optional element.</span></span><br /><br /> <span data-ttu-id="4d822-127">指定其值由控件显示的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="4d822-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="4d822-128">GroupBy 的 ExpressionBinding 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4d822-128">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="4d822-129">可选元素。</span><span class="sxs-lookup"><span data-stu-id="4d822-129">Optional element.</span></span><br /><br /> <span data-ttu-id="4d822-130">指定其值由控件显示的脚本。</span><span class="sxs-lookup"><span data-stu-id="4d822-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4d822-131">父元素</span><span class="sxs-lookup"><span data-stu-id="4d822-131">Parent Elements</span></span>

|<span data-ttu-id="4d822-132">元素</span><span class="sxs-lookup"><span data-stu-id="4d822-132">Element</span></span>|<span data-ttu-id="4d822-133">描述</span><span class="sxs-lookup"><span data-stu-id="4d822-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4d822-134">GroupBy 的 CustomEntry 的 CustomItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4d822-134">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="4d822-135">定义自定义控件视图显示的数据及其显示方式。</span><span class="sxs-lookup"><span data-stu-id="4d822-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="4d822-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4d822-136">See Also</span></span>

[<span data-ttu-id="4d822-137">GroupBy 的 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4d822-137">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="4d822-138">GroupBy 的 ExpressionBinding 的 EnumerateCollection 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4d822-138">EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="4d822-139">GroupBy 的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4d822-139">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="4d822-140">GroupBy 的 ExpressionBinding 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="4d822-140">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="4d822-141">GroupBy 的 ExpressionBinding 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4d822-141">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="4d822-142">GroupBy 的 CustomEntry 的 CustomItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4d822-142">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="4d822-143">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="4d822-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
