---
title: TableControl （Format）的 TableRowEntry 的 TableColumnItems 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: d05437aaa9652e7f81d0854d1a746acffe145699
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361806"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="18558-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="18558-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="18558-103">定义其值显示在行中的属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="18558-103">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="18558-104">TableRowEntry for TableRowEntries 的 TableControl （Format） TableControl 元素的配置元素（格式） ViewDefinitions 元素（格式） TableControl 元素（format） TableRowEntries 元素（format）TableControl 的 TableControlEntry 的 TableColumnItems 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="18558-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="18558-105">语法</span><span class="sxs-lookup"><span data-stu-id="18558-105">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="18558-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="18558-106">Attributes and Elements</span></span>

<span data-ttu-id="18558-107">以下各节介绍 `TableColumnItems` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="18558-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="18558-108">属性</span><span class="sxs-lookup"><span data-stu-id="18558-108">Attributes</span></span>

<span data-ttu-id="18558-109">无。</span><span class="sxs-lookup"><span data-stu-id="18558-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="18558-110">子元素</span><span class="sxs-lookup"><span data-stu-id="18558-110">Child Elements</span></span>

|<span data-ttu-id="18558-111">元素</span><span class="sxs-lookup"><span data-stu-id="18558-111">Element</span></span>|<span data-ttu-id="18558-112">描述</span><span class="sxs-lookup"><span data-stu-id="18558-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="18558-113">TableControl 的 TableColumnItems 的 TableColumnItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="18558-113">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="18558-114">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="18558-114">Required element.</span></span><br /><br /> <span data-ttu-id="18558-115">定义其值显示在行的列中的属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="18558-115">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="18558-116">父元素</span><span class="sxs-lookup"><span data-stu-id="18558-116">Parent Elements</span></span>

|<span data-ttu-id="18558-117">元素</span><span class="sxs-lookup"><span data-stu-id="18558-117">Element</span></span>|<span data-ttu-id="18558-118">描述</span><span class="sxs-lookup"><span data-stu-id="18558-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="18558-119">TableControl 的 TableRowEntries 的 TableRowEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="18558-119">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="18558-120">定义在表的行中显示的数据。</span><span class="sxs-lookup"><span data-stu-id="18558-120">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="18558-121">备注</span><span class="sxs-lookup"><span data-stu-id="18558-121">Remarks</span></span>

<span data-ttu-id="18558-122">行的每个列都需要 @no__t 0 元素。</span><span class="sxs-lookup"><span data-stu-id="18558-122">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="18558-123">第一项显示在第一列中，第二项显示在第二列，依此类推。</span><span class="sxs-lookup"><span data-stu-id="18558-123">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="18558-124">有关表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="18558-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="18558-125">示例</span><span class="sxs-lookup"><span data-stu-id="18558-125">Example</span></span>

<span data-ttu-id="18558-126">下面的示例演示一个 `TableColumnItems` 元素，该元素[定义了 system.exception 对象的](/dotnet/api/System.Diagnostics.Process)三个属性。</span><span class="sxs-lookup"><span data-stu-id="18558-126">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItems>
  <TableColumnItem>
    <PropertyName>Status</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>Name</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>DisplayName</PropertyName>
  </TableColumnItem>
</TableColumnItems>

```

## <a name="see-also"></a><span data-ttu-id="18558-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="18558-127">See Also</span></span>

[<span data-ttu-id="18558-128">创建表视图</span><span class="sxs-lookup"><span data-stu-id="18558-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="18558-129">TableColumnItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="18558-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="18558-130">TableRowEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="18558-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="18558-131">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="18558-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
