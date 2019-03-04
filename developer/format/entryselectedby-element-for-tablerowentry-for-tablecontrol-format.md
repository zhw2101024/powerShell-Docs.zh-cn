---
title: TableControl （格式） 的 TableRowEntry EntrySelectedBy 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: e18564c10898c73128e0a4bc7d077e7c7ffb1c22
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862323"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a><span data-ttu-id="5166e-102">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="5166e-102">EntrySelectedBy Element for TableRowEntry  for TableControl (Format)</span></span>

<span data-ttu-id="5166e-103">定义使用此定义的表视图或必须存在要使用此定义的条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="5166e-103">Defines the .NET types that use this definition of the table view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="5166e-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableRowEntries 元素 （格式） TableRowEntry 元素 （格式） EntrySelectedBy 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="5166e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5166e-105">语法</span><span class="sxs-lookup"><span data-stu-id="5166e-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5166e-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="5166e-106">Attributes and Elements</span></span>

<span data-ttu-id="5166e-107">以下各节描述了特性、 子元素和父元素的`EntrySelectedBy`元素。</span><span class="sxs-lookup"><span data-stu-id="5166e-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5166e-108">特性</span><span class="sxs-lookup"><span data-stu-id="5166e-108">Attributes</span></span>

<span data-ttu-id="5166e-109">无。</span><span class="sxs-lookup"><span data-stu-id="5166e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5166e-110">子元素</span><span class="sxs-lookup"><span data-stu-id="5166e-110">Child Elements</span></span>

|<span data-ttu-id="5166e-111">元素</span><span class="sxs-lookup"><span data-stu-id="5166e-111">Element</span></span>|<span data-ttu-id="5166e-112">描述</span><span class="sxs-lookup"><span data-stu-id="5166e-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5166e-113">TableControl （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="5166e-113">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="5166e-114">可选元素。</span><span class="sxs-lookup"><span data-stu-id="5166e-114">Optional element.</span></span><br /><br /> <span data-ttu-id="5166e-115">定义必须存在要使用此表视图定义的条件。</span><span class="sxs-lookup"><span data-stu-id="5166e-115">Defines the condition that must exist for this table view definition to be used.</span></span>|
|[<span data-ttu-id="5166e-116">TableControl （格式） 的 EntrySelectedBy SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="5166e-116">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="5166e-117">可选元素。</span><span class="sxs-lookup"><span data-stu-id="5166e-117">Optional element.</span></span><br /><br /> <span data-ttu-id="5166e-118">指定一组使用此表视图定义的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="5166e-118">Specifies a set of .NET types that use this table view definition.</span></span>|
|[<span data-ttu-id="5166e-119">TableControl （格式） 的 EntrySelectedBy 的 TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="5166e-119">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="5166e-120">可选元素。</span><span class="sxs-lookup"><span data-stu-id="5166e-120">Optional element.</span></span><br /><br /> <span data-ttu-id="5166e-121">指定将使用此表视图定义的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="5166e-121">Specifies a .NET type that uses this table view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5166e-122">父元素</span><span class="sxs-lookup"><span data-stu-id="5166e-122">Parent Elements</span></span>

|<span data-ttu-id="5166e-123">元素</span><span class="sxs-lookup"><span data-stu-id="5166e-123">Element</span></span>|<span data-ttu-id="5166e-124">描述</span><span class="sxs-lookup"><span data-stu-id="5166e-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5166e-125">TableControl （格式） 的 TableRowEntry 元素</span><span class="sxs-lookup"><span data-stu-id="5166e-125">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)|<span data-ttu-id="5166e-126">定义表的行中显示的数据。</span><span class="sxs-lookup"><span data-stu-id="5166e-126">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5166e-127">备注</span><span class="sxs-lookup"><span data-stu-id="5166e-127">Remarks</span></span>

<span data-ttu-id="5166e-128">必须指定至少一个类型、 选择集或选择表视图定义的条件。</span><span class="sxs-lookup"><span data-stu-id="5166e-128">You must specify at least one type, selection set, or selection condition for a table view definition.</span></span> <span data-ttu-id="5166e-129">可以使用的子元素的数目没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="5166e-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="5166e-130">使用选择条件来定义要使用，例如当一个对象具有特定属性的定义中必须存在一个条件或特定属性值或脚本的计算结果为`true`。</span><span class="sxs-lookup"><span data-stu-id="5166e-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="5166e-131">有关选择条件的详细信息，请参阅[时视图条目定义条件或使用项](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="5166e-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="5166e-132">表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="5166e-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="5166e-133">示例</span><span class="sxs-lookup"><span data-stu-id="5166e-133">Example</span></span>

<span data-ttu-id="5166e-134">下面的示例演示`TableRowEntry`用来显示的属性的元素[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)对象。</span><span class="sxs-lookup"><span data-stu-id="5166e-134">The following example shows a `TableRowEntry` element that is used to display the properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5166e-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5166e-135">See Also</span></span>

[<span data-ttu-id="5166e-136">创建表视图</span><span class="sxs-lookup"><span data-stu-id="5166e-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="5166e-137">TableControl （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="5166e-137">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="5166e-138">TableControl （格式） 的 EntrySelectedBy SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="5166e-138">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="5166e-139">TableControl （格式） 的 TableRowEntry 元素</span><span class="sxs-lookup"><span data-stu-id="5166e-139">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[<span data-ttu-id="5166e-140">TableControl （格式） 的 EntrySelectedBy 的 TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="5166e-140">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="5166e-141">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="5166e-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
