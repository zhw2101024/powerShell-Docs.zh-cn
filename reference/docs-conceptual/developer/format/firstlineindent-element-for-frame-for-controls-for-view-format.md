---
title: 视图（格式）的控件的框架的 FirstLineIndent 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec63f4f9-8858-4529-8646-ffbbc278f83e
caps.latest.revision: 7
ms.openlocfilehash: 694c5baaa5e90a772257276ba139d90acf7ec0e3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363086"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-view-format"></a><span data-ttu-id="4ec38-102">FirstLineIndent Element for Frame for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="4ec38-102">FirstLineIndent Element for Frame for Controls for View (Format)</span></span>

<span data-ttu-id="4ec38-103">指定第一行数据向右移动的字符数。</span><span class="sxs-lookup"><span data-stu-id="4ec38-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="4ec38-104">定义可由视图使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="4ec38-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="4ec38-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 元素（format） Control 元素 for View （format） CustomControl 元素的控件元素，用于控件的 View （format） CustomEntries 元素CustomControl for View （Format） CustomEntry 元素 for CustomEntries for view （format） CustomItem 元素 for CustomEntry for view （format）元素 for view （format）视图控件的（格式）</span><span class="sxs-lookup"><span data-stu-id="4ec38-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format) FirstLineIndent Element of Frame of Controls of View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4ec38-106">语法</span><span class="sxs-lookup"><span data-stu-id="4ec38-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4ec38-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="4ec38-107">Attributes and Elements</span></span>

<span data-ttu-id="4ec38-108">以下各节介绍 `FirstLineIndent` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4ec38-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4ec38-109">属性</span><span class="sxs-lookup"><span data-stu-id="4ec38-109">Attributes</span></span>

<span data-ttu-id="4ec38-110">无。</span><span class="sxs-lookup"><span data-stu-id="4ec38-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4ec38-111">子元素</span><span class="sxs-lookup"><span data-stu-id="4ec38-111">Child Elements</span></span>

<span data-ttu-id="4ec38-112">无。</span><span class="sxs-lookup"><span data-stu-id="4ec38-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4ec38-113">父元素</span><span class="sxs-lookup"><span data-stu-id="4ec38-113">Parent Elements</span></span>

|<span data-ttu-id="4ec38-114">元素</span><span class="sxs-lookup"><span data-stu-id="4ec38-114">Element</span></span>|<span data-ttu-id="4ec38-115">描述</span><span class="sxs-lookup"><span data-stu-id="4ec38-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4ec38-116">用于视图的控件的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4ec38-116">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="4ec38-117">定义数据的显示方式，例如，将数据向左或向右移动。</span><span class="sxs-lookup"><span data-stu-id="4ec38-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4ec38-118">文本值</span><span class="sxs-lookup"><span data-stu-id="4ec38-118">Text Value</span></span>

<span data-ttu-id="4ec38-119">指定要将数据的第一行移动到的字符数。</span><span class="sxs-lookup"><span data-stu-id="4ec38-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="4ec38-120">备注</span><span class="sxs-lookup"><span data-stu-id="4ec38-120">Remarks</span></span>

<span data-ttu-id="4ec38-121">如果指定此元素，则不能指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="4ec38-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ec38-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4ec38-122">See Also</span></span>

[<span data-ttu-id="4ec38-123">View 的控件的框架的 FirstLineHanging 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4ec38-123">FirstLineHanging Element for Frame for Controls for View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="4ec38-124">用于视图的控件的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4ec38-124">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="4ec38-125">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="4ec38-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
