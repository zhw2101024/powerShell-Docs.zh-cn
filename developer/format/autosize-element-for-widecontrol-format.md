---
title: WideControl （格式） 的自动调整大小元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: def37479-7b6e-40cf-bc81-0f7cbc651b31
caps.latest.revision: 11
ms.openlocfilehash: 6dbaef5886a0600bd9fe96dbc8d21f00a674dfcf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857083"
---
# <a name="autosize-element-for-widecontrol-format"></a><span data-ttu-id="03709-102">AutoSize Element for WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="03709-102">AutoSize Element for WideControl (Format)</span></span>

<span data-ttu-id="03709-103">指定列的大小和列数会调整基于数据的大小。</span><span class="sxs-lookup"><span data-stu-id="03709-103">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>

<span data-ttu-id="03709-104">元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） WideControl 元素 （格式） 自动调整大小的配置元素 WideControl （格式）</span><span class="sxs-lookup"><span data-stu-id="03709-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) Autosize Element for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="03709-105">语法</span><span class="sxs-lookup"><span data-stu-id="03709-105">Syntax</span></span>

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="03709-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="03709-106">Attributes and Elements</span></span>

<span data-ttu-id="03709-107">以下各节描述了特性、 子元素和父元素的`AutoSize`元素。</span><span class="sxs-lookup"><span data-stu-id="03709-107">The following sections describe attributes, child elements, and the parent element of the `AutoSize` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="03709-108">特性</span><span class="sxs-lookup"><span data-stu-id="03709-108">Attributes</span></span>

<span data-ttu-id="03709-109">无。</span><span class="sxs-lookup"><span data-stu-id="03709-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="03709-110">子元素</span><span class="sxs-lookup"><span data-stu-id="03709-110">Child Elements</span></span>

<span data-ttu-id="03709-111">无</span><span class="sxs-lookup"><span data-stu-id="03709-111">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="03709-112">父元素</span><span class="sxs-lookup"><span data-stu-id="03709-112">Parent Elements</span></span>

|<span data-ttu-id="03709-113">元素</span><span class="sxs-lookup"><span data-stu-id="03709-113">Element</span></span>|<span data-ttu-id="03709-114">描述</span><span class="sxs-lookup"><span data-stu-id="03709-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="03709-115">WideControl 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="03709-115">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="03709-116">定义范围内 （单个值） 的视图的列表格式。</span><span class="sxs-lookup"><span data-stu-id="03709-116">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="03709-117">备注</span><span class="sxs-lookup"><span data-stu-id="03709-117">Remarks</span></span>

<span data-ttu-id="03709-118">在定义较宽的视图，你可以添加`AutoSize`元素或[ColumnNumber](./columnnumber-element-for-widecontrol-format.md)元素，但您不能将同时添加。</span><span class="sxs-lookup"><span data-stu-id="03709-118">When defining a wide view, you can add the `AutoSize` element or the [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element, but you cannot add both.</span></span>

<span data-ttu-id="03709-119">有关较宽的视图的组件的详细信息，请参阅[创建较宽的视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="03709-119">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="03709-120">有关较宽的视图的示例，请参阅[宽的视图 （基本）](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="03709-120">For an example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="03709-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="03709-121">See Also</span></span>

[<span data-ttu-id="03709-122">ColumnNumber WideControl （格式） 的元素</span><span class="sxs-lookup"><span data-stu-id="03709-122">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="03709-123">创建较宽的视图</span><span class="sxs-lookup"><span data-stu-id="03709-123">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="03709-124">WideControl 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="03709-124">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="03709-125">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="03709-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
