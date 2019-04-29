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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066305"
---
# <a name="defining-selection-sets"></a>定义选项集

创建多个视图和控件时，可以为所选内容集定义引用的对象的集。 所选内容集使你可以定义的对象一次，而无需为每个视图或控件重复定义。 通常情况下，有一组相关的.NET 对象时使用的选项集。 例如，`FileSystem`格式设置文件 (FileSystem.format.ps1xml) 定义一选择多个视图，使用文件系统类型。

## <a name="where-selection-sets-are-defined-and-referenced"></a>所选内容集的定义和引用

可由所有视图和格式设置文件中定义的控件的常见数据的一部分定义的选项集。 下面的示例演示如何定义三个所选内容集。

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

您可以引用选择以下方式设置：

- 每个视图具有`ViewSelectedBy`元素，用于定义使用视图将显示哪些对象。 `ViewSelectedBy`元素具有`SelectionSetName`指定选择的子元素设置的视图使用的所有定义。 选择集，可以从视图引用的数量没有限制。

- 中的视图或控件，每个定义`EntrySelectedBy`元素定义使用该定义将显示哪些对象。 通常一个视图或控件具有只有一个定义以便对象由定义`ViewSelectedBy`元素。 `EntrySelectedBy`定义的元素具有`SelectionSetName`指定所选内容集的子元素。 如果指定选项集的定义，您不能指定任何其他子元素的`EntrySelectedBy`元素。

- 中的视图或控件，每个定义`SelectionCondition`元素可用于指定当使用定义的条件。 `SelectionCondition`元素具有`SelectionSetName`子元素，它指定所选内容设置触发条件。 显示任何选定内容集中定义的对象时，会触发条件。 有关如何设置这些条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。

## <a name="selection-set-example"></a>选择设置示例

下面的示例显示了示例直接摘自一选择组`FileSystem`格式设置提供的 Windows PowerShell 文件。 有关其他 Windows PowerShell 格式设置文件的详细信息，请参阅[Windows PowerShell 格式设置文件](./powershell-formatting-files.md)。

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

上一个选择集的引用中`ViewSelectedBy`表视图中的元素。

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

 可以定义的所选内容集的数量没有限制。 以下 XML 元素用于创建选项集。

- [SelectionSets](./selectionsets-element-format.md)元素定义的集的.NET 对象的引用的视图和控件的格式设置文件。

- [SelectionSet](./selectionset-element-format.md)元素定义一组.NET 对象。

- [名称](./name-element-for-selectionset-format.md)元素指定用于引用选项集的名称。

- [类型](./types-element-for-selectionset-format.md)元素指定的选项集的对象的.NET 类型。 （在格式设置文件，对象是由指定它们的.NET 类型。）

 以下 XML 元素用于指定所选内容集。

- 下面的元素指定选项集以在视图的所有定义中使用：

    - [ViewSelectedBy （格式） 的 SelectionSetName 元素](./selectionsetname-element-for-viewselectedby-format.md)

    - [GroupBy （格式） 的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- 以下元素指定所使用的单一视图定义的选择集：

    - [ListControl （格式） 的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [TableControl （格式） 的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [WideControl （格式） 的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [为视图 （格式） 的 CustomControl EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- 以下元素指定所使用的常见的选择集，并查看控件定义：

    - [视图 （格式） 的控件的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [配置 （格式） 的控件的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- 以下元素指定定义要展开的对象时使用的选项集：

    - [EnumerableExpansion （格式） 的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- 以下元素指定所使用的选择条件的选择集。

    - [配置 （格式） 的控件的 SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [视图 （格式） 的控件的 SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [为视图 （格式） 的 CustomControl SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [有关 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [有关 ListEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [TableControl （格式） 的 EntrySelectedBy 的 SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [有关 WideEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [GroupBy （格式） 的 SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a>另请参阅

[SelectionSets](./selectionsets-element-format.md)

[SelectionSet](./selectionset-element-format.md)

[Name](./name-element-for-selectionset-format.md)

[类型](./types-element-for-selectionset-format.md)

[PowerShell 格式设置文件](./powershell-formatting-files.md)

[定义何时显示数据的条件](./defining-conditions-for-displaying-data.md)

[编写的 PowerShell 格式设置和文件类型](./writing-a-powershell-formatting-file.md)
