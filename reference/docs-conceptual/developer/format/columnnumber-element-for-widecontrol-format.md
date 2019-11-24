---
title: WideControl 的 ColumnNumber 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe9eb5f9-a193-41a4-ad47-a96ba3f8d7e3
caps.latest.revision: 8
ms.openlocfilehash: 49f501538b8f72777984a5e575b999866abcdebf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364216"
---
# <a name="columnnumber-element-for-widecontrol-format"></a><span data-ttu-id="9d5d1-102">ColumnNumber Element for WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="9d5d1-102">ColumnNumber Element for WideControl (Format)</span></span>

<span data-ttu-id="9d5d1-103">指定宽视图中显示的列数。</span><span class="sxs-lookup"><span data-stu-id="9d5d1-103">Specifies the number of columns displayed in the wide view.</span></span>

<span data-ttu-id="9d5d1-104">WideControl 的 Configuration 元素（格式） ViewDefinitions 元素（格式） WideControl 元素（format） ColumnNumber 元素（format）</span><span class="sxs-lookup"><span data-stu-id="9d5d1-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) ColumnNumber Element for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9d5d1-105">语法</span><span class="sxs-lookup"><span data-stu-id="9d5d1-105">Syntax</span></span>

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9d5d1-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="9d5d1-106">Attributes and Elements</span></span>

<span data-ttu-id="9d5d1-107">以下各节介绍了 `ColumnNumber` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9d5d1-107">The following sections describe attributes, child elements, and the parent element of the `ColumnNumber` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9d5d1-108">特性</span><span class="sxs-lookup"><span data-stu-id="9d5d1-108">Attributes</span></span>

<span data-ttu-id="9d5d1-109">无。</span><span class="sxs-lookup"><span data-stu-id="9d5d1-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9d5d1-110">子元素</span><span class="sxs-lookup"><span data-stu-id="9d5d1-110">Child Elements</span></span>

<span data-ttu-id="9d5d1-111">无。</span><span class="sxs-lookup"><span data-stu-id="9d5d1-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9d5d1-112">父元素</span><span class="sxs-lookup"><span data-stu-id="9d5d1-112">Parent Elements</span></span>

|<span data-ttu-id="9d5d1-113">元素</span><span class="sxs-lookup"><span data-stu-id="9d5d1-113">Element</span></span>|<span data-ttu-id="9d5d1-114">描述</span><span class="sxs-lookup"><span data-stu-id="9d5d1-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9d5d1-115">WideControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9d5d1-115">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="9d5d1-116">定义视图的宽（单值）列表格式。</span><span class="sxs-lookup"><span data-stu-id="9d5d1-116">Defines a wide (single value) list format for the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9d5d1-117">文本值</span><span class="sxs-lookup"><span data-stu-id="9d5d1-117">Text Value</span></span>

<span data-ttu-id="9d5d1-118">指定一个正整数值。</span><span class="sxs-lookup"><span data-stu-id="9d5d1-118">Specify a positive integer value.</span></span>

## <a name="remarks"></a><span data-ttu-id="9d5d1-119">备注</span><span class="sxs-lookup"><span data-stu-id="9d5d1-119">Remarks</span></span>

<span data-ttu-id="9d5d1-120">定义宽视图时，可以添加 `AutoSize` 元素或 `ColumnNumber` 元素，但不能同时添加这两个元素。</span><span class="sxs-lookup"><span data-stu-id="9d5d1-120">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` element, but you cannot add both.</span></span>

<span data-ttu-id="9d5d1-121">有关宽视图组件的详细信息，请参阅[创建宽视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="9d5d1-121">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="9d5d1-122">有关宽视图的示例，请参阅[宽视图（基本）](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="9d5d1-122">For an example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9d5d1-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9d5d1-123">See Also</span></span>

[<span data-ttu-id="9d5d1-124">WideControl 的 Autosize 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="9d5d1-124">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="9d5d1-125">创建宽视图</span><span class="sxs-lookup"><span data-stu-id="9d5d1-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="9d5d1-126">宽视图（基本）</span><span class="sxs-lookup"><span data-stu-id="9d5d1-126">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="9d5d1-127">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="9d5d1-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
