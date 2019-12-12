---
title: CustomControl （Format）的 EntrySelectedBy 的 SelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368436"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a>SelectionCondition Element for EntrySelectedBy for CustomControl (Format)

定义要使用的控件定义必须存在的条件。 定义自定义控件视图时，将使用此元素。

Configuration Element （Format） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素 for View （format） CustomEntries 元素 for CustomControl for CustomEntry for CustomEntries for View （Format） CustomControl 元素 for view （Format） CustomItem 元素 for CustomEntry for CustomControl for for view （format） EntrySelectedBy 元素 for CustomEntry for CustomControl for SelectionCondition for view （format） EntrySelectedBy 元素

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
|[View 的 SelectionCondition for CustomControl 的 PropertyName 元素（Format）](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 指定触发条件的 .NET 属性。|
|[用于 View 的 SelectionCondition for CustomControl 的 ScriptBlock 元素（格式）](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 指定触发条件的脚本。|
|[用于视图的自定义控件的 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 指定触发条件的 .NET 类型集。|
|[用于 View 的 SelectionCondition for CustomControl 的 TypeName 元素（Format）](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 指定触发条件的 .NET 类型。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[用于 View 的 CustomControl 的 CustomEntry 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|定义使用此控件定义的 .NET 类型或要使用此定义时必须存在的条件。|

## <a name="remarks"></a>备注

定义选择条件时，需要满足以下要求：

- 选择条件必须指定至少一个属性名称或脚本块，但不能同时指定两者。

- 选择条件可以指定任意数量的 .NET 类型或选择集，但是不能同时指定两者。

有关如何使用选择条件的详细信息，请参阅为[数据显示定义条件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另请参阅

[View 的 SelectionCondition for CustomControl 的 PropertyName 元素（Format）](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[用于 View 的 SelectionCondition for CustomControl 的 ScriptBlock 元素（格式）](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[用于视图的自定义控件的 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[用于 View 的 SelectionCondition for CustomControl 的 TypeName 元素（Format）](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[用于 View 的 CustomControl 的 CustomEntry 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
