---
title: 定义选择集 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00dbb5ee-93d4-4914-a082-ef4d8b236b5c
caps.latest.revision: 16
ms.openlocfilehash: 596212f2e64401a751cf3dca0ee7d60b80912c00
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368846"
---
# <a name="defining-selection-sets"></a>定义选项集

在创建多个视图和控件时，可以定义称为选择集的对象集。 通过选择集，您可以一次性定义对象，而无需为每个视图或控件重复定义对象。 通常，当您有一组相关的 .NET 对象时，将使用选择集。 例如，`FileSystem` 格式设置文件（types.ps1xml）定义了多个视图使用的一组文件系统类型。

## <a name="where-selection-sets-are-defined-and-referenced"></a>定义和引用选择集的位置

将选择集定义为可由格式设置文件中定义的所有视图和控件使用的通用数据的一部分。 下面的示例演示如何定义三个选择集。

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

可以通过以下方式引用选项集：

- 每个视图都有一个 `ViewSelectedBy` 元素，该元素定义使用视图显示的对象。 @No__t-0 元素具有一个 @no__t 子元素，该元素指定视图的所有定义所使用的选择集。 对于可以从视图引用的选择集的数量没有限制。

- 在视图或控件的每个定义中，`EntrySelectedBy` 元素定义使用该定义显示的对象。 通常，视图或控件只有一个定义，因此这些对象由 `ViewSelectedBy` 元素定义。 定义的 `EntrySelectedBy` 元素具有指定选择集的 @no__t 1 子元素。 如果为定义指定选择集，则不能指定 `EntrySelectedBy` 元素的任何其他子元素。

- 在视图或控件的每个定义中，`SelectionCondition` 元素可用于指定使用定义的条件。 @No__t-0 元素具有一个 @no__t 子元素，该元素指定触发条件的选择集。 当显示选择集中定义的任何对象时，将触发该条件。 有关如何设置这些条件的详细信息，请参阅为[数据显示定义条件](./defining-conditions-for-displaying-data.md)。

## <a name="selection-set-example"></a>选择集示例

以下示例显示了直接从 Windows PowerShell 提供的 `FileSystem` 格式设置文件中获取的选项集。 有关其他 Windows PowerShell 格式设置文件的详细信息，请参阅[Windows Powershell 格式设置文件](./powershell-formatting-files.md)。

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

在表视图的 `ViewSelectedBy` 元素中引用了上一选择集。

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

## <a name="xml-elements"></a>XML 元素

 您可以定义的选项集数没有限制。 以下 XML 元素用于创建选择集。

- [SelectionSets](./selectionsets-element-format.md)元素定义格式设置文件的视图和控件引用的 .net 对象集。

- [SelectionSet](./selectionset-element-format.md)元素定义一组 .net 对象。

- [Name](./name-element-for-selectionset-format.md)元素指定用于引用选项集的名称。

- [类型](./types-element-for-selectionset-format.md)元素指定选择集的对象的 .net 类型。 （在格式设置文件中，对象由其 .NET 类型指定。）

 以下 XML 元素用于指定选择集。

- 以下元素指定要在视图的所有定义中使用的选择集：

    - [ViewSelectedBy 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-viewselectedby-format.md)

    - [GroupBy 的 EntrySelectedBy 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- 以下元素指定单个视图定义使用的选择集：

    - [ListControl 的 EntrySelectedBy 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [TableControl 的 EntrySelectedBy 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [WideControl 的 EntrySelectedBy 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [用于 View 的 CustomControl 的 EntrySelectedBy 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- 以下元素指定 common 和 view 控件定义所使用的选择集：

    - [用于视图的控件的 EntrySelectedBy 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [用于配置的控件的 EntrySelectedBy 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- 以下元素指定在定义要扩展的对象时所使用的选择集：

    - [EnumerableExpansion 的 EntrySelectedBy 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- 以下元素指定选择条件使用的选择集。

    - [用于配置的控件的 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [用于视图的控件的 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [用于 View 的 CustomControl 的 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [EnumerableExpansion 的 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素（Format）](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [ListEntry 的 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素（Format）](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [TableControl 的 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素（Format）](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [WideEntry 的 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素（Format）](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [GroupBy 的 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a>另请参阅

[SelectionSets](./selectionsets-element-format.md)

[SelectionSet](./selectionset-element-format.md)

[Name](./name-element-for-selectionset-format.md)

[各种](./types-element-for-selectionset-format.md)

[PowerShell 格式化文件](./powershell-formatting-files.md)

[定义显示数据的条件](./defining-conditions-for-displaying-data.md)

[编写 PowerShell 格式设置和类型文件](./writing-a-powershell-formatting-file.md)
