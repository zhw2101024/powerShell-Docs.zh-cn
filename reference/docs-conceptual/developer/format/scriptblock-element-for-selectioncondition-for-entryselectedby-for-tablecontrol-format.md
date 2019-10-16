---
title: 用于 TableControl 的 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b11fbcf-3426-48ae-9319-2c847969f723
caps.latest.revision: 10
ms.openlocfilehash: 7afc834e68ef332bee1e23da782fb5c5527fcf54
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368576"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a>ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)

指定触发条件的脚本块。 如果此脚本的计算结果为 `true`，则满足条件，并使用表项。

用于 EntrySelectedBy 的配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） TableControl 元素（格式） TableRowEntries 元素（格式） TableRowEntry 元素（format） TableRowEntry 元素（格式）SelectionCondition for EntrySelectedBy 的 TableRowEntry （Format） ScriptBlock 元素的 EntrySelectedBy 的 SelectionCondition 元素（Format）

## <a name="syntax"></a>语法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `ScriptBlock` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableRowEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|定义要使用此表项必须存在的条件。|

## <a name="text-value"></a>文本值

指定要评估的脚本。

## <a name="remarks"></a>备注

选择条件必须指定至少一个脚本块或属性名称，但不能同时指定两者。 有关如何使用选择条件的详细信息，请参阅[定义使用视图条目或项的条件](./defining-conditions-for-displaying-data.md)。

有关表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。

## <a name="see-also"></a>另请参阅

[创建表视图](./creating-a-table-view.md)

[定义显示数据的条件](./defining-conditions-for-displaying-data.md)

[TableRowEntry 的 SelectionCondition for EntrySelectedBy 的 PropertyName 元素（Format）](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[TableRowEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
