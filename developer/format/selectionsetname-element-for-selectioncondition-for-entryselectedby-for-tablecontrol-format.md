---
title: TableControl （格式） 的 EntrySelectedBy 的 SelectionCondition SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ae4d6b-dc95-4a1d-8e32-31ff084a951f
caps.latest.revision: 10
ms.openlocfilehash: edb163f2b0b5129bd741677dce882888d9bbfd89
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863273"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a>SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)

指定.NET 类型的触发器条件的集。 当存在任何此集中的类型时，满足该条件，并通过使用此定义的表视图中显示该对象。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableRowEntries 元素 （格式） TableRowEntry 元素 （格式） EntrySelectedBy 元素 TableRowEntry （格式）有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition TableRowEntry （格式） SelectionSetName 元素 EntrySelectedBy SelectionCondition 元素

## <a name="syntax"></a>语法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`SelectionSetName`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|定义必须存在要用于此定义的表视图的条件。|

## <a name="text-value"></a>文本值

指定所选内容集的名称。

## <a name="remarks"></a>备注

选择条件可以指定所选内容集或.NET 类型，但不能同时指定。 有关如何使用选择条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。

所选内容集是常见的可以使用的格式设置文件定义任何视图的.NET 对象分组。 有关创建和引用所选内容集的详细信息，请参阅[定义设置的对象](./defining-selection-sets.md)。

有关较宽的视图的其他组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。

## <a name="see-also"></a>另请参阅

[创建表视图](./creating-a-table-view.md)

[定义何时显示数据的条件](./defining-conditions-for-displaying-data.md)

[有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 的 TypeName 元素](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
