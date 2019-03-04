---
title: 范围图 （格式） 的 CustomControl FirstLineHanging 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6ac3d86-0529-4b93-9bc7-ee94fcef9618
caps.latest.revision: 8
ms.openlocfilehash: ae4ad8ae3e6cb5d1174dc001b30aa84dd182a606
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860233"
---
# <a name="firstlinehanging-element-for-frame-for-customcontrol-for-view-format"></a><span data-ttu-id="b5976-102">FirstLineHanging Element for Frame for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="b5976-102">FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>

<span data-ttu-id="b5976-103">指定向左移动数据的第一行的字符数。</span><span class="sxs-lookup"><span data-stu-id="b5976-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="b5976-104">定义自定义控件视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="b5976-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="b5976-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素 （格式） CustomEntries 元素 CustomControl 视图 （格式） 的视图 （格式） CustomItem 元素 CustomEntries CustomEntry 元素CustomEntry CutomControlView （格式） 的视图 （格式） 的 CustomControl 的帧的视图 （格式） FirstLineHanging 元素 CustomControl CustomItem 框架元素</span><span class="sxs-lookup"><span data-stu-id="b5976-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CutomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format) FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b5976-106">语法</span><span class="sxs-lookup"><span data-stu-id="b5976-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b5976-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="b5976-107">Attributes and Elements</span></span>

<span data-ttu-id="b5976-108">以下各节描述了特性、 子元素和父元素的`FirstLineHanging`元素。</span><span class="sxs-lookup"><span data-stu-id="b5976-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b5976-109">特性</span><span class="sxs-lookup"><span data-stu-id="b5976-109">Attributes</span></span>

<span data-ttu-id="b5976-110">无。</span><span class="sxs-lookup"><span data-stu-id="b5976-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b5976-111">子元素</span><span class="sxs-lookup"><span data-stu-id="b5976-111">Child Elements</span></span>

<span data-ttu-id="b5976-112">无。</span><span class="sxs-lookup"><span data-stu-id="b5976-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b5976-113">父元素</span><span class="sxs-lookup"><span data-stu-id="b5976-113">Parent Elements</span></span>

|<span data-ttu-id="b5976-114">元素</span><span class="sxs-lookup"><span data-stu-id="b5976-114">Element</span></span>|<span data-ttu-id="b5976-115">描述</span><span class="sxs-lookup"><span data-stu-id="b5976-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5976-116">为视图 （格式） 的 CustomControl CustomItem 的框架元素</span><span class="sxs-lookup"><span data-stu-id="b5976-116">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="b5976-117">定义如何显示数据，如向左或向右移位数据。</span><span class="sxs-lookup"><span data-stu-id="b5976-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b5976-118">文本值</span><span class="sxs-lookup"><span data-stu-id="b5976-118">Text Value</span></span>

<span data-ttu-id="b5976-119">指定你想要迁移数据的第一行的字符数。</span><span class="sxs-lookup"><span data-stu-id="b5976-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="b5976-120">备注</span><span class="sxs-lookup"><span data-stu-id="b5976-120">Remarks</span></span>

<span data-ttu-id="b5976-121">如果指定此元素，则不能指定[FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="b5976-121">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5976-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b5976-122">See Also</span></span>

[<span data-ttu-id="b5976-123">范围图 （格式） 的 CustomControl FirstLineIndent 元素</span><span class="sxs-lookup"><span data-stu-id="b5976-123">FirstLineIndent Element for Frame for CustomControl for View (Format)</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b5976-124">为视图 （格式） 的 CustomControl CustomItem 的框架元素</span><span class="sxs-lookup"><span data-stu-id="b5976-124">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b5976-125">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="b5976-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
