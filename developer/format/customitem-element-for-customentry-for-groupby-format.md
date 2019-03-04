---
title: GroupBy （格式） 的 CustomEntry CustomItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856923"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="b2ff8-102">CustomItem Element for CustomEntry for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b2ff8-102">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="b2ff8-103">定义由自定义控件视图中显示的数据和显示方式。</span><span class="sxs-lookup"><span data-stu-id="b2ff8-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="b2ff8-104">定义如何显示一组新对象时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="b2ff8-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="b2ff8-105">GroupBy （格式） 的 GroupBy （格式） CustomItem 元素 CustomControl CustomEntries 元素的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素GroupBy （格式） 的 CustomEntry</span><span class="sxs-lookup"><span data-stu-id="b2ff8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b2ff8-106">语法</span><span class="sxs-lookup"><span data-stu-id="b2ff8-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b2ff8-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="b2ff8-107">Attributes and Elements</span></span>

<span data-ttu-id="b2ff8-108">以下各节描述了特性、 子元素和父元素的`CustomItem`元素。</span><span class="sxs-lookup"><span data-stu-id="b2ff8-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b2ff8-109">特性</span><span class="sxs-lookup"><span data-stu-id="b2ff8-109">Attributes</span></span>

<span data-ttu-id="b2ff8-110">无。</span><span class="sxs-lookup"><span data-stu-id="b2ff8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b2ff8-111">子元素</span><span class="sxs-lookup"><span data-stu-id="b2ff8-111">Child Elements</span></span>

|<span data-ttu-id="b2ff8-112">元素</span><span class="sxs-lookup"><span data-stu-id="b2ff8-112">Element</span></span>|<span data-ttu-id="b2ff8-113">描述</span><span class="sxs-lookup"><span data-stu-id="b2ff8-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b2ff8-114">GroupBy （格式） 的 CustomItem ExpressionBinding 元素</span><span class="sxs-lookup"><span data-stu-id="b2ff8-114">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="b2ff8-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b2ff8-115">Optional element.</span></span><br /><br /> <span data-ttu-id="b2ff8-116">定义由控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="b2ff8-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="b2ff8-117">GroupBy （格式） 的 CustomItem 的框架元素</span><span class="sxs-lookup"><span data-stu-id="b2ff8-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="b2ff8-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b2ff8-118">Optional element.</span></span><br /><br /> <span data-ttu-id="b2ff8-119">定义由自定义控件视图中显示的数据和显示方式。</span><span class="sxs-lookup"><span data-stu-id="b2ff8-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="b2ff8-120">GroupBy （格式） 的 CustomItem 的换行元素</span><span class="sxs-lookup"><span data-stu-id="b2ff8-120">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="b2ff8-121">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b2ff8-121">Optional element.</span></span><br /><br /> <span data-ttu-id="b2ff8-122">将空白的行添加到控件的显示。</span><span class="sxs-lookup"><span data-stu-id="b2ff8-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="b2ff8-123">GroupBy （格式） 的 CustomItem 的文本元素</span><span class="sxs-lookup"><span data-stu-id="b2ff8-123">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="b2ff8-124">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b2ff8-124">Optional element.</span></span><br /><br /> <span data-ttu-id="b2ff8-125">指定由控件显示的数据的其他文本。</span><span class="sxs-lookup"><span data-stu-id="b2ff8-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b2ff8-126">父元素</span><span class="sxs-lookup"><span data-stu-id="b2ff8-126">Parent Elements</span></span>

|<span data-ttu-id="b2ff8-127">元素</span><span class="sxs-lookup"><span data-stu-id="b2ff8-127">Element</span></span>|<span data-ttu-id="b2ff8-128">描述</span><span class="sxs-lookup"><span data-stu-id="b2ff8-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b2ff8-129">GroupBy （格式） 的 CustomControl CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="b2ff8-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="b2ff8-130">提供自定义控件视图的定义。</span><span class="sxs-lookup"><span data-stu-id="b2ff8-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b2ff8-131">备注</span><span class="sxs-lookup"><span data-stu-id="b2ff8-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="b2ff8-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b2ff8-132">See Also</span></span>

[<span data-ttu-id="b2ff8-133">GroupBy （格式） 的 CustomControl CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="b2ff8-133">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="b2ff8-134">GroupBy （格式） 的 CustomItem ExpressionBinding 元素</span><span class="sxs-lookup"><span data-stu-id="b2ff8-134">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="b2ff8-135">GroupBy （格式） 的 CustomItem 的框架元素</span><span class="sxs-lookup"><span data-stu-id="b2ff8-135">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="b2ff8-136">GroupBy （格式） 的 CustomItem 的换行元素</span><span class="sxs-lookup"><span data-stu-id="b2ff8-136">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="b2ff8-137">GroupBy （格式） 的 CustomItem 的文本元素</span><span class="sxs-lookup"><span data-stu-id="b2ff8-137">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="b2ff8-138">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="b2ff8-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
