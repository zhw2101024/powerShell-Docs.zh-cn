---
title: GroupBy （Format）框架的 FirstLineHanging 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cdcf66e-96a5-47b5-9269-b4330bde29f2
caps.latest.revision: 6
ms.openlocfilehash: 08db1f2d89c3fe6c1e9a5a522de3071425042c3f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363816"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a><span data-ttu-id="76305-102">FirstLineHanging Element for Frame for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="76305-102">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>

<span data-ttu-id="76305-103">指定将第一行数据向左移动的字符数。</span><span class="sxs-lookup"><span data-stu-id="76305-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="76305-104">此元素在定义如何显示新的对象组时使用。</span><span class="sxs-lookup"><span data-stu-id="76305-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="76305-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format）对于 GroupBy （format） CustomEntries 元素，用于元素的 CustomControl 元素（format）用于 CustomEntry for groupby （format） CustomItem 元素的 CustomControl for groupby （format）元素，用于 groupby 的帧的的元素（格式）</span><span class="sxs-lookup"><span data-stu-id="76305-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format) FirstLineHanging Element for Frame for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="76305-106">语法</span><span class="sxs-lookup"><span data-stu-id="76305-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="76305-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="76305-107">Attributes and Elements</span></span>

<span data-ttu-id="76305-108">以下各节介绍 `FirstLineHanging` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="76305-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="76305-109">属性</span><span class="sxs-lookup"><span data-stu-id="76305-109">Attributes</span></span>

<span data-ttu-id="76305-110">无。</span><span class="sxs-lookup"><span data-stu-id="76305-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="76305-111">子元素</span><span class="sxs-lookup"><span data-stu-id="76305-111">Child Elements</span></span>

<span data-ttu-id="76305-112">无。</span><span class="sxs-lookup"><span data-stu-id="76305-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="76305-113">父元素</span><span class="sxs-lookup"><span data-stu-id="76305-113">Parent Elements</span></span>

|<span data-ttu-id="76305-114">元素</span><span class="sxs-lookup"><span data-stu-id="76305-114">Element</span></span>|<span data-ttu-id="76305-115">描述</span><span class="sxs-lookup"><span data-stu-id="76305-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="76305-116">GroupBy 的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="76305-116">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="76305-117">定义数据的显示方式，例如，将数据向左或向右移动。</span><span class="sxs-lookup"><span data-stu-id="76305-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="76305-118">文本值</span><span class="sxs-lookup"><span data-stu-id="76305-118">Text Value</span></span>

<span data-ttu-id="76305-119">指定要将数据的第一行移动到的字符数。</span><span class="sxs-lookup"><span data-stu-id="76305-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="76305-120">备注</span><span class="sxs-lookup"><span data-stu-id="76305-120">Remarks</span></span>

<span data-ttu-id="76305-121">如果指定此元素，则不能指定[FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="76305-121">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="76305-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="76305-122">See Also</span></span>

[<span data-ttu-id="76305-123">GroupBy 的帧的 FirstLineIndent 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="76305-123">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="76305-124">GroupBy 的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="76305-124">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="76305-125">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="76305-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
