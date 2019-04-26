---
title: 视图 （格式） 的控件的 CustomEntry CustomItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066373"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="3fed3-102">CustomItem Element for CustomEntry for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="3fed3-102">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="3fed3-103">定义由控件显示的数据和显示方式。</span><span class="sxs-lookup"><span data-stu-id="3fed3-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="3fed3-104">定义一个视图，可以使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="3fed3-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="3fed3-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 控件元素 （格式） 控制元素的控件的视图 （格式） CustomEntries 元素的控件的控件的视图 （格式） CustomControl 元素CustomControl CustomEntries CustomEntry 视图 （格式） 的控件的视图 （格式） CustomItem 元素的控件的视图 （格式） CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="3fed3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3fed3-106">语法</span><span class="sxs-lookup"><span data-stu-id="3fed3-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3fed3-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="3fed3-107">Attributes and Elements</span></span>

<span data-ttu-id="3fed3-108">以下各节描述了特性、 子元素和父元素的`CustomItem`元素。</span><span class="sxs-lookup"><span data-stu-id="3fed3-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="3fed3-109">有关详细信息，请参阅备注。</span><span class="sxs-lookup"><span data-stu-id="3fed3-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="3fed3-110">属性</span><span class="sxs-lookup"><span data-stu-id="3fed3-110">Attributes</span></span>

<span data-ttu-id="3fed3-111">无。</span><span class="sxs-lookup"><span data-stu-id="3fed3-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3fed3-112">子元素</span><span class="sxs-lookup"><span data-stu-id="3fed3-112">Child Elements</span></span>

|<span data-ttu-id="3fed3-113">元素</span><span class="sxs-lookup"><span data-stu-id="3fed3-113">Element</span></span>|<span data-ttu-id="3fed3-114">说明</span><span class="sxs-lookup"><span data-stu-id="3fed3-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3fed3-115">ExpressionBinding CustomItem 视图 （格式） 的控件元素</span><span class="sxs-lookup"><span data-stu-id="3fed3-115">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="3fed3-116">可选元素。</span><span class="sxs-lookup"><span data-stu-id="3fed3-116">Optional element.</span></span><br /><br /> <span data-ttu-id="3fed3-117">定义由控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="3fed3-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="3fed3-118">CustomItem 视图 （格式） 的控件的框架元素</span><span class="sxs-lookup"><span data-stu-id="3fed3-118">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="3fed3-119">可选元素。</span><span class="sxs-lookup"><span data-stu-id="3fed3-119">Optional element.</span></span><br /><br /> <span data-ttu-id="3fed3-120">定义如何显示数据，如向左或向右移位数据。</span><span class="sxs-lookup"><span data-stu-id="3fed3-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="3fed3-121">CustomItem 视图 （格式） 的控件的新行元素</span><span class="sxs-lookup"><span data-stu-id="3fed3-121">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="3fed3-122">可选元素。</span><span class="sxs-lookup"><span data-stu-id="3fed3-122">Optional element.</span></span><br /><br /> <span data-ttu-id="3fed3-123">将空白的行添加到控件的显示。</span><span class="sxs-lookup"><span data-stu-id="3fed3-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="3fed3-124">CustomItem 视图 （格式） 的控件的文本元素</span><span class="sxs-lookup"><span data-stu-id="3fed3-124">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="3fed3-125">可选元素。</span><span class="sxs-lookup"><span data-stu-id="3fed3-125">Optional element.</span></span><br /><br /> <span data-ttu-id="3fed3-126">向控件显示的文本，例如圆括号或大括号。</span><span class="sxs-lookup"><span data-stu-id="3fed3-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3fed3-127">父元素</span><span class="sxs-lookup"><span data-stu-id="3fed3-127">Parent Elements</span></span>

|<span data-ttu-id="3fed3-128">元素</span><span class="sxs-lookup"><span data-stu-id="3fed3-128">Element</span></span>|<span data-ttu-id="3fed3-129">说明</span><span class="sxs-lookup"><span data-stu-id="3fed3-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3fed3-130">视图 （格式） 的控件的 CustomEntries CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="3fed3-130">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="3fed3-131">提供控件的定义。</span><span class="sxs-lookup"><span data-stu-id="3fed3-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3fed3-132">备注</span><span class="sxs-lookup"><span data-stu-id="3fed3-132">Remarks</span></span>

<span data-ttu-id="3fed3-133">指定的子元素时`CustomItem`元素，请记住以下：</span><span class="sxs-lookup"><span data-stu-id="3fed3-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="3fed3-134">必须按以下顺序添加的子元素： `ExpressionBinding`， `NewLine`， `Text`，和`Frame`。</span><span class="sxs-lookup"><span data-stu-id="3fed3-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="3fed3-135">可以指定的序列数没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="3fed3-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="3fed3-136">在每个序列中，没有最大限制数`ExpressionBinding`可以使用的元素。</span><span class="sxs-lookup"><span data-stu-id="3fed3-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="3fed3-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3fed3-137">See Also</span></span>

[<span data-ttu-id="3fed3-138">ExpressionBinding CustomItem 视图 （格式） 的控件元素</span><span class="sxs-lookup"><span data-stu-id="3fed3-138">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="3fed3-139">CustomItem 视图 （格式） 的控件的框架元素</span><span class="sxs-lookup"><span data-stu-id="3fed3-139">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="3fed3-140">CustomItem 视图 （格式） 的控件的新行元素</span><span class="sxs-lookup"><span data-stu-id="3fed3-140">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="3fed3-141">CustomItem 视图 （格式） 的控件的文本元素</span><span class="sxs-lookup"><span data-stu-id="3fed3-141">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="3fed3-142">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="3fed3-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
