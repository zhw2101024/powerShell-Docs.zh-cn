---
title: ColumnNumber WideControl （格式） 的元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe9eb5f9-a193-41a4-ad47-a96ba3f8d7e3
caps.latest.revision: 8
ms.openlocfilehash: 49f501538b8f72777984a5e575b999866abcdebf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856223"
---
# <a name="columnnumber-element-for-widecontrol-format"></a><span data-ttu-id="20bf2-102">ColumnNumber Element for WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="20bf2-102">ColumnNumber Element for WideControl (Format)</span></span>

<span data-ttu-id="20bf2-103">指定宽视图中显示的列数。</span><span class="sxs-lookup"><span data-stu-id="20bf2-103">Specifies the number of columns displayed in the wide view.</span></span>

<span data-ttu-id="20bf2-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） WideControl 元素 （格式） ColumnNumber 元素 WideControl （格式）</span><span class="sxs-lookup"><span data-stu-id="20bf2-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) ColumnNumber Element for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="20bf2-105">语法</span><span class="sxs-lookup"><span data-stu-id="20bf2-105">Syntax</span></span>

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="20bf2-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="20bf2-106">Attributes and Elements</span></span>

<span data-ttu-id="20bf2-107">以下各节描述了特性、 子元素和父元素的`ColumnNumber`元素。</span><span class="sxs-lookup"><span data-stu-id="20bf2-107">The following sections describe attributes, child elements, and the parent element of the `ColumnNumber` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="20bf2-108">特性</span><span class="sxs-lookup"><span data-stu-id="20bf2-108">Attributes</span></span>

<span data-ttu-id="20bf2-109">无。</span><span class="sxs-lookup"><span data-stu-id="20bf2-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="20bf2-110">子元素</span><span class="sxs-lookup"><span data-stu-id="20bf2-110">Child Elements</span></span>

<span data-ttu-id="20bf2-111">无。</span><span class="sxs-lookup"><span data-stu-id="20bf2-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="20bf2-112">父元素</span><span class="sxs-lookup"><span data-stu-id="20bf2-112">Parent Elements</span></span>

|<span data-ttu-id="20bf2-113">元素</span><span class="sxs-lookup"><span data-stu-id="20bf2-113">Element</span></span>|<span data-ttu-id="20bf2-114">描述</span><span class="sxs-lookup"><span data-stu-id="20bf2-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="20bf2-115">WideControl 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="20bf2-115">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="20bf2-116">定义范围内 （单个值） 的视图的列表格式。</span><span class="sxs-lookup"><span data-stu-id="20bf2-116">Defines a wide (single value) list format for the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="20bf2-117">文本值</span><span class="sxs-lookup"><span data-stu-id="20bf2-117">Text Value</span></span>

<span data-ttu-id="20bf2-118">指定一个正整数值。</span><span class="sxs-lookup"><span data-stu-id="20bf2-118">Specify a positive integer value.</span></span>

## <a name="remarks"></a><span data-ttu-id="20bf2-119">备注</span><span class="sxs-lookup"><span data-stu-id="20bf2-119">Remarks</span></span>

<span data-ttu-id="20bf2-120">在定义较宽的视图，你可以添加`AutoSize`元素或`ColumnNumber`元素，但您不能将同时添加。</span><span class="sxs-lookup"><span data-stu-id="20bf2-120">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` element, but you cannot add both.</span></span>

<span data-ttu-id="20bf2-121">有关较宽的视图的组件的详细信息，请参阅[创建较宽的视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="20bf2-121">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="20bf2-122">有关较宽的视图的示例，请参阅[宽的视图 （基本）](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="20bf2-122">For an example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="20bf2-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="20bf2-123">See Also</span></span>

[<span data-ttu-id="20bf2-124">WideControl （格式） 的自动调整大小元素</span><span class="sxs-lookup"><span data-stu-id="20bf2-124">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="20bf2-125">创建较宽的视图</span><span class="sxs-lookup"><span data-stu-id="20bf2-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="20bf2-126">宽的视图 (Basic)</span><span class="sxs-lookup"><span data-stu-id="20bf2-126">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="20bf2-127">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="20bf2-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
