---
title: 格式化 XML 架构参考 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac6f7aaa-d0cc-4c7b-a341-85e736174579
caps.latest.revision: 21
ms.openlocfilehash: 437b3d6bb62fdd3a74f3392ec71df360c01a1974
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065778"
---
# <a name="format-schema-xml-reference"></a>格式架构 XML 参考

在本部分中的主题介绍使用格式化文件 （Format.ps1xml 文件） 的 XML 元素。 格式设置文件定义的.NET 对象的显示方式;它们不会更改对象本身。

## <a name="in-this-section"></a>本部分内容

[TableControl （格式） 的 TableColumnHeader 的对齐方式元素](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)定义如何显示列标题中的数据。

[TableControl （格式） 的 TableColumnItem 的对齐方式元素](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)定义如何显示行中的数据。

[TableControl （格式） 的自动调整大小元素](./autosize-element-for-tablecontrol-format.md)指定是否调整列大小和列数基于数据的大小。

[WideControl （格式） 的自动调整大小元素](./autosize-element-for-widecontrol-format.md)指定是否调整列大小和列数基于数据的大小。

[ColumnNumber WideControl （格式） 的元素](./columnnumber-element-for-widecontrol-format.md)指定宽视图中显示的列数。

[配置元素 （格式）](./configuration-element-format.md)表示的格式设置文件的顶级元素。

[控件的配置 （格式） 的控件元素](./control-element-for-controls-for-configuration-format.md)定义可由格式设置文件和名称，用于引用该控件的所有视图的公共控件。

[控件的视图 （格式） 的控件元素](./control-element-for-controls-for-view-format.md)定义的视图和用于引用该控件的名称可以使用的控件。

[控制配置 （格式） 的元素](./controls-element-for-configuration-format.md)定义可由格式设置文件的所有视图的公共控件。

[控制视图 （格式） 的元素](./controls-element-for-view-format.md)定义可由特定视图的视图控件。

[配置 （格式） 的控件的 CustomControl 元素](./customcontrol-element-for-control-for-controls-for-configuration-format.md)定义了一个控件。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

[控件的视图 （格式） 的控件的 CustomControl 元素](./customcontrol-element-for-control-for-controls-for-view-format.md)定义视图使用的控件。

[GroupBy （格式） 的 CustomControl 元素](./customcontrol-element-for-groupby-format.md)定义显示新组的自定义控件。

[CustomControl 元素 （格式）](./customcontrol-element-for-groupby-format.md)定义视图的自定义控件格式。

[配置 （格式） 的控件的 ExpressionBinding 的 CustomControlName 元素](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)指定公共控件的名称。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

[视图 （格式） 的控件的 ExpressionBindine CustomControlName 元素](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)指定公共控件或视图控件的名称。 定义一个视图，可以使用的控件时，将使用此元素。

[GroupBy （格式） 的 CustomControlName 元素](./customcontrolname-element-for-groupby-format.md)指定用来显示新组的自定义控件的名称。 定义表、 列表、 宽或自定义控件视图时，将使用此元素。

[配置 （格式） 的控件的 CustomControl CustomEntry 元素](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)提供了一个常用的控件的定义。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

[视图 （格式） 的控件的 CustomEntries CustomEntry 元素](./customentry-element-for-customentries-for-controls-for-view-format.md)提供控件的定义。 定义一个视图，可以使用的控件时，将使用此元素。

[视图 （格式） 的 CustomEntries CustomEntry 元素](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)提供的自定义控件视图的定义。

[GroupBy （格式） 的 CustomControl CustomEntry 元素](./customentry-element-for-customcontrol-for-groupby-format.md)提供控件的定义。 定义如何显示一组新对象时，将使用此元素。

[配置 （格式） 的 CustomControl CustomEntries 元素](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)提供了公共控件的定义。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

[视图 （格式） 的控件的 CustomControl CustomEntries 元素](./customentries-element-for-customcontrol-for-controls-for-view-format.md)为控件提供定义。 定义一个视图，可以使用的控件时，将使用此元素。

[GroupBy （格式） 的 CustomControl CustomEntries 元素](./customentries-element-for-customcontrol-for-groupby-format.md)为控件提供定义。 定义如何显示一组新对象时，将使用此元素。

[视图 （格式） 的 CustomControl CustomEntries 元素](./customentries-element-for-customcontrol-for-view-format.md)提供了自定义控件视图的定义。 自定义控件视图必须指定一个或多个定义。

