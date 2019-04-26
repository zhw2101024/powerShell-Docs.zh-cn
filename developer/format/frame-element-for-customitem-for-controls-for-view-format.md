---
title: 对的帧元素 CustomItem 控件的视图 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065710"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="81366-102">Frame Element for CustomItem for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="81366-102">Frame Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="81366-103">定义如何显示数据，如向左或向右移位数据。</span><span class="sxs-lookup"><span data-stu-id="81366-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="81366-104">定义一个视图，可以使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="81366-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="81366-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 控件元素 （格式） 控制元素的控件的视图 （格式） CustomEntries 元素的控件的控件的视图 （格式） CustomControl 元素CustomControl CustomEntries CustomEntry CustomItem 视图 （格式） 的控件的视图 （格式） 框架元素的控件的视图 （格式） CustomItem 元素的控件的视图 （格式） CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="81366-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="81366-106">语法</span><span class="sxs-lookup"><span data-stu-id="81366-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="81366-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="81366-107">Attributes and Elements</span></span>

<span data-ttu-id="81366-108">以下各节描述了特性、 子元素和父元素的`Frame`元素。</span><span class="sxs-lookup"><span data-stu-id="81366-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="81366-109">属性</span><span class="sxs-lookup"><span data-stu-id="81366-109">Attributes</span></span>

<span data-ttu-id="81366-110">无。</span><span class="sxs-lookup"><span data-stu-id="81366-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="81366-111">子元素</span><span class="sxs-lookup"><span data-stu-id="81366-111">Child Elements</span></span>

|<span data-ttu-id="81366-112">元素</span><span class="sxs-lookup"><span data-stu-id="81366-112">Element</span></span>|<span data-ttu-id="81366-113">说明</span><span class="sxs-lookup"><span data-stu-id="81366-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="81366-114">所需的元素</span><span class="sxs-lookup"><span data-stu-id="81366-114">Required Element</span></span>|
|[<span data-ttu-id="81366-115">控件的视图 （格式） 的帧的 FirstLineHanging 元素</span><span class="sxs-lookup"><span data-stu-id="81366-115">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="81366-116">可选元素。</span><span class="sxs-lookup"><span data-stu-id="81366-116">Optional element.</span></span><br /><br /> <span data-ttu-id="81366-117">指定向左移动第一行的字符数。</span><span class="sxs-lookup"><span data-stu-id="81366-117">Specifies how many characters the first line is shifted to the left.</span></span>|
|[<span data-ttu-id="81366-118">控件的视图 （格式） 的帧的 FirstLineIndent 元素</span><span class="sxs-lookup"><span data-stu-id="81366-118">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="81366-119">可选元素。</span><span class="sxs-lookup"><span data-stu-id="81366-119">Optional element.</span></span><br /><br /> <span data-ttu-id="81366-120">指定向右移动第一行的字符数。</span><span class="sxs-lookup"><span data-stu-id="81366-120">Specifies how many characters the first line is shifted to the right.</span></span>|
|[<span data-ttu-id="81366-121">控件的视图 （格式） 的帧的 LeftIndent 元素</span><span class="sxs-lookup"><span data-stu-id="81366-121">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="81366-122">可选元素。</span><span class="sxs-lookup"><span data-stu-id="81366-122">Optional element.</span></span><br /><br /> <span data-ttu-id="81366-123">指定左边距远离数据向右移的字符数。</span><span class="sxs-lookup"><span data-stu-id="81366-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="81366-124">控件的视图 （格式） 的帧的 RightIndent 元素</span><span class="sxs-lookup"><span data-stu-id="81366-124">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="81366-125">可选元素。</span><span class="sxs-lookup"><span data-stu-id="81366-125">Optional element.</span></span><br /><br /> <span data-ttu-id="81366-126">指定数据向右移离开右边距的字符数。</span><span class="sxs-lookup"><span data-stu-id="81366-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="81366-127">父元素</span><span class="sxs-lookup"><span data-stu-id="81366-127">Parent Elements</span></span>

|<span data-ttu-id="81366-128">元素</span><span class="sxs-lookup"><span data-stu-id="81366-128">Element</span></span>|<span data-ttu-id="81366-129">说明</span><span class="sxs-lookup"><span data-stu-id="81366-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="81366-130">视图 （格式） 的控件的 CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="81366-130">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="81366-131">定义由控件显示的数据和显示方式。</span><span class="sxs-lookup"><span data-stu-id="81366-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="81366-132">备注</span><span class="sxs-lookup"><span data-stu-id="81366-132">Remarks</span></span>

<span data-ttu-id="81366-133">不能指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)并[FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md)中相同的元素`Frame`元素。</span><span class="sxs-lookup"><span data-stu-id="81366-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="81366-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="81366-134">See Also</span></span>

[<span data-ttu-id="81366-135">控件的视图 （格式） 的帧的 FirstLineHanging 元素</span><span class="sxs-lookup"><span data-stu-id="81366-135">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="81366-136">控件的视图 （格式） 的帧的 FirstLineIndent 元素</span><span class="sxs-lookup"><span data-stu-id="81366-136">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="81366-137">控件的视图 （格式） 的帧的 LeftIndent 元素</span><span class="sxs-lookup"><span data-stu-id="81366-137">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="81366-138">控件的视图 （格式） 的帧的 RightIndent 元素</span><span class="sxs-lookup"><span data-stu-id="81366-138">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="81366-139">视图 （格式） 的控件的 CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="81366-139">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="81366-140">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="81366-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
