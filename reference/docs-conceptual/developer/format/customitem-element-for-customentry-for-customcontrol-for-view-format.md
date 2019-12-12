---
title: 用于 CustomControl for View （Format）的 CustomEntry 的 CustomItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363946"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="6feac-102">CustomItem Element for CustomEntry for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="6feac-102">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="6feac-103">定义自定义控件视图显示的数据及其显示方式。</span><span class="sxs-lookup"><span data-stu-id="6feac-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="6feac-104">定义自定义控件视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="6feac-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="6feac-105">用于 CustomEntry 的 CustomControl for view （format） CustomEntries 元素的 ViewDefinitions 元素（format） View 元素（format） CustomControl 元素（format） CustomEntries 元素CustomEntry for View （Format）</span><span class="sxs-lookup"><span data-stu-id="6feac-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6feac-106">语法</span><span class="sxs-lookup"><span data-stu-id="6feac-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6feac-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="6feac-107">Attributes and Elements</span></span>

<span data-ttu-id="6feac-108">以下各节介绍了 `CustomItem` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6feac-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6feac-109">属性</span><span class="sxs-lookup"><span data-stu-id="6feac-109">Attributes</span></span>

<span data-ttu-id="6feac-110">无。</span><span class="sxs-lookup"><span data-stu-id="6feac-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6feac-111">子元素</span><span class="sxs-lookup"><span data-stu-id="6feac-111">Child Elements</span></span>

|<span data-ttu-id="6feac-112">元素</span><span class="sxs-lookup"><span data-stu-id="6feac-112">Element</span></span>|<span data-ttu-id="6feac-113">描述</span><span class="sxs-lookup"><span data-stu-id="6feac-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6feac-114">用于 View 的 CustomControl 的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6feac-114">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="6feac-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="6feac-115">Optional element.</span></span><br /><br /> <span data-ttu-id="6feac-116">定义控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="6feac-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="6feac-117">View 的 CustomItem for CustomControl 的 Frame 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="6feac-117">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="6feac-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="6feac-118">Optional element.</span></span><br /><br /> <span data-ttu-id="6feac-119">定义自定义控件视图显示的数据及其显示方式。</span><span class="sxs-lookup"><span data-stu-id="6feac-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="6feac-120">用于视图的自定义控件的 CustomItem 的换行符元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6feac-120">NewLine Element for CustomItem for Custom Control for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="6feac-121">可选元素。</span><span class="sxs-lookup"><span data-stu-id="6feac-121">Optional element.</span></span><br /><br /> <span data-ttu-id="6feac-122">向控件的显示添加一个空白行。</span><span class="sxs-lookup"><span data-stu-id="6feac-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="6feac-123">View 的 CustomItem for CustomControl 的 Text 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="6feac-123">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)|<span data-ttu-id="6feac-124">可选元素。</span><span class="sxs-lookup"><span data-stu-id="6feac-124">Optional element.</span></span><br /><br /> <span data-ttu-id="6feac-125">指定由控件显示的数据的附加文本。</span><span class="sxs-lookup"><span data-stu-id="6feac-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6feac-126">父元素</span><span class="sxs-lookup"><span data-stu-id="6feac-126">Parent Elements</span></span>

|<span data-ttu-id="6feac-127">元素</span><span class="sxs-lookup"><span data-stu-id="6feac-127">Element</span></span>|<span data-ttu-id="6feac-128">描述</span><span class="sxs-lookup"><span data-stu-id="6feac-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6feac-129">用于 View 的 CustomControl 的 CustomEntries 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6feac-129">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="6feac-130">提供自定义控件视图的定义。</span><span class="sxs-lookup"><span data-stu-id="6feac-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6feac-131">备注</span><span class="sxs-lookup"><span data-stu-id="6feac-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="6feac-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6feac-132">See Also</span></span>

[<span data-ttu-id="6feac-133">用于视图的 CustomEntries 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6feac-133">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="6feac-134">用于 View 的 CustomControl 的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6feac-134">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="6feac-135">View 的 CustomItem for CustomControl 的 Frame 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="6feac-135">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="6feac-136">用于 View 的 CustomItem for CustomControl 的换行符元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6feac-136">NewLine Element for CustomItem for CustomControl for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="6feac-137">View 的 CustomItem for CustomControl 的 Text 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="6feac-137">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)

[<span data-ttu-id="6feac-138">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="6feac-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
