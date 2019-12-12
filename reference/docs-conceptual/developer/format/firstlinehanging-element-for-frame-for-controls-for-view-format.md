---
title: 视图（格式）的控件的框架的 FirstLineHanging 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53694f08-57f7-4185-b443-1636a0918afc
caps.latest.revision: 8
ms.openlocfilehash: 387340cd9b0aae2ad0419b187d96ab4fee183d5a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363786"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-view-format"></a><span data-ttu-id="09738-102">FirstLineHanging Element for Frame for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="09738-102">FirstLineHanging Element for Frame for Controls for View (Format)</span></span>

<span data-ttu-id="09738-103">指定将第一行数据向左移动的字符数。</span><span class="sxs-lookup"><span data-stu-id="09738-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="09738-104">定义可由视图使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="09738-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="09738-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 元素（format） Control 元素 for View （format） CustomControl 元素的控件元素，用于控件的 View （format） CustomEntries 元素CustomControl for View （Format） CustomEntry 元素 for CustomEntries for view （format） CustomItem 元素 for CustomEntry for view （format）元素 for CustomItem for view （format） FirstLineHanging 元素的控件视图控件的框架（格式）</span><span class="sxs-lookup"><span data-stu-id="09738-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format) FirstLineHanging Element of Frame of Controls of View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="09738-106">语法</span><span class="sxs-lookup"><span data-stu-id="09738-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="09738-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="09738-107">Attributes and Elements</span></span>

<span data-ttu-id="09738-108">以下各节介绍 `FirstLineHanging` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="09738-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="09738-109">属性</span><span class="sxs-lookup"><span data-stu-id="09738-109">Attributes</span></span>

<span data-ttu-id="09738-110">无。</span><span class="sxs-lookup"><span data-stu-id="09738-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="09738-111">子元素</span><span class="sxs-lookup"><span data-stu-id="09738-111">Child Elements</span></span>

<span data-ttu-id="09738-112">无。</span><span class="sxs-lookup"><span data-stu-id="09738-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="09738-113">父元素</span><span class="sxs-lookup"><span data-stu-id="09738-113">Parent Elements</span></span>

|<span data-ttu-id="09738-114">元素</span><span class="sxs-lookup"><span data-stu-id="09738-114">Element</span></span>|<span data-ttu-id="09738-115">描述</span><span class="sxs-lookup"><span data-stu-id="09738-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="09738-116">用于视图的控件的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="09738-116">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="09738-117">定义数据的显示方式，例如，将数据向左或向右移动。</span><span class="sxs-lookup"><span data-stu-id="09738-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="09738-118">文本值</span><span class="sxs-lookup"><span data-stu-id="09738-118">Text Value</span></span>

<span data-ttu-id="09738-119">指定要将数据的第一行移动到的字符数。</span><span class="sxs-lookup"><span data-stu-id="09738-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="09738-120">备注</span><span class="sxs-lookup"><span data-stu-id="09738-120">Remarks</span></span>

<span data-ttu-id="09738-121">如果指定此元素，则不能指定[FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="09738-121">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="09738-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="09738-122">See Also</span></span>

[<span data-ttu-id="09738-123">View 的控件的框架的 FirstLineIndent 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="09738-123">FirstLineIndent Element for Frame for Controls for View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="09738-124">用于视图的控件的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="09738-124">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="09738-125">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="09738-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
