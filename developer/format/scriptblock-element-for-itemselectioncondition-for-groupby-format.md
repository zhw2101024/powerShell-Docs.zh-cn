---
title: GroupBy （格式） 的 ItemSelectionCondition 的脚本块元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58d25835-4636-4c58-9f6c-0332b9318051
caps.latest.revision: 6
ms.openlocfilehash: 4045196e306e766cd805b3e7ae31bfcb3de184ee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860943"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a>ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)

指定触发条件的脚本。 当此脚本的计算结果为`true`、 满足该条件，并使用该控件。 定义如何显示一组新对象时，将使用此元素。

GroupBy （格式） 的 GroupBy （格式） CustomEntry 元素 CustomControl CustomEntries 元素的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素CustomControl GroupBy （格式） 的 GroupBy （格式） 的 GroupBy （格式） 的 GroupBy （格式） 的脚本块元素 ExpressionBinding ItemSelectionCondition 元素 CustomItem ExpressionBinding 元素 CustomEntry CustomItem 元素GroupBy （格式） 的 ItemSelectionCondition

## <a name="syntax"></a>语法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`ScriptBlock`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[GroupBy （格式） 的 ExpressionBinding 的 ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|定义要在使用此控件中必须存在的条件。|

## <a name="text-value"></a>文本值

指定计算的脚本。

## <a name="remarks"></a>备注

如果使用此元素时，不能指定[PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)元素定义的选择条件时。

## <a name="see-also"></a>另请参阅

[GroupBy （格式） 的 ExpressionBinding 的 ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[GroupBy （格式） 的 ItemSelectionCondition PropertyName 元素](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
