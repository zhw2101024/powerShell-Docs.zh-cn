---
title: 有关 ListControl （格式） 的 EntrySelectedBy SelectionCondition 的 TypeName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd025a3a-3780-40db-a068-873e7df38015
caps.latest.revision: 9
ms.openlocfilehash: 2b76b040b39088cc9c3b9d6890c38df3c533b39f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083852"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)

指定触发条件的.NET 类型。 当存在此类型时，才使用列表项。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素 ListControl （格式） EntrySelectedBy 元素 ListEntries ListControl （格式） ListEntry 元素ListEntry ListControl （格式） 的 ListControl （格式） 的 EntrySelectedBy SelectionCondition TypeName 元素 EntrySelectedBy ListControl （格式） SelectionCondition 元素

## <a name="syntax"></a>语法

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`TypeName`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[ListControl （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|定义要使用此列表项中必须存在的条件。|

## <a name="text-value"></a>文本值

指定.NET 类型的完全限定的名称，例如`System.IO.DirectoryInfo`。

## <a name="remarks"></a>备注

选择条件可以指定任意数量的.NET 类型，或者选择设置，但不能同时指定。 有关如何使用选择条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。

有关其他详细信息的组件的列表视图中，请参阅[创建列表视图](./creating-a-list-view.md)。

## <a name="see-also"></a>另请参阅

[创建列表视图](./creating-a-list-view.md)

[定义何时显示数据的条件](./defining-conditions-for-displaying-data.md)

[ListControl （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
