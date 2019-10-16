---
title: 用于 CustomControl for View （Format）的 SelectionCondition 的 SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52b05a9-762e-4f1c-ad57-9d1710149722
caps.latest.revision: 10
ms.openlocfilehash: 25d46665ca5df3ddf49af5718d513b84c77988c8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368266"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a>SelectionSetName Element for SelectionCondition for CustomControl for View (Format)

指定触发条件的 .NET 类型集。 如果此集中的任何类型存在，则满足条件，并使用此控件显示该对象。 定义自定义控件视图时，将使用此元素。

用于 CustomEntry 的 CustomControl for view （format） CustomEntries 元素的配置元素（格式） ViewDefinitions 元素（格式） CustomControl 元素（format） CustomEntries 元素 EntrySelectedByView 的 CustomEntry 元素（格式）

## <a name="syntax"></a>语法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `SelectionSetName` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[用于 View 的 CustomControl 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|定义要使用的控件定义必须存在的条件。|

## <a name="text-value"></a>文本值

指定选择集的名称。

## <a name="remarks"></a>备注

选择集是可由格式设置文件所定义的任何视图使用的常用 .NET 对象组。 有关创建和引用选项集的详细信息，请参阅[定义对象集](./defining-selection-sets.md)。

选择条件可以指定选择集或 .NET 类型，但不能同时指定两者。 有关如何使用选择条件的详细信息，请参阅为[数据显示定义条件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另请参阅

[用于 View 的 CustomControl 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[定义显示数据的条件](./defining-conditions-for-displaying-data.md)

[定义选择集](./defining-selection-sets.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
