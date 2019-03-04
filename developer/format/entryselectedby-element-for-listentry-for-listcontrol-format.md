---
title: ListControl （格式） 的 ListEntry EntrySelectedBy 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 723619e67612b859d0acbab37eecd82141adf923
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854943"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="bdbf7-102">EntrySelectedBy Element for ListEntry for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="bdbf7-102">EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="bdbf7-103">定义使用此列表视图定义的.NET 类型或要使用此定义中必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="bdbf7-103">Defines the .NET types that use this list view definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="bdbf7-104">在大多数情况下只有一个定义列表视图的需要。</span><span class="sxs-lookup"><span data-stu-id="bdbf7-104">In most cases only one definition is needed for a list view.</span></span> <span data-ttu-id="bdbf7-105">但是，如果你想要使用相同的列表视图来显示不同的对象的不同数据可以提供多个列表视图的定义。</span><span class="sxs-lookup"><span data-stu-id="bdbf7-105">However, you can provide multiple definitions for the list view if you want to use the same list view to display different data for different objects.</span></span>

<span data-ttu-id="bdbf7-106">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素 ListControl （格式） EntrySelectedBy 元素 ListEntry ListControl （格式） ListEntry 元素ListEntry 的 ListControl （格式）</span><span class="sxs-lookup"><span data-stu-id="bdbf7-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntry for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bdbf7-107">语法</span><span class="sxs-lookup"><span data-stu-id="bdbf7-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bdbf7-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="bdbf7-108">Attributes and Elements</span></span>

<span data-ttu-id="bdbf7-109">以下各节描述了特性、 子元素和父元素的`EntrySelectedBy`元素。</span><span class="sxs-lookup"><span data-stu-id="bdbf7-109">The following sections describe the attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bdbf7-110">特性</span><span class="sxs-lookup"><span data-stu-id="bdbf7-110">Attributes</span></span>

<span data-ttu-id="bdbf7-111">无。</span><span class="sxs-lookup"><span data-stu-id="bdbf7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bdbf7-112">子元素</span><span class="sxs-lookup"><span data-stu-id="bdbf7-112">Child Elements</span></span>

|<span data-ttu-id="bdbf7-113">元素</span><span class="sxs-lookup"><span data-stu-id="bdbf7-113">Element</span></span>|<span data-ttu-id="bdbf7-114">描述</span><span class="sxs-lookup"><span data-stu-id="bdbf7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bdbf7-115">ListControl （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="bdbf7-115">SelectionCondition Element for EntrySelectedBy for ListControl  (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="bdbf7-116">可选元素。</span><span class="sxs-lookup"><span data-stu-id="bdbf7-116">Optional element.</span></span><br /><br /> <span data-ttu-id="bdbf7-117">定义必须存在要使用此列表视图定义的条件。</span><span class="sxs-lookup"><span data-stu-id="bdbf7-117">Defines the condition that must exist for this list view definition to be used.</span></span>|
|[<span data-ttu-id="bdbf7-118">ListControl （格式） 的 EnrtySelectedBy SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="bdbf7-118">SelectionSetName Element for EnrtySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="bdbf7-119">可选元素。</span><span class="sxs-lookup"><span data-stu-id="bdbf7-119">Optional element.</span></span><br /><br /> <span data-ttu-id="bdbf7-120">指定一组使用此列表视图定义的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="bdbf7-120">Specifies a set of .NET types that use this list view definition.</span></span>|
|[<span data-ttu-id="bdbf7-121">ListControl （格式） 的 EntrySelectedBy 的 TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="bdbf7-121">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="bdbf7-122">可选元素。</span><span class="sxs-lookup"><span data-stu-id="bdbf7-122">Optional element.</span></span><br /><br /> <span data-ttu-id="bdbf7-123">指定将使用此列表视图定义的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="bdbf7-123">Specifies a .NET type that uses this list view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bdbf7-124">父元素</span><span class="sxs-lookup"><span data-stu-id="bdbf7-124">Parent Elements</span></span>

|<span data-ttu-id="bdbf7-125">元素</span><span class="sxs-lookup"><span data-stu-id="bdbf7-125">Element</span></span>|<span data-ttu-id="bdbf7-126">描述</span><span class="sxs-lookup"><span data-stu-id="bdbf7-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bdbf7-127">ListControl （格式） 的 ListEntry 元素</span><span class="sxs-lookup"><span data-stu-id="bdbf7-127">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="bdbf7-128">定义列表的行的显示方式。</span><span class="sxs-lookup"><span data-stu-id="bdbf7-128">Defines how the rows of the list are displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bdbf7-129">备注</span><span class="sxs-lookup"><span data-stu-id="bdbf7-129">Remarks</span></span>

<span data-ttu-id="bdbf7-130">必须指定至少一个类型、 选择集或选择列表视图定义的条件。</span><span class="sxs-lookup"><span data-stu-id="bdbf7-130">You must specify at least one type, selection set, or selection condition for a list view definition.</span></span> <span data-ttu-id="bdbf7-131">可以使用的子元素的数目没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="bdbf7-131">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="bdbf7-132">使用选择条件来定义要使用，例如当一个对象具有特定属性的定义中必须存在一个条件或特定属性值或脚本的计算结果为`true`。</span><span class="sxs-lookup"><span data-stu-id="bdbf7-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="bdbf7-133">有关选择条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="bdbf7-133">For more information about selection conditions, see [Defining Conditions for when Data is displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="bdbf7-134">列表视图的组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="bdbf7-134">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="bdbf7-135">示例</span><span class="sxs-lookup"><span data-stu-id="bdbf7-135">Example</span></span>

<span data-ttu-id="bdbf7-136">下面的示例演示如何定义使用其.NET 类型名称的列表视图的对象。</span><span class="sxs-lookup"><span data-stu-id="bdbf7-136">The following example shows how to define the objects for a list view using their .NET type name.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="bdbf7-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bdbf7-137">See Also</span></span>

[<span data-ttu-id="bdbf7-138">ListControl （格式） 的 ListEntry 元素</span><span class="sxs-lookup"><span data-stu-id="bdbf7-138">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="bdbf7-139">ListControl （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="bdbf7-139">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="bdbf7-140">ListControl （格式） 的 EnrtySelectedBy SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="bdbf7-140">SelectionSetName Element for EnrtySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="bdbf7-141">ListControl （格式） 的 EntrySelectedBy 的 TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="bdbf7-141">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="bdbf7-142">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="bdbf7-142">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="bdbf7-143">定义何时显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="bdbf7-143">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="bdbf7-144">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="bdbf7-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)