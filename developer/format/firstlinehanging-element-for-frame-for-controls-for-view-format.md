---
title: 视图 （格式） 的控件的帧的 FirstLineHanging 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53694f08-57f7-4185-b443-1636a0918afc
caps.latest.revision: 8
ms.openlocfilehash: 387340cd9b0aae2ad0419b187d96ab4fee183d5a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065795"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-view-format"></a><span data-ttu-id="60ad3-102">FirstLineHanging Element for Frame for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="60ad3-102">FirstLineHanging Element for Frame for Controls for View (Format)</span></span>

<span data-ttu-id="60ad3-103">指定向左移动数据的第一行的字符数。</span><span class="sxs-lookup"><span data-stu-id="60ad3-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="60ad3-104">定义一个视图，可以使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="60ad3-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="60ad3-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 控件元素 （格式） 控制元素的控件的视图 （格式） CustomEntries 元素的控件的控件的视图 （格式） CustomControl 元素CustomControl CustomEntries CustomEntry CustomItem 视图 （格式） FirstLineHanging 元素的控件的视图 （格式） 框架元素的控件的视图 （格式） CustomItem 元素的控件的视图 （格式） CustomEntry 元素控件的视图 （格式） 的框架</span><span class="sxs-lookup"><span data-stu-id="60ad3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format) FirstLineHanging Element of Frame of Controls of View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="60ad3-106">语法</span><span class="sxs-lookup"><span data-stu-id="60ad3-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="60ad3-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="60ad3-107">Attributes and Elements</span></span>

<span data-ttu-id="60ad3-108">以下各节描述了特性、 子元素和父元素的`FirstLineHanging`元素。</span><span class="sxs-lookup"><span data-stu-id="60ad3-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="60ad3-109">属性</span><span class="sxs-lookup"><span data-stu-id="60ad3-109">Attributes</span></span>

<span data-ttu-id="60ad3-110">无。</span><span class="sxs-lookup"><span data-stu-id="60ad3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="60ad3-111">子元素</span><span class="sxs-lookup"><span data-stu-id="60ad3-111">Child Elements</span></span>

<span data-ttu-id="60ad3-112">无。</span><span class="sxs-lookup"><span data-stu-id="60ad3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="60ad3-113">父元素</span><span class="sxs-lookup"><span data-stu-id="60ad3-113">Parent Elements</span></span>

|<span data-ttu-id="60ad3-114">元素</span><span class="sxs-lookup"><span data-stu-id="60ad3-114">Element</span></span>|<span data-ttu-id="60ad3-115">说明</span><span class="sxs-lookup"><span data-stu-id="60ad3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="60ad3-116">CustomItem 视图 （格式） 的控件的框架元素</span><span class="sxs-lookup"><span data-stu-id="60ad3-116">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="60ad3-117">定义如何显示数据，如向左或向右移位数据。</span><span class="sxs-lookup"><span data-stu-id="60ad3-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="60ad3-118">文本值</span><span class="sxs-lookup"><span data-stu-id="60ad3-118">Text Value</span></span>

<span data-ttu-id="60ad3-119">指定你想要迁移数据的第一行的字符数。</span><span class="sxs-lookup"><span data-stu-id="60ad3-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="60ad3-120">备注</span><span class="sxs-lookup"><span data-stu-id="60ad3-120">Remarks</span></span>

<span data-ttu-id="60ad3-121">如果指定此元素，则不能指定[FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="60ad3-121">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="60ad3-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="60ad3-122">See Also</span></span>

[<span data-ttu-id="60ad3-123">视图 （格式） 的控件的帧的 FirstLineIndent 元素</span><span class="sxs-lookup"><span data-stu-id="60ad3-123">FirstLineIndent Element for Frame for Controls for View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="60ad3-124">CustomItem 视图 （格式） 的控件的框架元素</span><span class="sxs-lookup"><span data-stu-id="60ad3-124">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="60ad3-125">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="60ad3-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
