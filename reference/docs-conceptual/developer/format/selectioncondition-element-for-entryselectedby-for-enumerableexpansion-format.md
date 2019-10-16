---
title: EnumerableExpansion （Format）的 EntrySelectedBy 的 SelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362006"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a>SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)

定义扩展此定义的集合对象时必须存在的条件。

用于 EnumerableExpansion 的 SelectionCondition （Format） EntrySelectedBy 元素的配置元素（格式） DefaultSettings 元素（format） EnumerableExpansions 元素（format） EntrySelectedBy 元素EnumerableExpansion （格式）

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

以下各节介绍了 `SelectionCondition` 元素的属性、子元素和父元素。 必须指定单个 @no__t 0 或 `ScriptBlock` 元素。 @No__t，@no__t 元素是可选的。 可以指定任一元素中的一个。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 的 SelectionCondition for EntrySelectedBy 的 PropertyName 元素（Format）](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|可选元素。<br /><br /> 指定触发条件的 .NET 属性。|
|[EnumerableExpansion 的 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|可选元素。<br /><br /> 指定触发条件的脚本。|
|[EnumerableExpansion 的 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素（Format）](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|可选元素。<br /><br /> 指定触发条件的 .NET 类型集。|
|[EnumerableExpansion 的 SelectionCondition for EntrySelectedBy 的 TypeName 元素（Format）](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|可选元素。<br /><br /> 指定触发条件的 .NET 类型。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-enumerableexpansion-format.md)|定义通过此定义扩展哪些 .NET 集合对象。|

## <a name="remarks"></a>备注

每个定义都必须定义至少一个类型名称、选择集或选择条件。

定义选择条件时，需要满足以下要求：

- 选择条件必须指定至少一个属性名称或脚本块，但不能同时指定两者。

- 选择条件可以指定任意数量的 .NET 类型或选择集，但是不能同时指定两者。

有关如何使用选择条件的详细信息，请参阅[定义 Diplaying 数据的条件](./defining-conditions-for-displaying-data.md)。

有关大视图的其他组件的详细信息，请参阅[宽视图](./creating-a-wide-view.md)。

## <a name="see-also"></a>另请参阅

[定义显示数据的条件](./defining-conditions-for-displaying-data.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
