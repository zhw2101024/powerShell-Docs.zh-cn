---
title: 配置 （格式） 的控件的 EntrySelectedBy SelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075760"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a>SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)

定义必须存在要使用的常见控件定义的条件。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

配置 （格式） 的配置 （格式） 的 Controls 的 CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素配置 （格式） 的 Controls 的配置 （格式） 的 Controls 的配置 （格式） SelectionCondition 元素，用于为 CustomEntry 的 EntrySelectedBy CustomEntry EntrySelectedBy 元素 CustomControl CustomEntry 元素配置 （格式）

## <a name="syntax"></a>语法

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`SelectionCondition`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[SelectionCondition 配置 （格式） 的控件的属性名称元素](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 指定触发条件的.NET 属性。|
|[SelectionCondition 的 Controls 的配置 （格式） 的脚本块元素](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 指定触发条件的脚本。|
|[配置 （格式） 的控件的 SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 指定触发条件的.NET 类型集。|
|[SelectionCondition 配置 （格式） 的控件的类型名称元素](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 指定触发条件的.NET 类型。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[配置 （格式） 的控件的 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|定义使用常见的控件定义的此项的.NET 类型。|

## <a name="remarks"></a>备注

定义选择条件时，必须遵循以下准则：

- 选择条件必须指定至少一个属性名或脚本块，但不能同时指定。

- 选择条件可以指定任意数量的.NET 类型，或者选择设置，但不能同时指定。

有关如何使用选择条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另请参阅

[SelectionCondition 配置 （格式） 的控件的属性名称元素](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[SelectionCondition 的 Controls 的配置 （格式） 的脚本块元素](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[配置 （格式） 的控件的 SelectionCondition SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[SelectionCondition 配置 （格式） 的控件的类型名称元素](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[配置 （格式） 的控件的 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[编写 Windows PowerShell 格式设置和文件类型](./writing-a-powershell-formatting-file.md)