[有关配置控件 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-controls-for-configuration-format.md)定义由控件显示的数据和显示方式。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

[视图 （格式） 的控件的 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-controls-for-view-format.md)定义由控件显示的数据和显示方式。 定义一个视图，可以使用的控件时，将使用此元素。

[视图 （格式） 的 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)定义由自定义控件视图中显示的数据和显示方式。 定义自定义控件视图时，将使用此元素。

[GroupBy （格式） 的 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-groupby-format.md)定义由自定义控件视图中显示的数据和显示方式。 定义如何显示一组新对象时，将使用此元素。

[DefaultSettings 元素 （格式）](./defaultsettings-element-format.md)定义将应用于的格式设置文件的所有视图的常见设置。 常用的设置包括显示错误，表定义如何将扩展集合，和的详细信息中的文本换行。

[DisplayError 元素 （格式）](./displayerror-element-format.md)指定出错时显示一段数据显示 #ERR 的字符串。

[配置 （格式） 的控件的 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)定义使用公共控件或要在使用此控件中必须存在的条件的定义的.NET 类型。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

[视图 （格式） 的控件的 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)定义使用此控件定义或要使用此定义中必须存在的条件的.NET 类型。 定义一个视图，可以使用的控件时，将使用此元素。

[视图 （格式） 的 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)定义使用此自定义项或要使用此项必须存在的条件的.NET 类型。

[EnumerableExpansion （格式） 的 EntrySelectedBy 元素](./entryselectedby-element-for-enumerableexpansion-format.md)定义使用此定义或要使用此定义中必须存在的条件的.NET 类型。

[GroupBy （格式） 的 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-groupby-format.md)定义使用此控件定义或要使用此定义中必须存在的条件的.NET 类型。 定义如何显示一组新对象时，将使用此元素。

[ListControl （格式） 的 ListEntry EntrySelectedBy 元素](./entryselectedby-element-for-listentry-for-listcontrol-format.md)定义使用此列表视图定义或要使用此定义中必须存在的条件的.NET 类型。 在大多数情况下只有一个定义列表视图的需要。 但是，如果你想要使用相同的列表视图来显示不同的对象的不同数据可以提供多个列表视图的定义。

[TableRowEntry （格式） 的 EntrySelectedBy 元素](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)定义其属性值显示的行中的.NET 类型。

[WideEntry （格式） 的 EntrySelectedBy 元素](./entryselectedby-element-for-wideentry-format.md)定义使用宽视图或必须存在要使用此定义的条件的此定义的.NET 类型。

[EnumerableExpansion 元素 （格式）](./enumerableexpansion-element-format.md)定义如何特定对象在视图中显示时进行扩展的.NET 集合。

[EnumerableExpansions 元素 （格式）](./enumerableexpansions-element-format.md)定义显示在视图中时如何展开.NET 集合对象。

[配置 （格式） 的控件的 ExpressionBinding 的 EnumerateCollection 元素](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)指定控件将显示个集合的元素。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

[ExpressionBinding 的 Controls 的视图 （格式） 的 EnumerateCollection 元素](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)指定显示的元素的集合。 定义一个视图，可以使用的控件时，将使用此元素。

[有关表达式绑定的视图 （格式） 的 CustomControl EnumerateCollection 元素](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)指定集合的元素的形式显示。 定义自定义控件视图时，将使用此元素。

[GroupBy （格式） 的 ExpressionBinding 的 EnumerateCollection 元素](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)指定集合的元素的形式显示。 定义如何显示一组新对象时，将使用此元素。

[展开元素 （格式）](./expand-element-format.md)指定如何为此定义扩展的集合对象。

[配置 （格式） 的控件的 CustomItem ExpressionBinding 元素](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)定义由控件显示的数据。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

[ExpressionBinding 元素视图 （格式） 的控件的 CustomItem](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)定义由控件显示的数据。 定义一个视图，可以使用的控件时，将使用此元素。

[ExpressionBinding 元素的视图 （格式） 的 CustomControl CustomItem](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)定义由控件显示的数据。 定义自定义控件视图时，将使用此元素。

[GroupBy （格式） 的 CustomItem ExpressionBinding 元素](./expressionbinding-element-for-customitem-for-groupby-format.md)定义由控件显示的数据。 定义如何显示一组新对象时，将使用此元素。

[配置 （格式） 的控件的帧的 FirstLineHanging 元素](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)指定向左移动数据的第一行的字符数。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

