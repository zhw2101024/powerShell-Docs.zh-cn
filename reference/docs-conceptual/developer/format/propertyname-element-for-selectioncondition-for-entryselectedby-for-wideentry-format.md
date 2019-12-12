---
title: WideEntry 的 SelectionCondition for EntrySelectedBy 的 PropertyName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 340abb12-6df1-42f4-bdae-b0509c90952c
caps.latest.revision: 11
ms.openlocfilehash: 196877b97db9ed0592e357486c1318dc1e7efd31
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362236"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a>PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)

指定触发条件的 .NET 属性。 如果该属性存在或其计算结果为 `true`，则满足条件，并使用定义。

配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（format） EntrySelectedBy 元素 for WideEntry （Format） SelectionCondition 元素 forSelectionCondition for EntrySelectedBy for WideEntry 的 WideEntry （Format） PropertyName 元素的 EntrySelectedBy （Format）

## <a name="syntax"></a>语法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `PropertyName` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[WideEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|定义要使用此定义必须存在的条件。|

## <a name="text-value"></a>文本值

指定 .NET 属性名称。

## <a name="remarks"></a>备注

选择条件必须指定至少一个要计算的属性名称或脚本，但不能同时指定两者。 有关如何使用选择条件的详细信息，请参阅为[数据显示定义条件](./defining-conditions-for-displaying-data.md)。

有关大视图的其他组件的详细信息，请参阅[宽视图](./creating-a-wide-view.md)。

## <a name="see-also"></a>另请参阅

[创建宽视图](./creating-a-wide-view.md)

[定义显示数据的条件](./defining-conditions-for-displaying-data.md)

[WideEntry 的 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[WideEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
