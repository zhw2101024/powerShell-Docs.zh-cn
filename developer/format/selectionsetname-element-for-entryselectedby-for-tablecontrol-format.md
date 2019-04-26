---
title: TableControl （格式） 的 EntrySelectedBy SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063915"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a>SelectionSetName Element for EntrySelectedBy for TableControl (Format)

指定一组.NET 类型使用此项的表视图。 可以为一个条目指定的所选内容集的数量没有限制。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableRowEntries 元素 （格式） TableRowEntry 元素 （格式） EntrySelectedBy 元素 （格式） SelectionSetName 元素EntrySelectedBy 为 TableRowEntry （格式） 的

## <a name="syntax"></a>语法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[EntrySelectedBy 元素 （格式）](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|定义使用此项或要使用此项必须存在的条件的.NET 类型。|

## <a name="text-value"></a>文本值

指定所选内容集的名称。

## <a name="remarks"></a>备注

当你想要在多个视图中定义的一组使用的对象时通常使用的选项集。 例如，你可能想要创建的表视图和同一组对象的列表视图。 有关定义的选项集的详细信息，请参阅[定义的视图的对象设置](./defining-selection-sets.md)。

如果指定的选项集的条目，则无法指定类型名称。 有关如何指定.NET 类型的详细信息，请参阅[TableRowEntry （格式） 的 EntrySelectedBy 的 TypeName 元素](./typename-element-for-entryselectedby-for-tablecontrol-format.md)。

表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。

## <a name="see-also"></a>另请参阅

[EntrySelectedBy 元素 （格式）](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[为视图定义对象的集](./defining-selection-sets.md)

[创建表视图](./creating-a-table-view.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
