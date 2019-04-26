---
title: SelectionSetName 元素的视图 （格式） 的 CustomControl SelectionCondition |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52b05a9-762e-4f1c-ad57-9d1710149722
caps.latest.revision: 10
ms.openlocfilehash: 25d46665ca5df3ddf49af5718d513b84c77988c8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075573"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a>SelectionSetName Element for SelectionCondition for CustomControl for View (Format)

指定.NET 类型的触发器条件的集。 当存在任何此集中的类型时，满足条件，并且使用此控件显示该对象。 定义自定义控件视图时，将使用此元素。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素 （格式） CustomEntries 元素 CustomControl 视图 （格式） 的视图 （格式） EntrySelectedBy CustomEntries CustomEntry 元素CustomEntry 视图 （格式） 的元素

## <a name="syntax"></a>语法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`SelectionSetName`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[为视图 （格式） 的 CustomControl EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|定义必须存在要使用的控件定义的条件。|

## <a name="text-value"></a>文本值

指定所选内容集的名称。

## <a name="remarks"></a>备注

所选内容集是常见的可以使用的格式设置文件定义任何视图的.NET 对象分组。 有关创建和引用所选内容集的详细信息，请参阅[定义设置的对象](./defining-selection-sets.md)。

选择条件可以指定所选内容集或.NET 类型，但不能同时指定。 有关如何使用选择条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另请参阅

[为视图 （格式） 的 CustomControl EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[定义何时显示数据的条件](./defining-conditions-for-displaying-data.md)

[定义的选项集](./defining-selection-sets.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
