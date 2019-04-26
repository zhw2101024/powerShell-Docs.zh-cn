---
title: ExpressionBinding 的 Controls 的视图 （格式） 的 ItemSelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065472"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a>ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)

定义要在使用此控件中必须存在的条件。 定义一个视图，可以使用的控件时，将使用此元素。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 控件元素 （格式） 控制元素的控件的视图 （格式） CustomEntries 元素的控件的控件的视图 （格式） CustomControl 元素CustomControl CustomEntries CustomEntry CustomItem 视图 （格式） 的控件的视图 （格式） ExpressionBinding 元素的控件的视图 （格式） CustomItem 元素的控件的视图 （格式） CustomEntry 元素ExpressionBinding 的 Controls 的视图 （格式） 的 ItemSelectionCondition 元素

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
|[ItemSelectionCondition 视图 （格式） 的控件的属性名称元素](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|可选元素。<br /><br /> 指定触发条件的.NET 属性。|
|[ItemSelectionCondition 的 Controls 的视图 （格式） 的脚本块元素](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|可选元素。<br /><br /> 指定触发条件的脚本。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[ExpressionBinding CustomItem 视图 （格式） 的控件元素](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|定义由控件显示的数据。|

## <a name="remarks"></a>备注

您可以指定一个属性名称或用于这种情况的脚本，但不能同时指定。

## <a name="see-also"></a>另请参阅

[ItemSelectionCondition 视图 （格式） 的控件的属性名称元素](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[ItemSelectionCondition 的 Controls 的视图 （格式） 的脚本块元素](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[ExpressionBinding CustomItem 视图 （格式） 的控件元素](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
