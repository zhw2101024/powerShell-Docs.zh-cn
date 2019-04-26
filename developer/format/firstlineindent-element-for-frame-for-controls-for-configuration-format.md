---
title: 配置 （格式） 的控件的帧的 FirstLineIndent 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2f489720-11f6-4019-940e-07f423d4278d
caps.latest.revision: 6
ms.openlocfilehash: c5b2d971fe1590116f96b024ae8769334768acf2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065982"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-configuration-format"></a><span data-ttu-id="80f60-102">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="80f60-102">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>

<span data-ttu-id="80f60-103">指定向右移动数据的第一行的字符数。</span><span class="sxs-lookup"><span data-stu-id="80f60-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="80f60-104">定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。</span><span class="sxs-lookup"><span data-stu-id="80f60-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="80f60-105">配置 （格式） 的配置 （格式） 的配置 （CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素CustomControl CustomEntry CustomItem 的 Controls 的帧的配置 （格式） FirstLineIndent 元素的配置框架元素的控件的配置 （格式） CustomItem 元素的控件的格式） CustomEntry 元素配置 （格式） 的控件</span><span class="sxs-lookup"><span data-stu-id="80f60-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format) FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="80f60-106">语法</span><span class="sxs-lookup"><span data-stu-id="80f60-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="80f60-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="80f60-107">Attributes and Elements</span></span>

<span data-ttu-id="80f60-108">以下各节描述了特性、 子元素和父元素的`FirstLineIndent`元素。</span><span class="sxs-lookup"><span data-stu-id="80f60-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="80f60-109">属性</span><span class="sxs-lookup"><span data-stu-id="80f60-109">Attributes</span></span>

<span data-ttu-id="80f60-110">无。</span><span class="sxs-lookup"><span data-stu-id="80f60-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="80f60-111">子元素</span><span class="sxs-lookup"><span data-stu-id="80f60-111">Child Elements</span></span>

<span data-ttu-id="80f60-112">无。</span><span class="sxs-lookup"><span data-stu-id="80f60-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="80f60-113">父元素</span><span class="sxs-lookup"><span data-stu-id="80f60-113">Parent Elements</span></span>

|<span data-ttu-id="80f60-114">元素</span><span class="sxs-lookup"><span data-stu-id="80f60-114">Element</span></span>|<span data-ttu-id="80f60-115">说明</span><span class="sxs-lookup"><span data-stu-id="80f60-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="80f60-116">CustomItem 配置 （格式） 的控件的框架元素</span><span class="sxs-lookup"><span data-stu-id="80f60-116">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="80f60-117">定义如何显示数据，如向左或向右移位数据。</span><span class="sxs-lookup"><span data-stu-id="80f60-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="80f60-118">文本值</span><span class="sxs-lookup"><span data-stu-id="80f60-118">Text Value</span></span>

<span data-ttu-id="80f60-119">指定你想要迁移数据的第一行的字符数。</span><span class="sxs-lookup"><span data-stu-id="80f60-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="80f60-120">备注</span><span class="sxs-lookup"><span data-stu-id="80f60-120">Remarks</span></span>

<span data-ttu-id="80f60-121">如果指定此元素，则不能指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="80f60-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="80f60-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="80f60-122">See Also</span></span>

[<span data-ttu-id="80f60-123">配置 （格式） 的控件的帧的 FirstLineHanging 元素</span><span class="sxs-lookup"><span data-stu-id="80f60-123">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="80f60-124">CustomItem 配置 （格式） 的控件的框架元素</span><span class="sxs-lookup"><span data-stu-id="80f60-124">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="80f60-125">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="80f60-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
