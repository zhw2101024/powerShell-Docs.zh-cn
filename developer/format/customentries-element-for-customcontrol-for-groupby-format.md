---
title: GroupBy （格式） 的 CustomControl CustomEntries 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853673"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="4b1d7-102">CustomEntries Element for CustomControl for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4b1d7-102">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="4b1d7-103">提供控件的定义。</span><span class="sxs-lookup"><span data-stu-id="4b1d7-103">Provides the definitions for the control.</span></span> <span data-ttu-id="4b1d7-104">定义如何显示一组新对象时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="4b1d7-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="4b1d7-105">GroupBy （格式） 的 GroupBy （格式） 的 CustomControl CustomEntries 元素的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="4b1d7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4b1d7-106">语法</span><span class="sxs-lookup"><span data-stu-id="4b1d7-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4b1d7-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="4b1d7-107">Attributes and Elements</span></span>

<span data-ttu-id="4b1d7-108">以下各节描述了特性、 子元素和父元素的`CustomEntries`元素。</span><span class="sxs-lookup"><span data-stu-id="4b1d7-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="4b1d7-109">可以指定的子元素的数目没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="4b1d7-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="4b1d7-110">特性</span><span class="sxs-lookup"><span data-stu-id="4b1d7-110">Attributes</span></span>

<span data-ttu-id="4b1d7-111">无。</span><span class="sxs-lookup"><span data-stu-id="4b1d7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4b1d7-112">子元素</span><span class="sxs-lookup"><span data-stu-id="4b1d7-112">Child Elements</span></span>

|<span data-ttu-id="4b1d7-113">元素</span><span class="sxs-lookup"><span data-stu-id="4b1d7-113">Element</span></span>|<span data-ttu-id="4b1d7-114">描述</span><span class="sxs-lookup"><span data-stu-id="4b1d7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4b1d7-115">GroupBy （格式） 的 CustomControl CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="4b1d7-115">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="4b1d7-116">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="4b1d7-116">Required element.</span></span><br /><br /> <span data-ttu-id="4b1d7-117">提供控件的定义。</span><span class="sxs-lookup"><span data-stu-id="4b1d7-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4b1d7-118">父元素</span><span class="sxs-lookup"><span data-stu-id="4b1d7-118">Parent Elements</span></span>

|<span data-ttu-id="4b1d7-119">元素</span><span class="sxs-lookup"><span data-stu-id="4b1d7-119">Element</span></span>|<span data-ttu-id="4b1d7-120">描述</span><span class="sxs-lookup"><span data-stu-id="4b1d7-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4b1d7-121">GroupBy （格式） 的 CustomControl 元素</span><span class="sxs-lookup"><span data-stu-id="4b1d7-121">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="4b1d7-122">定义显示新组的自定义控件。</span><span class="sxs-lookup"><span data-stu-id="4b1d7-122">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4b1d7-123">备注</span><span class="sxs-lookup"><span data-stu-id="4b1d7-123">Remarks</span></span>

<span data-ttu-id="4b1d7-124">在大多数情况下，控件具有只有一个定义，指定在单个`CustomEntry`元素。</span><span class="sxs-lookup"><span data-stu-id="4b1d7-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="4b1d7-125">但是，就可以提供多个定义，如果你想要使用相同的控件来显示不同的组。</span><span class="sxs-lookup"><span data-stu-id="4b1d7-125">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="4b1d7-126">在这些情况下，你可以定义`CustomEntry`元素组。</span><span class="sxs-lookup"><span data-stu-id="4b1d7-126">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b1d7-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4b1d7-127">See Also</span></span>

[<span data-ttu-id="4b1d7-128">视图 （格式） 的控件的 CustomEntries CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="4b1d7-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="4b1d7-129">GroupBy （格式） 的 CustomControl 元素</span><span class="sxs-lookup"><span data-stu-id="4b1d7-129">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="4b1d7-130">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="4b1d7-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
