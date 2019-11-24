---
title: TableControl （Format）的 TableRowEntries 的 TableRowEntry 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 946ffb3fe857503c02b9000238a86775969abbd6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361796"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a><span data-ttu-id="ab96f-102">TableRowEntry Element for TableRowEntries for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ab96f-102">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

<span data-ttu-id="ab96f-103">定义在表的行中显示的数据。</span><span class="sxs-lookup"><span data-stu-id="ab96f-103">Defines the data that is displayed in a row of the table.</span></span>

<span data-ttu-id="ab96f-104">TableRowEntry for TableRowEntries 的 TableControl （Format） TableControl 元素的配置元素（格式） ViewDefinitions 元素（格式） TableControl 元素（format） TableRowEntries 元素（format）</span><span class="sxs-lookup"><span data-stu-id="ab96f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ab96f-105">语法</span><span class="sxs-lookup"><span data-stu-id="ab96f-105">Syntax</span></span>

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ab96f-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="ab96f-106">Attributes and Elements</span></span>

<span data-ttu-id="ab96f-107">以下各节介绍 `TableRowEntry` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ab96f-107">The following sections describe attributes, child elements, and parent element of the `TableRowEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ab96f-108">特性</span><span class="sxs-lookup"><span data-stu-id="ab96f-108">Attributes</span></span>

<span data-ttu-id="ab96f-109">无。</span><span class="sxs-lookup"><span data-stu-id="ab96f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ab96f-110">子元素</span><span class="sxs-lookup"><span data-stu-id="ab96f-110">Child Elements</span></span>

|<span data-ttu-id="ab96f-111">元素</span><span class="sxs-lookup"><span data-stu-id="ab96f-111">Element</span></span>|<span data-ttu-id="ab96f-112">描述</span><span class="sxs-lookup"><span data-stu-id="ab96f-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ab96f-113">TableControl 的 TableRowEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ab96f-113">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="ab96f-114">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="ab96f-114">Required element.</span></span><br /><br /> <span data-ttu-id="ab96f-115">定义其属性值显示在行中的对象。</span><span class="sxs-lookup"><span data-stu-id="ab96f-115">Defines the objects whose property values are displayed in the row.</span></span>|
|[<span data-ttu-id="ab96f-116">TableControl 的 TableRowEntry 的 TableColumnItems 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ab96f-116">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="ab96f-117">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="ab96f-117">Required element.</span></span><br /><br /> <span data-ttu-id="ab96f-118">定义要显示其值的属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="ab96f-118">Defines the properties or scripts whose values are displayed.</span></span>|
|[<span data-ttu-id="ab96f-119">TableControl 的 TableRowEntry 的 Wrap 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ab96f-119">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="ab96f-120">可选元素。</span><span class="sxs-lookup"><span data-stu-id="ab96f-120">Optional element.</span></span><br /><br /> <span data-ttu-id="ab96f-121">指定在下一行显示超过列宽的文本。</span><span class="sxs-lookup"><span data-stu-id="ab96f-121">Specifies that text that exceeds the column width is displayed on the next line.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ab96f-122">父元素</span><span class="sxs-lookup"><span data-stu-id="ab96f-122">Parent Elements</span></span>

|<span data-ttu-id="ab96f-123">元素</span><span class="sxs-lookup"><span data-stu-id="ab96f-123">Element</span></span>|<span data-ttu-id="ab96f-124">描述</span><span class="sxs-lookup"><span data-stu-id="ab96f-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ab96f-125">TableControl 的 TableRowEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ab96f-125">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="ab96f-126">定义表中的行。</span><span class="sxs-lookup"><span data-stu-id="ab96f-126">Defines the rows of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ab96f-127">备注</span><span class="sxs-lookup"><span data-stu-id="ab96f-127">Remarks</span></span>

<span data-ttu-id="ab96f-128">必须指定一个 `TableColumnItems` 元素和一个 `EntrySelectedBy` 元素。</span><span class="sxs-lookup"><span data-stu-id="ab96f-128">One `TableColumnItems` element and one `EntrySelectedBy` element must be specified.</span></span>

<span data-ttu-id="ab96f-129">有关表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="ab96f-129">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="ab96f-130">示例</span><span class="sxs-lookup"><span data-stu-id="ab96f-130">Example</span></span>

<span data-ttu-id="ab96f-131">下面的示例演示一个 `TableRowEntry` 元素，该元素定义一个行，该行[显示了 system.exception 对象的](/dotnet/api/System.Diagnostics.Process)两个属性的值。</span><span class="sxs-lookup"><span data-stu-id="ab96f-131">The following example shows a `TableRowEntry` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
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
```

## <a name="see-also"></a><span data-ttu-id="ab96f-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ab96f-132">See Also</span></span>

[<span data-ttu-id="ab96f-133">创建表视图</span><span class="sxs-lookup"><span data-stu-id="ab96f-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="ab96f-134">TableControl 的 TableRowEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ab96f-134">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="ab96f-135">TableControl 的 TableRowEntry 的 TableColumnItems 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ab96f-135">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="ab96f-136">TableControl 的 TableRowEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ab96f-136">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="ab96f-137">TableControl 的 TableRowEntry 的 Wrap 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ab96f-137">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="ab96f-138">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="ab96f-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
