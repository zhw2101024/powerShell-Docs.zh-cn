---
title: 用于视图（格式）的控件的 CustomItem 的框架元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363646"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="d2500-102">Frame Element for CustomItem for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="d2500-102">Frame Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="d2500-103">定义数据的显示方式，例如，将数据向左或向右移动。</span><span class="sxs-lookup"><span data-stu-id="d2500-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="d2500-104">定义可由视图使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="d2500-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="d2500-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 元素（format） Control 元素 for View （format） CustomControl 元素的控件元素，用于控件的 View （format） CustomEntries 元素CustomControl for View （Format） CustomEntry 元素 for CustomEntries for view （format） CustomItem 元素 for for view （format）元素 for view （format）</span><span class="sxs-lookup"><span data-stu-id="d2500-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d2500-106">语法</span><span class="sxs-lookup"><span data-stu-id="d2500-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d2500-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="d2500-107">Attributes and Elements</span></span>

<span data-ttu-id="d2500-108">以下各节介绍了 `Frame` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d2500-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d2500-109">属性</span><span class="sxs-lookup"><span data-stu-id="d2500-109">Attributes</span></span>

<span data-ttu-id="d2500-110">无。</span><span class="sxs-lookup"><span data-stu-id="d2500-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d2500-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d2500-111">Child Elements</span></span>

|<span data-ttu-id="d2500-112">元素</span><span class="sxs-lookup"><span data-stu-id="d2500-112">Element</span></span>|<span data-ttu-id="d2500-113">描述</span><span class="sxs-lookup"><span data-stu-id="d2500-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="d2500-114">必需的元素</span><span class="sxs-lookup"><span data-stu-id="d2500-114">Required Element</span></span>|
|[<span data-ttu-id="d2500-115">视图控件的框架的 FirstLineHanging 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="d2500-115">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="d2500-116">可选元素。</span><span class="sxs-lookup"><span data-stu-id="d2500-116">Optional element.</span></span><br /><br /> <span data-ttu-id="d2500-117">指定第一行向左移动的字符数。</span><span class="sxs-lookup"><span data-stu-id="d2500-117">Specifies how many characters the first line is shifted to the left.</span></span>|
|[<span data-ttu-id="d2500-118">视图控件的框架的 FirstLineIndent 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="d2500-118">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="d2500-119">可选元素。</span><span class="sxs-lookup"><span data-stu-id="d2500-119">Optional element.</span></span><br /><br /> <span data-ttu-id="d2500-120">指定第一行向右移动的字符数。</span><span class="sxs-lookup"><span data-stu-id="d2500-120">Specifies how many characters the first line is shifted to the right.</span></span>|
|[<span data-ttu-id="d2500-121">视图控件的框架的 LeftIndent 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="d2500-121">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="d2500-122">可选元素。</span><span class="sxs-lookup"><span data-stu-id="d2500-122">Optional element.</span></span><br /><br /> <span data-ttu-id="d2500-123">指定数据从左边距向外移动的字符数。</span><span class="sxs-lookup"><span data-stu-id="d2500-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="d2500-124">视图控件的框架的 RightIndent 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="d2500-124">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="d2500-125">可选元素。</span><span class="sxs-lookup"><span data-stu-id="d2500-125">Optional element.</span></span><br /><br /> <span data-ttu-id="d2500-126">指定数据从右边缘向外移动的字符数。</span><span class="sxs-lookup"><span data-stu-id="d2500-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d2500-127">父元素</span><span class="sxs-lookup"><span data-stu-id="d2500-127">Parent Elements</span></span>

|<span data-ttu-id="d2500-128">元素</span><span class="sxs-lookup"><span data-stu-id="d2500-128">Element</span></span>|<span data-ttu-id="d2500-129">描述</span><span class="sxs-lookup"><span data-stu-id="d2500-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d2500-130">用于视图的控件的 CustomEntry 的 CustomItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d2500-130">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="d2500-131">定义控件显示的数据及其显示方式。</span><span class="sxs-lookup"><span data-stu-id="d2500-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d2500-132">备注</span><span class="sxs-lookup"><span data-stu-id="d2500-132">Remarks</span></span>

<span data-ttu-id="d2500-133">不能在同一 `Frame` 元素中指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)和[FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="d2500-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="d2500-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d2500-134">See Also</span></span>

[<span data-ttu-id="d2500-135">视图控件的框架的 FirstLineHanging 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="d2500-135">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="d2500-136">视图控件的框架的 FirstLineIndent 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="d2500-136">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="d2500-137">视图控件的框架的 LeftIndent 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="d2500-137">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="d2500-138">视图控件的框架的 RightIndent 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="d2500-138">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="d2500-139">用于视图的控件的 CustomEntry 的 CustomItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d2500-139">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="d2500-140">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="d2500-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
