---
title: 定义的选项集，|Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00dbb5ee-93d4-4914-a082-ef4d8b236b5c
caps.latest.revision: 16
ms.openlocfilehash: 596212f2e64401a751cf3dca0ee7d60b80912c00
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858923"
---
# <a name="defining-selection-sets"></a><span data-ttu-id="42e8d-102">定义选项集</span><span class="sxs-lookup"><span data-stu-id="42e8d-102">Defining Selection Sets</span></span>

<span data-ttu-id="42e8d-103">创建多个视图和控件时，可以为所选内容集定义引用的对象的集。</span><span class="sxs-lookup"><span data-stu-id="42e8d-103">When creating multiple views and controls, you can define sets of objects that are referred to as selection sets.</span></span> <span data-ttu-id="42e8d-104">所选内容集使你可以定义的对象一次，而无需为每个视图或控件重复定义。</span><span class="sxs-lookup"><span data-stu-id="42e8d-104">A selection set enables you to define the objects one time, without having to define them repeatedly for each view or control.</span></span> <span data-ttu-id="42e8d-105">通常情况下，有一组相关的.NET 对象时使用的选项集。</span><span class="sxs-lookup"><span data-stu-id="42e8d-105">Typically, selection sets are used when you have a set of related .NET objects.</span></span> <span data-ttu-id="42e8d-106">例如，`FileSystem`格式设置文件 (FileSystem.format.ps1xml) 定义一选择多个视图，使用文件系统类型。</span><span class="sxs-lookup"><span data-stu-id="42e8d-106">For example, The `FileSystem` formatting file (FileSystem.format.ps1xml) defines a selection set of the file system types that several views use.</span></span>

## <a name="where-selection-sets-are-defined-and-referenced"></a><span data-ttu-id="42e8d-107">所选内容集的定义和引用</span><span class="sxs-lookup"><span data-stu-id="42e8d-107">Where Selection Sets are Defined and Referenced</span></span>

<span data-ttu-id="42e8d-108">可由所有视图和格式设置文件中定义的控件的常见数据的一部分定义的选项集。</span><span class="sxs-lookup"><span data-stu-id="42e8d-108">You define selection sets as part of the common data that can be used by all the views and controls defined in the formatting file.</span></span> <span data-ttu-id="42e8d-109">下面的示例演示如何定义三个所选内容集。</span><span class="sxs-lookup"><span data-stu-id="42e8d-109">The following example shows how to define three selection sets.</span></span>

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

<span data-ttu-id="42e8d-110">您可以引用选择以下方式设置：</span><span class="sxs-lookup"><span data-stu-id="42e8d-110">You can reference a selection sets in the following ways:</span></span>

- <span data-ttu-id="42e8d-111">每个视图具有`ViewSelectedBy`元素，用于定义使用视图将显示哪些对象。</span><span class="sxs-lookup"><span data-stu-id="42e8d-111">Each view has a `ViewSelectedBy` element that defines which objects are displayed by using the view.</span></span> <span data-ttu-id="42e8d-112">`ViewSelectedBy`元素具有`SelectionSetName`指定选择的子元素设置的视图使用的所有定义。</span><span class="sxs-lookup"><span data-stu-id="42e8d-112">The `ViewSelectedBy` element has a `SelectionSetName` child element that specifies the selection set that all the definitions of the view use.</span></span> <span data-ttu-id="42e8d-113">选择集，可以从视图引用的数量没有限制。</span><span class="sxs-lookup"><span data-stu-id="42e8d-113">There is no restriction on the number of selection sets that you can reference from a view.</span></span>

- <span data-ttu-id="42e8d-114">中的视图或控件，每个定义`EntrySelectedBy`元素定义使用该定义将显示哪些对象。</span><span class="sxs-lookup"><span data-stu-id="42e8d-114">In each definition of a view or control, the `EntrySelectedBy` element defines which objects are displayed by using that definition.</span></span> <span data-ttu-id="42e8d-115">通常一个视图或控件具有只有一个定义以便对象由定义`ViewSelectedBy`元素。</span><span class="sxs-lookup"><span data-stu-id="42e8d-115">Typically a view or control has only one definition so the objects are defined by the `ViewSelectedBy` element.</span></span> <span data-ttu-id="42e8d-116">`EntrySelectedBy`定义的元素具有`SelectionSetName`指定所选内容集的子元素。</span><span class="sxs-lookup"><span data-stu-id="42e8d-116">The `EntrySelectedBy` element of the definition has a `SelectionSetName` child element that specifies the selection set.</span></span> <span data-ttu-id="42e8d-117">如果指定选项集的定义，您不能指定任何其他子元素的`EntrySelectedBy`元素。</span><span class="sxs-lookup"><span data-stu-id="42e8d-117">If you specify the selection set for a definition, you cannot specify any of the other child elements of the `EntrySelectedBy` element.</span></span>

