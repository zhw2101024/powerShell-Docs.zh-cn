---
title: ListEntry 的 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eae67e47-6c60-4741-8430-78d2cb6067b1
caps.latest.revision: 10
ms.openlocfilehash: ccfc0b772ad3b2d1979c7c832a5153de870035d7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368396"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a>SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)

指定触发条件的 .NET 类型集。 如果此集中的任何类型存在，则满足条件，并使用此列表视图的定义显示该对象。

配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） ListControl 元素（格式） ListEntries 元素（格式） ListEntry 元素（format） EntrySelectedBy 元素 for ListEntry （Format） SelectionCondition 元素 forEntrySelectedBy for ListEntry （Format） SelectionSetName 元素 for SelectionCondition for EntrySelectedBy for ListEntry （Format）

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
|[ListEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|定义使用此列表视图的定义时必须存在的条件。|

## <a name="text-value"></a>文本值

指定选择集的名称。

## <a name="remarks"></a>备注

选择条件可以指定选择集或 .NET 类型，但不能同时指定两者。 有关如何使用选择条件的详细信息，请参阅为[数据显示定义条件](./defining-conditions-for-displaying-data.md)。

选择集是可由格式设置文件所定义的任何视图使用的常用 .NET 对象组。 有关创建和引用选项集的详细信息，请参阅[定义对象集](./defining-selection-sets.md)。

有关列表视图的其他组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。

## <a name="see-also"></a>另请参阅

[创建列表视图](./creating-a-list-view.md)

[定义显示数据的条件](./defining-conditions-for-displaying-data.md)

[ListEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
