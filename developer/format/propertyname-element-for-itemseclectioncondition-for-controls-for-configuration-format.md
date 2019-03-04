---
title: ItemSeclectionCondition 配置 （格式） 的控件的属性名称元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad8ab181-c559-492e-a0cf-299e381fdcc3
caps.latest.revision: 6
ms.openlocfilehash: ce25789bdfc2679372ca9e42f99dcc6a30ae2def
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860923"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a>PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)

指定触发条件的.NET 属性。 存在此属性时或当计算结果为`true`、 满足该条件，并使用该控件。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

配置 （格式） 的配置 （格式） 的配置 （CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素CustomControl CustomEntry 配置 ExpressionBinding CustomItem 配置 （格式） 的控件元素的控件的配置 （格式） CustomItem 元素的控件的格式） CustomEntry 元素ExpressionBinding ItemSeclectionCondition 的 Controls 的配置 （格式） 的配置 （格式） PropertyName 元素的控件的 ItemSelectionCondition 元素

## <a name="syntax"></a>语法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`PropertyName`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[配置 （格式） 的控件的 ExpressionBinding 的 ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|定义要在使用此控件中必须存在的条件。|

## <a name="text-value"></a>文本值

指定触发条件的.NET 属性的名称。

## <a name="remarks"></a>备注

如果使用此元素时，不能指定[ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)元素定义的选择条件时。

## <a name="see-also"></a>另请参阅

[ItemSeclectionCondition 的 Controls 的配置 （格式） 的脚本块元素](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[配置 （格式） 的控件的 ExpressionBinding 的 ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
