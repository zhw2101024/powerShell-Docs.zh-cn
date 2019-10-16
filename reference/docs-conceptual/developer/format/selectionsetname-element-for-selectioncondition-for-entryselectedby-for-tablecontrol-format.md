---
title: TableControl 的 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ae4d6b-dc95-4a1d-8e32-31ff084a951f
caps.latest.revision: 10
ms.openlocfilehash: edb163f2b0b5129bd741677dce882888d9bbfd89
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361916"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a>SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)

指定触发条件的 .NET 类型集。 如果此集中的任何类型存在，则满足条件，并使用表视图的这一定义显示该对象。

用于 EntrySelectedBy 的配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） TableControl 元素（格式） TableRowEntries 元素（格式） TableRowEntry 元素（format） TableRowEntry 元素（格式）SelectionCondition for EntrySelectedBy 的 TableRowEntry （Format） SelectionSetName 元素的 EntrySelectedBy 的 SelectionCondition 元素（Format）

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
|[TableRowEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|定义必须存在才能用于此表视图定义的条件。|

## <a name="text-value"></a>文本值

指定选择集的名称。

## <a name="remarks"></a>备注

选择条件可以指定选择集或 .NET 类型，但不能同时指定两者。 有关如何使用选择条件的详细信息，请参阅为[数据显示定义条件](./defining-conditions-for-displaying-data.md)。

选择集是可由格式设置文件所定义的任何视图使用的常用 .NET 对象组。 有关创建和引用选项集的详细信息，请参阅[定义对象集](./defining-selection-sets.md)。

有关大视图的其他组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。

## <a name="see-also"></a>另请参阅

[创建表视图](./creating-a-table-view.md)

[定义显示数据的条件](./defining-conditions-for-displaying-data.md)

[TableRowEntry 的 SelectionCondition for EntrySelectedBy 的 TypeName 元素（Format）](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[TableRowEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
