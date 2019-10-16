---
title: TableControl （Format）的 EntrySelectedBy 的 SelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 912f3e63-e4d5-41ce-8710-6dfd8c885dc2
caps.latest.revision: 12
ms.openlocfilehash: 2faca6021dc26878869bdd2d35bc4ffc64d0fe7b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368386"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a>SelectionCondition Element for EntrySelectedBy for TableControl (Format)

定义必须存在才能用于此表视图定义的条件。 对于可为表定义指定的选择条件数没有限制。

用于 EntrySelectedBy 的配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） TableControl 元素（格式） TableRowEntries 元素（格式） TableRowEntry 元素（format） TableRowEntry 元素（格式）TableRowEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）

## <a name="syntax"></a>语法

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 SelectionCondition 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableRowEntry 的 SelectionCondition for EntrySelectedBy 的 PropertyName 元素（Format）](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|可选元素。<br /><br /> 指定触发条件的 .NET 属性。|
|[TableRowEntry 的 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|可选元素。<br /><br /> 指定触发条件的脚本。|
|[TableRowEntry 的 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素（Format）](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|可选元素。<br /><br /> 指定触发条件的 .NET 类型集。|
|[TableRowEntry 的 SelectionCondition for EntrySelectedBy 的 TypeName 元素（Format）](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|可选元素。<br /><br /> 指定触发条件的 .NET 类型。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableRowEntry 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|定义使用此表项的 .NET 类型或此项要使用的条件。|

## <a name="remarks"></a>备注

每个列表项必须至少定义一个类型名称、选择集或选择条件。

定义选择条件时，需要满足以下要求：

- 选择条件必须指定至少一个属性名称或脚本块，但不能同时指定两者。

- 选择条件可以指定任意数量的 .NET 类型或选择集，但是不能同时指定两者。

有关如何使用选择条件的详细信息，请参阅[定义使用视图条目或项的条件](./defining-conditions-for-displaying-data.md)。

有关表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。

## <a name="see-also"></a>另请参阅

[创建表视图](./creating-a-table-view.md)

[定义显示数据的条件](./defining-conditions-for-displaying-data.md)

[EntrySelectedBy 元素（格式）](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[TableRowEntry 的 SelectionCondition for EntrySelectedBy 的 PropertyName 元素（Format）](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[TableRowEntry 的 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[TableRowEntry 的 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素（Format）](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[TableRowEntry 的 SelectionCondition for EntrySelectedBy 的 TypeName 元素（Format）](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[编写 Windows PowerShell 格式设置和类型文件](./writing-a-powershell-formatting-file.md)