- <span data-ttu-id="42e8d-118">中的视图或控件，每个定义`SelectionCondition`元素可用于指定当使用定义的条件。</span><span class="sxs-lookup"><span data-stu-id="42e8d-118">In each definition of a view or control, the `SelectionCondition` element can be used to specify a condition for when the definition is used.</span></span> <span data-ttu-id="42e8d-119">`SelectionCondition`元素具有`SelectionSetName`子元素，它指定所选内容设置触发条件。</span><span class="sxs-lookup"><span data-stu-id="42e8d-119">The `SelectionCondition` element has a `SelectionSetName` child element that specifies the selection set that triggers the condition.</span></span> <span data-ttu-id="42e8d-120">显示任何选定内容集中定义的对象时，会触发条件。</span><span class="sxs-lookup"><span data-stu-id="42e8d-120">The condition is triggered when any of the objects defined in the selection set are displayed.</span></span> <span data-ttu-id="42e8d-121">有关如何设置这些条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="42e8d-121">For more information about how to set these conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="selection-set-example"></a><span data-ttu-id="42e8d-122">选择设置示例</span><span class="sxs-lookup"><span data-stu-id="42e8d-122">Selection Set Example</span></span>

<span data-ttu-id="42e8d-123">下面的示例显示了示例直接摘自一选择组`FileSystem`格式设置提供的 Windows PowerShell 文件。</span><span class="sxs-lookup"><span data-stu-id="42e8d-123">The following example shows a selection set that is taken directly from the `FileSystem` formatting file provided by Windows PowerShell.</span></span> <span data-ttu-id="42e8d-124">有关其他 Windows PowerShell 格式设置文件的详细信息，请参阅[Windows PowerShell 格式设置文件](./powershell-formatting-files.md)。</span><span class="sxs-lookup"><span data-stu-id="42e8d-124">For more information about other Windows PowerShell formatting files, see [Windows PowerShell Formatting Files](./powershell-formatting-files.md).</span></span>

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

<span data-ttu-id="42e8d-125">上一个选择集的引用中`ViewSelectedBy`表视图中的元素。</span><span class="sxs-lookup"><span data-stu-id="42e8d-125">The previous selection set is referenced in the `ViewSelectedBy` element of a table view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>Files</Name>
    <ViewSelectedBy>
      <SelectionSetName>FileSystemTypes</SelectionSetName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="xml-elements"></a><span data-ttu-id="42e8d-126">XML 元素</span><span class="sxs-lookup"><span data-stu-id="42e8d-126">XML Elements</span></span>

 <span data-ttu-id="42e8d-127">可以定义的所选内容集的数量没有限制。</span><span class="sxs-lookup"><span data-stu-id="42e8d-127">There is no limit to the number of selection sets that you can define.</span></span> <span data-ttu-id="42e8d-128">以下 XML 元素用于创建选项集。</span><span class="sxs-lookup"><span data-stu-id="42e8d-128">The following XML elements are used to create a selection set.</span></span>

- <span data-ttu-id="42e8d-129">[SelectionSets](./selectionsets-element-format.md)元素定义的集的.NET 对象的引用的视图和控件的格式设置文件。</span><span class="sxs-lookup"><span data-stu-id="42e8d-129">The [SelectionSets](./selectionsets-element-format.md) element defines the sets of .NET objects that are referenced by the views and controls of the formatting file.</span></span>

- <span data-ttu-id="42e8d-130">[SelectionSet](./selectionset-element-format.md)元素定义一组.NET 对象。</span><span class="sxs-lookup"><span data-stu-id="42e8d-130">The [SelectionSet](./selectionset-element-format.md) element defines a single set of .NET objects.</span></span>

- <span data-ttu-id="42e8d-131">[名称](./name-element-for-selectionset-format.md)元素指定用于引用选项集的名称。</span><span class="sxs-lookup"><span data-stu-id="42e8d-131">The [Name](./name-element-for-selectionset-format.md) element specifies the name that is used to reference the selection set.</span></span>

