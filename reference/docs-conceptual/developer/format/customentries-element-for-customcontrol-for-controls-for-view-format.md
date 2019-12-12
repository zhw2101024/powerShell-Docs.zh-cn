---
title: 用于视图（格式）的 CustomControl 的 CustomEntries 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368806"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a><span data-ttu-id="21301-102">CustomEntries Element for CustomControl for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="21301-102">CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

<span data-ttu-id="21301-103">提供控件的定义。</span><span class="sxs-lookup"><span data-stu-id="21301-103">Provides the definitions for the control.</span></span> <span data-ttu-id="21301-104">定义可由视图使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="21301-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="21301-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 元素（format） Control 元素 for View （format） CustomControl 元素的控件元素，用于控件的 View （format） CustomEntries 元素视图控件的 CustomControl （格式）</span><span class="sxs-lookup"><span data-stu-id="21301-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="21301-106">语法</span><span class="sxs-lookup"><span data-stu-id="21301-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="21301-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="21301-107">Attributes and Elements</span></span>

<span data-ttu-id="21301-108">以下各节介绍 `CustomEntries` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="21301-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="21301-109">对于可指定的子元素数没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="21301-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="21301-110">属性</span><span class="sxs-lookup"><span data-stu-id="21301-110">Attributes</span></span>

<span data-ttu-id="21301-111">无。</span><span class="sxs-lookup"><span data-stu-id="21301-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="21301-112">子元素</span><span class="sxs-lookup"><span data-stu-id="21301-112">Child Elements</span></span>

|<span data-ttu-id="21301-113">元素</span><span class="sxs-lookup"><span data-stu-id="21301-113">Element</span></span>|<span data-ttu-id="21301-114">描述</span><span class="sxs-lookup"><span data-stu-id="21301-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="21301-115">用于视图的控件的 CustomEntries 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="21301-115">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="21301-116">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="21301-116">Required element.</span></span><br /><br /> <span data-ttu-id="21301-117">提供控件的定义。</span><span class="sxs-lookup"><span data-stu-id="21301-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="21301-118">父元素</span><span class="sxs-lookup"><span data-stu-id="21301-118">Parent Elements</span></span>

|<span data-ttu-id="21301-119">元素</span><span class="sxs-lookup"><span data-stu-id="21301-119">Element</span></span>|<span data-ttu-id="21301-120">描述</span><span class="sxs-lookup"><span data-stu-id="21301-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="21301-121">用于控件的控件的 CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="21301-121">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="21301-122">定义视图使用的控件。</span><span class="sxs-lookup"><span data-stu-id="21301-122">Defines the control used by the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="21301-123">备注</span><span class="sxs-lookup"><span data-stu-id="21301-123">Remarks</span></span>

<span data-ttu-id="21301-124">在大多数情况下，控件只有一个定义，该定义是在单个 `CustomEntry` 元素中指定的。</span><span class="sxs-lookup"><span data-stu-id="21301-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="21301-125">但是，如果您希望使用同一控件显示不同的 .NET 对象，则可以提供多个定义。</span><span class="sxs-lookup"><span data-stu-id="21301-125">However, it is possible to provide multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="21301-126">在这些情况下，可以为每个对象或一组对象定义 `CustomEntry` 元素。</span><span class="sxs-lookup"><span data-stu-id="21301-126">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="21301-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="21301-127">See Also</span></span>

[<span data-ttu-id="21301-128">用于视图的控件的 CustomEntries 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="21301-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="21301-129">用于控件的控件的 CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="21301-129">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="21301-130">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="21301-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
