---
title: EnumerableExpansion 的 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7af0b2-68e6-43c3-adcc-7c58007fced8
caps.latest.revision: 13
ms.openlocfilehash: 6f7c8d9af3c1c2fbda0208148b0088161701fdbe
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361986"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)

指定触发条件的 .NET 类型集。 如果此集中的任何类型存在，则满足条件。

用于 EnumerableExpansion 的 DefaultSettings 元素（format） EnumerableExpansions 元素（format） EnumerableExpansions 元素（format） EntrySelectedBy 元素EnumerableExpansion （Format） SelectionSetName 元素 for SelectionCondition for EntrySelectedBy for EnumerableExpansion （Format）

## <a name="syntax"></a>语法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍 `SelectionSetName` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|定义扩展此定义的集合对象时必须存在的条件。|

## <a name="text-value"></a>文本值

指定选择集的名称。

## <a name="remarks"></a>备注

选择条件可以指定选择集或 .NET 类型，但不能同时指定两者。 有关如何使用选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。

选择集是可由格式设置文件所定义的任何视图使用的常用 .NET 对象组。 有关创建和引用选项集的详细信息，请参阅[定义选择集](./defining-selection-sets.md)。

## <a name="see-also"></a>另请参阅

[定义选择集](./defining-selection-sets.md)

[EnumerableExpansion 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
