---
title: GroupBy （Format）框架的 FirstLineIndent 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33be3b9e-53c8-433f-8c11-c65b0d46744c
caps.latest.revision: 6
ms.openlocfilehash: 9ba6fc1b9924a4b0d5b56ee15290a2293217403c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363076"
---
# <a name="firstlineindent-element-for-frame-for-groupby-format"></a><span data-ttu-id="9419b-102">FirstLineIndent Element for Frame for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9419b-102">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>

<span data-ttu-id="9419b-103">指定第一行数据向右移动的字符数。</span><span class="sxs-lookup"><span data-stu-id="9419b-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="9419b-104">此元素在定义如何显示新的对象组时使用。</span><span class="sxs-lookup"><span data-stu-id="9419b-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="9419b-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format）对于 GroupBy （format） CustomEntries 元素，用于元素的 CustomControl 元素（format）用于 CustomEntry for groupby （format） CustomItem 元素的 CustomControl for groupby （format）元素，用于 groupby 的帧的的元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9419b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format) FirstLineIndent Element for Frame for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9419b-106">语法</span><span class="sxs-lookup"><span data-stu-id="9419b-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9419b-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="9419b-107">Attributes and Elements</span></span>

<span data-ttu-id="9419b-108">以下各节介绍 `FirstLineIndent` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9419b-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9419b-109">属性</span><span class="sxs-lookup"><span data-stu-id="9419b-109">Attributes</span></span>

<span data-ttu-id="9419b-110">无。</span><span class="sxs-lookup"><span data-stu-id="9419b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9419b-111">子元素</span><span class="sxs-lookup"><span data-stu-id="9419b-111">Child Elements</span></span>

<span data-ttu-id="9419b-112">无。</span><span class="sxs-lookup"><span data-stu-id="9419b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9419b-113">父元素</span><span class="sxs-lookup"><span data-stu-id="9419b-113">Parent Elements</span></span>

|<span data-ttu-id="9419b-114">元素</span><span class="sxs-lookup"><span data-stu-id="9419b-114">Element</span></span>|<span data-ttu-id="9419b-115">描述</span><span class="sxs-lookup"><span data-stu-id="9419b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9419b-116">GroupBy 的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9419b-116">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="9419b-117">定义数据的显示方式，例如，将数据向左或向右移动。</span><span class="sxs-lookup"><span data-stu-id="9419b-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9419b-118">文本值</span><span class="sxs-lookup"><span data-stu-id="9419b-118">Text Value</span></span>

<span data-ttu-id="9419b-119">指定要将数据的第一行移动到的字符数。</span><span class="sxs-lookup"><span data-stu-id="9419b-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="9419b-120">备注</span><span class="sxs-lookup"><span data-stu-id="9419b-120">Remarks</span></span>

<span data-ttu-id="9419b-121">如果指定此元素，则不能指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="9419b-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="9419b-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9419b-122">See Also</span></span>

[<span data-ttu-id="9419b-123">GroupBy 的帧的 FirstLineHanging 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9419b-123">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="9419b-124">GroupBy 的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9419b-124">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="9419b-125">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="9419b-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
