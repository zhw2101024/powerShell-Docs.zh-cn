---
title: TableControl （格式） 的 TableColumnItems TableColumnItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 159f943f6bfb33c5403b5714380631351523789f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063932"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="e93ab-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e93ab-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="e93ab-103">定义属性或其值显示在一行的列中的脚本。</span><span class="sxs-lookup"><span data-stu-id="e93ab-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="e93ab-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableRowEntries 元素 TableControl （格式） 的 TableRowEntries TableControl （格式） TableRowEntry 元素TableControl （格式） 的 TableColumnItems TableControl （格式） TableColumnItem 元素 TableControlEntry TableColumnItems 元素</span><span class="sxs-lookup"><span data-stu-id="e93ab-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e93ab-105">语法</span><span class="sxs-lookup"><span data-stu-id="e93ab-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e93ab-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e93ab-106">Attributes and Elements</span></span>

<span data-ttu-id="e93ab-107">以下各节描述的特性、 子元素和父元素的`TableColumnItem`元素。</span><span class="sxs-lookup"><span data-stu-id="e93ab-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e93ab-108">属性</span><span class="sxs-lookup"><span data-stu-id="e93ab-108">Attributes</span></span>

<span data-ttu-id="e93ab-109">无。</span><span class="sxs-lookup"><span data-stu-id="e93ab-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e93ab-110">子元素</span><span class="sxs-lookup"><span data-stu-id="e93ab-110">Child Elements</span></span>

|<span data-ttu-id="e93ab-111">元素</span><span class="sxs-lookup"><span data-stu-id="e93ab-111">Element</span></span>|<span data-ttu-id="e93ab-112">说明</span><span class="sxs-lookup"><span data-stu-id="e93ab-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e93ab-113">TableControl （格式） 的 TableColumnItem 的对齐方式元素</span><span class="sxs-lookup"><span data-stu-id="e93ab-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="e93ab-114">可选元素。</span><span class="sxs-lookup"><span data-stu-id="e93ab-114">Optional element.</span></span><br /><br /> <span data-ttu-id="e93ab-115">定义如何显示的行的列中的数据。</span><span class="sxs-lookup"><span data-stu-id="e93ab-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="e93ab-116">TableControl （格式） 的 TableColumnItem 的 FormatString 元素</span><span class="sxs-lookup"><span data-stu-id="e93ab-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="e93ab-117">指定用于设置格式的行的列中的数据的格式模式。</span><span class="sxs-lookup"><span data-stu-id="e93ab-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="e93ab-118">TableControl （格式） 的 TableColumnItem PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="e93ab-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="e93ab-119">可选元素。</span><span class="sxs-lookup"><span data-stu-id="e93ab-119">Optional element.</span></span><br /><br /> <span data-ttu-id="e93ab-120">指定显示其值的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="e93ab-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="e93ab-121">TableControl （格式） 的 TableColumnItem 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="e93ab-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="e93ab-122">可选元素。</span><span class="sxs-lookup"><span data-stu-id="e93ab-122">Optional element.</span></span><br /><br /> <span data-ttu-id="e93ab-123">指定行的列中显示其值的脚本。</span><span class="sxs-lookup"><span data-stu-id="e93ab-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e93ab-124">父元素</span><span class="sxs-lookup"><span data-stu-id="e93ab-124">Parent Elements</span></span>

|<span data-ttu-id="e93ab-125">元素</span><span class="sxs-lookup"><span data-stu-id="e93ab-125">Element</span></span>|<span data-ttu-id="e93ab-126">说明</span><span class="sxs-lookup"><span data-stu-id="e93ab-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e93ab-127">TableControl （格式） 的 TableControlEntry TableColumnItems 元素</span><span class="sxs-lookup"><span data-stu-id="e93ab-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="e93ab-128">定义属性或其值显示的行中的脚本。</span><span class="sxs-lookup"><span data-stu-id="e93ab-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e93ab-129">备注</span><span class="sxs-lookup"><span data-stu-id="e93ab-129">Remarks</span></span>

<span data-ttu-id="e93ab-130">行的每个列中，可以指定一个或多个脚本的属性。</span><span class="sxs-lookup"><span data-stu-id="e93ab-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="e93ab-131">如果不指定了任何子元素，该项目是一个占位符，并不显示任何数据。</span><span class="sxs-lookup"><span data-stu-id="e93ab-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="e93ab-132">表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="e93ab-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e93ab-133">示例</span><span class="sxs-lookup"><span data-stu-id="e93ab-133">Example</span></span>

<span data-ttu-id="e93ab-134">此示例演示`TableColumnItem`显示的值的元素`Status`的属性[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)对象。</span><span class="sxs-lookup"><span data-stu-id="e93ab-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="e93ab-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e93ab-135">See Also</span></span>

[<span data-ttu-id="e93ab-136">创建表视图</span><span class="sxs-lookup"><span data-stu-id="e93ab-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e93ab-137">TableControl （格式） 的 TableColumnItem 的对齐方式元素</span><span class="sxs-lookup"><span data-stu-id="e93ab-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="e93ab-138">TableColumnItems 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="e93ab-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="e93ab-139">TableControl （格式） 的 TableColumnItem 的 FormatString 元素</span><span class="sxs-lookup"><span data-stu-id="e93ab-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="e93ab-140">TableControl （格式） 的 TableColumnItem PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="e93ab-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="e93ab-141">TableControl （格式） 的 TableColumnItem 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="e93ab-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="e93ab-142">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="e93ab-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
