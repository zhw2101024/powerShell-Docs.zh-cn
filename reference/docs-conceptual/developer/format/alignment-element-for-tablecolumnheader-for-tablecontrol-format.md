---
title: TableControl 的 TableColumnHeader 的对齐元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff85e83a-c9c2-4c37-accc-e6a27c182f3c
caps.latest.revision: 19
ms.openlocfilehash: 16b41535109ca503e679a135f5ba30054e33de5b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364376"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="e4e50-102">Alignment Element for TableColumnHeader for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e4e50-102">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="e4e50-103">定义列标题中的数据的显示方式。</span><span class="sxs-lookup"><span data-stu-id="e4e50-103">Defines how the data in a column header is displayed.</span></span>

<span data-ttu-id="e4e50-104">TableColumnHeader 的 ViewDefinitions 元素（格式）视图元素（格式） TableControl 元素（格式） TableHeaders 元素（格式） TableColumnHeader 元素（格式）对齐元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e4e50-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element (Format) TableColumnHeader Element (Format) Alignment Element for TableColumnHeader (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e4e50-105">语法</span><span class="sxs-lookup"><span data-stu-id="e4e50-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e4e50-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="e4e50-106">Attributes and Elements</span></span>

<span data-ttu-id="e4e50-107">以下各节介绍 `Alignment` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e4e50-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e4e50-108">属性</span><span class="sxs-lookup"><span data-stu-id="e4e50-108">Attributes</span></span>

<span data-ttu-id="e4e50-109">无。</span><span class="sxs-lookup"><span data-stu-id="e4e50-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e4e50-110">子元素</span><span class="sxs-lookup"><span data-stu-id="e4e50-110">Child Elements</span></span>

<span data-ttu-id="e4e50-111">无。</span><span class="sxs-lookup"><span data-stu-id="e4e50-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e4e50-112">父元素</span><span class="sxs-lookup"><span data-stu-id="e4e50-112">Parent Elements</span></span>

|<span data-ttu-id="e4e50-113">元素</span><span class="sxs-lookup"><span data-stu-id="e4e50-113">Element</span></span>|<span data-ttu-id="e4e50-114">描述</span><span class="sxs-lookup"><span data-stu-id="e4e50-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e4e50-115">TableColumnHeader 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e4e50-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="e4e50-116">定义表中某一列的数据的标签、宽度和对齐方式。</span><span class="sxs-lookup"><span data-stu-id="e4e50-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e4e50-117">文本值</span><span class="sxs-lookup"><span data-stu-id="e4e50-117">Text Value</span></span>

<span data-ttu-id="e4e50-118">指定下列值之一。</span><span class="sxs-lookup"><span data-stu-id="e4e50-118">Specify one of the following values.</span></span> <span data-ttu-id="e4e50-119">这些值不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="e4e50-119">These values are not case-sensitive.</span></span>

<span data-ttu-id="e4e50-120">如果未指定此元素，则在左侧的列中将显示数据左对齐。</span><span class="sxs-lookup"><span data-stu-id="e4e50-120">Left Aligns the data displayed in the column on the left This is the default if this element is not specified.</span></span>

<span data-ttu-id="e4e50-121">右对齐显示在右侧列中的数据。</span><span class="sxs-lookup"><span data-stu-id="e4e50-121">Right Aligns the data displayed in the column on the right.</span></span>

<span data-ttu-id="e4e50-122">居中将列中显示的数据居中。</span><span class="sxs-lookup"><span data-stu-id="e4e50-122">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="e4e50-123">备注</span><span class="sxs-lookup"><span data-stu-id="e4e50-123">Remarks</span></span>

<span data-ttu-id="e4e50-124">有关表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="e4e50-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e4e50-125">示例</span><span class="sxs-lookup"><span data-stu-id="e4e50-125">Example</span></span>

<span data-ttu-id="e4e50-126">此示例演示一个 `TableColumnHeader` 元素，其数据在左侧对齐。</span><span class="sxs-lookup"><span data-stu-id="e4e50-126">This example shows a `TableColumnHeader` element whose data is aligned on the left.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="e4e50-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e4e50-127">See Also</span></span>

[<span data-ttu-id="e4e50-128">创建表视图</span><span class="sxs-lookup"><span data-stu-id="e4e50-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e4e50-129">TableColumnHeader 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e4e50-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="e4e50-130">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="e4e50-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
