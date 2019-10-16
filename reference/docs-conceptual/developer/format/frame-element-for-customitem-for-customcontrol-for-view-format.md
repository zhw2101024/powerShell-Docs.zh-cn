---
title: View 的 CustomItem for CustomControl 的 Frame 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363636"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="e54bf-102">Frame Element for CustomItem for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="e54bf-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="e54bf-103">定义数据的显示方式，例如，将数据向左或向右移动。</span><span class="sxs-lookup"><span data-stu-id="e54bf-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="e54bf-104">定义自定义控件视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="e54bf-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="e54bf-105">用于 CustomEntry 的 CustomControl for view （format） CustomEntries 元素的 ViewDefinitions 元素（format） View 元素（format） CustomControl 元素（format） CustomEntries 元素用于 CustomItem for CustomControl for View 的 CustomControlView （Format） Frame 元素的 CustomEntry</span><span class="sxs-lookup"><span data-stu-id="e54bf-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e54bf-106">语法</span><span class="sxs-lookup"><span data-stu-id="e54bf-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e54bf-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="e54bf-107">Attributes and Elements</span></span>

<span data-ttu-id="e54bf-108">以下各节介绍了 `Frame` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e54bf-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e54bf-109">属性</span><span class="sxs-lookup"><span data-stu-id="e54bf-109">Attributes</span></span>

<span data-ttu-id="e54bf-110">无。</span><span class="sxs-lookup"><span data-stu-id="e54bf-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e54bf-111">子元素</span><span class="sxs-lookup"><span data-stu-id="e54bf-111">Child Elements</span></span>

|<span data-ttu-id="e54bf-112">元素</span><span class="sxs-lookup"><span data-stu-id="e54bf-112">Element</span></span>|<span data-ttu-id="e54bf-113">描述</span><span class="sxs-lookup"><span data-stu-id="e54bf-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="e54bf-114">必需的元素</span><span class="sxs-lookup"><span data-stu-id="e54bf-114">Required Element</span></span>|
|[<span data-ttu-id="e54bf-115">FirstLineHanging 元素</span><span class="sxs-lookup"><span data-stu-id="e54bf-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="e54bf-116">可选元素。</span><span class="sxs-lookup"><span data-stu-id="e54bf-116">Optional element.</span></span><br /><br /> <span data-ttu-id="e54bf-117">指定将第一行数据向左移动的字符数。</span><span class="sxs-lookup"><span data-stu-id="e54bf-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="e54bf-118">FirstLineIndent 元素</span><span class="sxs-lookup"><span data-stu-id="e54bf-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="e54bf-119">可选元素。</span><span class="sxs-lookup"><span data-stu-id="e54bf-119">Optional element.</span></span><br /><br /> <span data-ttu-id="e54bf-120">指定第一行数据向右移动的字符数。</span><span class="sxs-lookup"><span data-stu-id="e54bf-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="e54bf-121">LeftIndent 元素</span><span class="sxs-lookup"><span data-stu-id="e54bf-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="e54bf-122">可选元素。</span><span class="sxs-lookup"><span data-stu-id="e54bf-122">Optional element.</span></span><br /><br /> <span data-ttu-id="e54bf-123">指定数据从左边距向外移动的字符数。</span><span class="sxs-lookup"><span data-stu-id="e54bf-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="e54bf-124">RightIndent 元素</span><span class="sxs-lookup"><span data-stu-id="e54bf-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="e54bf-125">可选元素。</span><span class="sxs-lookup"><span data-stu-id="e54bf-125">Optional element.</span></span><br /><br /> <span data-ttu-id="e54bf-126">指定数据从右边缘向外移动的字符数。</span><span class="sxs-lookup"><span data-stu-id="e54bf-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e54bf-127">父元素</span><span class="sxs-lookup"><span data-stu-id="e54bf-127">Parent Elements</span></span>

|<span data-ttu-id="e54bf-128">元素</span><span class="sxs-lookup"><span data-stu-id="e54bf-128">Element</span></span>|<span data-ttu-id="e54bf-129">描述</span><span class="sxs-lookup"><span data-stu-id="e54bf-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e54bf-130">用于视图的 CustomEntry 的 CustomItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e54bf-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="e54bf-131">定义控件显示的数据及其显示方式。</span><span class="sxs-lookup"><span data-stu-id="e54bf-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e54bf-132">备注</span><span class="sxs-lookup"><span data-stu-id="e54bf-132">Remarks</span></span>

<span data-ttu-id="e54bf-133">不能在同一 `Frame` 元素中指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)和[FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="e54bf-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="e54bf-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e54bf-134">See Also</span></span>

[<span data-ttu-id="e54bf-135">FirstLineHanging 元素</span><span class="sxs-lookup"><span data-stu-id="e54bf-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e54bf-136">FirstLineIndent 元素</span><span class="sxs-lookup"><span data-stu-id="e54bf-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e54bf-137">LeftIndent 元素</span><span class="sxs-lookup"><span data-stu-id="e54bf-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e54bf-138">RightIndent 元素</span><span class="sxs-lookup"><span data-stu-id="e54bf-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e54bf-139">用于视图的 CustomEntry 的 CustomItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e54bf-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e54bf-140">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="e54bf-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
