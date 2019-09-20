---
title: TableControl （Format）的 TableColumnItems 的 TableColumnItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 9e6cffc7476ef01124d95ecbf287d9788b0324c9
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2019
ms.locfileid: "71143578"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="9738a-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="9738a-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="9738a-103">定义其值显示在行的列中的属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="9738a-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="9738a-104">TableRowEntry for TableRowEntries 的 TableControl （Format） TableControl 元素的配置元素（格式） ViewDefinitions 元素（格式） TableControl 元素（format） TableRowEntries 元素（format）TableColumnItems 的 TableControlEntry for TableControl （Format） TableColumnItem 元素的 TableColumnItems 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="9738a-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9738a-105">语法</span><span class="sxs-lookup"><span data-stu-id="9738a-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9738a-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="9738a-106">Attributes and Elements</span></span>

<span data-ttu-id="9738a-107">以下各节描述了`TableColumnItem`元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9738a-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9738a-108">属性</span><span class="sxs-lookup"><span data-stu-id="9738a-108">Attributes</span></span>

<span data-ttu-id="9738a-109">无。</span><span class="sxs-lookup"><span data-stu-id="9738a-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9738a-110">子元素</span><span class="sxs-lookup"><span data-stu-id="9738a-110">Child Elements</span></span>

|<span data-ttu-id="9738a-111">元素</span><span class="sxs-lookup"><span data-stu-id="9738a-111">Element</span></span>|<span data-ttu-id="9738a-112">说明</span><span class="sxs-lookup"><span data-stu-id="9738a-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9738a-113">TableControl 的 TableColumnItem 的对齐元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9738a-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="9738a-114">可选元素。</span><span class="sxs-lookup"><span data-stu-id="9738a-114">Optional element.</span></span><br /><br /> <span data-ttu-id="9738a-115">定义行的列中数据的显示方式。</span><span class="sxs-lookup"><span data-stu-id="9738a-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="9738a-116">TableControl 的 TableColumnItem 的格式字符串元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9738a-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="9738a-117">指定用于设置行的列中数据的格式的格式模式。</span><span class="sxs-lookup"><span data-stu-id="9738a-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="9738a-118">TableControl 的 TableColumnItem 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="9738a-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="9738a-119">可选元素。</span><span class="sxs-lookup"><span data-stu-id="9738a-119">Optional element.</span></span><br /><br /> <span data-ttu-id="9738a-120">指定显示其值的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="9738a-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="9738a-121">TableControl 的 TableColumnItem 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9738a-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="9738a-122">可选元素。</span><span class="sxs-lookup"><span data-stu-id="9738a-122">Optional element.</span></span><br /><br /> <span data-ttu-id="9738a-123">指定其值显示在行的列中的脚本。</span><span class="sxs-lookup"><span data-stu-id="9738a-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9738a-124">父元素</span><span class="sxs-lookup"><span data-stu-id="9738a-124">Parent Elements</span></span>

|<span data-ttu-id="9738a-125">元素</span><span class="sxs-lookup"><span data-stu-id="9738a-125">Element</span></span>|<span data-ttu-id="9738a-126">说明</span><span class="sxs-lookup"><span data-stu-id="9738a-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9738a-127">TableControl 的 TableControlEntry 的 TableColumnItems 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9738a-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="9738a-128">定义其值显示在行中的属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="9738a-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9738a-129">备注</span><span class="sxs-lookup"><span data-stu-id="9738a-129">Remarks</span></span>

<span data-ttu-id="9738a-130">可以在行的每个列中指定对象或脚本的属性。</span><span class="sxs-lookup"><span data-stu-id="9738a-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="9738a-131">如果未指定子元素，则该项是占位符，不显示任何数据。</span><span class="sxs-lookup"><span data-stu-id="9738a-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="9738a-132">有关表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="9738a-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="9738a-133">示例</span><span class="sxs-lookup"><span data-stu-id="9738a-133">Example</span></span>

<span data-ttu-id="9738a-134">此示例演示一个`TableColumnItem`元素，该元素显示[system.object](/dotnet/api/System.Diagnostics.Process)对象`Status`的属性的值。</span><span class="sxs-lookup"><span data-stu-id="9738a-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="9738a-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9738a-135">See Also</span></span>

[<span data-ttu-id="9738a-136">创建表视图</span><span class="sxs-lookup"><span data-stu-id="9738a-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="9738a-137">TableControl 的 TableColumnItem 的对齐元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9738a-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="9738a-138">TableColumnItems 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9738a-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="9738a-139">TableControl 的 TableColumnItem 的格式字符串元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9738a-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="9738a-140">TableControl 的 TableColumnItem 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="9738a-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="9738a-141">TableControl 的 TableColumnItem 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9738a-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="9738a-142">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="9738a-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
