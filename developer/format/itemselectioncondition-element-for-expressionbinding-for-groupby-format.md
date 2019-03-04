---
title: GroupBy （格式） 的 ExpressionBinding 的 ItemSelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853133"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a>ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)

定义要在使用此控件中必须存在的条件。 可以为控件项指定的选择条件数目没有限制。 定义如何显示一组新对象时，将使用此元素。

GroupBy （格式） 的 GroupBy （格式） CustomEntry 元素 CustomControl CustomEntries 元素的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素CustomControl ExpressionBinding 的 GroupBy （格式） 的 GroupBy （格式） ItemSelectionCondition 元素 CustomItem GroupBy （格式） ExpressionBinding 元素 CustomEntry GroupBy （格式） CustomItem 元素

## <a name="syntax"></a>语法

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`ItemSelectionCondition`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[GroupBy （格式） 的 ItemSelectionCondition PropertyName 元素](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|可选元素。<br /><br /> 指定触发条件的.NET 属性。|
|[GroupBy （格式） 的 ItemSelectionCondition 的脚本块元素](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|可选元素。<br /><br /> 指定触发条件的脚本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[GroupBy （格式） 的 CustomItem ExpressionBinding 元素](./expressionbinding-element-for-customitem-for-groupby-format.md)|定义由控件显示的数据。|

## <a name="remarks"></a>备注

您可以指定一个属性名称或用于这种情况的脚本，但不能同时指定。

## <a name="see-also"></a>另请参阅

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

[GroupBy （格式） 的 CustomItem ExpressionBinding 元素](./expressionbinding-element-for-customitem-for-groupby-format.md)