- <span data-ttu-id="42e8d-132">[类型](./types-element-for-selectionset-format.md)元素指定的选项集的对象的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="42e8d-132">The [Types](./types-element-for-selectionset-format.md) element specifies the .NET types of the objects of the selection set.</span></span> <span data-ttu-id="42e8d-133">（在格式设置文件，对象是由指定它们的.NET 类型。）</span><span class="sxs-lookup"><span data-stu-id="42e8d-133">(Within formatting files, objects are specified by their .NET type.)</span></span>

 <span data-ttu-id="42e8d-134">以下 XML 元素用于指定所选内容集。</span><span class="sxs-lookup"><span data-stu-id="42e8d-134">The following XML elements are used to specify a selection set.</span></span>

- <span data-ttu-id="42e8d-135">下面的元素指定选项集以在视图的所有定义中使用：</span><span class="sxs-lookup"><span data-stu-id="42e8d-135">The following element specifies the selection set to use in all the definitions of the view:</span></span>

    - [<span data-ttu-id="42e8d-136">ViewSelectedBy （格式） 的 SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="42e8d-136">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

    - [<span data-ttu-id="42e8d-137">GroupBy （格式） 的 EntrySelectedBy SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="42e8d-137">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="42e8d-138">以下元素指定所使用的单一视图定义的选择集：</span><span class="sxs-lookup"><span data-stu-id="42e8d-138">The following elements specify the selection set used by a single view definition:</span></span>

    - [<span data-ttu-id="42e8d-139">ListControl （格式） 的 EntrySelectedBy SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="42e8d-139">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="42e8d-140">TableControl （格式） 的 EntrySelectedBy SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="42e8d-140">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="42e8d-141">WideControl （格式） 的 EntrySelectedBy SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="42e8d-141">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="42e8d-142">为视图 （格式） 的 CustomControl EntrySelectedBy SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="42e8d-142">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- <span data-ttu-id="42e8d-143">以下元素指定所使用的常见的选择集，并查看控件定义：</span><span class="sxs-lookup"><span data-stu-id="42e8d-143">The following elements specify the selection set used by common and view control definitions:</span></span>

    - [<span data-ttu-id="42e8d-144">视图 （格式） 的控件的 EntrySelectedBy SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="42e8d-144">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [<span data-ttu-id="42e8d-145">配置 （格式） 的控件的 EntrySelectedBy SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="42e8d-145">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- <span data-ttu-id="42e8d-146">以下元素指定定义要展开的对象时使用的选项集：</span><span class="sxs-lookup"><span data-stu-id="42e8d-146">The following elements specify the selection set used when you define which object to expand:</span></span>

    - [<span data-ttu-id="42e8d-147">EnumerableExpansion （格式） 的 EntrySelectedBy SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="42e8d-147">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="42e8d-148">以下元素指定所使用的选择条件的选择集。</span><span class="sxs-lookup"><span data-stu-id="42e8d-148">The following elements specify the selection set used by selection conditions.</span></span>

    - [<span data-ttu-id="42e8d-149">配置 （格式） 的控件的 SelectionCondition SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="42e8d-149">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="42e8d-150">视图 （格式） 的控件的 SelectionCondition SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="42e8d-150">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [<span data-ttu-id="42e8d-151">为视图 （格式） 的 CustomControl SelectionCondition SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="42e8d-151">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [<span data-ttu-id="42e8d-152">有关 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="42e8d-152">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [<span data-ttu-id="42e8d-153">有关 ListEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="42e8d-153">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [<span data-ttu-id="42e8d-154">TableControl （格式） 的 EntrySelectedBy 的 SelectionCondition SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="42e8d-154">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="42e8d-155">有关 WideEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="42e8d-155">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [<span data-ttu-id="42e8d-156">GroupBy （格式） 的 SelectionCondition SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="42e8d-156">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="42e8d-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="42e8d-157">See Also</span></span>

[<span data-ttu-id="42e8d-158">SelectionSets</span><span class="sxs-lookup"><span data-stu-id="42e8d-158">SelectionSets</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="42e8d-159">SelectionSet</span><span class="sxs-lookup"><span data-stu-id="42e8d-159">SelectionSet</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="42e8d-160">名称</span><span class="sxs-lookup"><span data-stu-id="42e8d-160">Name</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="42e8d-161">类型</span><span class="sxs-lookup"><span data-stu-id="42e8d-161">Types</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="42e8d-162">PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="42e8d-162">PowerShell Formatting Files</span></span>](./powershell-formatting-files.md)

[<span data-ttu-id="42e8d-163">定义何时显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="42e8d-163">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="42e8d-164">编写的 PowerShell 格式设置和文件类型</span><span class="sxs-lookup"><span data-stu-id="42e8d-164">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