[框架的控件的视图 （格式） 的 FirstLineHanging 元素](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)指定向左移动数据的第一行的字符数。 定义一个视图，可以使用的控件时，将使用此元素。

[范围图 （格式） 的 CustomControl FirstLineHanging 元素](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)指定向左移动数据的第一行的字符数。 定义自定义控件视图时，将使用此元素。

[GroupBy （格式） 的帧的 FirstLineHanging 元素](./firstlinehanging-element-for-frame-for-groupby-format.md)指定向左移动数据的第一行的字符数。 定义如何显示一组新对象时，将使用此元素。

[配置 （格式） 的控件的帧的 FirstLineIndent 元素](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)指定向右移动数据的第一行的字符数。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

[框架的控件的视图 （格式） 的 FirstLineIndent 元素](./firstlineindent-element-for-frame-for-controls-for-view-format.md)指定向右移动数据的第一行的字符数。 定义一个视图，可以使用的控件时，将使用此元素。

[FirstLineIndent 元素](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)指定向右移动数据的第一行的字符数。 定义自定义控件视图时，将使用此元素。

[GroupBy （格式） 的帧的 FirstLineIndent 元素](./firstlineindent-element-for-frame-for-groupby-format.md)指定向右移动数据的第一行的字符数。 定义如何显示一组新对象时，将使用此元素。

[ListItem （格式） 的 FormatString 元素](./formatstring-element-for-listitem-for-listcontrol-format.md)指定格式模式，它定义如何显示的属性或脚本的值。

[TableColumnItem （格式） 的 FormatString 元素](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)指定格式模式，它定义如何显示表的属性或脚本值。

[FormatString 元素 WideControl （格式） 的 WideItem](./formatstring-element-for-wideitem-for-widecontrol-format.md)指定格式模式，它定义如何在视图中显示的属性或脚本的值。

[对 CustomItem 配置 （格式） 的控件的帧元素](./frame-element-for-customitem-for-controls-for-configuration-format.md)定义如何显示数据，如向左或向右移位数据。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

[对控件的视图 （格式） 的 CustomItem 的帧元素](./frame-element-for-customitem-for-controls-for-view-format.md)定义如何显示数据，如向左或向右移位数据。 定义一个视图，可以使用的控件时，将使用此元素。

[对 CustomItem 的帧元素的视图 （格式） 的 CustomControl](./frame-element-for-customitem-for-customcontrol-for-view-format.md)定义如何显示数据，如向左或向右移位数据。 定义自定义控件视图时，将使用此元素。

[对 GroupBy （格式） 的元素帧为 CustomItem](./frame-element-for-customitem-for-groupby-format.md)定义如何显示数据，如向左或向右移位数据。 定义如何显示一组新对象时，将使用此元素。

[视图 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)定义 Windows PowerShell 如何显示对象的新的组。

[HideTableHeaders 元素 （格式）](./hidetableheaders-element-format.md)指定表的标头，不会显示。

[配置 （格式） 的控件的 ExpressionBinding 的 ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)定义要在使用此控件中必须存在的条件。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

[ItemSelectionCondition 元素的视图 （格式） 的控件的 ExpressionBinding](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)定义要在使用此控件中必须存在的条件。 定义一个视图，可以使用的控件时，将使用此元素。

[有关表达式绑定的视图 （格式） 的 CustomControl ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)定义要在使用此控件中必须存在的条件。 可以为控件项指定的选择条件数目没有限制。 定义自定义控件视图时，将使用此元素。

[GroupBy （格式） 的 ExpressionBinding 的 ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)定义要在使用此控件中必须存在的条件。 可以为控件项指定的选择条件数目没有限制。 定义如何显示一组新对象时，将使用此元素。

[ListItem （格式） 的 ItemSelectionCondition 元素](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)定义必须存在要使用此列表项的条件。

[元素使用的 ListItem 标签为 ListControl(Format)](./label-element-for-listitem-for-listcontrol-format.md)行中指定的属性或脚本的值的标签。

[使用 GroupBy （格式） 的标签元素](./label-element-for-groupby-format.md)指定遇到新的组时显示的标签。

[使用 TableColumnHeader （格式） 的标签元素](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)定义显示在某一列顶部的标签。

[配置 （格式） 的控件的帧的 LeftIndent 元素](./leftindent-element-for-frame-for-controls-for-configuration-format.md)指定左边距远离数据向右移的字符数。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

