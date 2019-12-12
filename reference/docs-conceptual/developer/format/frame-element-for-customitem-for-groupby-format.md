---
title: GroupBy （格式）的 CustomItem 的框架元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362946"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="2a93d-102">Frame Element for CustomItem for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2a93d-102">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="2a93d-103">定义数据的显示方式，例如，将数据向左或向右移动。</span><span class="sxs-lookup"><span data-stu-id="2a93d-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="2a93d-104">此元素在定义如何显示新的对象组时使用。</span><span class="sxs-lookup"><span data-stu-id="2a93d-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="2a93d-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format）对于 GroupBy （format） CustomEntries 元素，用于元素的 CustomControl 元素（format）用于 CustomEntry for groupby 的 for groupby （format） CustomItem 元素的 CustomControl （format）</span><span class="sxs-lookup"><span data-stu-id="2a93d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2a93d-106">语法</span><span class="sxs-lookup"><span data-stu-id="2a93d-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2a93d-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="2a93d-107">Attributes and Elements</span></span>

<span data-ttu-id="2a93d-108">以下各节介绍了 `Frame` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2a93d-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2a93d-109">属性</span><span class="sxs-lookup"><span data-stu-id="2a93d-109">Attributes</span></span>

<span data-ttu-id="2a93d-110">无。</span><span class="sxs-lookup"><span data-stu-id="2a93d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2a93d-111">子元素</span><span class="sxs-lookup"><span data-stu-id="2a93d-111">Child Elements</span></span>

|<span data-ttu-id="2a93d-112">元素</span><span class="sxs-lookup"><span data-stu-id="2a93d-112">Element</span></span>|<span data-ttu-id="2a93d-113">描述</span><span class="sxs-lookup"><span data-stu-id="2a93d-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="2a93d-114">必需的元素</span><span class="sxs-lookup"><span data-stu-id="2a93d-114">Required Element</span></span>|
|[<span data-ttu-id="2a93d-115">GroupBy 的帧的 FirstLineHanging 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2a93d-115">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="2a93d-116">可选元素。</span><span class="sxs-lookup"><span data-stu-id="2a93d-116">Optional element.</span></span><br /><br /> <span data-ttu-id="2a93d-117">指定将第一行数据向左移动的字符数。</span><span class="sxs-lookup"><span data-stu-id="2a93d-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="2a93d-118">GroupBy 的帧的 FirstLineIndent 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2a93d-118">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="2a93d-119">可选元素。</span><span class="sxs-lookup"><span data-stu-id="2a93d-119">Optional element.</span></span><br /><br /> <span data-ttu-id="2a93d-120">指定第一行数据向右移动的字符数。</span><span class="sxs-lookup"><span data-stu-id="2a93d-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="2a93d-121">GroupBy 的帧的 LeftIndent 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2a93d-121">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="2a93d-122">可选元素。</span><span class="sxs-lookup"><span data-stu-id="2a93d-122">Optional element.</span></span><br /><br /> <span data-ttu-id="2a93d-123">指定数据从左边距向外移动的字符数。</span><span class="sxs-lookup"><span data-stu-id="2a93d-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="2a93d-124">[GroupBy 的帧的 RightIndent 元素（格式）](./rightindent-element-for-frame-for-groupby-format.md)RightIndent 元素</span><span class="sxs-lookup"><span data-stu-id="2a93d-124">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="2a93d-125">可选元素。</span><span class="sxs-lookup"><span data-stu-id="2a93d-125">Optional element.</span></span><br /><br /> <span data-ttu-id="2a93d-126">指定数据从右边缘向外移动的字符数。</span><span class="sxs-lookup"><span data-stu-id="2a93d-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2a93d-127">父元素</span><span class="sxs-lookup"><span data-stu-id="2a93d-127">Parent Elements</span></span>

|<span data-ttu-id="2a93d-128">元素</span><span class="sxs-lookup"><span data-stu-id="2a93d-128">Element</span></span>|<span data-ttu-id="2a93d-129">描述</span><span class="sxs-lookup"><span data-stu-id="2a93d-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2a93d-130">GroupBy 的 CustomEntry 的 CustomItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2a93d-130">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="2a93d-131">定义控件显示的数据及其显示方式。</span><span class="sxs-lookup"><span data-stu-id="2a93d-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2a93d-132">备注</span><span class="sxs-lookup"><span data-stu-id="2a93d-132">Remarks</span></span>

<span data-ttu-id="2a93d-133">不能在同一个 `Frame` 元素中指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md)和[FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="2a93d-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a93d-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2a93d-134">See Also</span></span>

[<span data-ttu-id="2a93d-135">GroupBy 的帧的 FirstLineHanging 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2a93d-135">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="2a93d-136">GroupBy 的帧的 FirstLineIndent 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2a93d-136">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="2a93d-137">GroupBy 的帧的 LeftIndent 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2a93d-137">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="2a93d-138">GroupBy 的帧的 RightIndent 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2a93d-138">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="2a93d-139">GroupBy 的 CustomEntry 的 CustomItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2a93d-139">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="2a93d-140">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="2a93d-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
