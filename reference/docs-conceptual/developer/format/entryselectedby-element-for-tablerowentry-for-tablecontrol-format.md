---
title: TableControl （Format）的 TableRowEntry 的 EntrySelectedBy 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: 9302bfed0324773cb98d698acdcf608f34ee19c1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363336"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a><span data-ttu-id="188d0-102">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="188d0-102">EntrySelectedBy Element for TableRowEntry  for TableControl (Format)</span></span>

<span data-ttu-id="188d0-103">定义使用表视图的此定义的 .NET 类型或要使用此定义时必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="188d0-103">Defines the .NET types that use this definition of the table view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="188d0-104">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） TableControl 元素（格式） TableRowEntries 元素（格式） TableRowEntry 元素（格式） EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="188d0-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="188d0-105">语法</span><span class="sxs-lookup"><span data-stu-id="188d0-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="188d0-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="188d0-106">Attributes and Elements</span></span>

<span data-ttu-id="188d0-107">以下各节介绍了 `EntrySelectedBy` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="188d0-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="188d0-108">属性</span><span class="sxs-lookup"><span data-stu-id="188d0-108">Attributes</span></span>

<span data-ttu-id="188d0-109">无。</span><span class="sxs-lookup"><span data-stu-id="188d0-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="188d0-110">子元素</span><span class="sxs-lookup"><span data-stu-id="188d0-110">Child Elements</span></span>

|<span data-ttu-id="188d0-111">元素</span><span class="sxs-lookup"><span data-stu-id="188d0-111">Element</span></span>|<span data-ttu-id="188d0-112">描述</span><span class="sxs-lookup"><span data-stu-id="188d0-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="188d0-113">TableControl 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="188d0-113">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="188d0-114">可选元素。</span><span class="sxs-lookup"><span data-stu-id="188d0-114">Optional element.</span></span><br /><br /> <span data-ttu-id="188d0-115">定义要使用此表视图定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="188d0-115">Defines the condition that must exist for this table view definition to be used.</span></span>|
|[<span data-ttu-id="188d0-116">TableControl 的 EntrySelectedBy 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="188d0-116">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="188d0-117">可选元素。</span><span class="sxs-lookup"><span data-stu-id="188d0-117">Optional element.</span></span><br /><br /> <span data-ttu-id="188d0-118">指定一组使用此表视图定义的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="188d0-118">Specifies a set of .NET types that use this table view definition.</span></span>|
|[<span data-ttu-id="188d0-119">TableControl 的 EntrySelectedBy 的 TypeName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="188d0-119">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="188d0-120">可选元素。</span><span class="sxs-lookup"><span data-stu-id="188d0-120">Optional element.</span></span><br /><br /> <span data-ttu-id="188d0-121">指定使用此表视图定义的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="188d0-121">Specifies a .NET type that uses this table view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="188d0-122">父元素</span><span class="sxs-lookup"><span data-stu-id="188d0-122">Parent Elements</span></span>

|<span data-ttu-id="188d0-123">元素</span><span class="sxs-lookup"><span data-stu-id="188d0-123">Element</span></span>|<span data-ttu-id="188d0-124">描述</span><span class="sxs-lookup"><span data-stu-id="188d0-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="188d0-125">TableControl 的 TableRowEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="188d0-125">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="188d0-126">定义在表的行中显示的数据。</span><span class="sxs-lookup"><span data-stu-id="188d0-126">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="188d0-127">备注</span><span class="sxs-lookup"><span data-stu-id="188d0-127">Remarks</span></span>

<span data-ttu-id="188d0-128">对于表视图定义，必须至少指定一个类型、选择集或选择条件。</span><span class="sxs-lookup"><span data-stu-id="188d0-128">You must specify at least one type, selection set, or selection condition for a table view definition.</span></span> <span data-ttu-id="188d0-129">您可以使用的子元素数没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="188d0-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="188d0-130">选择条件用于定义要使用的定义必须存在的条件，例如当对象具有特定属性或特定属性值或脚本计算结果为 `true`时。</span><span class="sxs-lookup"><span data-stu-id="188d0-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="188d0-131">有关选择条件的详细信息，请参阅[定义使用视图条目或项的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="188d0-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="188d0-132">有关表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="188d0-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="188d0-133">示例</span><span class="sxs-lookup"><span data-stu-id="188d0-133">Example</span></span>

<span data-ttu-id="188d0-134">下面的示例演示一个 `TableRowEntry` 元素，该元素用于显示[system.object](/dotnet/api/System.Diagnostics.Process)对象的属性。</span><span class="sxs-lookup"><span data-stu-id="188d0-134">The following example shows a `TableRowEntry` element that is used to display the properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName>PropertyForFirstColumn</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName>PropertyForSecondColumn</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a><span data-ttu-id="188d0-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="188d0-135">See Also</span></span>

[<span data-ttu-id="188d0-136">创建表视图</span><span class="sxs-lookup"><span data-stu-id="188d0-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="188d0-137">TableControl 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="188d0-137">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="188d0-138">TableControl 的 EntrySelectedBy 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="188d0-138">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="188d0-139">TableControl 的 TableRowEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="188d0-139">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="188d0-140">TableControl 的 EntrySelectedBy 的 TypeName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="188d0-140">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="188d0-141">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="188d0-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
