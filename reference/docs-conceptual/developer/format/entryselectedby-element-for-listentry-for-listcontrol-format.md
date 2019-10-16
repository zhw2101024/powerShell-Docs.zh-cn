---
title: ListControl （Format）的 ListEntry 的 EntrySelectedBy 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363826"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="70fab-102">EntrySelectedBy Element for ListEntry for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="70fab-102">EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="70fab-103">定义使用此列表视图定义或要使用此定义必须存在的条件的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="70fab-103">Defines the .NET types that use this list view definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="70fab-104">在大多数情况下，列表视图只需要一个定义。</span><span class="sxs-lookup"><span data-stu-id="70fab-104">In most cases only one definition is needed for a list view.</span></span> <span data-ttu-id="70fab-105">但是，如果您希望使用同一列表视图为不同对象显示不同的数据，则可以为列表视图提供多个定义。</span><span class="sxs-lookup"><span data-stu-id="70fab-105">However, you can provide multiple definitions for the list view if you want to use the same list view to display different data for different objects.</span></span>

<span data-ttu-id="70fab-106">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（format） ListEntries 元素 for ListControl （Format） ListEntry 元素 for ListEntry for ListControl （Format） EntrySelectedBy 元素 forListEntry for ListControl （Format）</span><span class="sxs-lookup"><span data-stu-id="70fab-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntry for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="70fab-107">语法</span><span class="sxs-lookup"><span data-stu-id="70fab-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="70fab-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="70fab-108">Attributes and Elements</span></span>

<span data-ttu-id="70fab-109">以下各节介绍了 `EntrySelectedBy` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="70fab-109">The following sections describe the attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="70fab-110">属性</span><span class="sxs-lookup"><span data-stu-id="70fab-110">Attributes</span></span>

<span data-ttu-id="70fab-111">无。</span><span class="sxs-lookup"><span data-stu-id="70fab-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="70fab-112">子元素</span><span class="sxs-lookup"><span data-stu-id="70fab-112">Child Elements</span></span>

|<span data-ttu-id="70fab-113">元素</span><span class="sxs-lookup"><span data-stu-id="70fab-113">Element</span></span>|<span data-ttu-id="70fab-114">描述</span><span class="sxs-lookup"><span data-stu-id="70fab-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="70fab-115">ListControl 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="70fab-115">SelectionCondition Element for EntrySelectedBy for ListControl  (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="70fab-116">可选元素。</span><span class="sxs-lookup"><span data-stu-id="70fab-116">Optional element.</span></span><br /><br /> <span data-ttu-id="70fab-117">定义要使用此列表视图定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="70fab-117">Defines the condition that must exist for this list view definition to be used.</span></span>|
|[<span data-ttu-id="70fab-118">ListControl 的 EntrySelectedBy 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="70fab-118">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="70fab-119">可选元素。</span><span class="sxs-lookup"><span data-stu-id="70fab-119">Optional element.</span></span><br /><br /> <span data-ttu-id="70fab-120">指定一组使用此列表视图定义的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="70fab-120">Specifies a set of .NET types that use this list view definition.</span></span>|
|[<span data-ttu-id="70fab-121">ListControl 的 EntrySelectedBy 的 TypeName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="70fab-121">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="70fab-122">可选元素。</span><span class="sxs-lookup"><span data-stu-id="70fab-122">Optional element.</span></span><br /><br /> <span data-ttu-id="70fab-123">指定使用此列表视图定义的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="70fab-123">Specifies a .NET type that uses this list view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="70fab-124">父元素</span><span class="sxs-lookup"><span data-stu-id="70fab-124">Parent Elements</span></span>

|<span data-ttu-id="70fab-125">元素</span><span class="sxs-lookup"><span data-stu-id="70fab-125">Element</span></span>|<span data-ttu-id="70fab-126">描述</span><span class="sxs-lookup"><span data-stu-id="70fab-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="70fab-127">ListControl 的 ListEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="70fab-127">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="70fab-128">定义列表行的显示方式。</span><span class="sxs-lookup"><span data-stu-id="70fab-128">Defines how the rows of the list are displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="70fab-129">备注</span><span class="sxs-lookup"><span data-stu-id="70fab-129">Remarks</span></span>

<span data-ttu-id="70fab-130">对于列表视图定义，必须至少指定一个类型、选择集或选择条件。</span><span class="sxs-lookup"><span data-stu-id="70fab-130">You must specify at least one type, selection set, or selection condition for a list view definition.</span></span> <span data-ttu-id="70fab-131">您可以使用的子元素数没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="70fab-131">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="70fab-132">选择条件用于定义要使用的定义必须存在的条件，例如当对象具有特定属性或特定属性值或脚本计算结果为 `true` 时。</span><span class="sxs-lookup"><span data-stu-id="70fab-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="70fab-133">有关选择条件的详细信息，请参阅为[数据显示定义条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="70fab-133">For more information about selection conditions, see [Defining Conditions for when Data is displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="70fab-134">有关列表视图组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="70fab-134">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="70fab-135">示例</span><span class="sxs-lookup"><span data-stu-id="70fab-135">Example</span></span>

<span data-ttu-id="70fab-136">下面的示例演示如何使用 .NET 类型名称定义列表视图的对象。</span><span class="sxs-lookup"><span data-stu-id="70fab-136">The following example shows how to define the objects for a list view using their .NET type name.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="70fab-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="70fab-137">See Also</span></span>

[<span data-ttu-id="70fab-138">ListControl 的 ListEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="70fab-138">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="70fab-139">ListControl 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="70fab-139">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="70fab-140">ListControl 的 EntrySelectedBy 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="70fab-140">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="70fab-141">ListControl 的 EntrySelectedBy 的 TypeName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="70fab-141">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="70fab-142">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="70fab-142">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="70fab-143">定义显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="70fab-143">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="70fab-144">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="70fab-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
