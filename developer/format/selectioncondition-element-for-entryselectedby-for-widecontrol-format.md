---
title: WideControl （格式） 的 EntrySelectedBy SelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854113"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a>SelectionCondition Element for EntrySelectedBy for WideControl (Format)

定义必须存在要使用此定义的条件。 可以为宽的项定义中指定的选择条件数目没有限制。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） WideControl 元素 （格式） WideEntries 元素 （格式） WideEntry 元素 （格式） EntrySelectedBy 元素 WideEntry （格式） SelectionCondition 元素EntrySelectedBy 为 WideEntry （格式） 的

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

以下各节描述了特性、 子元素和父元素的`SelectionCondition`元素。 必须指定单个`PropertyName`或`ScriptBlock`元素。 `SelectionSetName`和`TypeName`元素是可选的。 您可以指定一个其中一个元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[有关 WideEntry （格式） 的 EntrySelectedBy SelectionCondition PropertyName 元素](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|可选元素。<br /><br /> 指定触发条件的.NET 属性。|
|[有关 WideEntry （格式） 的 EntrySelectedBy SelectionCondition 的脚本块元素](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|可选元素。<br /><br /> 指定触发条件的脚本块。|
|[有关 WideEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|可选元素。<br /><br /> 指定触发条件的.NET 类型集。|
|[有关 WideEntry （格式） 的 EntrySelectedBy SelectionCondition 的 TypeName 元素](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|可选元素。<br /><br /> 指定触发条件的.NET 类型。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[WideEntry （格式） 的 EntrySelectedBy 元素](./entryselectedby-element-for-wideentry-format.md)|定义使用此宽的项或要使用此项必须存在的条件的.NET 类型。|

## <a name="remarks"></a>备注

每个宽的条目必须有至少一个类型名称、 选择集或选择条件定义。

在定义的选择条件时，必须满足以下要求：

- 选择条件必须指定至少一个属性名或脚本块，但不能同时指定。

- 选择条件可以指定任意数量的.NET 类型，或者选择设置，但不能同时指定。

有关如何使用选择条件的详细信息，请参阅[时视图条目定义条件或使用项](./defining-conditions-for-displaying-data.md)。

有关较宽的视图的其他组件的详细信息，请参阅[创建较宽的视图](./creating-a-wide-view.md)。

## <a name="see-also"></a>另请参阅

[创建较宽的视图](./creating-a-wide-view.md)

[定义何时显示数据的条件](./defining-conditions-for-displaying-data.md)

[WideEntry （格式） 的 EntrySelectedBy 元素](./entryselectedby-element-for-wideentry-format.md)

[有关 WideEntry （格式） 的 EntrySelectedBy SelectionCondition PropertyName 元素](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[有关 WideEntry （格式） 的 EntrySelectedBy SelectionCondition 的脚本块元素](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[有关 WideEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[有关 WideEntry （格式） 的 EntrySelectedBy SelectionCondition 的 TypeName 元素](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
