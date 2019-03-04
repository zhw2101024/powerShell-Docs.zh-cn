---
title: EnumerableExpansion （格式） 的 EntrySelectedBy 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855583"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a>EntrySelectedBy Element for EnumerableExpansion (Format)

定义使用此定义或要使用此定义中必须存在的条件的.NET 类型。

配置元素 （格式） DefaultSettings 元素 （格式） EnumerableExpansions 元素 （格式） EnumerableExpansion 元素 （格式） EntrySelectedBy 元素 EnumerableExpansion （格式）

## <a name="syntax"></a>语法

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`EntrySelectedBy`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|可选元素。<br /><br /> 定义要展开此定义的集合对象必须存在的条件。|
|[EnumerableExpansion （格式） 的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|可选元素。<br /><br /> 指定一组使用如何扩展的集合对象的此定义的.NET 类型。|
|[EnumerableExpansion （格式） 的 EntrySelectedBy 的 TypeName 元素](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|可选元素。<br /><br /> 指定将使用如何扩展的集合对象的此定义的.NET 类型。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 元素 （格式）](./enumerableexpansion-element-format.md)|定义如何特定对象在视图中显示时进行扩展的.NET 集合。|

## <a name="remarks"></a>备注

必须指定至少一个类型、 所选内容集或定义项的选择条件。 可以使用的子元素的数目没有最大限制。

使用选择条件来定义要使用，例如当一个对象具有特定属性的定义中必须存在一个条件或特定属性值或脚本的计算结果为`true`。 有关选择条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另请参阅

[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)

[EnumerableExpansion 元素 （格式）](./enumerableexpansion-element-format.md)

[EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[EnumerableExpansion （格式） 的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[EnumerableExpansion （格式） 的 EntrySelectedBy 的 TypeName 元素](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
