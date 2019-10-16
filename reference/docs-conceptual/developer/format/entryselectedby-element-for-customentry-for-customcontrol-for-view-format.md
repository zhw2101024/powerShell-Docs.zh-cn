---
title: 用于 CustomControl for View （Format）的 CustomEntry 的 EntrySelectedBy 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368776"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a>EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)

定义使用此自定义项的 .NET 类型或此项要使用的条件。

用于 CustomEntry 的 CustomControl for view （format） CustomEntries 元素的配置元素（格式） ViewDefinitions 元素（格式） CustomControl 元素（format） CustomEntries 元素 EntrySelectedByView 的 CustomEntry 元素（格式）

## <a name="syntax"></a>语法

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `EntrySelectedBy` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[CustomEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|可选元素。<br /><br /> 定义要使用此定义必须存在的条件。|
|[CustomEntry 的 EntrySelectedBy 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 指定一组使用控件视图的此定义的 .NET 类型。|
|[CustomEntry 的 EntrySelectedBy 的 TypeName 元素（Format）](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 指定使用控件视图的此定义的 .NET 类型。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[用于视图的 CustomEntries 的 CustomEntry 元素（格式）](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|定义特定 .NET 对象使用的控件。|

## <a name="remarks"></a>备注

您必须为某个条目指定至少一个类型、选择集或选择条件。 您可以使用的子元素数没有最大限制。

选择条件用于定义要使用的项必须存在的条件，例如当对象具有特定属性或特定属性值或脚本计算结果为 `true` 时。 有关选择条件的详细信息，请参阅[定义使用视图条目或项的条件](./defining-conditions-for-displaying-data.md)。

有关自定义控件视图组件的详细信息，请参阅[自定义控件视图](./creating-custom-controls.md)。

## <a name="see-also"></a>另请参阅

[CustomEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[CustomEntry 的 EntrySelectedBy 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[CustomEntry 的 EntrySelectedBy 的 TypeName 元素（Format）](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[用于视图的 CustomEntries 的 CustomEntry 元素（格式）](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[自定义控件视图](./creating-custom-controls.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
