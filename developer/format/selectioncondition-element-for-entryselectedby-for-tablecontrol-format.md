---
title: TableControl （格式） 的 EntrySelectedBy SelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 912f3e63-e4d5-41ce-8710-6dfd8c885dc2
caps.latest.revision: 12
ms.openlocfilehash: 2faca6021dc26878869bdd2d35bc4ffc64d0fe7b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861233"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a>SelectionCondition Element for EntrySelectedBy for TableControl (Format)

定义必须存在要用于此定义的表视图的条件。 可以为表定义指定的选择条件数目没有限制。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableRowEntries 元素 （格式） TableRowEntry 元素 （格式） EntrySelectedBy 元素 TableRowEntry （格式）TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 元素

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

以下各节描述了特性、 子元素和 SelectionCondition 元素的父元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition PropertyName 元素](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|可选元素。<br /><br /> 指定触发条件的.NET 属性。|
|[有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 的脚本块元素](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|可选元素。<br /><br /> 指定触发条件的脚本。|
|[有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|可选元素。<br /><br /> 指定.NET 类型的触发器条件的集。|
|[有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 的 TypeName 元素](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|可选元素。<br /><br /> 指定触发条件的.NET 类型。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableRowEntry （格式） 的 EntrySelectedBy 元素](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|定义使用此表项或要使用此项必须存在的条件的.NET 类型。|

## <a name="remarks"></a>备注

每个列表项必须具有至少一个类型名称、 选择集或定义的选择条件。

在定义的选择条件时，必须满足以下要求：

- 选择条件必须指定至少一个属性名或脚本块，但不能同时指定。

- 选择条件可以指定任意数量的.NET 类型，或者选择设置，但不能同时指定。

有关如何使用选择条件的详细信息，请参阅[时视图条目定义条件或使用项](./defining-conditions-for-displaying-data.md)。

表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。

## <a name="see-also"></a>另请参阅

[创建表视图](./creating-a-table-view.md)

[定义何时显示数据的条件](./defining-conditions-for-displaying-data.md)

[EntrySelectedBy 元素 （格式）](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition PropertyName 元素](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 的脚本块元素](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 的 TypeName 元素](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[编写 Windows PowerShell 格式设置和文件类型](./writing-a-powershell-formatting-file.md)
