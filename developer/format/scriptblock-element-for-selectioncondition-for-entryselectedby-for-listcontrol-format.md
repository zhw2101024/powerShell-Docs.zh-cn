---
title: 脚本块元素的 ListControl （格式） 的 EntrySelectedBy SelectionCondition |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: b65d953169f6daf15fb617ce4d0303cf4cb584ee
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057767"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)

指定触发条件的脚本。 当此脚本的计算结果为`true`、 满足该条件，以及使用列表项。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素 （格式） ListEntry 元素 （格式） EntrySelectedBy 元素 ListEntry （格式） SelectionCondition 元素EntrySelectedBy ListEntry （格式） 的 EntrySelectedBy 的 SelectionCondition ListEntry （格式） 脚本块元素

## <a name="syntax"></a>语法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`ScriptBlock`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[ListEntry （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|定义要使用此列表项中必须存在的条件。|

## <a name="text-value"></a>文本值

指定计算的脚本。

## <a name="remarks"></a>备注

选择条件必须指定至少一个脚本或属性名称来评估，但不能同时指定。 (有关如何使用选择条件的详细信息，请参阅[时视图条目定义条件或使用项](./defining-conditions-for-displaying-data.md)。)

列表视图的其他组件的详细信息，请参阅[列表视图](./creating-a-list-view.md)。

## <a name="see-also"></a>另请参阅

[ListEntry 元素 （格式）](./listentry-element-for-listcontrol-format.md)

[有关 ListEntry （格式） 的 EntrySelectedBy SelectionCondition PropertyName 元素](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[ListEntry （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[列表视图](./creating-a-list-view.md)

[使用视图条目或项时定义的条件](./defining-conditions-for-displaying-data.md)

[编写 Windows PowerShell 格式设置和文件类型](./writing-a-powershell-formatting-file.md)
