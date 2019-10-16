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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363896"
---
# <a name="defining-conditions-for-displaying-data"></a>定义用于显示数据的条件

定义视图或控件显示的数据时，您可以指定一个必须存在的条件，以便显示数据。 条件可由特定属性触发，或者在脚本或属性值的计算结果为 `true` 时触发。 如果满足选择条件，将使用视图或控件的定义。

## <a name="specifying-a-selection-condition-for-a-definition"></a>为定义指定选择条件

创建视图或控件的定义时，@no__t 的元素用于指定将使用定义的对象或必须存在的条件才能使用定义。 条件由 `SelectionCondition` 元素指定。

在下面的示例中，将为表视图的定义指定选择条件。 在此示例中，仅当指定的脚本计算为 `true` 时，才使用定义。

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

对于您可以为视图或控件的定义指定的选择条件数没有限制。 唯一的要求如下：

- 选择条件必须指定一个属性名称或脚本来触发条件，但不能同时指定两者。

- 选择条件可以指定任意数量的 .NET 类型或选择集，但是不能同时指定两者。

## <a name="specifying-a-selection-condition-for-an-item"></a>指定项的选择条件

你还可以通过在项定义中包含 `ItemSelectionCondition` 元素来指定何时使用列表视图或控件的项。 在下面的示例中，为列表视图的项指定了选择条件。 在此示例中，仅当将脚本计算为 `true` 时才使用此项。

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

只能为项指定一个选择条件。 条件必须指定一个属性名称或脚本来触发条件，但不能同时指定两者。

## <a name="xml-elements"></a>XML 元素

 以下 XML 元素用于创建选择条件。

- 以下元素指定了视图定义的选择条件：

    - [TableControl 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [ListControl 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [WideControl 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [CustomControl 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- 以下元素指定常用和视图控件定义的选择条件：

    - [用于配置的控件的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [用于视图的控件的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- 以下元素指定展开集合对象的选择条件：

    - [EnumerableExpansion 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- 以下元素指定用于显示新数据组的选择条件：

    - [GroupBy 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- 以下元素为列表视图指定项选择条件：

    - [ListControl 的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- 以下元素为控件指定项选择条件：

    - [用于配置的控件的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [用于视图的控件的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [CustomControl 的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a>另请参阅

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
