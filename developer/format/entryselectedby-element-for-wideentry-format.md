---
title: WideEntry （格式） 的 EntrySelectedBy 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066169"
---
# <a name="entryselectedby-element-for-wideentry-format"></a>EntrySelectedBy Element for WideEntry (Format)

定义使用宽视图或必须存在要使用此定义的条件的此定义的.NET 类型。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） WideControl 元素 （格式） WideEntries 元素 （格式） WideEntry 元素 （格式） EntrySelectedBy 元素 WideEntry （格式）

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
|[WideEntry （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|可选元素。<br /><br /> 定义必须存在要使用此宽的视图定义的条件。|
|[WideEntry （格式） 的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|可选元素。<br /><br /> 指定一组使用此宽的视图定义的.NET 类型。|
|[WideEntry （格式） 的 EntrySelectedBy 的 TypeName 元素](./typename-element-for-entryselectedby-for-wideentry-format.md)|可选元素。<br /><br /> 指定将使用此宽的视图定义的.NET 类型。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[WideEntry 元素 （格式）](./wideentry-element-for-widecontrol-format.md)|提供了宽的视图的定义。|

## <a name="remarks"></a>备注

必须指定至少一个类型、 选择组或宽的视图定义的选择条件。 可以使用的子元素的数目没有最大限制。

使用选择条件来定义要使用，例如当一个对象具有特定属性的定义中必须存在一个条件或特定属性值或脚本值的计算结果为`true`。 有关选择条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。

有关较宽的视图的其他组件的详细信息，请参阅[创建较宽的视图](./creating-a-wide-view.md)。

## <a name="see-also"></a>另请参阅

[WideEntry 元素 （格式）](./wideentry-element-for-widecontrol-format.md)

[WideEntry （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[WideEntry （格式） 的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[WideEntry （格式） 的 EntrySelectedBy 的 TypeName 元素](./typename-element-for-entryselectedby-for-wideentry-format.md)

[创建较宽的视图](./creating-a-wide-view.md)

[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
