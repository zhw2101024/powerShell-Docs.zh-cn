---
title: 配置 （格式） 的控件的 CustomItem ExpressionBinding 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855133"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="b11c3-102">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="b11c3-102">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="b11c3-103">定义由控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="b11c3-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="b11c3-104">定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。</span><span class="sxs-lookup"><span data-stu-id="b11c3-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="b11c3-105">配置 （格式） 的配置 （格式） 的配置 （CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素CustomControl CustomEntry 配置 ExpressionBinding CustomItem 配置 （格式） 的控件元素的控件的配置 （格式） CustomItem 元素的控件的格式） CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="b11c3-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b11c3-106">语法</span><span class="sxs-lookup"><span data-stu-id="b11c3-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="b11c3-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="b11c3-107">Attributes and Elements</span></span>

<span data-ttu-id="b11c3-108">以下各节描述了特性、 子元素和父元素的`ExpressionBinding`元素。</span><span class="sxs-lookup"><span data-stu-id="b11c3-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b11c3-109">特性</span><span class="sxs-lookup"><span data-stu-id="b11c3-109">Attributes</span></span>

<span data-ttu-id="b11c3-110">无。</span><span class="sxs-lookup"><span data-stu-id="b11c3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b11c3-111">子元素</span><span class="sxs-lookup"><span data-stu-id="b11c3-111">Child Elements</span></span>

|<span data-ttu-id="b11c3-112">元素</span><span class="sxs-lookup"><span data-stu-id="b11c3-112">Element</span></span>|<span data-ttu-id="b11c3-113">描述</span><span class="sxs-lookup"><span data-stu-id="b11c3-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="b11c3-114">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b11c3-114">Optional element.</span></span><br /><br /> <span data-ttu-id="b11c3-115">定义此控件使用的控件。</span><span class="sxs-lookup"><span data-stu-id="b11c3-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="b11c3-116">配置 （格式） 的控件的 ExpressionBinding 的 CustomControlName 元素</span><span class="sxs-lookup"><span data-stu-id="b11c3-116">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="b11c3-117">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b11c3-117">Optional element.</span></span><br /><br /> <span data-ttu-id="b11c3-118">指定公共控件或视图控件的名称。</span><span class="sxs-lookup"><span data-stu-id="b11c3-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="b11c3-119">配置 （格式） 的控件的 ExpressionBinding 的 EnumerateCollection 元素</span><span class="sxs-lookup"><span data-stu-id="b11c3-119">EnumerateCollection Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="b11c3-120">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b11c3-120">Optional element.</span></span><br /><br /> <span data-ttu-id="b11c3-121">指定控件将显示个集合的元素。</span><span class="sxs-lookup"><span data-stu-id="b11c3-121">Specified that the elements of collections are displayed by the control.</span></span>|
|[<span data-ttu-id="b11c3-122">配置 （格式） 的控件的 ExpressionBinding 的 ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="b11c3-122">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="b11c3-123">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b11c3-123">Optional element.</span></span><br /><br /> <span data-ttu-id="b11c3-124">定义要在使用此公共控件中必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="b11c3-124">Defines the condition that must exist for this common control to be used.</span></span>|
|[<span data-ttu-id="b11c3-125">ExpressionBinding 的配置 （格式） 的控件的属性名称元素</span><span class="sxs-lookup"><span data-stu-id="b11c3-125">PropertyName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="b11c3-126">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b11c3-126">Optional element.</span></span><br /><br /> <span data-ttu-id="b11c3-127">指定其值显示的一个常用的控件的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="b11c3-127">Specifies the .NET property whose value is displayed by the common control.</span></span>|
|[<span data-ttu-id="b11c3-128">ExpressionBinding 的 Controls 的配置 （格式） 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="b11c3-128">ScriptBlock Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="b11c3-129">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b11c3-129">Optional element.</span></span><br /><br /> <span data-ttu-id="b11c3-130">指定其值显示的一个常用的控件的脚本。</span><span class="sxs-lookup"><span data-stu-id="b11c3-130">Specifies the script whose value is displayed by the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b11c3-131">父元素</span><span class="sxs-lookup"><span data-stu-id="b11c3-131">Parent Elements</span></span>

|<span data-ttu-id="b11c3-132">元素</span><span class="sxs-lookup"><span data-stu-id="b11c3-132">Element</span></span>|<span data-ttu-id="b11c3-133">描述</span><span class="sxs-lookup"><span data-stu-id="b11c3-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b11c3-134">有关配置控件 CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="b11c3-134">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="b11c3-135">定义由自定义控件视图中显示的数据和显示方式。</span><span class="sxs-lookup"><span data-stu-id="b11c3-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b11c3-136">备注</span><span class="sxs-lookup"><span data-stu-id="b11c3-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="b11c3-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b11c3-137">See Also</span></span>

[<span data-ttu-id="b11c3-138">有关配置控件 CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="b11c3-138">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="b11c3-139">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="b11c3-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
