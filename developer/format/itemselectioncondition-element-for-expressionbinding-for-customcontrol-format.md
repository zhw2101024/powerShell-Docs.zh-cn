---
title: CustomControl （格式） 的 ExpressionBinding 的 ItemSelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065806"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a>ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)

定义要在使用此控件中必须存在的条件。 可以为控件项指定的选择条件数目没有限制。 定义自定义控件视图时，将使用此元素。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素 （格式） CustomEntries 元素 CustomControl 视图 （格式） 的视图 （格式） CustomItem 元素 CustomEntries CustomEntry 元素CustomEntry CustomItem CustomControl CustomControl 视图 （格式） 的表达式绑定的视图 （格式） ItemSelectionCondition 元素的视图 （格式） ExpressionBinding 元素

## <a name="syntax"></a>语法

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`ItemSelectionCondition`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[为视图 （格式为 CustomControl ItemSelectionCondition PropertyName 元素](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 指定触发条件的.NET 属性。|
|[为视图 （格式） 的 CustomControl ItemSelectionCondition 的脚本块元素](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 指定触发条件的脚本。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[为视图 （格式） 的 CustomControl CustomItem ExpressionBinding 元素](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|定义由控件显示的数据。|

## <a name="remarks"></a>备注

您可以指定一个属性名称或用于这种情况的脚本，但不能同时指定。

## <a name="see-also"></a>另请参阅

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

[为视图 （格式） 的 CustomControl CustomItem ExpressionBinding 元素](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
