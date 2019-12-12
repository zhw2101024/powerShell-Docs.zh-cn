---
title: ListControl 的 EntrySelectedBy 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 0f7216d4dcc0380bceb47ea7c15b3d4a7e5ceeb2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361656"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a>TypeName Element for EntrySelectedBy for ListControl (Format)

指定使用此列表视图项的 .NET 类型。 对于列表项可以指定的类型数量没有限制。

配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） ListControl 元素（格式） ListEntries 元素（格式） ListEntry 元素（format） EntrySelectedBy 元素 for ListEntry （Format） TypeName 元素 forEntrySelectedBy for ListControl （Format）

## <a name="syntax"></a>语法

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `TypeName` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ListEntry 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|定义使用此列表项的 .NET 类型或此项要使用的条件。|

## <a name="text-value"></a>文本值

指定 .NET 类型的完全限定名称，如 `System.IO.DirectoryInfo`。

## <a name="remarks"></a>备注

每个列表项必须至少定义一个类型名称、选择集或选择条件。

有关如何在列表视图中使用此元素的详细信息，请参阅[列表视图](./creating-a-list-view.md)。

## <a name="example"></a>示例

下面的示例演示如何为列表视图的条目指定选择集。

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a>另请参阅

[创建列表视图](./creating-a-list-view.md)

[ListEntry 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[ListEntry 的 EntrySelectedBy 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