[框架的控件的视图 （格式） 的 LeftIndent 元素](./leftindent-element-for-frame-for-controls-for-view-format.md)指定左边距远离数据向右移的字符数。 定义一个视图，可以使用的控件时，将使用此元素。

[范围图 （格式） 的 CustomControl LeftIndent 元素](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)指定左边距远离数据向右移的字符数。 定义自定义控件视图时，将使用此元素。

[GroupBy （格式） 的帧的 LeftIndent 元素](./leftindent-element-for-frame-for-groupby-format.md)指定左边距远离数据向右移的字符数。 定义如何显示一组新对象时，将使用此元素。

[ListControl 元素 （格式）](./listcontrol-element-format.md)定义视图的列表格式。

[ListEntry 元素 （格式）](./listentry-element-for-listcontrol-format.md)提供列表视图的定义。

[ListEntries 元素 （格式）](./listentries-element-for-listcontrol-format.md)定义如何显示列表视图的行。

[ListItem 元素 （格式）](./listitem-element-for-listitems-for-listcontrol-format.md)定义属性或其值显示在列表视图的行中的脚本。

[Listitem 元素 （格式）](./listitems-element-for-listentry-for-listcontrol-format.md)定义的属性和显示在列表视图中的脚本。

[配置 （格式） 的控件的控件的名称元素](./name-element-for-control-for-controls-for-configuration-format.md)指定控件的名称。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

[SelectionSet （格式） 的名称元素](./name-element-for-selectionset-format.md)指定用来引用所选内容集的名称。

[视图 （格式） 的名称元素](./name-element-for-view-format.md)指定用于标识该视图的名称。

[配置 （格式） 的控件的 CustomItem 的换行元素](./newline-element-for-customitem-for-controls-for-configuration-format.md)将空白行添加到控件的显示。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

[CustomItem 视图 （格式） 的控件的新行元素](./newline-element-for-customitem-for-controls-for-view-format.md)将空白行添加到控件的显示。 定义一个视图，可以使用的控件时，将使用此元素。

[换行元素的视图 （格式） 的 CustomControl CustomItem](./newline-element-for-customitem-for-customcontrol-for-view-format.md)将空白行添加到控件的显示。 定义自定义控件视图时，将使用此元素。

[GroupBy （格式） 的 CustomItem 的换行元素](./newline-element-for-customitem-for-groupby-format.md)将空白行添加到控件的显示。 定义如何显示一组新对象时，将使用此元素。

[ExpressionBinding 的配置 （格式） 的控件的属性名称元素](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)指定其值显示的一个常用的控件的.NET 属性。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

[ExpressionBinding 的视图 （格式） 的控件的属性名称元素](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)指定控件显示其值的.NET 属性。 定义一个视图，可以使用的控件时，将使用此元素。

[为视图 （格式） 的 CustomControl ExpressionBinding 的 PropertyName 元素](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)指定控件显示其值的.NET 属性。 定义自定义控件视图时使用此元素

[GroupBy （格式） 的 ExpressionBinding 的 PropertyName 元素](./propertyname-element-for-expressionbinding-for-groupby-format.md)指定控件显示其值的.NET 属性。 定义如何显示一组新对象时，将使用此元素。

[GroupBy （格式） 的属性名称元素](./propertyname-element-for-groupby-format.md)指定它的值发生更改时启动新的组的.NET 属性。

[ItemSeclectionCondition 配置 （格式） 的控件的属性名称元素](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)指定触发条件的.NET 属性。 存在此属性时或当计算结果为`true`、 满足该条件，并使用该控件。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

[ItemSelectionCondition 视图 （格式） 的控件的属性名称元素](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)指定触发条件的.NET 属性。 存在此属性时或当计算结果为`true`、 满足该条件，并使用该控件。 定义一个视图，可以使用的控件时，将使用此元素。

