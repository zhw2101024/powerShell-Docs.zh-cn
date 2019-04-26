---
title: ExpressionBinding 元素的视图 （格式） 的 CustomControl CustomItem |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065914"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="ee7dd-102">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="ee7dd-102">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="ee7dd-103">定义由控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="ee7dd-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="ee7dd-104">定义自定义控件视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="ee7dd-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="ee7dd-105">视图 （格式） 的视图 （格式） 的视图 (CustomControl CustomEntries CustomEntry 元素 CustomControl CustomEntries 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素格式） 的视图 （格式） 的视图 （格式） 的 CustomControl CustomItem ExpressionBinding 元素 CustomControl CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="ee7dd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ee7dd-106">语法</span><span class="sxs-lookup"><span data-stu-id="ee7dd-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="ee7dd-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="ee7dd-107">Attributes and Elements</span></span>

<span data-ttu-id="ee7dd-108">以下各节描述了特性、 子元素和父元素的`ExpressionBinding`元素。</span><span class="sxs-lookup"><span data-stu-id="ee7dd-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ee7dd-109">属性</span><span class="sxs-lookup"><span data-stu-id="ee7dd-109">Attributes</span></span>

<span data-ttu-id="ee7dd-110">无。</span><span class="sxs-lookup"><span data-stu-id="ee7dd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ee7dd-111">子元素</span><span class="sxs-lookup"><span data-stu-id="ee7dd-111">Child Elements</span></span>

|<span data-ttu-id="ee7dd-112">元素</span><span class="sxs-lookup"><span data-stu-id="ee7dd-112">Element</span></span>|<span data-ttu-id="ee7dd-113">说明</span><span class="sxs-lookup"><span data-stu-id="ee7dd-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="ee7dd-114">可选元素。</span><span class="sxs-lookup"><span data-stu-id="ee7dd-114">Optional element.</span></span><br /><br /> <span data-ttu-id="ee7dd-115">定义此控件使用的控件。</span><span class="sxs-lookup"><span data-stu-id="ee7dd-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="ee7dd-116">为视图 （格式） 的 CustomControl ExpressionBinding 的 CustomControlName 元素</span><span class="sxs-lookup"><span data-stu-id="ee7dd-116">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="ee7dd-117">可选元素。</span><span class="sxs-lookup"><span data-stu-id="ee7dd-117">Optional element.</span></span><br /><br /> <span data-ttu-id="ee7dd-118">指定公共控件或视图控件的名称。</span><span class="sxs-lookup"><span data-stu-id="ee7dd-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="ee7dd-119">为视图 （格式） 的 CustomControl ExpressionBinding 的 EnumerateCollection 元素</span><span class="sxs-lookup"><span data-stu-id="ee7dd-119">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="ee7dd-120">可选元素。</span><span class="sxs-lookup"><span data-stu-id="ee7dd-120">Optional element.</span></span><br /><br /> <span data-ttu-id="ee7dd-121">指定显示的元素的集合。</span><span class="sxs-lookup"><span data-stu-id="ee7dd-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="ee7dd-122">为视图 （格式） 的 CustomControl ExpressionBinding 的 ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="ee7dd-122">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="ee7dd-123">可选元素。</span><span class="sxs-lookup"><span data-stu-id="ee7dd-123">Optional element.</span></span><br /><br /> <span data-ttu-id="ee7dd-124">定义要在使用此控件中必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="ee7dd-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="ee7dd-125">为视图 （格式） 的 CustomControl ExpressionBinding 的 PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="ee7dd-125">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="ee7dd-126">可选元素。</span><span class="sxs-lookup"><span data-stu-id="ee7dd-126">Optional element.</span></span><br /><br /> <span data-ttu-id="ee7dd-127">指定控件显示其值的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="ee7dd-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="ee7dd-128">为视图 （格式） 的 CustomCustomControl ExpressionBinding 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="ee7dd-128">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="ee7dd-129">可选元素。</span><span class="sxs-lookup"><span data-stu-id="ee7dd-129">Optional element.</span></span><br /><br /> <span data-ttu-id="ee7dd-130">指定控件显示其值的脚本。</span><span class="sxs-lookup"><span data-stu-id="ee7dd-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ee7dd-131">父元素</span><span class="sxs-lookup"><span data-stu-id="ee7dd-131">Parent Elements</span></span>

|<span data-ttu-id="ee7dd-132">元素</span><span class="sxs-lookup"><span data-stu-id="ee7dd-132">Element</span></span>|<span data-ttu-id="ee7dd-133">说明</span><span class="sxs-lookup"><span data-stu-id="ee7dd-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ee7dd-134">为视图 （格式） 的 CustomControl CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="ee7dd-134">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="ee7dd-135">定义由自定义控件视图中显示的数据和显示方式。</span><span class="sxs-lookup"><span data-stu-id="ee7dd-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ee7dd-136">备注</span><span class="sxs-lookup"><span data-stu-id="ee7dd-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="ee7dd-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ee7dd-137">See Also</span></span>

[<span data-ttu-id="ee7dd-138">为视图 （格式） 的 CustomControl ExpressionBinding 的 CustomControlName 元素</span><span class="sxs-lookup"><span data-stu-id="ee7dd-138">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ee7dd-139">为视图 （格式） 的 CustomControl ExpressionBinding 的 EnumerateCollection 元素</span><span class="sxs-lookup"><span data-stu-id="ee7dd-139">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ee7dd-140">为视图 （格式） 的 CustomControl ExpressionBinding 的 ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="ee7dd-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="ee7dd-141">为视图 （格式） 的 CustomControl ExpressionBinding 的 PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="ee7dd-141">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ee7dd-142">为视图 （格式） 的 CustomControl ExpressionBinding 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="ee7dd-142">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ee7dd-143">为视图 （格式） 的 CustomControl CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="ee7dd-143">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ee7dd-144">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="ee7dd-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
