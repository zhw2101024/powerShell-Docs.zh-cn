---
title: PropertyName 元素为 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ae11924-0072-451e-bf70-c5ffb25dccc0
caps.latest.revision: 13
ms.openlocfilehash: 0c20512e660c8d2b61d063dbd7078b55b23efeb8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859623"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)

指定触发条件的.NET 属性。 存在此属性时或当计算结果为`true`、 满足该条件，以及使用该定义。

用于为 EntrySelectedBy EnumerableExpansion （格式） SelectionCondition 元素的配置元素 （格式） DefaultSettings 元素 （格式） EnumerableExpansions 元素 （格式） EnumerableExpansion 元素 （格式） EntrySelectedBy 元素有关 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition EnumerableExpansion （格式） PropertyName 元素

## <a name="syntax"></a>语法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`PropertyName`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|定义要展开此定义的集合对象必须存在的条件。|

## <a name="text-value"></a>文本值

指定.NET 属性名称。

## <a name="remarks"></a>备注

选择条件必须指定至少一个属性名称或脚本来评估，但不能同时指定。 有关如何使用选择条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另请参阅

[定义条件的数据时显示](./defining-conditions-for-displaying-data.md)

[有关 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 的脚本块元素](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
