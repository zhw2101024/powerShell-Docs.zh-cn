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
ms.openlocfilehash: 5d80bdd736ad540f01c5ebc1f3d31dc9bd628ba5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862413"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="b8c44-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b8c44-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="b8c44-103">定义属性或其值显示在一行的列中的脚本。</span><span class="sxs-lookup"><span data-stu-id="b8c44-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="b8c44-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableRowEntries 元素 TableControl （格式） 的 TableRowEntries TableControl （格式） TableRowEntry 元素TableControl （格式） 的 TableColumnItems TableControl （格式） TableColumnItem 元素 TableControlEntry TableColumnItems 元素</span><span class="sxs-lookup"><span data-stu-id="b8c44-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b8c44-105">语法</span><span class="sxs-lookup"><span data-stu-id="b8c44-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <SciptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b8c44-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="b8c44-106">Attributes and Elements</span></span>

<span data-ttu-id="b8c44-107">以下各节描述的特性、 子元素和父元素的`TableColumnItem`元素。</span><span class="sxs-lookup"><span data-stu-id="b8c44-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b8c44-108">特性</span><span class="sxs-lookup"><span data-stu-id="b8c44-108">Attributes</span></span>

<span data-ttu-id="b8c44-109">无。</span><span class="sxs-lookup"><span data-stu-id="b8c44-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b8c44-110">子元素</span><span class="sxs-lookup"><span data-stu-id="b8c44-110">Child Elements</span></span>

|<span data-ttu-id="b8c44-111">元素</span><span class="sxs-lookup"><span data-stu-id="b8c44-111">Element</span></span>|<span data-ttu-id="b8c44-112">描述</span><span class="sxs-lookup"><span data-stu-id="b8c44-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b8c44-113">TableControl （格式） 的 TableColumnItem 的对齐方式元素</span><span class="sxs-lookup"><span data-stu-id="b8c44-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="b8c44-114">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b8c44-114">Optional element.</span></span><br /><br /> <span data-ttu-id="b8c44-115">定义如何显示的行的列中的数据。</span><span class="sxs-lookup"><span data-stu-id="b8c44-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="b8c44-116">TableControl （格式） 的 TableColumnItem 的 FormatString 元素</span><span class="sxs-lookup"><span data-stu-id="b8c44-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="b8c44-117">指定用于设置格式的行的列中的数据的格式模式。</span><span class="sxs-lookup"><span data-stu-id="b8c44-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="b8c44-118">TableControl （格式） 的 TableColumnItem PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="b8c44-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="b8c44-119">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b8c44-119">Optional element.</span></span><br /><br /> <span data-ttu-id="b8c44-120">指定显示其值的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="b8c44-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="b8c44-121">TableControl （格式） 的 TableColumnItem 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="b8c44-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="b8c44-122">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b8c44-122">Optional element.</span></span><br /><br /> <span data-ttu-id="b8c44-123">指定行的列中显示其值的脚本。</span><span class="sxs-lookup"><span data-stu-id="b8c44-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b8c44-124">父元素</span><span class="sxs-lookup"><span data-stu-id="b8c44-124">Parent Elements</span></span>

|<span data-ttu-id="b8c44-125">元素</span><span class="sxs-lookup"><span data-stu-id="b8c44-125">Element</span></span>|<span data-ttu-id="b8c44-126">描述</span><span class="sxs-lookup"><span data-stu-id="b8c44-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b8c44-127">TableControl （格式） 的 TableControlEntry TableColumnItems 元素</span><span class="sxs-lookup"><span data-stu-id="b8c44-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="b8c44-128">定义属性或其值显示的行中的脚本。</span><span class="sxs-lookup"><span data-stu-id="b8c44-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b8c44-129">备注</span><span class="sxs-lookup"><span data-stu-id="b8c44-129">Remarks</span></span>

<span data-ttu-id="b8c44-130">行的每个列中，可以指定一个或多个脚本的属性。</span><span class="sxs-lookup"><span data-stu-id="b8c44-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="b8c44-131">如果不指定了任何子元素，该项目是一个占位符，并不显示任何数据。</span><span class="sxs-lookup"><span data-stu-id="b8c44-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="b8c44-132">表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="b8c44-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b8c44-133">示例</span><span class="sxs-lookup"><span data-stu-id="b8c44-133">Example</span></span>

<span data-ttu-id="b8c44-134">此示例演示`TableColumnItem`显示的值的元素`Status`的属性[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)对象。</span><span class="sxs-lookup"><span data-stu-id="b8c44-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="b8c44-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b8c44-135">See Also</span></span>

[<span data-ttu-id="b8c44-136">创建表视图</span><span class="sxs-lookup"><span data-stu-id="b8c44-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b8c44-137">TableControl （格式） 的 TableColumnItem 的对齐方式元素</span><span class="sxs-lookup"><span data-stu-id="b8c44-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="b8c44-138">TableColumnItems 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b8c44-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="b8c44-139">TableControl （格式） 的 TableColumnItem 的 FormatString 元素</span><span class="sxs-lookup"><span data-stu-id="b8c44-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="b8c44-140">TableControl （格式） 的 TableColumnItem PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="b8c44-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="b8c44-141">TableControl （格式） 的 TableColumnItem 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="b8c44-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="b8c44-142">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="b8c44-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
