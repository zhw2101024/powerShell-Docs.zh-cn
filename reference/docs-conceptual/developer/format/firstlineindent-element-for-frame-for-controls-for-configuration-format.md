---
title: 用于配置的控件的框架的 FirstLineIndent 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2f489720-11f6-4019-940e-07f423d4278d
caps.latest.revision: 6
ms.openlocfilehash: c5b2d971fe1590116f96b024ae8769334768acf2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363116"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-configuration-format"></a><span data-ttu-id="bc5bc-102">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="bc5bc-102">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>

<span data-ttu-id="bc5bc-103">指定第一行数据向右移动的字符数。</span><span class="sxs-lookup"><span data-stu-id="bc5bc-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="bc5bc-104">此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。</span><span class="sxs-lookup"><span data-stu-id="bc5bc-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="bc5bc-105">Configuration 元素（格式）控制配置（format） CustomControl 元素的控件的配置（Format）控件元素的元素，以控制 CustomControl for configuration （Format） CustomEntries 元素的配置（Format）用于 CustomControl 的 CustomEntry 元素，用于配置（Format） CustomItem 元素 for CustomEntry 的的配置框架元素的控件用于配置的控件（格式）</span><span class="sxs-lookup"><span data-stu-id="bc5bc-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format) FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bc5bc-106">语法</span><span class="sxs-lookup"><span data-stu-id="bc5bc-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bc5bc-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="bc5bc-107">Attributes and Elements</span></span>

<span data-ttu-id="bc5bc-108">以下各节介绍 `FirstLineIndent` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="bc5bc-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bc5bc-109">属性</span><span class="sxs-lookup"><span data-stu-id="bc5bc-109">Attributes</span></span>

<span data-ttu-id="bc5bc-110">无。</span><span class="sxs-lookup"><span data-stu-id="bc5bc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bc5bc-111">子元素</span><span class="sxs-lookup"><span data-stu-id="bc5bc-111">Child Elements</span></span>

<span data-ttu-id="bc5bc-112">无。</span><span class="sxs-lookup"><span data-stu-id="bc5bc-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bc5bc-113">父元素</span><span class="sxs-lookup"><span data-stu-id="bc5bc-113">Parent Elements</span></span>

|<span data-ttu-id="bc5bc-114">元素</span><span class="sxs-lookup"><span data-stu-id="bc5bc-114">Element</span></span>|<span data-ttu-id="bc5bc-115">描述</span><span class="sxs-lookup"><span data-stu-id="bc5bc-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bc5bc-116">用于配置的控件的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="bc5bc-116">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="bc5bc-117">定义数据的显示方式，例如，将数据向左或向右移动。</span><span class="sxs-lookup"><span data-stu-id="bc5bc-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bc5bc-118">文本值</span><span class="sxs-lookup"><span data-stu-id="bc5bc-118">Text Value</span></span>

<span data-ttu-id="bc5bc-119">指定要将数据的第一行移动到的字符数。</span><span class="sxs-lookup"><span data-stu-id="bc5bc-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="bc5bc-120">备注</span><span class="sxs-lookup"><span data-stu-id="bc5bc-120">Remarks</span></span>

<span data-ttu-id="bc5bc-121">如果指定此元素，则不能指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="bc5bc-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="bc5bc-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bc5bc-122">See Also</span></span>

[<span data-ttu-id="bc5bc-123">用于配置的控件的框架的 FirstLineHanging 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="bc5bc-123">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="bc5bc-124">用于配置的控件的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="bc5bc-124">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="bc5bc-125">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="bc5bc-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
