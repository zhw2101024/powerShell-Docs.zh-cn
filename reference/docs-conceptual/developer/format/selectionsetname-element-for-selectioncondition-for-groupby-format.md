---
title: GroupBy （Format）的 SelectionCondition 的 SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361856"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a>SelectionSetName Element for SelectionCondition for GroupBy (Format)

指定触发条件的 .NET 类型集。 如果此集中的任何类型存在，则满足条件，并使用此控件显示该对象。 此元素在定义如何显示新的对象组时使用。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（format）对于 GroupBy （format） CustomEntries 元素，用于元素的 CustomControl 元素（format）CustomControl for groupby （format） EntrySelectedBy 元素 for CustomEntry for groupby （format） SelectionCondition 元素 for EntrySelectedBy for groupby （format） SelectionSetName 元素 for groupby （Format）

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
|[GroupBy 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|定义要使用的控件定义必须存在的条件。|

## <a name="text-value"></a>文本值

指定选择集的名称。

## <a name="remarks"></a>备注

选择集是可由格式设置文件所定义的任何视图使用的常用 .NET 对象组。 有关创建和引用选项集的详细信息，请参阅[定义选择集](./defining-selection-sets.md)。

如果指定此元素，则不能指定[TypeName](./typename-element-for-selectioncondition-for-groupby-format.md)元素。 有关定义选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另请参阅

[GroupBy 的 SelectionCondition 的 TypeName 元素（Format）](./typename-element-for-selectioncondition-for-groupby-format.md)

[GroupBy 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[定义显示数据的条件](./defining-conditions-for-displaying-data.md)

[定义选择集](./defining-selection-sets.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
