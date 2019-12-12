---
title: 用于配置的控件（格式）的 ExpressionBinding 的 ItemSelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd3ddc33-b21c-4464-b3f2-a78dbe0062a8
caps.latest.revision: 8
ms.openlocfilehash: 4865d716ebe0460b662253a3019e93e82428b882
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362916"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a>ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)

定义要使用此控件必须存在的条件。 此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。

Configuration 元素（格式）控制配置（format） CustomControl 元素的控件的配置（Format）控件元素的元素，以控制 CustomControl for configuration （Format） CustomEntries 元素的配置（Format） CustomEntry 元素 for CustomControl for CustomItem 元素 for CustomEntry for 元素 for for ExpressionBinding for configuration CustomItem 元素 for for control用于配置的控件的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）

## <a name="syntax"></a>语法

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `ItemSelectionCondition` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[用于配置的控件的 ItemSelectionCondition 的 PropertyName 元素（格式）](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 指定触发条件的 .NET 属性。|
|[用于配置的控件的 ItemSelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 指定触发条件的脚本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[用于配置的控件的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|定义控件显示的数据。|

## <a name="remarks"></a>备注

您可以为此条件指定一个属性名称或脚本，但不能同时指定两者。

## <a name="see-also"></a>另请参阅

[用于配置的控件的 ItemSelectionCondition 的 PropertyName 元素（格式）](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[用于配置的控件的 ItemSelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[用于配置的控件的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
