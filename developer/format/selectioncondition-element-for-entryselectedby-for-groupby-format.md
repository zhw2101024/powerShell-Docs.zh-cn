---
title: GroupBy （格式） 的 EntrySelectedBy SelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc2093a-dc54-42c4-ada3-c8d089ba1e8e
caps.latest.revision: 6
ms.openlocfilehash: a6738a7c4c934b2d6a16695a711f7c6c80afdd2d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075709"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a>SelectionCondition Element for EntrySelectedBy for GroupBy (Format)

定义必须存在要使用的控件定义的条件。 定义如何显示一组新对象时，将使用此元素。

GroupBy （格式） 的 GroupBy （格式） CustomEntry 元素 CustomControl CustomEntries 元素的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素CustomControl GroupBy （格式） 的 GroupBy （格式） 的 GroupBy （格式） 的 EntrySelectedBy SelectionCondition 元素 CustomEntry EntrySelectedBy 元素

## <a name="syntax"></a>语法

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`SelectionCondition`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[GroupBy （格式） 的 SelectionCondition PropertyName 元素](./propertyname-element-for-selectioncondition-for-groupby-format.md)|可选元素。<br /><br /> 指定触发条件的.NET 属性。|
|[GroupBy （格式） 的 SelectionCondition 的脚本块元素](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|可选元素。<br /><br /> 指定触发条件的脚本。|
|[GroupBy （格式） 的 SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|可选元素。<br /><br /> 指定触发条件的.NET 类型集。|
|[GroupBy （格式） 的 SelectionCondition 的 TypeName 元素](./typename-element-for-selectioncondition-for-groupby-format.md)|可选元素。<br /><br /> 指定触发条件的.NET 类型。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[GroupBy （格式） 的 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-groupby-format.md)|定义使用此控件定义或要使用此定义中必须存在的条件的.NET 类型。|

## <a name="remarks"></a>备注

在定义的选择条件时，必须满足以下要求：

- 选择条件必须指定至少一个属性名或脚本块，但不能同时指定。

- 选择条件可以指定任意数量的.NET 类型，或者选择设置，但不能同时指定。

有关如何使用选择条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另请参阅

[属性名称的视图 （格式） 的 CustomControl SelectionCondition 元素](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[为视图 （格式） 的 CustomControl SelectionCondition 的脚本块元素](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[自定义控件的视图 （格式） 的 SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[GroupBy （格式） 的 SelectionCondition 的 TypeName 元素](./typename-element-for-selectioncondition-for-groupby-format.md)

[GroupBy （格式） 的 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-groupby-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