[有关视图的 CustomControl ItemSelectionCondition PropertyName 元素 (格式](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)指定触发条件的.NET 属性。 存在此属性时或当计算结果为`true`、 满足该条件，并使用该控件。 定义自定义控件视图时，将使用此元素。

[GroupBy （格式） 的 ItemSelectionCondition PropertyName 元素](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)指定触发条件的.NET 属性。 存在此属性时或当计算结果为`true`、 满足该条件，并使用该控件。 定义如何显示一组新对象时，将使用此元素。

[ListItem （格式） 的 ItemSelectionCondition PropertyName 元素](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)指定触发条件的.NET 属性。 存在此属性时或当计算结果为`true`、 满足该条件，以及使用该视图。 定义列表视图时，将使用此元素。

[PropertyName ListControl （格式） 的 ListItem 元素](./propertyname-element-for-listitem-for-listcontrol-format.md)指定其值显示在列表中的.NET 属性。

[有关 ListEntry （格式） 的 EntrySelectedBy SelectionCondition PropertyName 元素](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)指定触发条件的.NET 属性。 存在此属性时或当计算结果为`true`、 满足该条件，和使用的项。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

[SelectionCondition 视图 （格式） 的控件的属性名称元素](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)指定触发条件的.NET 属性。 存在此属性时或当计算结果为`true`、 满足该条件，和使用的项。 定义一个视图，可以使用的控件时，将使用此元素。

[PropertyName 元素的视图 （格式） 的 CustomControl SelectionCondition](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)指定触发条件的.NET 属性。 存在此属性时或当计算结果为`true`、 满足该条件，以及使用该定义。 定义自定义控件视图时，将使用此元素。

[有关 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition PropertyName 元素](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)指定触发条件的.NET 属性。 存在此属性时或当计算结果为`true`、 满足该条件，以及使用该定义。

[GroupBy （格式） 的 SelectionCondition PropertyName 元素](./propertyname-element-for-selectioncondition-for-groupby-format.md)指定触发条件的.NET 属性。 存在此属性时或当计算结果为`true`、 满足该条件，以及使用该定义。 定义如何显示一组新对象时，将使用此元素。

[有关 ListEntry （格式） 的 EntrySelectedBy SelectionCondition PropertyName 元素](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)指定触发条件的.NET 属性。 存在此属性时或当计算结果为`true`、 满足该条件，以及使用列表项。

[有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition PropertyName 元素](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)指定触发条件的.NET 属性。 存在此属性时或当计算结果为`true`、 满足该条件，以及使用的表项。

[有关 WideEntry （格式） 的 EntrySelectedBy SelectionCondition PropertyName 元素](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)指定触发条件的.NET 属性。 存在此属性时或当计算结果为`true`、 满足该条件，以及使用该定义。

[TableColumnItem （格式） 的属性名称元素](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)指定其值显示在一行的列中的属性。

[WideItem （格式） 的属性名称元素](./propertyname-element-for-wideitem-for-widecontrol-format.md)指定宽视图中显示其值的对象的属性。

[配置 （格式） 的控件的帧的 RightIndent 元素](./rightindent-element-for-frame-for-controls-for-configuration-format.md)指定数据向右移离开右边距的字符数。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

[框架的控件的视图 （格式） 的 RightIndent 元素](./rightindent-element-for-frame-for-controls-for-view-format.md)指定数据向右移离开右边距的字符数。 定义一个视图，可以使用的控件时，将使用此元素。

[RightIndent 元素](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)指定数据向右移离开右边距的字符数。 定义自定义控件视图时，将使用此元素。

[GroupBy （格式） 的帧的 RightIndent 元素](./rightindent-element-for-frame-for-groupby-format.md)指定数据向右移离开右边距的字符数。 定义如何显示一组新对象时，将使用此元素。

[ExpressionBinding 的 Controls 的配置 （格式） 的脚本块元素](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)指定其值显示的一个常用的控件的脚本。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

[ExpressionBinding 的 Controls 的视图 （格式） 的脚本块元素](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)指定控件显示其值的脚本。 定义一个视图，可以使用的控件时，将使用此元素。

[脚本块元素的视图 （格式） 的 CustomCustomControl ExpressionBinding](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)指定控件显示其值的脚本。 定义自定义控件视图时，将使用此元素。

[ExpressionBinding 的 GroupBy （格式） 的脚本块元素](./scriptblock-element-for-expressionbinding-for-groupby-format.md)指定控件显示其值的脚本。 定义如何显示一组新对象时，将使用此元素。

[GroupBy （格式） 的脚本块元素](./scriptblock-element-for-groupby-format.md)指定它的值发生更改时启动新的组的脚本。

[ItemSelectionCondition 的 Controls 的配置 （格式） 的脚本块元素](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)指定触发条件的脚本。 当此脚本的计算结果为`true`、 满足该条件，并使用该控件。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

[ItemSelectionCondition 的 Controls 的视图 （格式） 的脚本块元素](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)指定触发条件的脚本。 当此脚本的计算结果为`true`、 满足该条件，并使用该控件。 定义一个视图，可以使用的控件时，将使用此元素。

[脚本块元素的视图 （格式） 的 CustomControl ItemSelectionCondition](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)指定触发条件的脚本。 当此脚本的计算结果为`true`、 满足该条件，并使用该控件。 定义自定义控件视图时，将使用此元素。

[GroupBy （格式） 的 ItemSelectionCondition 的脚本块元素](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)指定触发条件的脚本。 当此脚本的计算结果为`true`、 满足该条件，并使用该控件。 定义如何显示一组新对象时，将使用此元素。

[ItemSelectionCondition 的 ListControl （格式） 的脚本块元素](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)指定触发条件的脚本。 当此脚本的计算结果为`true`、 满足该条件，以及使用列表项。 定义列表视图时，将使用此元素。

[ListItem （格式） 的脚本块元素](./scriptblock-element-for-listitem-for-listcontrol-format.md)指定其值显示在列表的行中的脚本。

[SelectionCondition 的 Controls 的配置 （格式） 的脚本块元素](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)指定触发条件的脚本。 当此脚本的计算结果为`true`、 满足该条件，以及使用该定义。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

[SelectionCondition 的 Controls 的视图 （格式） 的脚本块元素](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)指定触发条件的脚本。 当此脚本的计算结果为`true`、 满足该条件，以及使用该定义。 定义一个视图，可以使用的控件时，将使用此元素。

[脚本块元素的视图 （格式） 的 CustomControl SelectionCondition](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)指定触发条件的脚本。 当此脚本的计算结果为`true`、 满足该条件，以及使用该定义。 定义自定义控件视图时，将使用此元素。

[有关 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 的脚本块元素](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)指定触发条件的脚本。

[GroupBy （格式） 的 SelectionCondition 的脚本块元素](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)指定触发条件的脚本。 当此脚本的计算结果为`true`、 满足该条件，以及使用该定义。 定义如何显示一组新对象时，将使用此元素。

[有关 ListEntry （格式） 的 EntrySelectedBy SelectionCondition 的脚本块元素](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)指定触发条件的脚本。 当此脚本的计算结果为`true`、 满足该条件，以及使用列表项。

[有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 的脚本块元素](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)指定触发条件的脚本块。 当此脚本的计算结果为`true`、 满足该条件，以及使用的表项。

[有关 WideEntry （格式） 的 EntrySelectedBy SelectionCondition 的脚本块元素](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)指定触发条件的脚本。 当此脚本的计算结果为`true`、 满足该条件，以及使用宽的项定义。

[TableColumnItem （格式） 的脚本块元素](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)指定其值显示在一行的列中的脚本。

[WideItem （格式） 的脚本块元素](./scriptblock-element-for-wideitem-for-widecontrol-format.md)指定其值宽视图中显示的脚本。

[SelectionCondition 元素的配置 （格式） 的 CustomEntry EntrySelectedBy](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)定义必须存在要使用的常见控件定义的条件。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

[视图 （格式） 的控件的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)定义必须存在要使用的控件定义的条件。 定义一个视图，可以使用的控件时，将使用此元素。

[为视图 （格式） 的 CustomControl EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)定义必须存在要使用的控件定义的条件。 定义自定义控件视图时，将使用此元素。

[EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)定义要展开此定义的集合对象必须存在的条件。

[GroupBy （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)定义必须存在要使用的控件定义的条件。 定义如何显示一组新对象时，将使用此元素。

[ListEntry （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)定义要使用此列表视图的定义必须存在的条件。 可以为列表定义指定的选择条件数目没有限制。

[TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)定义必须存在要用于此定义的表视图的条件。 可以为表定义指定的选择条件数目没有限制。

[WideEntry （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)定义必须存在要使用此定义的条件。 可以为宽的项定义中指定的选择条件数目没有限制。

[SelectionSet 元素 （格式）](./selectionset-element-format.md)定义一组的集的名称，可以引用.NET 对象。

[配置 （格式） 的控件的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)指定一组使用控件的此定义的.NET 类型。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

[视图 （格式） 的控件的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)指定一组使用控件的此定义的.NET 类型。 定义一个视图，可以使用的控件时，将使用此元素。

[CustomEntry （格式） 的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)指定一组.NET 对象列表项。 可以为一个条目指定的所选内容集的数量没有限制。

[EnumerableExpansion （格式） 的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)指定的.NET 类型的情况下此定义展开组。

[GroupBy （格式） 的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)指定一组.NET 对象列表项。 可以为一个条目指定的所选内容集的数量没有限制。 定义如何显示一组新对象时，将使用此元素。

[ListEntry （格式） 的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)指定一组.NET 对象列表项。 可以为一个条目指定的所选内容集的数量没有限制。

[TableRowEntry （格式） 的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)指定一组.NET 类型使用此项的表视图。 可以为一个条目指定的所选内容集的数量没有限制。

[WideEntry （格式） 的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)指定一组定义的.NET 对象。 定义用于显示这些对象之一时。

[配置 （格式） 的控件的 SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)指定的.NET 类型的触发器条件集。 当存在任何此集中的类型时，满足该条件，并使用此控件显示该对象。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

[视图 （格式） 的控件的 SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)指定的.NET 类型的触发器条件集。 当存在任何此集中的类型时，满足条件，并且使用此控件显示该对象。 定义一个视图，可以使用的控件时，将使用此元素。

[视图 （格式） 的 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)指定的.NET 类型的触发器条件集。 当存在任何此集中的类型时，满足条件，并且使用此控件显示该对象。 定义自定义控件视图时，将使用此元素。

[有关 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)指定的.NET 类型的触发器条件集。 当存在任何此集中的类型时，是满足的条件。

[GroupBy （格式） 的 SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)指定的.NET 类型的触发器条件集。 当存在任何此集中的类型时，满足该条件，并使用此控件显示该对象。 定义如何显示一组新对象时，将使用此元素。

[有关 ListEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)指定的.NET 类型的触发器条件集。 当存在任何此集中的类型时，满足该条件，并通过使用此定义列表视图显示该对象。

[有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)指定的.NET 类型的触发器条件集。 当存在任何此集中的类型时，满足该条件，并通过使用此定义的表视图中显示该对象。

[有关 WideEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)指定的.NET 类型的触发器条件集。 当存在任何此集中的类型时，满足该条件，并通过使用此定义宽视图显示该对象。

[ViewSelectedBy （格式） 的 SelectionSetName 元素](./selectionsetname-element-for-viewselectedby-format.md)指定一组.NET 对象所显示的视图。

[SelectionSets 元素 （格式）](./selectionsets-element-format.md)定义可由单个格式视图的.NET 对象的集。

[ShowError 元素 （格式）](./showerror-element-format.md)指定在出错时显示一段数据时，显示完整的错误记录。

[TableControl （格式） 的 TableHeaders TableColumnHeader 元素](./tablecolumnheader-element-format.md)定义标签的列的宽度和表的列标签的对齐方式。

[TableColumnItem 元素 （格式）](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)定义属性或其值显示在一行的列中的脚本。

[TableColumnItems 元素 （格式）](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)定义的属性或其值显示的行中的脚本。

[TableControl 元素 （格式）](./tablecontrol-element-format.md)定义视图的表格式。

[TableHeaders 元素 （格式）](./tableheaders-element-format.md)定义表的列的标头。

[TableRowEntries 元素 （格式）](./tablerowentries-element-for-tablecontrol-format.md)定义的表的行。

[TableRowEntry 元素 （格式）](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)定义的表的行中显示的数据。

[文本元素用于配置 （格式） 的控件的 CustomItem](./text-element-for-customitem-for-controls-for-configuration-format.md)添加到控件，如标签，显示的数据的指定文本方括号括起的数据和数据的缩进。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

[CustomItem 视图 （格式） 的控件的文本元素](./text-element-for-customitem-for-controls-for-view-format.md)添加到控件，如标签，显示的数据的指定文本方括号括起的数据和数据的缩进。 定义一个视图，可以使用的控件时，将使用此元素。

[CustomItem （格式） 的文本元素](./text-element-for-customitem-for-customview-for-view-format.md)添加到控件，如标签，显示的数据的指定文本方括号括起的数据和数据的缩进。 定义自定义控件视图时，将使用此元素。

[文本元素用于为 GroupBy （格式） 的 CustomItem](./text-element-for-customitem-for-groupby-format.md)添加到控件，如标签，显示的数据的指定文本方括号括起的数据和数据的缩进。 定义如何显示一组新对象时，将使用此元素。

[配置 （格式） 的控件的 EntrySelectedBy 的 TypeName 元素](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)指定将使用该控件的此定义的.NET 类型。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

[EntrySelectedBy 视图 （格式） 的控件的类型名称元素](./typename-element-for-entryselectedby-for-controls-for-view-format.md)指定将使用该控件的此定义的.NET 类型。 定义一个视图，可以使用的控件时，将使用此元素。

[TypeName 元素的视图 （格式） 的 CustomEntry EntrySelectedBy](./typename-element-for-entryselectedby-for-customentry-for-view-format.md)指定使用此视图定义的自定义控件的.NET 类型。 可以为定义指定的类型的数量没有限制。

[TypeName 元素 EnumerableExpansion （格式） 的 EntrySelectedBy](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)指定通过此定义扩展的.NET 类型。 定义默认设置时，将使用此元素。

[GroupBy （格式） 的 EntrySelectedBy 的 TypeName 元素](./typename-element-for-entryselectedby-for-groupby-format.md)指定使用自定义控件的此定义的.NET 类型。 定义如何显示一组新对象时，将使用此元素。

[TypeName 元素 ListControl （格式） 的 EntrySelectedBy](./typename-element-for-entryselectedby-for-listcontrol-format.md)指定使用此项的列表视图中的.NET 类型。 可以指定列表项的类型的数量没有限制。

[TypeName 元素 TableRowEntry （格式） 的 EntrySelectedBy](./typename-element-for-entryselectedby-for-tablecontrol-format.md)指定.NET 类型使用此项的表视图。 可以为表条目指定的类型的数量没有限制。

[TypeName 元素 WideEntry （格式） 的 EntrySelectedBy](./typename-element-for-entryselectedby-for-wideentry-format.md)指定定义的.NET 类型。 定义用于显示此对象时。

[配置 （格式） 的控件的 SelectionCondition 的 TypeName 元素](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)指定触发条件的.NET 类型。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

[SelectionCondition 视图 （格式） 的控件的类型名称元素](./typename-element-for-selectioncondition-for-controls-for-view-format.md)指定触发条件的.NET 类型。 定义一个视图，可以使用的控件时，将使用此元素。

[TypeName 元素的视图 （格式） 的 CustomControl SelectionCondition](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)指定触发条件的.NET 类型。 定义自定义控件视图时，将使用此元素。

[有关 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 的 TypeName 元素](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)指定触发条件的.NET 类型。

[GroupBy （格式） 的 SelectionCondition 的 TypeName 元素](./typename-element-for-selectioncondition-for-groupby-format.md)指定触发条件的.NET 类型。 定义如何显示一组新对象时，将使用此元素。

[有关 ListControl （格式） 的 EntrySelectedBy SelectionCondition 的 TypeName 元素](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)指定触发条件的.NET 类型。 当存在此类型时，才使用列表项。

[有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 的 TypeName 元素](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)指定触发条件的.NET 类型。 当存在此类型时，满足该条件，并使用表行。

[有关 WideEntry （格式） 的 EntrySelectedBy SelectionCondition 的 TypeName 元素](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)指定触发条件的.NET 类型。 当存在此类型时，使用该定义。

[类型 （格式） 的类型名称元素](./typename-element-for-types-format.md)指定属于所选内容集的对象的.NET 类型。

[ViewSelectedBy （格式） 的类型名称元素](./typename-element-for-viewselectedby-format.md)指定视图显示一个.NET 对象。

[类型元素 （格式）](./types-element-for-selectionset-format.md)定义集内所选内容的.NET 对象。

[查看元素 （格式）](./view-element-format.md)定义用于显示一个或多个.NET 对象的视图。

[ViewDefinitions 元素 （格式）](./viewdefinitions-element-format.md)定义用来显示对象的视图。

[ViewSelectedBy 元素 （格式）](./viewselectedby-element-format.md)定义视图所显示的.NET 对象。

[WideControl 元素 （格式）](./widecontrol-element-format.md)定义范围内 （单个值） 列表的视图的格式。 此视图显示单个属性值或为每个对象的脚本值。

[WideEntries 元素 （格式）](./wideentries-element-for-widecontrol-format.md)提供了宽的视图的定义。 宽的视图必须指定一个或多个定义。

[WideEntry 元素 （格式）](./wideentry-element-for-widecontrol-format.md)提供了宽的视图的定义。

[WideItem 元素 （格式）](./wideitem-element-for-widecontrol-format.md)定义属性或其值显示的脚本。

[Width 元素 （格式）](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)定义列的宽度 （以字符为单位）。

[包装元素 （格式）](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)指定在下一行显示超过列宽的文本。

[WrapTables 元素 （格式）](./wraptables-element-format.md)指定的表单元中的数据移动到下一行数据是否超过了列的宽度。

## <a name="see-also"></a>另请参阅

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
