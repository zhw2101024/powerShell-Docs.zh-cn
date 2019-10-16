---
title: ListControl （Format）的 EntrySelectedBy 的 SelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: f04a07c241268566eaedfe2b299c33d5be4dc19d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364816"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a>SelectionCondition Element for EntrySelectedBy for ListControl (Format)

定义使用此列表视图的定义时必须存在的条件。 对于列表定义可以指定的选择条件数量没有限制。

配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） ListControl 元素（格式） ListEntries 元素（格式） ListEntry 元素（format） EntrySelectedBy 元素 for ListEntry （Format） SelectionCondition 元素 forEntrySelectedBy for ListEntry （Format）

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

以下各节介绍了 `SelectionCondition` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ListEntry 的 SelectionCondition for EntrySelectedBy 的 PropertyName 元素（Format）](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|可选元素。<br /><br /> 指定触发条件的 .NET 属性。|
|[ListEntry 的 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|可选元素。<br /><br /> 指定触发条件的脚本。|
|[ListEntry 的 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素（Format）](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|可选元素。<br /><br /> 指定触发条件的 .NET 类型集。|
|[ListEntry 的 SelectionCondition for EntrySelectedBy 的 TypeName 元素（Format）](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|可选元素。<br /><br /> 指定触发条件的 .NET 类型。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableRowEntry 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|定义使用此表项的 .NET 类型或此项要使用的条件。|

## <a name="remarks"></a>备注

lWhen 正在定义选择条件，以下要求适用：

- 选择条件必须指定至少一个属性名称或脚本块，但不能同时指定两者。

- 选择条件可以指定任意数量的 .NET 类型或选择集，但是不能同时指定两者。

有关如何使用选择条件的详细信息，请参阅为[数据显示定义条件](./defining-conditions-for-displaying-data.md)。

有关列表视图的其他组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。

## <a name="see-also"></a>另请参阅

[创建列表视图](./creating-a-list-view.md)

[定义显示数据的条件](./defining-conditions-for-displaying-data.md)

[ListEntry 元素（格式）](./listentry-element-for-listcontrol-format.md)

[ListEntry 的 EntrySelectedBy 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[ListEntry 的 EntrySelectedBy 的 TypeName 元素（Format）](/powershell/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
