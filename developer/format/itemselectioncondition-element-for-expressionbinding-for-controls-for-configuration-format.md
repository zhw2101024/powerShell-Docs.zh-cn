---
title: 配置 （格式） 的控件的 ExpressionBinding 的 ItemSelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd3ddc33-b21c-4464-b3f2-a78dbe0062a8
caps.latest.revision: 8
ms.openlocfilehash: 4865d716ebe0460b662253a3019e93e82428b882
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065491"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a>ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)

定义要在使用此控件中必须存在的条件。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

配置 （格式） 的配置 （格式） 的配置 （CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素CustomControl CustomEntry 配置 ExpressionBinding CustomItem 配置 （格式） 的控件元素的控件的配置 （格式） CustomItem 元素的控件的格式） CustomEntry 元素配置 （格式） 的控件的 ExpressionBinding 的 ItemSelectionCondition 元素

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
|[ItemSelectionCondition 配置 （格式） 的控件的属性名称元素](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 指定触发条件的.NET 属性。|
|[ItemSelectionCondition 的 Controls 的配置 （格式） 的脚本块元素](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 指定触发条件的脚本。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[配置 （格式） 的控件的 CustomItem ExpressionBinding 元素](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|定义由控件显示的数据。|

## <a name="remarks"></a>备注

您可以指定一个属性名称或用于这种情况的脚本，但不能同时指定。

## <a name="see-also"></a>另请参阅

[ItemSelectionCondition 配置 （格式） 的控件的属性名称元素](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[ItemSelectionCondition 的 Controls 的配置 （格式） 的脚本块元素](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[配置 （格式） 的控件的 CustomItem ExpressionBinding 元素](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
