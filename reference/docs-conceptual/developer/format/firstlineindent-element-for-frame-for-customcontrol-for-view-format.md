---
title: 用于视图的 CustomControl 的帧的 FirstLineIndent 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb4e1564-3fd3-4be3-b93e-ac90480e05c0
caps.latest.revision: 6
ms.openlocfilehash: 3130ecc69f7d1568bcbd392dd24e8cdcc3382905
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363056"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a><span data-ttu-id="6f865-102">FirstLineIndent Element for Frame for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="6f865-102">FirstLineIndent Element for Frame for CustomControl for View (Format)</span></span>

<span data-ttu-id="6f865-103">指定第一行数据向右移动的字符数。</span><span class="sxs-lookup"><span data-stu-id="6f865-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="6f865-104">定义自定义控件视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="6f865-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="6f865-105">用于 CustomEntry 的 CustomControl for view （format） CustomEntries 元素的 ViewDefinitions 元素（format） View 元素（format） CustomControl 元素（format） CustomEntries 元素用于 CustomItem for CustomControl for View （Format） FirstLineIndent 元素的 CustomControlView （Format） Frame 元素的 CustomEntry</span><span class="sxs-lookup"><span data-stu-id="6f865-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format) FirstLineIndent Element</span></span>

## <a name="syntax"></a><span data-ttu-id="6f865-106">语法</span><span class="sxs-lookup"><span data-stu-id="6f865-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6f865-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="6f865-107">Attributes and Elements</span></span>

<span data-ttu-id="6f865-108">以下各节介绍 `FirstLineIndent` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6f865-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6f865-109">属性</span><span class="sxs-lookup"><span data-stu-id="6f865-109">Attributes</span></span>

<span data-ttu-id="6f865-110">无。</span><span class="sxs-lookup"><span data-stu-id="6f865-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6f865-111">子元素</span><span class="sxs-lookup"><span data-stu-id="6f865-111">Child Elements</span></span>

<span data-ttu-id="6f865-112">无。</span><span class="sxs-lookup"><span data-stu-id="6f865-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6f865-113">父元素</span><span class="sxs-lookup"><span data-stu-id="6f865-113">Parent Elements</span></span>

|<span data-ttu-id="6f865-114">元素</span><span class="sxs-lookup"><span data-stu-id="6f865-114">Element</span></span>|<span data-ttu-id="6f865-115">描述</span><span class="sxs-lookup"><span data-stu-id="6f865-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6f865-116">View 的 CustomItem for CustomControl 的 Frame 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="6f865-116">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="6f865-117">定义数据的显示方式，例如，将数据向左或向右移动。</span><span class="sxs-lookup"><span data-stu-id="6f865-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6f865-118">文本值</span><span class="sxs-lookup"><span data-stu-id="6f865-118">Text Value</span></span>

<span data-ttu-id="6f865-119">指定要将数据的第一行移动到的字符数。</span><span class="sxs-lookup"><span data-stu-id="6f865-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="6f865-120">备注</span><span class="sxs-lookup"><span data-stu-id="6f865-120">Remarks</span></span>

<span data-ttu-id="6f865-121">如果指定此元素，则不能指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="6f865-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f865-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6f865-122">See Also</span></span>

[<span data-ttu-id="6f865-123">用于视图的 CustomControl 的帧的 FirstLineHanging 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6f865-123">FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="6f865-124">View 的 CustomItem for CustomControl 的 Frame 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="6f865-124">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="6f865-125">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="6f865-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
