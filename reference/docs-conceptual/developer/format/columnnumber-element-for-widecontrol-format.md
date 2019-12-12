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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364216"
---
# <a name="columnnumber-element-for-widecontrol-format"></a><span data-ttu-id="f5007-102">ColumnNumber Element for WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="f5007-102">ColumnNumber Element for WideControl (Format)</span></span>

<span data-ttu-id="f5007-103">指定宽视图中显示的列数。</span><span class="sxs-lookup"><span data-stu-id="f5007-103">Specifies the number of columns displayed in the wide view.</span></span>

<span data-ttu-id="f5007-104">WideControl 的 Configuration 元素（格式） ViewDefinitions 元素（格式） WideControl 元素（format） ColumnNumber 元素（format）</span><span class="sxs-lookup"><span data-stu-id="f5007-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) ColumnNumber Element for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f5007-105">语法</span><span class="sxs-lookup"><span data-stu-id="f5007-105">Syntax</span></span>

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f5007-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="f5007-106">Attributes and Elements</span></span>

<span data-ttu-id="f5007-107">以下各节介绍了 `ColumnNumber` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f5007-107">The following sections describe attributes, child elements, and the parent element of the `ColumnNumber` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f5007-108">属性</span><span class="sxs-lookup"><span data-stu-id="f5007-108">Attributes</span></span>

<span data-ttu-id="f5007-109">无。</span><span class="sxs-lookup"><span data-stu-id="f5007-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f5007-110">子元素</span><span class="sxs-lookup"><span data-stu-id="f5007-110">Child Elements</span></span>

<span data-ttu-id="f5007-111">无。</span><span class="sxs-lookup"><span data-stu-id="f5007-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f5007-112">父元素</span><span class="sxs-lookup"><span data-stu-id="f5007-112">Parent Elements</span></span>

|<span data-ttu-id="f5007-113">元素</span><span class="sxs-lookup"><span data-stu-id="f5007-113">Element</span></span>|<span data-ttu-id="f5007-114">描述</span><span class="sxs-lookup"><span data-stu-id="f5007-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f5007-115">WideControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f5007-115">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="f5007-116">定义视图的宽（单值）列表格式。</span><span class="sxs-lookup"><span data-stu-id="f5007-116">Defines a wide (single value) list format for the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f5007-117">文本值</span><span class="sxs-lookup"><span data-stu-id="f5007-117">Text Value</span></span>

<span data-ttu-id="f5007-118">指定一个正整数值。</span><span class="sxs-lookup"><span data-stu-id="f5007-118">Specify a positive integer value.</span></span>

## <a name="remarks"></a><span data-ttu-id="f5007-119">备注</span><span class="sxs-lookup"><span data-stu-id="f5007-119">Remarks</span></span>

<span data-ttu-id="f5007-120">定义宽视图时，可以添加 `AutoSize` 元素或 `ColumnNumber` 元素，但不能同时添加这两个元素。</span><span class="sxs-lookup"><span data-stu-id="f5007-120">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` element, but you cannot add both.</span></span>

<span data-ttu-id="f5007-121">有关宽视图组件的详细信息，请参阅[创建宽视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="f5007-121">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="f5007-122">有关宽视图的示例，请参阅[宽视图（基本）](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="f5007-122">For an example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f5007-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f5007-123">See Also</span></span>

[<span data-ttu-id="f5007-124">WideControl 的 Autosize 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="f5007-124">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="f5007-125">创建宽视图</span><span class="sxs-lookup"><span data-stu-id="f5007-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="f5007-126">宽视图（基本）</span><span class="sxs-lookup"><span data-stu-id="f5007-126">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="f5007-127">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="f5007-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
