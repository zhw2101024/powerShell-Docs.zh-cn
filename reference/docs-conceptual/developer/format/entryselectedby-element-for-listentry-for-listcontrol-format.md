---
title: ListControl （Format）的 ListEntry 的 EntrySelectedBy 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363826"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a>EntrySelectedBy Element for ListEntry for ListControl (Format)

定义使用此列表视图定义或要使用此定义必须存在的条件的 .NET 类型。 在大多数情况下，列表视图只需要一个定义。 但是，如果您希望使用同一列表视图为不同对象显示不同的数据，则可以为列表视图提供多个定义。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（format） ListEntries 元素 for ListControl （Format） ListEntry 元素 for ListEntry for ListControl （Format） EntrySelectedBy 元素 forListEntry for ListControl （Format）

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
|[ListControl 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|可选元素。<br /><br /> 定义要使用此列表视图定义必须存在的条件。|
|[ListControl 的 EntrySelectedBy 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|可选元素。<br /><br /> 指定一组使用此列表视图定义的 .NET 类型。|
|[ListControl 的 EntrySelectedBy 的 TypeName 元素（Format）](./typename-element-for-entryselectedby-for-listcontrol-format.md)|可选元素。<br /><br /> 指定使用此列表视图定义的 .NET 类型。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ListControl 的 ListEntry 元素（格式）](./listentry-element-for-listcontrol-format.md)|定义列表行的显示方式。|

## <a name="remarks"></a>备注

对于列表视图定义，必须至少指定一个类型、选择集或选择条件。 您可以使用的子元素数没有最大限制。

选择条件用于定义要使用的定义必须存在的条件，例如当对象具有特定属性或特定属性值或脚本计算结果为 `true`时。 有关选择条件的详细信息，请参阅为[数据显示定义条件](./defining-conditions-for-displaying-data.md)。

有关列表视图组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。

## <a name="example"></a>示例

下面的示例演示如何使用 .NET 类型名称定义列表视图的对象。

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a>另请参阅

[ListControl 的 ListEntry 元素（格式）](./listentry-element-for-listcontrol-format.md)

[ListControl 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[ListControl 的 EntrySelectedBy 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[ListControl 的 EntrySelectedBy 的 TypeName 元素（Format）](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[创建列表视图](./creating-a-list-view.md)

[定义显示数据的条件](./defining-conditions-for-displaying-data.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
