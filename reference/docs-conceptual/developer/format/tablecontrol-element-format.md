---
title: TableControl 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368196"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="10fd4-102">TableControl Element (Format)</span><span class="sxs-lookup"><span data-stu-id="10fd4-102">TableControl Element (Format)</span></span>

<span data-ttu-id="10fd4-103">定义视图的表格格式。</span><span class="sxs-lookup"><span data-stu-id="10fd4-103">Defines a table format for a view.</span></span>

<span data-ttu-id="10fd4-104">ViewDefinitions 元素（格式） View 元素（Format） TableControl 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="10fd4-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="10fd4-105">语法</span><span class="sxs-lookup"><span data-stu-id="10fd4-105">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="10fd4-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="10fd4-106">Attributes and Elements</span></span>

<span data-ttu-id="10fd4-107">以下各节介绍 `TableControl` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="10fd4-107">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="10fd4-108">您必须指定表中的行。</span><span class="sxs-lookup"><span data-stu-id="10fd4-108">You must specify the rows of the table.</span></span> <span data-ttu-id="10fd4-109">所有其他子元素都是可选的。</span><span class="sxs-lookup"><span data-stu-id="10fd4-109">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="10fd4-110">属性</span><span class="sxs-lookup"><span data-stu-id="10fd4-110">Attributes</span></span>

<span data-ttu-id="10fd4-111">无。</span><span class="sxs-lookup"><span data-stu-id="10fd4-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="10fd4-112">子元素</span><span class="sxs-lookup"><span data-stu-id="10fd4-112">Child Elements</span></span>

|<span data-ttu-id="10fd4-113">元素</span><span class="sxs-lookup"><span data-stu-id="10fd4-113">Element</span></span>|<span data-ttu-id="10fd4-114">描述</span><span class="sxs-lookup"><span data-stu-id="10fd4-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="10fd4-115">TableControl 的 AutoSize 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="10fd4-115">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="10fd4-116">可选元素。</span><span class="sxs-lookup"><span data-stu-id="10fd4-116">Optional element.</span></span><br /><br /> <span data-ttu-id="10fd4-117">指定是否根据数据大小调整列大小和列数。</span><span class="sxs-lookup"><span data-stu-id="10fd4-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="10fd4-118">TableControl 的 HideTableHeaders 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="10fd4-118">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="10fd4-119">可选元素。</span><span class="sxs-lookup"><span data-stu-id="10fd4-119">Optional element.</span></span><br /><br /> <span data-ttu-id="10fd4-120">指示是否不显示表的标头。</span><span class="sxs-lookup"><span data-stu-id="10fd4-120">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="10fd4-121">TableControl 的 TableHeaders 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="10fd4-121">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="10fd4-122">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="10fd4-122">Required element.</span></span><br /><br /> <span data-ttu-id="10fd4-123">为表视图的列定义标签、宽度和数据的对齐方式。</span><span class="sxs-lookup"><span data-stu-id="10fd4-123">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="10fd4-124">TableControl 的 TableRowEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="10fd4-124">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="10fd4-125">可选元素。</span><span class="sxs-lookup"><span data-stu-id="10fd4-125">Optional element.</span></span><br /><br /> <span data-ttu-id="10fd4-126">提供表视图的定义。</span><span class="sxs-lookup"><span data-stu-id="10fd4-126">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="10fd4-127">父元素</span><span class="sxs-lookup"><span data-stu-id="10fd4-127">Parent Elements</span></span>

|<span data-ttu-id="10fd4-128">元素</span><span class="sxs-lookup"><span data-stu-id="10fd4-128">Element</span></span>|<span data-ttu-id="10fd4-129">描述</span><span class="sxs-lookup"><span data-stu-id="10fd4-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="10fd4-130">View 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="10fd4-130">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="10fd4-131">定义一个视图，该视图用于显示一个或多个对象的成员。</span><span class="sxs-lookup"><span data-stu-id="10fd4-131">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="10fd4-132">备注</span><span class="sxs-lookup"><span data-stu-id="10fd4-132">Remarks</span></span>

<span data-ttu-id="10fd4-133">有关表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="10fd4-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="10fd4-134">示例</span><span class="sxs-lookup"><span data-stu-id="10fd4-134">Example</span></span>

<span data-ttu-id="10fd4-135">此示例演示用于显示[system.serviceprocess. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)对象的属性的 `TableControl` 元素。</span><span class="sxs-lookup"><span data-stu-id="10fd4-135">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>...</TableHeaders>
    <TableRowEntries>...</TableRowEntries>
  </TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="10fd4-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="10fd4-136">See Also</span></span>

[<span data-ttu-id="10fd4-137">创建表视图</span><span class="sxs-lookup"><span data-stu-id="10fd4-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="10fd4-138">View 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="10fd4-138">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="10fd4-139">TableControl 的 AutoSize 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="10fd4-139">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="10fd4-140">HideTableHeaders 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="10fd4-140">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="10fd4-141">TableHeaders 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="10fd4-141">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="10fd4-142">TableRowEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="10fd4-142">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="10fd4-143">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="10fd4-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
