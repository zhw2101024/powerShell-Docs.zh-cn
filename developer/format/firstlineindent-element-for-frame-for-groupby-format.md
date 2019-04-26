---
title: GroupBy （格式） 的帧的 FirstLineIndent 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33be3b9e-53c8-433f-8c11-c65b0d46744c
caps.latest.revision: 6
ms.openlocfilehash: 9ba6fc1b9924a4b0d5b56ee15290a2293217403c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065843"
---
# <a name="firstlineindent-element-for-frame-for-groupby-format"></a><span data-ttu-id="cca64-102">FirstLineIndent Element for Frame for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cca64-102">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>

<span data-ttu-id="cca64-103">指定向右移动数据的第一行的字符数。</span><span class="sxs-lookup"><span data-stu-id="cca64-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="cca64-104">定义如何显示一组新对象时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="cca64-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="cca64-105">GroupBy （格式） 的 GroupBy （格式） CustomEntry 元素 CustomControl CustomEntries 元素的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素CustomControl CustomEntry GroupBy （格式） 的帧的 GroupBy （格式） FirstLineIndent 元素 CustomItem GroupBy （格式） 框架元素的 GroupBy （格式） CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="cca64-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format) FirstLineIndent Element for Frame for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cca64-106">语法</span><span class="sxs-lookup"><span data-stu-id="cca64-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cca64-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="cca64-107">Attributes and Elements</span></span>

<span data-ttu-id="cca64-108">以下各节描述了特性、 子元素和父元素的`FirstLineIndent`元素。</span><span class="sxs-lookup"><span data-stu-id="cca64-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cca64-109">属性</span><span class="sxs-lookup"><span data-stu-id="cca64-109">Attributes</span></span>

<span data-ttu-id="cca64-110">无。</span><span class="sxs-lookup"><span data-stu-id="cca64-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cca64-111">子元素</span><span class="sxs-lookup"><span data-stu-id="cca64-111">Child Elements</span></span>

<span data-ttu-id="cca64-112">无。</span><span class="sxs-lookup"><span data-stu-id="cca64-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cca64-113">父元素</span><span class="sxs-lookup"><span data-stu-id="cca64-113">Parent Elements</span></span>

|<span data-ttu-id="cca64-114">元素</span><span class="sxs-lookup"><span data-stu-id="cca64-114">Element</span></span>|<span data-ttu-id="cca64-115">说明</span><span class="sxs-lookup"><span data-stu-id="cca64-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cca64-116">GroupBy （格式） 的 CustomItem 的框架元素</span><span class="sxs-lookup"><span data-stu-id="cca64-116">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="cca64-117">定义如何显示数据，如向左或向右移位数据。</span><span class="sxs-lookup"><span data-stu-id="cca64-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cca64-118">文本值</span><span class="sxs-lookup"><span data-stu-id="cca64-118">Text Value</span></span>

<span data-ttu-id="cca64-119">指定你想要迁移数据的第一行的字符数。</span><span class="sxs-lookup"><span data-stu-id="cca64-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="cca64-120">备注</span><span class="sxs-lookup"><span data-stu-id="cca64-120">Remarks</span></span>

<span data-ttu-id="cca64-121">如果指定此元素，则不能指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="cca64-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="cca64-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cca64-122">See Also</span></span>

[<span data-ttu-id="cca64-123">GroupBy （格式） 的帧的 FirstLineHanging 元素</span><span class="sxs-lookup"><span data-stu-id="cca64-123">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="cca64-124">GroupBy （格式） 的 CustomItem 的框架元素</span><span class="sxs-lookup"><span data-stu-id="cca64-124">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="cca64-125">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="cca64-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
