---
title: ListControl （格式） 的 ListEntry EntrySelectedBy 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 723619e67612b859d0acbab37eecd82141adf923
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854943"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a>EntrySelectedBy Element for ListEntry for ListControl (Format)

定义使用此列表视图定义的.NET 类型或要使用此定义中必须存在的条件。 在大多数情况下只有一个定义列表视图的需要。 但是，如果你想要使用相同的列表视图来显示不同的对象的不同数据可以提供多个列表视图的定义。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素 ListControl （格式） EntrySelectedBy 元素 ListEntry ListControl （格式） ListEntry 元素ListEntry 的 ListControl （格式）

## <a name="syntax"></a>语法

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`EntrySelectedBy`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ListControl （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|可选元素。<br /><br /> 定义必须存在要使用此列表视图定义的条件。|
|[ListControl （格式） 的 EnrtySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|可选元素。<br /><br /> 指定一组使用此列表视图定义的.NET 类型。|
|[ListControl （格式） 的 EntrySelectedBy 的 TypeName 元素](./typename-element-for-entryselectedby-for-listcontrol-format.md)|可选元素。<br /><br /> 指定将使用此列表视图定义的.NET 类型。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ListControl （格式） 的 ListEntry 元素](./listentry-element-for-listcontrol-format.md)|定义列表的行的显示方式。|

## <a name="remarks"></a>备注

必须指定至少一个类型、 选择集或选择列表视图定义的条件。 可以使用的子元素的数目没有最大限制。

使用选择条件来定义要使用，例如当一个对象具有特定属性的定义中必须存在一个条件或特定属性值或脚本的计算结果为`true`。 有关选择条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。

列表视图的组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。

## <a name="example"></a>示例

下面的示例演示如何定义使用其.NET 类型名称的列表视图的对象。

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a>另请参阅

[ListControl （格式） 的 ListEntry 元素](./listentry-element-for-listcontrol-format.md)

[ListControl （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[ListControl （格式） 的 EnrtySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[ListControl （格式） 的 EntrySelectedBy 的 TypeName 元素](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[创建列表视图](./creating-a-list-view.md)

[定义何时显示数据的条件](./defining-conditions-for-displaying-data.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
