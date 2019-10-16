---
title: TableControl 的 TableRowEntries 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368146"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="946d5-102">TableRowEntries Element for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="946d5-102">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="946d5-103">定义表中的行。</span><span class="sxs-lookup"><span data-stu-id="946d5-103">Defines the rows of the table.</span></span>

<span data-ttu-id="946d5-104">TableControl 的 Configuration 元素（格式） ViewDefinitions 元素（格式） TableControl 元素（format） TableRowEntries 元素（format）</span><span class="sxs-lookup"><span data-stu-id="946d5-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="946d5-105">语法</span><span class="sxs-lookup"><span data-stu-id="946d5-105">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="946d5-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="946d5-106">Attributes and Elements</span></span>

<span data-ttu-id="946d5-107">以下各节介绍 `TableRowEntries` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="946d5-107">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="946d5-108">属性</span><span class="sxs-lookup"><span data-stu-id="946d5-108">Attributes</span></span>

<span data-ttu-id="946d5-109">无。</span><span class="sxs-lookup"><span data-stu-id="946d5-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="946d5-110">子元素</span><span class="sxs-lookup"><span data-stu-id="946d5-110">Child Elements</span></span>

|<span data-ttu-id="946d5-111">元素</span><span class="sxs-lookup"><span data-stu-id="946d5-111">Element</span></span>|<span data-ttu-id="946d5-112">描述</span><span class="sxs-lookup"><span data-stu-id="946d5-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="946d5-113">TableControl 的 TableRowEntries 的 TableRowEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="946d5-113">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="946d5-114">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="946d5-114">Required element.</span></span><br /><br /> <span data-ttu-id="946d5-115">定义在表的行中显示的数据。</span><span class="sxs-lookup"><span data-stu-id="946d5-115">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="946d5-116">父元素</span><span class="sxs-lookup"><span data-stu-id="946d5-116">Parent Elements</span></span>

|<span data-ttu-id="946d5-117">元素</span><span class="sxs-lookup"><span data-stu-id="946d5-117">Element</span></span>|<span data-ttu-id="946d5-118">描述</span><span class="sxs-lookup"><span data-stu-id="946d5-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="946d5-119">TableControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="946d5-119">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="946d5-120">定义视图的表格格式。</span><span class="sxs-lookup"><span data-stu-id="946d5-120">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="946d5-121">备注</span><span class="sxs-lookup"><span data-stu-id="946d5-121">Remarks</span></span>

<span data-ttu-id="946d5-122">您必须为表视图指定一个或多个 `TableRowEntry` 元素。</span><span class="sxs-lookup"><span data-stu-id="946d5-122">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="946d5-123">对于可以添加的 @no__t 0 个元素，其顺序并没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="946d5-123">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="946d5-124">有关表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="946d5-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="946d5-125">示例</span><span class="sxs-lookup"><span data-stu-id="946d5-125">Example</span></span>

<span data-ttu-id="946d5-126">下面的示例演示一个 `TableRowEntries` 元素，该元素定义一个行，该行[显示了 system.exception 对象的](/dotnet/api/System.Diagnostics.Process)两个属性的值。</span><span class="sxs-lookup"><span data-stu-id="946d5-126">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>
    <EntrySelectedBy>
      <TypeName>System.Diagnostics.Process</TypeName>
    </EntrySelectedBy>
    <TableColumnItems>
      <TableColumnItem>
        <PropertyName> Property for first column</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName> Property for second column</PropertyName>
      </TableColumnItem>
    </TableColumnItems>
  </TableRowEntry>
</TableRowEntries>

```

## <a name="see-also"></a><span data-ttu-id="946d5-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="946d5-127">See Also</span></span>

[<span data-ttu-id="946d5-128">创建表视图</span><span class="sxs-lookup"><span data-stu-id="946d5-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="946d5-129">TableControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="946d5-129">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="946d5-130">TableRowEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="946d5-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="946d5-131">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="946d5-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
