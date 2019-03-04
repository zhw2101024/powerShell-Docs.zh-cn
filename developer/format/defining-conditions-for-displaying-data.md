---
title: 定义用于显示数据的条件 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855643"
---
# <a name="defining-conditions-for-displaying-data"></a>定义用于显示数据的条件

在定义的视图或控件显示的数据时，可以指定要显示的数据必须存在的条件。 由特定的属性，或脚本时，可触发条件或属性值的计算结果为`true`。 当满足选择条件，则将使用视图或控件的定义。

## <a name="specifying-a-selection-condition-for-a-definition"></a>指定选择条件的定义

创建视图或控件的定义时`EntrySelectedBy`元素用于指定哪些对象将使用的定义或定义要使用哪种条件必须存在。 通过指定的条件`SelectionCondition`元素。

在以下示例中，选择条件指定的表视图的定义。 定义用于在此示例中，仅当指定的脚本的计算结果为`true`。

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <SelectionCondition>
      <ScriptBlock>ScriptToEvaluate</ScriptBlock>
    </SelectionCondition>
  </EntrySelectedBy>
  <TableColumnItems>
  </TableColumnItems>
</TableRowEntry>

```

可以为视图或控件的定义指定的选择条件数目没有限制。 唯一的要求如下所示：

- 选择条件必须指定一个属性名称或脚本来触发条件，但不能同时指定。

- 选择条件可以指定任意数量的.NET 类型，或者选择设置，但不能同时指定。

## <a name="specifying-a-selection-condition-for-an-item"></a>指定项的选择条件

此外可以指定当由列表视图或控件的项包括`ItemSelectionCondition`项定义中的元素。 在以下示例中，列表视图的项被指定选择条件。 在此示例中，仅当该脚本的计算结果为时使用了项`true`。

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

可以指定只有一个选择条件的项。 和条件必须指定一个属性名称或脚本来触发条件，但不能同时指定。

## <a name="xml-elements"></a>XML 元素

 以下 XML 元素用于创建所选内容的条件。

- 以下元素指定视图定义的选择条件：

    - [TableControl （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [ListControl （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [WideControl （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [CustomControl （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- 以下元素指定选择条件的常见和视图控件定义：

    - [配置 （格式） 的控件的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [视图 （格式） 的控件的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- 下面的元素指定扩展的集合对象的选择条件：

    - [EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- 下面的元素指定用于显示数据的新组选择条件：

    - [GroupBy （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- 下面的元素指定列表视图项选择条件：

    - [ItemSelectionCondition ListControl （格式） 的 ListItem 元素](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- 以下元素指定控件的项选择条件：

    - [配置 （格式） 的控件的 ExpressionBinding 的 ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [ExpressionBinding 的 Controls 的视图 （格式） 的 ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [CustomControl （格式） 的 ExpressionBinding 的 ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a>另请参阅

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
