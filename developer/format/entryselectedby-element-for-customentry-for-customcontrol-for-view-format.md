---
title: EntrySelectedBy 元素的视图 （格式） 的 CustomControl CustomEntry |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066271"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a>EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)

定义使用此自定义项或要使用此项必须存在的条件的.NET 类型。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素 （格式） CustomEntries 元素 CustomControl 视图 （格式） 的视图 （格式） EntrySelectedBy CustomEntries CustomEntry 元素CustomEntry 视图 （格式） 的元素

## <a name="syntax"></a>语法

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`EntrySelectedBy`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[CustomEntry （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|可选元素。<br /><br /> 定义必须存在要使用此定义的条件。|
|[CustomEntry （格式） 的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 指定一组使用的控件视图此定义的.NET 类型。|
|[CustomEntry （格式） 的 EntrySelectedBy 的 TypeName 元素](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 指定将使用此定义的控件视图的.NET 类型。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[视图 （格式） 的 CustomEntries CustomEntry 元素](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|定义特定的.NET 对象所使用的控件。|

## <a name="remarks"></a>备注

必须指定至少一个类型、 选择集或选择条件的条目。 可以使用的子元素的数目没有最大限制。

使用选择条件来定义的条件必须存在要使用的项，例如当一个对象具有特定属性时，或者特定属性值或脚本的计算结果为`true`。 有关选择条件的详细信息，请参阅[时视图条目定义条件或使用项](./defining-conditions-for-displaying-data.md)。

有关组件的自定义控件视图的详细信息，请参阅[自定义控件视图](./creating-custom-controls.md)。

## <a name="see-also"></a>另请参阅

[CustomEntry （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[CustomEntry （格式） 的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[CustomEntry （格式） 的 EntrySelectedBy 的 TypeName 元素](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[视图 （格式） 的 CustomEntries CustomEntry 元素](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[自定义控件视图](./creating-custom-controls.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
