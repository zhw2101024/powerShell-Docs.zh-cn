---
title: 用于配置的控件（格式）的 CustomEntry 的 CustomItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364026"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="f7090-102">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="f7090-102">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="f7090-103">定义控件显示的数据及其显示方式。</span><span class="sxs-lookup"><span data-stu-id="f7090-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="f7090-104">此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。</span><span class="sxs-lookup"><span data-stu-id="f7090-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="f7090-105">Configuration 元素（格式）控制配置（format） CustomControl 元素的控件的配置（Format）控件元素的元素，以控制 CustomControl for configuration （Format） CustomEntries 元素的配置（Format） CustomEntry 元素 for CustomControl for configuration （Format） CustomItem 元素 for CustomEntry for control for control 的控件</span><span class="sxs-lookup"><span data-stu-id="f7090-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration</span></span>

## <a name="syntax"></a><span data-ttu-id="f7090-106">语法</span><span class="sxs-lookup"><span data-stu-id="f7090-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f7090-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="f7090-107">Attributes and Elements</span></span>

<span data-ttu-id="f7090-108">以下各节介绍了 `CustomItem` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f7090-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="f7090-109">有关详细信息，请参阅备注。</span><span class="sxs-lookup"><span data-stu-id="f7090-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="f7090-110">属性</span><span class="sxs-lookup"><span data-stu-id="f7090-110">Attributes</span></span>

<span data-ttu-id="f7090-111">无。</span><span class="sxs-lookup"><span data-stu-id="f7090-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f7090-112">子元素</span><span class="sxs-lookup"><span data-stu-id="f7090-112">Child Elements</span></span>

|<span data-ttu-id="f7090-113">元素</span><span class="sxs-lookup"><span data-stu-id="f7090-113">Element</span></span>|<span data-ttu-id="f7090-114">描述</span><span class="sxs-lookup"><span data-stu-id="f7090-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f7090-115">用于配置的控件的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f7090-115">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="f7090-116">可选元素。</span><span class="sxs-lookup"><span data-stu-id="f7090-116">Optional element.</span></span><br /><br /> <span data-ttu-id="f7090-117">定义控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="f7090-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="f7090-118">用于配置的控件的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f7090-118">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="f7090-119">可选元素。</span><span class="sxs-lookup"><span data-stu-id="f7090-119">Optional element.</span></span><br /><br /> <span data-ttu-id="f7090-120">定义数据的显示方式，例如，将数据向左或向右移动。</span><span class="sxs-lookup"><span data-stu-id="f7090-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="f7090-121">用于配置的控件的 CustomItem 的换行符元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f7090-121">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="f7090-122">可选元素。</span><span class="sxs-lookup"><span data-stu-id="f7090-122">Optional element.</span></span><br /><br /> <span data-ttu-id="f7090-123">向控件的显示添加一个空白行。</span><span class="sxs-lookup"><span data-stu-id="f7090-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="f7090-124">用于配置的控件的 CustomItem 的文本元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f7090-124">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="f7090-125">可选元素。</span><span class="sxs-lookup"><span data-stu-id="f7090-125">Optional element.</span></span><br /><br /> <span data-ttu-id="f7090-126">向控件的显示添加文本，如括号或方括号。</span><span class="sxs-lookup"><span data-stu-id="f7090-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f7090-127">父元素</span><span class="sxs-lookup"><span data-stu-id="f7090-127">Parent Elements</span></span>

|<span data-ttu-id="f7090-128">元素</span><span class="sxs-lookup"><span data-stu-id="f7090-128">Element</span></span>|<span data-ttu-id="f7090-129">描述</span><span class="sxs-lookup"><span data-stu-id="f7090-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f7090-130">用于配置的控件的 CustomControl 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f7090-130">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="f7090-131">提供控件的定义。</span><span class="sxs-lookup"><span data-stu-id="f7090-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f7090-132">备注</span><span class="sxs-lookup"><span data-stu-id="f7090-132">Remarks</span></span>

<span data-ttu-id="f7090-133">指定 `CustomItem` 元素的子元素时，请记住以下事项：</span><span class="sxs-lookup"><span data-stu-id="f7090-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="f7090-134">必须按以下顺序添加子元素： `ExpressionBinding`、`NewLine`、`Text`和 `Frame`。</span><span class="sxs-lookup"><span data-stu-id="f7090-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="f7090-135">您可以指定的序列数量没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="f7090-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="f7090-136">在每个序列中，可使用的 `ExpressionBinding` 元素数没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="f7090-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7090-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f7090-137">See Also</span></span>

[<span data-ttu-id="f7090-138">用于配置的控件的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f7090-138">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="f7090-139">用于配置的控件的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f7090-139">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="f7090-140">用于配置的控件的 CustomItem 的换行符元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f7090-140">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="f7090-141">用于配置的控件的 CustomItem 的文本元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f7090-141">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="f7090-142">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="f7090-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
