---
title: PropertyName 元素为 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3b4d9b-2b8c-4a3a-8887-6c606eb9d490
caps.latest.revision: 10
ms.openlocfilehash: 48011950ed64e78a84292762f2c7779003dc59fd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860983"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a>PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)

指定触发条件的.NET 属性。 存在此属性时或当计算结果为`true`、 满足该条件，以及使用的表项。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableRowEntries 元素 （格式） TableRowEntry 元素 （格式） EntrySelectedBy 元素 TableRowEntry （格式）有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition TableRowEntry （格式） PropertyName 元素 EntrySelectedBy SelectionCondition 元素

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
|[TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|定义要使用此表条目中必须存在的条件。|

## <a name="text-value"></a>文本值

指定.NET 属性名称。

## <a name="remarks"></a>备注

选择条件必须指定至少一个属性名称或脚本块，但不能同时指定。 有关如何使用选择条件的详细信息，请参阅[时视图条目定义条件或使用项](./defining-conditions-for-displaying-data.md)。

表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。

## <a name="see-also"></a>另请参阅

[创建表视图](./creating-a-table-view.md)

[定义何时显示数据的条件](./defining-conditions-for-displaying-data.md)

[有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 的脚本块元素](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
