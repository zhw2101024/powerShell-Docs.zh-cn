---
title: PropertyName 元素的视图 （格式） 的 CustomControl ItemSelectionCondition |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b12006-8d52-486b-91a3-e6224ca80e56
caps.latest.revision: 6
ms.openlocfilehash: 52d0b0816eaef6752220e0c3b1249e5a0e44a3ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064860"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a>PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)

指定触发条件的.NET 属性。 存在此属性时或当计算结果为`true`、 满足该条件，并使用该控件。 定义自定义控件视图时，将使用此元素。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素 （格式） CustomEntries 元素 CustomControl 视图 （格式） 的视图 （格式） CustomItem 元素 CustomEntries CustomEntry 元素CustomEntry 视图 （格式） 的视图 （格式） 的 ItemSelectionCondition PropertyName 元素 CustomControl 表达式绑定的视图 （格式） ItemSelectionCondition 元素 CustomControl CustomItem ExpressionBinding 元素视图 （格式为 CustomControl

## <a name="syntax"></a>语法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`PropertyName`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[视图 （格式） 的表达式绑定的 CustomControl ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|定义要在使用此控件中必须存在的条件。|

## <a name="text-value"></a>文本值

指定触发条件的.NET 属性的名称。

## <a name="remarks"></a>备注

如果使用此元素时，不能指定[ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)元素定义的选择条件时。

## <a name="see-also"></a>另请参阅

[为视图 （格式） 的 CustomControl ItemSelectionCondition 的脚本块元素](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[视图 （格式） 的表达式绑定的 CustomControl ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
