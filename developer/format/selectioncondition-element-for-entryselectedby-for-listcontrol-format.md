---
title: ListControl （格式） 的 EntrySelectedBy SelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: 633204f3b181316761746ea2679910216fb74657
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058957"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a>SelectionCondition Element for EntrySelectedBy for ListControl (Format)

定义要使用此列表视图的定义必须存在的条件。 可以为列表定义指定的选择条件数目没有限制。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素 （格式） ListEntry 元素 （格式） EntrySelectedBy 元素 ListEntry （格式） SelectionCondition 元素EntrySelectedBy 为 ListEntry （格式） 的

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

以下各节描述了特性、 子元素和父元素的`SelectionCondition`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[有关 ListEntry （格式） 的 EntrySelectedBy SelectionCondition PropertyName 元素](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|可选元素。<br /><br /> 指定触发条件的.NET 属性。|
|[有关 ListEntry （格式） 的 EntrySelectedBy SelectionCondition 的脚本块元素](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|可选元素。<br /><br /> 指定触发条件的脚本。|
|[有关 ListEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|可选元素。<br /><br /> 指定.NET 类型的触发器条件的集。|
|[有关 ListEntry （格式） 的 EntrySelectedBy SelectionCondition 的 TypeName 元素](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|可选元素。<br /><br /> 指定触发条件的.NET 类型。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[TableRowEntry （格式） 的 EntrySelectedBy 元素](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|定义使用此表项或要使用此项必须存在的条件的.NET 类型。|

## <a name="remarks"></a>备注

lWhen 定义选择条件，必须满足以下要求：

- 选择条件必须指定至少一个属性名或脚本块，但不能同时指定。

- 选择条件可以指定任意数量的.NET 类型，或者选择设置，但不能同时指定。

有关如何使用选择条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。

列表视图的其他组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。

## <a name="see-also"></a>另请参阅

[创建列表视图](./creating-a-list-view.md)

[定义何时显示数据的条件](./defining-conditions-for-displaying-data.md)

[ListEntry 元素 （格式）](./listentry-element-for-listcontrol-format.md)

[ListEntry （格式） 的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[ListEntry （格式） 的 EntrySelectedBy 的 TypeName 元素](http://msdn.microsoft.com/en-us/fcd4daa6-f3fd-43f7-a468-03c582d34533)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
