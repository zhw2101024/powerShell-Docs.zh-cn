---
title: TableControl 的 TableColumnItem 的对齐元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b07a53df-64f1-49b0-8cea-c993b3f1f76b
caps.latest.revision: 10
ms.openlocfilehash: 1bc936b94ee6fd6239e9e3c4afcdb8f14fbe36eb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369076"
---
# <a name="alignment-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="4c1e3-102">Alignment Element for TableColumnItem for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="4c1e3-102">Alignment Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="4c1e3-103">定义行的列中数据的显示方式。</span><span class="sxs-lookup"><span data-stu-id="4c1e3-103">Defines how the data in a column of the row is displayed.</span></span>

<span data-ttu-id="4c1e3-104">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） TableControl 元素（格式） TableRowEntries 元素（格式） TableRowEntry 元素（格式） TableColumnItems 元素（格式） TableColumnItem 元素（格式）TableColumnItem 的对齐元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4c1e3-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) Alignment Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4c1e3-105">语法</span><span class="sxs-lookup"><span data-stu-id="4c1e3-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4c1e3-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="4c1e3-106">Attributes and Elements</span></span>

<span data-ttu-id="4c1e3-107">以下各节介绍 `Alignment` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4c1e3-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4c1e3-108">属性</span><span class="sxs-lookup"><span data-stu-id="4c1e3-108">Attributes</span></span>

<span data-ttu-id="4c1e3-109">无。</span><span class="sxs-lookup"><span data-stu-id="4c1e3-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4c1e3-110">子元素</span><span class="sxs-lookup"><span data-stu-id="4c1e3-110">Child Elements</span></span>

<span data-ttu-id="4c1e3-111">无。</span><span class="sxs-lookup"><span data-stu-id="4c1e3-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4c1e3-112">父元素</span><span class="sxs-lookup"><span data-stu-id="4c1e3-112">Parent Elements</span></span>

|<span data-ttu-id="4c1e3-113">元素</span><span class="sxs-lookup"><span data-stu-id="4c1e3-113">Element</span></span>|<span data-ttu-id="4c1e3-114">描述</span><span class="sxs-lookup"><span data-stu-id="4c1e3-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4c1e3-115">TableColumnItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4c1e3-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="4c1e3-116">定义表中某一列的数据的标签、宽度和对齐方式。</span><span class="sxs-lookup"><span data-stu-id="4c1e3-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4c1e3-117">文本值</span><span class="sxs-lookup"><span data-stu-id="4c1e3-117">Text Value</span></span>

<span data-ttu-id="4c1e3-118">指定下列值之一。</span><span class="sxs-lookup"><span data-stu-id="4c1e3-118">Specify one of the following values.</span></span> <span data-ttu-id="4c1e3-119">（这些值不区分大小写。）</span><span class="sxs-lookup"><span data-stu-id="4c1e3-119">(These values are not case-sensitive.)</span></span>

<span data-ttu-id="4c1e3-120">向左移动列中显示的数据。</span><span class="sxs-lookup"><span data-stu-id="4c1e3-120">Left Shifts the data displayed in the column to the left.</span></span> <span data-ttu-id="4c1e3-121">（如果未指定此元素，则这是默认值。）</span><span class="sxs-lookup"><span data-stu-id="4c1e3-121">(This is the default if this element is not specified.)</span></span>

<span data-ttu-id="4c1e3-122">向右移动列中显示的数据。</span><span class="sxs-lookup"><span data-stu-id="4c1e3-122">Right Shifts the data displayed in the column to the right.</span></span>

<span data-ttu-id="4c1e3-123">居中将列中显示的数据居中。</span><span class="sxs-lookup"><span data-stu-id="4c1e3-123">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="4c1e3-124">备注</span><span class="sxs-lookup"><span data-stu-id="4c1e3-124">Remarks</span></span>

<span data-ttu-id="4c1e3-125">有关表视图的组件的详细信息，请参阅[表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="4c1e3-125">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4c1e3-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4c1e3-126">See Also</span></span>

[<span data-ttu-id="4c1e3-127">表视图</span><span class="sxs-lookup"><span data-stu-id="4c1e3-127">Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="4c1e3-128">TableColumnItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4c1e3-128">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)
