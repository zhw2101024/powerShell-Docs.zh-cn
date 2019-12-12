---
title: GroupBy （Format）的 CustomControl 的 CustomEntries 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364086"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="e0041-102">CustomEntries Element for CustomControl for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e0041-102">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="e0041-103">提供控件的定义。</span><span class="sxs-lookup"><span data-stu-id="e0041-103">Provides the definitions for the control.</span></span> <span data-ttu-id="e0041-104">此元素在定义如何显示新的对象组时使用。</span><span class="sxs-lookup"><span data-stu-id="e0041-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="e0041-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format）对于 groupby （format） CustomEntries 元素，用于元素的 CustomControl 元素（format）</span><span class="sxs-lookup"><span data-stu-id="e0041-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e0041-106">语法</span><span class="sxs-lookup"><span data-stu-id="e0041-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e0041-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="e0041-107">Attributes and Elements</span></span>

<span data-ttu-id="e0041-108">以下各节介绍 `CustomEntries` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e0041-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="e0041-109">对于可指定的子元素数没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="e0041-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="e0041-110">属性</span><span class="sxs-lookup"><span data-stu-id="e0041-110">Attributes</span></span>

<span data-ttu-id="e0041-111">无。</span><span class="sxs-lookup"><span data-stu-id="e0041-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e0041-112">子元素</span><span class="sxs-lookup"><span data-stu-id="e0041-112">Child Elements</span></span>

|<span data-ttu-id="e0041-113">元素</span><span class="sxs-lookup"><span data-stu-id="e0041-113">Element</span></span>|<span data-ttu-id="e0041-114">描述</span><span class="sxs-lookup"><span data-stu-id="e0041-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e0041-115">GroupBy 的 CustomControl 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e0041-115">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="e0041-116">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="e0041-116">Required element.</span></span><br /><br /> <span data-ttu-id="e0041-117">提供控件的定义。</span><span class="sxs-lookup"><span data-stu-id="e0041-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e0041-118">父元素</span><span class="sxs-lookup"><span data-stu-id="e0041-118">Parent Elements</span></span>

|<span data-ttu-id="e0041-119">元素</span><span class="sxs-lookup"><span data-stu-id="e0041-119">Element</span></span>|<span data-ttu-id="e0041-120">描述</span><span class="sxs-lookup"><span data-stu-id="e0041-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e0041-121">GroupBy 的 CustomControl 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="e0041-121">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="e0041-122">定义显示新组的自定义控件。</span><span class="sxs-lookup"><span data-stu-id="e0041-122">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e0041-123">备注</span><span class="sxs-lookup"><span data-stu-id="e0041-123">Remarks</span></span>

<span data-ttu-id="e0041-124">在大多数情况下，控件只有一个定义，该定义是在单个 `CustomEntry` 元素中指定的。</span><span class="sxs-lookup"><span data-stu-id="e0041-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="e0041-125">但是，如果要使用相同的控件来显示不同的组，则可以提供多个定义。</span><span class="sxs-lookup"><span data-stu-id="e0041-125">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="e0041-126">在这些情况下，可以为组定义 `CustomEntry` 元素。</span><span class="sxs-lookup"><span data-stu-id="e0041-126">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0041-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e0041-127">See Also</span></span>

[<span data-ttu-id="e0041-128">用于视图的控件的 CustomEntries 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e0041-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="e0041-129">GroupBy 的 CustomControl 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="e0041-129">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="e0041-130">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="e0041-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
