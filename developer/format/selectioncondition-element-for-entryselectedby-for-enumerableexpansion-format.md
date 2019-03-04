---
title: EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858283"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a>SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)

定义要展开此定义的集合对象必须存在的条件。

用于为 EntrySelectedBy EnumerableExpansion （格式） SelectionCondition 元素的配置元素 （格式） DefaultSettings 元素 （格式） EnumerableExpansions 元素 （格式） EnumerableExpansion 元素 （格式） EntrySelectedBy 元素EnumerableExpansion （格式）

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
|[有关 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition PropertyName 元素](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|可选元素。<br /><br /> 指定触发条件的.NET 属性。|
|[有关 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 的脚本块元素](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|可选元素。<br /><br /> 指定触发条件的脚本。|
|[有关 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|可选元素。<br /><br /> 指定触发条件的.NET 类型集。|
|[有关 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 的 TypeName 元素](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|可选元素。<br /><br /> 指定触发条件的.NET 类型。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion （格式） 的 EntrySelectedBy 元素](./entryselectedby-element-for-enumerableexpansion-format.md)|定义此定义的扩展的.NET 集合对象。|

## <a name="remarks"></a>备注

每个定义必须至少一个类型名称、 选择集或定义的选择条件。

在定义的选择条件时，必须满足以下要求：

- 选择条件必须指定至少一个属性名或脚本块，但不能同时指定。

- 选择条件可以指定任意数量的.NET 类型，或者选择设置，但不能同时指定。

有关如何使用选择条件的详细信息，请参阅[Diplaying 数据定义条件](./defining-conditions-for-displaying-data.md)。

有关较宽的视图的其他组件的详细信息，请参阅[宽视图](./creating-a-wide-view.md)。

## <a name="see-also"></a>另请参阅

[定义何时显示数据的条件](./defining-conditions-for-displaying-data.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
