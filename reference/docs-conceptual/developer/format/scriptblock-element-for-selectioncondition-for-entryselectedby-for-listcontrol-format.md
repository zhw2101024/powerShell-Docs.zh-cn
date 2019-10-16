---
title: 用于 ListControl 的 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: b65d953169f6daf15fb617ce4d0303cf4cb584ee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368586"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)

指定触发条件的脚本。 如果此脚本的计算结果为 `true`，则满足条件，并使用列表项。

配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） ListControl 元素（格式） ListEntries 元素（格式） ListEntry 元素（format） EntrySelectedBy 元素 for ListEntry （Format） SelectionCondition 元素 forEntrySelectedBy for ListEntry （Format） ScriptBlock 元素 for SelectionCondition for EntrySelectedBy for ListEntry （Format）

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
|[ListEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|定义要使用此列表项必须存在的条件。|

## <a name="text-value"></a>文本值

指定要评估的脚本。

## <a name="remarks"></a>备注

选择条件必须指定至少一个要计算的脚本或属性名称，但不能同时指定两者。 （有关如何使用选择条件的详细信息，请参阅[定义使用视图条目或项的条件](./defining-conditions-for-displaying-data.md)。）

有关列表视图的其他组件的详细信息，请参阅[列表视图](./creating-a-list-view.md)。

## <a name="see-also"></a>另请参阅

[ListEntry 元素（格式）](./listentry-element-for-listcontrol-format.md)

[ListEntry 的 SelectionCondition for EntrySelectedBy 的 PropertyName 元素（Format）](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[ListEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[列表视图](./creating-a-list-view.md)

[定义使用视图条目或项的条件](./defining-conditions-for-displaying-data.md)

[编写 Windows PowerShell 格式设置和类型文件](./writing-a-powershell-formatting-file.md)
