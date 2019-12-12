---
title: 用于视图（格式）的 ExpressionBinding 的 ItemSelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362936"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a>ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)

定义要使用此控件必须存在的条件。 定义可由视图使用的控件时，将使用此元素。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 元素（format） Control 元素 for View （format） CustomControl 元素的控件元素，用于控件的 View （format） CustomEntries 元素CustomControl for view （Format） CustomEntry 元素 for CustomEntries for view （format） CustomItem 元素 for CustomEntry for view （format）元素 for ExpressionBinding for view （format）的控件用于视图的控件的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）

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
|[View 的 ItemSelectionCondition for Controls 的 PropertyName 元素（Format）](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|可选元素。<br /><br /> 指定触发条件的 .NET 属性。|
|[用于视图的控件的 ItemSelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|可选元素。<br /><br /> 指定触发条件的脚本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[用于视图的控件的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|定义控件显示的数据。|

## <a name="remarks"></a>备注

您可以为此条件指定一个属性名称或脚本，但不能同时指定两者。

## <a name="see-also"></a>另请参阅

[View 的 ItemSelectionCondition for Controls 的 PropertyName 元素（Format）](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[用于视图的控件的 ItemSelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[用于视图的控件的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
