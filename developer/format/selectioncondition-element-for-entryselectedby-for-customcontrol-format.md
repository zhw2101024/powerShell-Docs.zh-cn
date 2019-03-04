---
title: CustomControl （格式） 的 EntrySelectedBy SelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858823"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a>SelectionCondition Element for EntrySelectedBy for CustomControl (Format)

定义必须存在要使用的控件定义的条件。 定义自定义控件视图时，将使用此元素。

视图 （格式） 的视图 （格式） 的视图 (CustomControl CustomEntries CustomEntry 元素 CustomControl CustomEntries 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素格式） 的视图 （格式） 的视图 （格式） 的视图 （格式） 的 CustomControl EntrySelectedBy SelectionCondition 元素 CustomControl CustomEntry EntrySelectedBy 元素 CustomControl CustomEntry CustomItem 元素

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

以下各节描述了特性、 子元素和父元素的`SelectionCondition`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[属性名称的视图 （格式） 的 CustomControl SelectionCondition 元素](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 指定触发条件的.NET 属性。|
|[为视图 （格式） 的 CustomControl SelectionCondition 的脚本块元素](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 指定触发条件的脚本。|
|[自定义控件的视图 （格式） 的 SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 指定触发条件的.NET 类型集。|
|[为视图 （格式） 的 CustomControl SelectionCondition 的 TypeName 元素](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 指定触发条件的.NET 类型。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[为视图 （格式） 的 CustomControl CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|定义使用此控件定义或要使用此定义中必须存在的条件的.NET 类型。|

## <a name="remarks"></a>备注

在定义的选择条件时，必须满足以下要求：

- 选择条件必须指定至少一个属性名或脚本块，但不能同时指定。

- 选择条件可以指定任意数量的.NET 类型，或者选择设置，但不能同时指定。

有关如何使用选择条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另请参阅

[属性名称的视图 （格式） 的 CustomControl SelectionCondition 元素](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[为视图 （格式） 的 CustomControl SelectionCondition 的脚本块元素](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[自定义控件的视图 （格式） 的 SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[为视图 （格式） 的 CustomControl SelectionCondition 的 TypeName 元素](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[为视图 （格式） 的 CustomControl CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
