---
title: WideControl （Format）的 EntrySelectedBy 的 SelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364776"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a>SelectionCondition Element for EntrySelectedBy for WideControl (Format)

定义要使用此定义必须存在的条件。 对于可为宽输入定义指定的选择条件数没有限制。

配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（format） EntrySelectedBy 元素 for WideEntry （Format） SelectionCondition 元素 forEntrySelectedBy for WideEntry （Format）

## <a name="syntax"></a>语法

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `SelectionCondition` 元素的属性、子元素和父元素。 必须指定单个 `PropertyName` 或 `ScriptBlock` 元素。 `SelectionSetName` 和 `TypeName` 元素是可选的。 可以指定任一元素中的一个。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[WideEntry 的 SelectionCondition for EntrySelectedBy 的 PropertyName 元素（Format）](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|可选元素。<br /><br /> 指定触发条件的 .NET 属性。|
|[WideEntry 的 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|可选元素。<br /><br /> 指定触发条件的脚本块。|
|[WideEntry 的 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素（Format）](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|可选元素。<br /><br /> 指定触发条件的 .NET 类型集。|
|[WideEntry 的 SelectionCondition for EntrySelectedBy 的 TypeName 元素（Format）](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|可选元素。<br /><br /> 指定触发条件的 .NET 类型。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[WideEntry 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-wideentry-format.md)|定义使用此宽项的 .NET 类型或此项要使用的条件。|

## <a name="remarks"></a>备注

每个宽条目都必须定义至少一个类型名称、选择集或选择条件。

定义选择条件时，需要满足以下要求：

- 选择条件必须指定至少一个属性名称或脚本块，但不能同时指定两者。

- 选择条件可以指定任意数量的 .NET 类型或选择集，但是不能同时指定两者。

有关如何使用选择条件的详细信息，请参阅[定义使用视图条目或项的条件](./defining-conditions-for-displaying-data.md)。

有关大视图的其他组件的详细信息，请参阅[创建宽视图](./creating-a-wide-view.md)。

## <a name="see-also"></a>另请参阅

[创建宽视图](./creating-a-wide-view.md)

[定义显示数据的条件](./defining-conditions-for-displaying-data.md)

[WideEntry 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-wideentry-format.md)

[WideEntry 的 SelectionCondition for EntrySelectedBy 的 PropertyName 元素（Format）](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[WideEntry 的 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[WideEntry 的 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素（Format）](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[WideEntry 的 SelectionCondition for EntrySelectedBy 的 TypeName 元素（Format）](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
