---
title: TableColumnHeader 元素 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: 15f47c97ac5d55cb76e153af86672b3ffaf176c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858593"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="e0cd3-102">TableColumnHeader Element (Format)</span><span class="sxs-lookup"><span data-stu-id="e0cd3-102">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="e0cd3-103">定义该标签，列的宽度和表的列标签的对齐方式。</span><span class="sxs-lookup"><span data-stu-id="e0cd3-103">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="e0cd3-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableHeaders 元素 TableControl （格式） 的 TableHeaders TableControl （格式） TableColumnHeader 元素</span><span class="sxs-lookup"><span data-stu-id="e0cd3-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e0cd3-105">语法</span><span class="sxs-lookup"><span data-stu-id="e0cd3-105">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e0cd3-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="e0cd3-106">Attributes and Elements</span></span>

<span data-ttu-id="e0cd3-107">以下各节描述了特性、 子元素和父元素的`TableColumnHeader`元素。</span><span class="sxs-lookup"><span data-stu-id="e0cd3-107">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e0cd3-108">属性</span><span class="sxs-lookup"><span data-stu-id="e0cd3-108">Attributes</span></span>

<span data-ttu-id="e0cd3-109">无。</span><span class="sxs-lookup"><span data-stu-id="e0cd3-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e0cd3-110">子元素</span><span class="sxs-lookup"><span data-stu-id="e0cd3-110">Child Elements</span></span>

|<span data-ttu-id="e0cd3-111">元素</span><span class="sxs-lookup"><span data-stu-id="e0cd3-111">Element</span></span>|<span data-ttu-id="e0cd3-112">说明</span><span class="sxs-lookup"><span data-stu-id="e0cd3-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e0cd3-113">TableControl （格式） 的 TableColumnHeader 的标签元素</span><span class="sxs-lookup"><span data-stu-id="e0cd3-113">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="e0cd3-114">可选元素。</span><span class="sxs-lookup"><span data-stu-id="e0cd3-114">Optional element.</span></span><br /><br /> <span data-ttu-id="e0cd3-115">定义显示在列顶部的标签。</span><span class="sxs-lookup"><span data-stu-id="e0cd3-115">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="e0cd3-116">如果未不指定任何标签，则使用其值显示在行中的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="e0cd3-116">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="e0cd3-117">TableControl （格式） 的 TableColumnHeader 的 width 元素</span><span class="sxs-lookup"><span data-stu-id="e0cd3-117">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="e0cd3-118">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="e0cd3-118">Required element.</span></span><br /><br /> <span data-ttu-id="e0cd3-119">指定列的宽度 （以字符为单位）。</span><span class="sxs-lookup"><span data-stu-id="e0cd3-119">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="e0cd3-120">TableControl （格式） 的 TableColumbnHeader 的对齐方式元素</span><span class="sxs-lookup"><span data-stu-id="e0cd3-120">Alignment Element for TableColumbnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="e0cd3-121">可选元素。</span><span class="sxs-lookup"><span data-stu-id="e0cd3-121">Optional element.</span></span><br /><br /> <span data-ttu-id="e0cd3-122">指定如何显示的列的标签。</span><span class="sxs-lookup"><span data-stu-id="e0cd3-122">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="e0cd3-123">如果指定不对齐，则标签左侧对齐。</span><span class="sxs-lookup"><span data-stu-id="e0cd3-123">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e0cd3-124">父元素</span><span class="sxs-lookup"><span data-stu-id="e0cd3-124">Parent Elements</span></span>

|<span data-ttu-id="e0cd3-125">元素</span><span class="sxs-lookup"><span data-stu-id="e0cd3-125">Element</span></span>|<span data-ttu-id="e0cd3-126">说明</span><span class="sxs-lookup"><span data-stu-id="e0cd3-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e0cd3-127">TableHeaders 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="e0cd3-127">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="e0cd3-128">定义表视图的列。</span><span class="sxs-lookup"><span data-stu-id="e0cd3-128">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e0cd3-129">备注</span><span class="sxs-lookup"><span data-stu-id="e0cd3-129">Remarks</span></span>

<span data-ttu-id="e0cd3-130">指定表的每个列的标头。</span><span class="sxs-lookup"><span data-stu-id="e0cd3-130">Specify a header for each column of the table.</span></span> <span data-ttu-id="e0cd3-131">列会显示的顺序在`TableColumnHeader`元素的定义。</span><span class="sxs-lookup"><span data-stu-id="e0cd3-131">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="e0cd3-132">表必须具有相同数量的`TableColumnHeader`元素作为`TableRowEntry`元素。</span><span class="sxs-lookup"><span data-stu-id="e0cd3-132">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="e0cd3-133">列标题定义如何显示表顶部的文本。</span><span class="sxs-lookup"><span data-stu-id="e0cd3-133">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="e0cd3-134">行项定义的表的行中显示的数据。</span><span class="sxs-lookup"><span data-stu-id="e0cd3-134">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="e0cd3-135">表视图的组件的详细信息，请参阅[表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="e0cd3-135">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e0cd3-136">示例</span><span class="sxs-lookup"><span data-stu-id="e0cd3-136">Example</span></span>

<span data-ttu-id="e0cd3-137">下面的示例演示两个`TableColumnHeader`元素。</span><span class="sxs-lookup"><span data-stu-id="e0cd3-137">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="e0cd3-138">第一个元素定义一个列和其标签为"列 1"，已包含 16 个字符的宽度上左边对齐其标签。</span><span class="sxs-lookup"><span data-stu-id="e0cd3-138">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="e0cd3-139">第二个元素定义一个列，其标签为"第 2 列"，宽度为 10 个字符，并且其标签居中列中。</span><span class="sxs-lookup"><span data-stu-id="e0cd3-139">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
    <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a><span data-ttu-id="e0cd3-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e0cd3-140">See Also</span></span>

[<span data-ttu-id="e0cd3-141">TableContrl （格式） 的 TableColumnHeader 的对齐方式元素</span><span class="sxs-lookup"><span data-stu-id="e0cd3-141">Alignment Element for TableColumnHeader for TableContrl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="e0cd3-142">创建表视图</span><span class="sxs-lookup"><span data-stu-id="e0cd3-142">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e0cd3-143">TableControl （格式） 的 TableColumnHeader 的标签元素</span><span class="sxs-lookup"><span data-stu-id="e0cd3-143">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="e0cd3-144">TableControl （格式） 的 TableHeaders 元素</span><span class="sxs-lookup"><span data-stu-id="e0cd3-144">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="e0cd3-145">TableColumnHeader TableControl 元素 （格式） 的宽度</span><span class="sxs-lookup"><span data-stu-id="e0cd3-145">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="e0cd3-146">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="e0cd3-146">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)