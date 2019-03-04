---
title: GroupBy （格式） 的 CustomEntry EntrySelectedBy 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862813"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a>EntrySelectedBy Element for CustomEntry for GroupBy (Format)

定义使用此控件定义或要使用此定义中必须存在的条件的.NET 类型。 定义如何显示一组新对象时，将使用此元素。

GroupBy （格式） 的 GroupBy （格式） CustomEntry 元素 CustomControl CustomEntries 元素的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素CustomControl CustomEntry 为 GroupBy （格式） 的 GroupBy （格式） EntrySelectedBy 元素

## <a name="syntax"></a>语法

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`EntrySelectedBy`元素。 必须指定至少一个类型、 选择集或选择条件的定义。 可以使用的子元素的数目没有最大限制。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[GroupBy （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|可选元素。<br /><br /> 定义必须存在要使用此定义的条件。|
|[GroupBy （格式） 的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|可选元素。<br /><br /> 指定一组使用控件的此定义的.NET 类型。|
|[GroupBy （格式） 的 EntrySelectedBy 的 TypeName 元素](./typename-element-for-entryselectedby-for-groupby-format.md)|可选元素。<br /><br /> 指定将使用该控件的此定义的.NET 类型。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[GroupBy （格式） 的 CustomControl CustomEntry 元素](./customentry-element-for-customcontrol-for-groupby-format.md)|提供控件的定义。|

## <a name="remarks"></a>备注

使用选择条件来定义的条件必须存在要使用的定义的例如当一个对象具有特定属性时，或者特定属性值或脚本的计算结果为`true`。 有关选择条件的详细信息，请参阅[时视图条目定义条件或使用项](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另请参阅

[GroupBy （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[GroupBy （格式） 的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[GroupBy （格式） 的 EntrySelectedBy 的 TypeName 元素](./typename-element-for-entryselectedby-for-groupby-format.md)

[视图 （格式） 的控件的 CustomEntries CustomEntry 元素](./customentry-element-for-customentries-for-controls-for-view-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
