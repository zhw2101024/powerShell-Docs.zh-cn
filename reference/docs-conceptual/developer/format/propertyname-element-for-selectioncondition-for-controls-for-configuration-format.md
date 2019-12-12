---
title: 用于配置（格式）的控件的 SelectionCondition 的 PropertyName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec048408-e1c6-41ef-b39b-72f4c2dcf2ac
caps.latest.revision: 6
ms.openlocfilehash: b4b2440fdb7171d09fdc16ac7cc4f25ed1a4bb78
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362396"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a>PropertyName Element for SelectionCondition for Controls for Configuration (Format)

指定触发条件的 .NET 属性。 如果该属性存在或其计算结果为 `true`，则满足条件，并使用该条目。 此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。

Configuration 元素（格式）控制配置（format） CustomControl 元素的控件的配置（Format）控件元素的元素，以控制 CustomControl for configuration （Format） CustomEntries 元素的配置（Format） CustomEntry 的 CustomControl 的元素，用于配置（Format） EntrySelectedBy 元素 for CustomEntry 的控件（format）元素 for for SelectionCondition for EntrySelectedBy 的控件（Format）用于 ListEntry 的 SelectionCondition for EntrySelectedBy 的 PropertyName 元素（Format）

## <a name="syntax"></a>语法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
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
|[用于配置的控件的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|定义要使用的公共控件定义必须存在的条件。|

## <a name="text-value"></a>文本值

指定 .NET 属性名称。

## <a name="remarks"></a>备注

选择条件必须指定至少一个属性名称或脚本，但不能同时指定两者。 有关如何使用选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另请参阅

[用于配置的控件的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
