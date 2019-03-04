---
title: TableControl （格式） 的 TableRowEntroes TableRowEntry 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 001d46debde61f928c338b2f68112fb201f96216
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853583"
---
# <a name="tablerowentry-element-for-tablerowentroes-for-tablecontrol-format"></a><span data-ttu-id="fd7c7-102">TableRowEntry Element for TableRowEntroes for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="fd7c7-102">TableRowEntry Element for TableRowEntroes for TableControl (Format)</span></span>

<span data-ttu-id="fd7c7-103">定义表的行中显示的数据。</span><span class="sxs-lookup"><span data-stu-id="fd7c7-103">Defines the data that is displayed in a row of the table.</span></span>

<span data-ttu-id="fd7c7-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableRowEntries 元素 TableControl （格式） 的 TableRowEntries TableControl （格式） TableRowEntry 元素</span><span class="sxs-lookup"><span data-stu-id="fd7c7-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fd7c7-105">语法</span><span class="sxs-lookup"><span data-stu-id="fd7c7-105">Syntax</span></span>

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fd7c7-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="fd7c7-106">Attributes and Elements</span></span>

<span data-ttu-id="fd7c7-107">以下各节描述了特性、 子元素和父元素的`TableRowEntry`元素。</span><span class="sxs-lookup"><span data-stu-id="fd7c7-107">The following sections describe attributes, child elements, and parent element of the `TableRowEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fd7c7-108">特性</span><span class="sxs-lookup"><span data-stu-id="fd7c7-108">Attributes</span></span>

<span data-ttu-id="fd7c7-109">无。</span><span class="sxs-lookup"><span data-stu-id="fd7c7-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fd7c7-110">子元素</span><span class="sxs-lookup"><span data-stu-id="fd7c7-110">Child Elements</span></span>

|<span data-ttu-id="fd7c7-111">元素</span><span class="sxs-lookup"><span data-stu-id="fd7c7-111">Element</span></span>|<span data-ttu-id="fd7c7-112">描述</span><span class="sxs-lookup"><span data-stu-id="fd7c7-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fd7c7-113">TableControl （格式） 的 TableRowEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="fd7c7-113">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="fd7c7-114">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="fd7c7-114">Required element.</span></span><br /><br /> <span data-ttu-id="fd7c7-115">定义其属性值显示的行中的对象。</span><span class="sxs-lookup"><span data-stu-id="fd7c7-115">Defines the objects whose property values are displayed in the row.</span></span>|
|[<span data-ttu-id="fd7c7-116">TableControl （格式） 的 TableRowEntry TableColumnItems 元素</span><span class="sxs-lookup"><span data-stu-id="fd7c7-116">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="fd7c7-117">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="fd7c7-117">Required element.</span></span><br /><br /> <span data-ttu-id="fd7c7-118">定义属性或其值将显示的脚本。</span><span class="sxs-lookup"><span data-stu-id="fd7c7-118">Defines the properties or scripts whose values are displayed.</span></span>|
|[<span data-ttu-id="fd7c7-119">元素为 TableRowEntry 包装以 TableCntrol （格式）</span><span class="sxs-lookup"><span data-stu-id="fd7c7-119">Wrap Element for TableRowEntry for TableCntrol (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrl-format.md)|<span data-ttu-id="fd7c7-120">可选元素。</span><span class="sxs-lookup"><span data-stu-id="fd7c7-120">Optional element.</span></span><br /><br /> <span data-ttu-id="fd7c7-121">指定在下一行显示超过列宽的文本。</span><span class="sxs-lookup"><span data-stu-id="fd7c7-121">Specifies that text that exceeds the column width is displayed on the next line.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fd7c7-122">父元素</span><span class="sxs-lookup"><span data-stu-id="fd7c7-122">Parent Elements</span></span>

|<span data-ttu-id="fd7c7-123">元素</span><span class="sxs-lookup"><span data-stu-id="fd7c7-123">Element</span></span>|<span data-ttu-id="fd7c7-124">描述</span><span class="sxs-lookup"><span data-stu-id="fd7c7-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fd7c7-125">TableControl （格式） 的 TableRowEntries 元素</span><span class="sxs-lookup"><span data-stu-id="fd7c7-125">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="fd7c7-126">定义表的行。</span><span class="sxs-lookup"><span data-stu-id="fd7c7-126">Defines the rows of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fd7c7-127">备注</span><span class="sxs-lookup"><span data-stu-id="fd7c7-127">Remarks</span></span>

<span data-ttu-id="fd7c7-128">一个`TableColumnItems`元素和一个`EntrySelectedBy`必须指定元素。</span><span class="sxs-lookup"><span data-stu-id="fd7c7-128">One `TableColumnItems` element and one `EntrySelectedBy` element must be specified.</span></span>

<span data-ttu-id="fd7c7-129">表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="fd7c7-129">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="fd7c7-130">示例</span><span class="sxs-lookup"><span data-stu-id="fd7c7-130">Example</span></span>

<span data-ttu-id="fd7c7-131">下面的示例演示`TableRowEntry`显示的两个属性的值将行定义的元素[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)对象。</span><span class="sxs-lookup"><span data-stu-id="fd7c7-131">The following example shows a `TableRowEntry` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="fd7c7-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fd7c7-132">See Also</span></span>

[<span data-ttu-id="fd7c7-133">创建表视图</span><span class="sxs-lookup"><span data-stu-id="fd7c7-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="fd7c7-134">TableControl （格式） 的 TableRowEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="fd7c7-134">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="fd7c7-135">TableControl （格式） 的 TableRowEntry TableColumnItems 元素</span><span class="sxs-lookup"><span data-stu-id="fd7c7-135">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="fd7c7-136">TableControl （格式） 的 TableRowEntries 元素</span><span class="sxs-lookup"><span data-stu-id="fd7c7-136">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="fd7c7-137">TableControl （格式） 的 TableRowEntries TableRowEntry 元素</span><span class="sxs-lookup"><span data-stu-id="fd7c7-137">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[<span data-ttu-id="fd7c7-138">元素为 TableRowEntry 包装以 TableCntrol （格式）</span><span class="sxs-lookup"><span data-stu-id="fd7c7-138">Wrap Element for TableRowEntry for TableCntrol (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrl-format.md)

[<span data-ttu-id="fd7c7-139">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="fd7c7-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
