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
ms.openlocfilehash: ea43e025f5f653ff000e1d7591b535e73da5c9e5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065965"
---
# <a name="firstlinehanging-element-for-frame-for-customcontrol-for-view-format"></a><span data-ttu-id="0be41-102">FirstLineHanging Element for Frame for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="0be41-102">FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>

<span data-ttu-id="0be41-103">指定向左移动数据的第一行的字符数。</span><span class="sxs-lookup"><span data-stu-id="0be41-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="0be41-104">定义自定义控件视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="0be41-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="0be41-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素 （格式） CustomEntries 元素 CustomControl 视图 （格式） 的视图 （格式） CustomItem 元素 CustomEntries CustomEntry 元素CustomEntry CustomControlView （格式） 的视图 （格式） 的 CustomControl 的帧的视图 （格式） FirstLineHanging 元素 CustomControl CustomItem 框架元素</span><span class="sxs-lookup"><span data-stu-id="0be41-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format) FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0be41-106">语法</span><span class="sxs-lookup"><span data-stu-id="0be41-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0be41-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="0be41-107">Attributes and Elements</span></span>

<span data-ttu-id="0be41-108">以下各节描述了特性、 子元素和父元素的`FirstLineHanging`元素。</span><span class="sxs-lookup"><span data-stu-id="0be41-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0be41-109">属性</span><span class="sxs-lookup"><span data-stu-id="0be41-109">Attributes</span></span>

<span data-ttu-id="0be41-110">无。</span><span class="sxs-lookup"><span data-stu-id="0be41-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0be41-111">子元素</span><span class="sxs-lookup"><span data-stu-id="0be41-111">Child Elements</span></span>

<span data-ttu-id="0be41-112">无。</span><span class="sxs-lookup"><span data-stu-id="0be41-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0be41-113">父元素</span><span class="sxs-lookup"><span data-stu-id="0be41-113">Parent Elements</span></span>

|<span data-ttu-id="0be41-114">元素</span><span class="sxs-lookup"><span data-stu-id="0be41-114">Element</span></span>|<span data-ttu-id="0be41-115">说明</span><span class="sxs-lookup"><span data-stu-id="0be41-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0be41-116">为视图 （格式） 的 CustomControl CustomItem 的框架元素</span><span class="sxs-lookup"><span data-stu-id="0be41-116">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="0be41-117">定义如何显示数据，如向左或向右移位数据。</span><span class="sxs-lookup"><span data-stu-id="0be41-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0be41-118">文本值</span><span class="sxs-lookup"><span data-stu-id="0be41-118">Text Value</span></span>

<span data-ttu-id="0be41-119">指定你想要迁移数据的第一行的字符数。</span><span class="sxs-lookup"><span data-stu-id="0be41-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="0be41-120">备注</span><span class="sxs-lookup"><span data-stu-id="0be41-120">Remarks</span></span>

<span data-ttu-id="0be41-121">如果指定此元素，则不能指定[FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="0be41-121">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="0be41-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0be41-122">See Also</span></span>

[<span data-ttu-id="0be41-123">范围图 （格式） 的 CustomControl FirstLineIndent 元素</span><span class="sxs-lookup"><span data-stu-id="0be41-123">FirstLineIndent Element for Frame for CustomControl for View (Format)</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0be41-124">为视图 （格式） 的 CustomControl CustomItem 的框架元素</span><span class="sxs-lookup"><span data-stu-id="0be41-124">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0be41-125">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="0be41-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
