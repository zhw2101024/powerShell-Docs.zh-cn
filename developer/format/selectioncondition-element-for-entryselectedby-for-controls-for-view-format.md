---
title: 视图 （格式） 的控件的 EntrySelectedBy SelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858013"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a>SelectionCondition Element for EntrySelectedBy for Controls for View (Format)

定义必须存在要使用的控件定义的条件。 定义一个视图，可以使用的控件时，将使用此元素。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 控件元素 （格式） 控制元素的控件的视图 （格式） CustomEntries 元素的控件的控件的视图 （格式） CustomControl 元素CustomControl CustomEntries CustomEntry EntrySelectedBy 视图 （控件的视图 （格式） SelectionCondition 元素的控件的视图 （格式） EntrySelectedBy 元素的控件的视图 （格式） CustomEntry 元素的控件格式）

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

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[SelectionCondition 视图 （格式） 的控件的属性名称元素](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|可选元素。<br /><br /> 指定触发条件的.NET 属性。|
|[SelectionCondition 的 Controls 的视图 （格式） 的脚本块元素](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|可选元素。<br /><br /> 指定触发条件的脚本。|
|[视图 （格式） 的控件的 SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|可选元素。<br /><br /> 指定触发条件的.NET 类型集。|
|[SelectionCondition 视图 （格式） 的控件的类型名称元素](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|可选元素。<br /><br /> 指定触发条件的.NET 类型。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[视图 （格式） 的控件的 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|定义使用此控件定义或要使用此定义中必须存在的条件的.NET 类型。|

## <a name="remarks"></a>备注

在定义的选择条件时，必须满足以下要求：

- 选择条件必须指定至少一个属性名或脚本块，但不能同时指定。

- 选择条件可以指定任意数量的.NET 类型，或者选择设置，但不能同时指定。

有关如何使用选择条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另请参阅

[SelectionCondition 视图 （格式） 的控件的属性名称元素](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[SelectionCondition 的 Controls 的视图 （格式） 的脚本块元素](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[视图 （格式） 的控件的 SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[SelectionCondition 视图 （格式） 的控件的类型名称元素](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[视图 （格式） 的控件的 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
