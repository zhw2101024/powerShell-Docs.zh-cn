---
title: GroupBy （Format）的 CustomEntry 的 CustomItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363876"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="55a21-102">CustomItem Element for CustomEntry for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="55a21-102">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="55a21-103">定义自定义控件视图显示的数据及其显示方式。</span><span class="sxs-lookup"><span data-stu-id="55a21-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="55a21-104">此元素在定义如何显示新的对象组时使用。</span><span class="sxs-lookup"><span data-stu-id="55a21-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="55a21-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format）对于 GroupBy （format） CustomEntries 元素，用于元素的 CustomControl 元素（format）CustomEntry for GroupBy （Format）</span><span class="sxs-lookup"><span data-stu-id="55a21-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="55a21-106">语法</span><span class="sxs-lookup"><span data-stu-id="55a21-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="55a21-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="55a21-107">Attributes and Elements</span></span>

<span data-ttu-id="55a21-108">以下各节介绍了 `CustomItem` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="55a21-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="55a21-109">属性</span><span class="sxs-lookup"><span data-stu-id="55a21-109">Attributes</span></span>

<span data-ttu-id="55a21-110">无。</span><span class="sxs-lookup"><span data-stu-id="55a21-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="55a21-111">子元素</span><span class="sxs-lookup"><span data-stu-id="55a21-111">Child Elements</span></span>

|<span data-ttu-id="55a21-112">元素</span><span class="sxs-lookup"><span data-stu-id="55a21-112">Element</span></span>|<span data-ttu-id="55a21-113">描述</span><span class="sxs-lookup"><span data-stu-id="55a21-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="55a21-114">GroupBy 的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="55a21-114">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="55a21-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="55a21-115">Optional element.</span></span><br /><br /> <span data-ttu-id="55a21-116">定义控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="55a21-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="55a21-117">GroupBy 的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="55a21-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="55a21-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="55a21-118">Optional element.</span></span><br /><br /> <span data-ttu-id="55a21-119">定义自定义控件视图显示的数据及其显示方式。</span><span class="sxs-lookup"><span data-stu-id="55a21-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="55a21-120">GroupBy 的 CustomItem 的换行符元素（格式）</span><span class="sxs-lookup"><span data-stu-id="55a21-120">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="55a21-121">可选元素。</span><span class="sxs-lookup"><span data-stu-id="55a21-121">Optional element.</span></span><br /><br /> <span data-ttu-id="55a21-122">向控件的显示添加一个空白行。</span><span class="sxs-lookup"><span data-stu-id="55a21-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="55a21-123">GroupBy 的 CustomItem 文本元素（格式）</span><span class="sxs-lookup"><span data-stu-id="55a21-123">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="55a21-124">可选元素。</span><span class="sxs-lookup"><span data-stu-id="55a21-124">Optional element.</span></span><br /><br /> <span data-ttu-id="55a21-125">指定由控件显示的数据的附加文本。</span><span class="sxs-lookup"><span data-stu-id="55a21-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="55a21-126">父元素</span><span class="sxs-lookup"><span data-stu-id="55a21-126">Parent Elements</span></span>

|<span data-ttu-id="55a21-127">元素</span><span class="sxs-lookup"><span data-stu-id="55a21-127">Element</span></span>|<span data-ttu-id="55a21-128">描述</span><span class="sxs-lookup"><span data-stu-id="55a21-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="55a21-129">GroupBy 的 CustomControl 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="55a21-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="55a21-130">提供自定义控件视图的定义。</span><span class="sxs-lookup"><span data-stu-id="55a21-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="55a21-131">备注</span><span class="sxs-lookup"><span data-stu-id="55a21-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="55a21-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="55a21-132">See Also</span></span>

[<span data-ttu-id="55a21-133">GroupBy 的 CustomControl 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="55a21-133">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="55a21-134">GroupBy 的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="55a21-134">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="55a21-135">GroupBy 的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="55a21-135">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="55a21-136">GroupBy 的 CustomItem 的换行符元素（格式）</span><span class="sxs-lookup"><span data-stu-id="55a21-136">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="55a21-137">GroupBy 的 CustomItem 文本元素（格式）</span><span class="sxs-lookup"><span data-stu-id="55a21-137">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="55a21-138">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="55a21-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
