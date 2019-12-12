---
title: 用于配置的控件（格式）的 CustomEntry 的 EntrySelectedBy 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368766"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a>EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)

定义使用公共控件定义的 .NET 类型或要使用此控件必须存在的条件。 此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。

Configuration 元素（格式）控制配置（format） CustomControl 元素的控件的配置（Format）控件元素的元素，以控制 CustomControl for configuration （Format） CustomEntries 元素的配置（Format） CustomEntry 元素 for CustomControl for EntrySelectedBy 元素 for 元素 for CustomEntry for control for control （Format）

## <a name="syntax"></a>语法

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `EntrySelectedBy` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[用于配置的控件的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 定义要使用的公共控件定义必须存在的条件。|
|[用于配置的控件的 EntrySelectedBy 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 指定一组使用此公共控件定义的 .NET 类型。|
|[用于配置的控件的 EntrySelectedBy 的 TypeName 元素（格式）](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 指定使用此公共控件定义的 .NET 类型。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[用于配置的控件的 CustomControl 的 CustomEntry 元素（格式）](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|提供公共控件的定义。|

## <a name="remarks"></a>备注

每个定义至少必须指定一个 .NET 类型、选择集或选择条件。 对于可以指定的类型、选择集或选择条件的数量没有最大限制。

## <a name="see-also"></a>另请参阅

[用于配置的控件的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[用于配置的控件的 EntrySelectedBy 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[用于配置的控件的 CustomControl 的 CustomEntry 元素（格式）](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[用于配置的控件的 EntrySelectedBy 的 TypeName 元素（格式）](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
