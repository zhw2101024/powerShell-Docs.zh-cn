---
title: 对的帧元素 CustomItem 控件的配置 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862973"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="b950f-102">Frame Element for CustomItem for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="b950f-102">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="b950f-103">定义如何显示数据，如向左或向右移位数据。</span><span class="sxs-lookup"><span data-stu-id="b950f-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="b950f-104">定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。</span><span class="sxs-lookup"><span data-stu-id="b950f-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="b950f-105">配置 （格式） 的配置 （格式） 的配置 （CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素CustomControl CustomEntry CustomItem 的 Controls 的配置 （格式） 的配置框架元素的控件的配置 （格式） CustomItem 元素的控件的格式） CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="b950f-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b950f-106">语法</span><span class="sxs-lookup"><span data-stu-id="b950f-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b950f-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="b950f-107">Attributes and Elements</span></span>

<span data-ttu-id="b950f-108">以下各节描述了特性、 子元素和父元素的`Frame`元素。</span><span class="sxs-lookup"><span data-stu-id="b950f-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b950f-109">特性</span><span class="sxs-lookup"><span data-stu-id="b950f-109">Attributes</span></span>

<span data-ttu-id="b950f-110">无。</span><span class="sxs-lookup"><span data-stu-id="b950f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b950f-111">子元素</span><span class="sxs-lookup"><span data-stu-id="b950f-111">Child Elements</span></span>

|<span data-ttu-id="b950f-112">元素</span><span class="sxs-lookup"><span data-stu-id="b950f-112">Element</span></span>|<span data-ttu-id="b950f-113">描述</span><span class="sxs-lookup"><span data-stu-id="b950f-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="b950f-114">所需的元素</span><span class="sxs-lookup"><span data-stu-id="b950f-114">Required Element</span></span>|
|[<span data-ttu-id="b950f-115">配置 （格式） 的控件的帧的 FirstLineHanging 元素</span><span class="sxs-lookup"><span data-stu-id="b950f-115">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="b950f-116">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b950f-116">Optional element.</span></span><br /><br /> <span data-ttu-id="b950f-117">指定向左移动数据的第一行的字符数。</span><span class="sxs-lookup"><span data-stu-id="b950f-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="b950f-118">配置 （格式） 的控件的帧的 FirstLineIndent 元素</span><span class="sxs-lookup"><span data-stu-id="b950f-118">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="b950f-119">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b950f-119">Optional element.</span></span><br /><br /> <span data-ttu-id="b950f-120">指定向右移动数据的第一行的字符数。</span><span class="sxs-lookup"><span data-stu-id="b950f-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="b950f-121">配置 （格式） 的控件的帧的 LeftIndent 元素</span><span class="sxs-lookup"><span data-stu-id="b950f-121">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="b950f-122">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b950f-122">Optional element.</span></span><br /><br /> <span data-ttu-id="b950f-123">指定左边距远离数据向右移的字符数。</span><span class="sxs-lookup"><span data-stu-id="b950f-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="b950f-124">配置 （格式） 的控件的帧的 RightIndent 元素</span><span class="sxs-lookup"><span data-stu-id="b950f-124">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="b950f-125">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b950f-125">Optional element.</span></span><br /><br /> <span data-ttu-id="b950f-126">指定数据向右移离开右边距的字符数。</span><span class="sxs-lookup"><span data-stu-id="b950f-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b950f-127">父元素</span><span class="sxs-lookup"><span data-stu-id="b950f-127">Parent Elements</span></span>

|<span data-ttu-id="b950f-128">元素</span><span class="sxs-lookup"><span data-stu-id="b950f-128">Element</span></span>|<span data-ttu-id="b950f-129">描述</span><span class="sxs-lookup"><span data-stu-id="b950f-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b950f-130">有关配置控件 CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="b950f-130">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="b950f-131">定义由控件显示的数据和显示方式。</span><span class="sxs-lookup"><span data-stu-id="b950f-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b950f-132">备注</span><span class="sxs-lookup"><span data-stu-id="b950f-132">Remarks</span></span>

<span data-ttu-id="b950f-133">不能指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)并[FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)中相同的元素`Frame`元素。</span><span class="sxs-lookup"><span data-stu-id="b950f-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="b950f-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b950f-134">See Also</span></span>

[<span data-ttu-id="b950f-135">配置 （格式） 的控件的帧的 FirstLineHanging 元素</span><span class="sxs-lookup"><span data-stu-id="b950f-135">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="b950f-136">配置 （格式） 的控件的帧的 FirstLineIndent 元素</span><span class="sxs-lookup"><span data-stu-id="b950f-136">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="b950f-137">配置 （格式） 的控件的帧的 LeftIndent 元素</span><span class="sxs-lookup"><span data-stu-id="b950f-137">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="b950f-138">配置 （格式） 的控件的帧的 RightIndent 元素</span><span class="sxs-lookup"><span data-stu-id="b950f-138">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="b950f-139">有关配置控件 CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="b950f-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="b950f-140">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="b950f-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
