---
title: 用于配置控件的 CustomItem 的框架元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363656"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="df4b5-102">Frame Element for CustomItem for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="df4b5-102">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="df4b5-103">定义数据的显示方式，例如，将数据向左或向右移动。</span><span class="sxs-lookup"><span data-stu-id="df4b5-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="df4b5-104">此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。</span><span class="sxs-lookup"><span data-stu-id="df4b5-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="df4b5-105">Configuration 元素（格式）控制配置（format） CustomControl 元素的控件的配置（Format）控件元素的元素，以控制 CustomControl for configuration （Format） CustomEntries 元素的配置（Format） CustomEntry 元素 for CustomControl for CustomItem 元素 for CustomEntry for 元素 for for 元素 for for CustomItem for control 的控件</span><span class="sxs-lookup"><span data-stu-id="df4b5-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="df4b5-106">语法</span><span class="sxs-lookup"><span data-stu-id="df4b5-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="df4b5-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="df4b5-107">Attributes and Elements</span></span>

<span data-ttu-id="df4b5-108">以下各节介绍了 `Frame` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="df4b5-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="df4b5-109">属性</span><span class="sxs-lookup"><span data-stu-id="df4b5-109">Attributes</span></span>

<span data-ttu-id="df4b5-110">无。</span><span class="sxs-lookup"><span data-stu-id="df4b5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="df4b5-111">子元素</span><span class="sxs-lookup"><span data-stu-id="df4b5-111">Child Elements</span></span>

|<span data-ttu-id="df4b5-112">元素</span><span class="sxs-lookup"><span data-stu-id="df4b5-112">Element</span></span>|<span data-ttu-id="df4b5-113">描述</span><span class="sxs-lookup"><span data-stu-id="df4b5-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="df4b5-114">必需的元素</span><span class="sxs-lookup"><span data-stu-id="df4b5-114">Required Element</span></span>|
|[<span data-ttu-id="df4b5-115">用于配置的控件的框架的 FirstLineHanging 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="df4b5-115">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="df4b5-116">可选元素。</span><span class="sxs-lookup"><span data-stu-id="df4b5-116">Optional element.</span></span><br /><br /> <span data-ttu-id="df4b5-117">指定将第一行数据向左移动的字符数。</span><span class="sxs-lookup"><span data-stu-id="df4b5-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="df4b5-118">用于配置的控件的框架的 FirstLineIndent 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="df4b5-118">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="df4b5-119">可选元素。</span><span class="sxs-lookup"><span data-stu-id="df4b5-119">Optional element.</span></span><br /><br /> <span data-ttu-id="df4b5-120">指定第一行数据向右移动的字符数。</span><span class="sxs-lookup"><span data-stu-id="df4b5-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="df4b5-121">用于配置的控件的框架的 LeftIndent 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="df4b5-121">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="df4b5-122">可选元素。</span><span class="sxs-lookup"><span data-stu-id="df4b5-122">Optional element.</span></span><br /><br /> <span data-ttu-id="df4b5-123">指定数据从左边距向外移动的字符数。</span><span class="sxs-lookup"><span data-stu-id="df4b5-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="df4b5-124">用于配置的控件的框架的 RightIndent 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="df4b5-124">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="df4b5-125">可选元素。</span><span class="sxs-lookup"><span data-stu-id="df4b5-125">Optional element.</span></span><br /><br /> <span data-ttu-id="df4b5-126">指定数据从右边缘向外移动的字符数。</span><span class="sxs-lookup"><span data-stu-id="df4b5-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="df4b5-127">父元素</span><span class="sxs-lookup"><span data-stu-id="df4b5-127">Parent Elements</span></span>

|<span data-ttu-id="df4b5-128">元素</span><span class="sxs-lookup"><span data-stu-id="df4b5-128">Element</span></span>|<span data-ttu-id="df4b5-129">描述</span><span class="sxs-lookup"><span data-stu-id="df4b5-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="df4b5-130">用于配置控件的 CustomEntry 的 CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="df4b5-130">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="df4b5-131">定义控件显示的数据及其显示方式。</span><span class="sxs-lookup"><span data-stu-id="df4b5-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="df4b5-132">备注</span><span class="sxs-lookup"><span data-stu-id="df4b5-132">Remarks</span></span>

<span data-ttu-id="df4b5-133">不能在同一 `Frame` 元素中指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)和[FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="df4b5-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="df4b5-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="df4b5-134">See Also</span></span>

[<span data-ttu-id="df4b5-135">用于配置的控件的框架的 FirstLineHanging 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="df4b5-135">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="df4b5-136">用于配置的控件的框架的 FirstLineIndent 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="df4b5-136">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="df4b5-137">用于配置的控件的框架的 LeftIndent 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="df4b5-137">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="df4b5-138">用于配置的控件的框架的 RightIndent 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="df4b5-138">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="df4b5-139">用于配置控件的 CustomEntry 的 CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="df4b5-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="df4b5-140">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="df4b5-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
