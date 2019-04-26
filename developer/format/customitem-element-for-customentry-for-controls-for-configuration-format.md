---
title: 配置 （格式） 的控件的 CustomEntry CustomItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066424"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="f7ac8-102">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="f7ac8-102">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="f7ac8-103">定义由控件显示的数据和显示方式。</span><span class="sxs-lookup"><span data-stu-id="f7ac8-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="f7ac8-104">定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。</span><span class="sxs-lookup"><span data-stu-id="f7ac8-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="f7ac8-105">配置 （格式） 的配置 （格式） 的配置 （CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素CustomControl CustomEntry 的 Controls 的配置的配置 （格式） CustomItem 元素的控件的格式） CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="f7ac8-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration</span></span>

## <a name="syntax"></a><span data-ttu-id="f7ac8-106">语法</span><span class="sxs-lookup"><span data-stu-id="f7ac8-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f7ac8-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="f7ac8-107">Attributes and Elements</span></span>

<span data-ttu-id="f7ac8-108">以下各节描述了特性、 子元素和父元素的`CustomItem`元素。</span><span class="sxs-lookup"><span data-stu-id="f7ac8-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="f7ac8-109">有关详细信息，请参阅备注。</span><span class="sxs-lookup"><span data-stu-id="f7ac8-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="f7ac8-110">属性</span><span class="sxs-lookup"><span data-stu-id="f7ac8-110">Attributes</span></span>

<span data-ttu-id="f7ac8-111">无。</span><span class="sxs-lookup"><span data-stu-id="f7ac8-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f7ac8-112">子元素</span><span class="sxs-lookup"><span data-stu-id="f7ac8-112">Child Elements</span></span>

|<span data-ttu-id="f7ac8-113">元素</span><span class="sxs-lookup"><span data-stu-id="f7ac8-113">Element</span></span>|<span data-ttu-id="f7ac8-114">说明</span><span class="sxs-lookup"><span data-stu-id="f7ac8-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f7ac8-115">配置 （格式） 的控件的 CustomItem ExpressionBinding 元素</span><span class="sxs-lookup"><span data-stu-id="f7ac8-115">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="f7ac8-116">可选元素。</span><span class="sxs-lookup"><span data-stu-id="f7ac8-116">Optional element.</span></span><br /><br /> <span data-ttu-id="f7ac8-117">定义由控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="f7ac8-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="f7ac8-118">CustomItem 配置 （格式） 的控件的框架元素</span><span class="sxs-lookup"><span data-stu-id="f7ac8-118">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="f7ac8-119">可选元素。</span><span class="sxs-lookup"><span data-stu-id="f7ac8-119">Optional element.</span></span><br /><br /> <span data-ttu-id="f7ac8-120">定义如何显示数据，如向左或向右移位数据。</span><span class="sxs-lookup"><span data-stu-id="f7ac8-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="f7ac8-121">配置 （格式） 的控件的 CustomItem 的换行元素</span><span class="sxs-lookup"><span data-stu-id="f7ac8-121">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="f7ac8-122">可选元素。</span><span class="sxs-lookup"><span data-stu-id="f7ac8-122">Optional element.</span></span><br /><br /> <span data-ttu-id="f7ac8-123">将空白的行添加到控件的显示。</span><span class="sxs-lookup"><span data-stu-id="f7ac8-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="f7ac8-124">CustomItem 配置 （格式） 的控件的文本元素</span><span class="sxs-lookup"><span data-stu-id="f7ac8-124">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="f7ac8-125">可选元素。</span><span class="sxs-lookup"><span data-stu-id="f7ac8-125">Optional element.</span></span><br /><br /> <span data-ttu-id="f7ac8-126">向控件显示的文本，例如圆括号或大括号。</span><span class="sxs-lookup"><span data-stu-id="f7ac8-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f7ac8-127">父元素</span><span class="sxs-lookup"><span data-stu-id="f7ac8-127">Parent Elements</span></span>

|<span data-ttu-id="f7ac8-128">元素</span><span class="sxs-lookup"><span data-stu-id="f7ac8-128">Element</span></span>|<span data-ttu-id="f7ac8-129">说明</span><span class="sxs-lookup"><span data-stu-id="f7ac8-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f7ac8-130">配置 （格式） 的控件的 CustomControl CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="f7ac8-130">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="f7ac8-131">提供控件的定义。</span><span class="sxs-lookup"><span data-stu-id="f7ac8-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f7ac8-132">备注</span><span class="sxs-lookup"><span data-stu-id="f7ac8-132">Remarks</span></span>

<span data-ttu-id="f7ac8-133">指定的子元素时`CustomItem`元素，请记住以下：</span><span class="sxs-lookup"><span data-stu-id="f7ac8-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="f7ac8-134">必须按以下顺序添加的子元素： `ExpressionBinding`， `NewLine`， `Text`，和`Frame`。</span><span class="sxs-lookup"><span data-stu-id="f7ac8-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="f7ac8-135">可以指定的序列数没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="f7ac8-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="f7ac8-136">在每个序列中，没有最大限制数`ExpressionBinding`可以使用的元素。</span><span class="sxs-lookup"><span data-stu-id="f7ac8-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7ac8-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f7ac8-137">See Also</span></span>

[<span data-ttu-id="f7ac8-138">配置 （格式） 的控件的 CustomItem ExpressionBinding 元素</span><span class="sxs-lookup"><span data-stu-id="f7ac8-138">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="f7ac8-139">CustomItem 配置 （格式） 的控件的框架元素</span><span class="sxs-lookup"><span data-stu-id="f7ac8-139">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="f7ac8-140">配置 （格式） 的控件的 CustomItem 的换行元素</span><span class="sxs-lookup"><span data-stu-id="f7ac8-140">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="f7ac8-141">CustomItem 配置 （格式） 的控件的文本元素</span><span class="sxs-lookup"><span data-stu-id="f7ac8-141">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="f7ac8-142">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="f7ac8-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
