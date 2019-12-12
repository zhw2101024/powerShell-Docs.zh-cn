---
title: EnumerableExpansion 的 SelectionCondition for EntrySelectedBy 的 PropertyName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ae11924-0072-451e-bf70-c5ffb25dccc0
caps.latest.revision: 13
ms.openlocfilehash: 0c20512e660c8d2b61d063dbd7078b55b23efeb8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362316"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)

指定触发条件的 .NET 属性。 如果该属性存在或其计算结果为 `true`，则满足条件，并使用定义。

用于 EnumerableExpansion 的 SelectionCondition （Format） EntrySelectedBy 元素的配置元素（格式） DefaultSettings 元素（format） EnumerableExpansions 元素（format） EntrySelectedBy 元素EnumerableExpansion 的 EntrySelectedBy 的 SelectionCondition 的 EnumerableExpansion （格式） PropertyName 元素（Format）

## <a name="syntax"></a>语法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `PropertyName` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|定义扩展此定义的集合对象时必须存在的条件。|

## <a name="text-value"></a>文本值

指定 .NET 属性名称。

## <a name="remarks"></a>备注

选择条件必须指定至少一个要计算的属性名称或脚本，但不能同时指定两者。 有关如何使用选择条件的详细信息，请参阅为[数据显示定义条件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另请参阅

[定义显示数据的条件](./defining-conditions-for-displaying-data.md)

[EnumerableExpansion 的 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[EnumerableExpansion 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
