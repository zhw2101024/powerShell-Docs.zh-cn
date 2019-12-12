---
title: GroupBy （Format）的 ExpressionBinding 的 ItemSelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365286"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a>ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)

定义要使用此控件必须存在的条件。 对于可为控件项指定的选择条件数没有限制。 此元素在定义如何显示新的对象组时使用。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（format）对于 GroupBy （format） CustomEntries 元素，用于元素的 CustomControl 元素（format）CustomControl for groupby （format） CustomItem 元素 for CustomEntry for groupby （format） ExpressionBinding 元素 for CustomItem for groupby （format） ItemSelectionCondition 元素 for groupby （Format）

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
|[GroupBy 的 ItemSelectionCondition 的 PropertyName 元素（Format）](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|可选元素。<br /><br /> 指定触发条件的 .NET 属性。|
|[GroupBy 的 ItemSelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|可选元素。<br /><br /> 指定触发条件的脚本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[GroupBy 的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-groupby-format.md)|定义控件显示的数据。|

## <a name="remarks"></a>备注

您可以为此条件指定一个属性名称或脚本，但不能同时指定两者。

## <a name="see-also"></a>另请参阅

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

[GroupBy 的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-groupby-format.md)
