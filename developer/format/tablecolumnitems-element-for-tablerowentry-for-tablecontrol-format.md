---
title: TableControl （格式） 的 TableRowEntry TableColumnItems 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: faa9ba78397e713400f6072df9915f20d966bb37
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859443"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="9681f-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="9681f-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="9681f-103">定义属性或其值显示在一行中的脚本。</span><span class="sxs-lookup"><span data-stu-id="9681f-103">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="9681f-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableRowEntries 元素 TableControl （格式） 的 TableRowEntries TableControl （格式） TableRowEntry 元素TableControl （格式） 的 TableControlEntry TableColumnItems 元素</span><span class="sxs-lookup"><span data-stu-id="9681f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9681f-105">语法</span><span class="sxs-lookup"><span data-stu-id="9681f-105">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9681f-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="9681f-106">Attributes and Elements</span></span>

<span data-ttu-id="9681f-107">以下各节描述的特性、 子元素和父元素的`TableColumnItems`元素。</span><span class="sxs-lookup"><span data-stu-id="9681f-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9681f-108">特性</span><span class="sxs-lookup"><span data-stu-id="9681f-108">Attributes</span></span>

<span data-ttu-id="9681f-109">无。</span><span class="sxs-lookup"><span data-stu-id="9681f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9681f-110">子元素</span><span class="sxs-lookup"><span data-stu-id="9681f-110">Child Elements</span></span>

|<span data-ttu-id="9681f-111">元素</span><span class="sxs-lookup"><span data-stu-id="9681f-111">Element</span></span>|<span data-ttu-id="9681f-112">描述</span><span class="sxs-lookup"><span data-stu-id="9681f-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9681f-113">TableControl （格式） 的 TableColumnItems TableColumnItem 元素</span><span class="sxs-lookup"><span data-stu-id="9681f-113">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="9681f-114">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="9681f-114">Required element.</span></span><br /><br /> <span data-ttu-id="9681f-115">定义属性或其值显示在一行的列中的脚本。</span><span class="sxs-lookup"><span data-stu-id="9681f-115">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9681f-116">父元素</span><span class="sxs-lookup"><span data-stu-id="9681f-116">Parent Elements</span></span>

|<span data-ttu-id="9681f-117">元素</span><span class="sxs-lookup"><span data-stu-id="9681f-117">Element</span></span>|<span data-ttu-id="9681f-118">描述</span><span class="sxs-lookup"><span data-stu-id="9681f-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9681f-119">TableControl （格式） 的 TableRowEntries TableRowEntry 元素</span><span class="sxs-lookup"><span data-stu-id="9681f-119">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)|<span data-ttu-id="9681f-120">定义表的行中显示的数据。</span><span class="sxs-lookup"><span data-stu-id="9681f-120">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9681f-121">备注</span><span class="sxs-lookup"><span data-stu-id="9681f-121">Remarks</span></span>

<span data-ttu-id="9681f-122">一个`TableColumnItem`元素是必需的行的每个列。</span><span class="sxs-lookup"><span data-stu-id="9681f-122">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="9681f-123">第一个条目显示在第一列，第二个条目中的第二个列，依此类推。</span><span class="sxs-lookup"><span data-stu-id="9681f-123">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="9681f-124">表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="9681f-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="9681f-125">示例</span><span class="sxs-lookup"><span data-stu-id="9681f-125">Example</span></span>

<span data-ttu-id="9681f-126">下面的示例演示`TableColumnItems`定义的三个属性的元素[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)对象。</span><span class="sxs-lookup"><span data-stu-id="9681f-126">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9681f-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9681f-127">See Also</span></span>

[<span data-ttu-id="9681f-128">创建表视图</span><span class="sxs-lookup"><span data-stu-id="9681f-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="9681f-129">TableColumnItem 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="9681f-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="9681f-130">TableRowEntry 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="9681f-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[<span data-ttu-id="9681f-131">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="9681f-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
