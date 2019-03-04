---
title: ItemSelectionCondition 视图 （格式） 的控件的属性名称元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3955bc-f3a1-4ef6-86ac-80ffc133ad1b
caps.latest.revision: 6
ms.openlocfilehash: 28ad31be4be7be20f1f43ea1b69ad5d294de86f6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857623"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a>PropertyName Element for ItemSelectionCondition for Controls for View (Format)

指定触发条件的.NET 属性。 存在此属性时或当计算结果为`true`、 满足该条件，并使用该控件。 定义一个视图，可以使用的控件时，将使用此元素。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 控件元素 （格式） 控制元素的控件的视图 （格式） CustomEntries 元素的控件的控件的视图 （格式） CustomControl 元素CustomControl CustomEntries CustomEntry CustomItem 视图 （格式） 的控件的视图 （格式） ExpressionBinding 元素的控件的视图 （格式） CustomItem 元素的控件的视图 （格式） CustomEntry 元素ExpressionBinding ItemSelectionCondition 视图 （格式） 的控件的视图 （格式） PropertyName 元素的控件的 ItemSelectionCondition 元素

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
|[ExpressionBinding 的 Controls 的视图 （格式） 的 ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|定义要在使用此控件中必须存在的条件。|

## <a name="text-value"></a>文本值

指定触发条件的.NET 属性的名称。

## <a name="remarks"></a>备注

如果使用此元素时，不能指定[ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)元素定义的选择条件时。

## <a name="see-also"></a>另请参阅

[ItemSelectionCondition 的 Controls 的视图 （格式） 的脚本块元素](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[ExpressionBinding 的 Controls 的视图 （格式） 的 ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
