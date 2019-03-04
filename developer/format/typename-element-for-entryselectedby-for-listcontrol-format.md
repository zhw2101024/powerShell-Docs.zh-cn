---
title: TypeName 元素 ListControl （格式） 的 EntrySelectedBy |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 3f0c0ba1fe85d70557e67a30b3a9a59a33043475
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856103"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a>TypeName Element for EntrySelectedBy for ListControl (Format)

指定使用此项的列表视图中的.NET 类型。 可以指定列表项的类型的数量没有限制。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素 （格式） ListEntry 元素 （格式） EntrySelectedBy 元素 ListEntry （格式） TypeName 元素EntrySelectedBy 的 ListControl （格式）

## <a name="syntax"></a>语法

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`TypeName`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ListEntry （格式） 的 EntrySelectedBy 元素](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|定义使用此列表项或要使用此项必须存在的条件的.NET 类型。|

## <a name="text-value"></a>文本值

指定.NET 类型的完全限定名称，例如`System.IO.DirectoryInfo`。

## <a name="remarks"></a>备注

每个列表项必须具有至少一个类型名称、 选择集或定义的选择条件。

有关如何在列表视图中使用此元素的详细信息，请参阅[列表视图](./creating-a-list-view.md)。

## <a name="example"></a>示例

下面的示例演示如何以指定的选项集列表视图的条目。

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

[ListEntry （格式） 的 EntrySelectedBy 元素](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[ListEntry （格式） 的 EnrtySelectedBy SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
