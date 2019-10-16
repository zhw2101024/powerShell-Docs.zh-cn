---
title: 用于配置（格式）的控件的 ItemSeclectionCondition 的 ScriptBlock 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51f7aec9-7b01-4370-84f4-1e58508a851f
caps.latest.revision: 6
ms.openlocfilehash: e92b2dfff07358132c480c47c34279e5365fe400
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362116"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a>ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)

指定触发条件的脚本。 如果此脚本的计算结果为 `true`，则满足条件，并使用控件。 此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。

Configuration 元素（格式）控制配置（format） CustomControl 元素的控件的配置（Format）控件元素的元素，以控制 CustomControl for configuration （Format） CustomEntries 元素的配置（Format） CustomEntry 元素 for CustomControl for CustomItem 元素 for CustomEntry for 元素 for for ExpressionBinding for configuration CustomItem 元素 for for controlExpressionBinding 的 ItemSelectionCondition 元素，用于配置的控件的 ItemSelectionCondition 的 ScriptBlock 元素（格式）

## <a name="syntax"></a>语法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `ScriptBlock` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[用于配置的控件的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|定义要使用此控件必须存在的条件。|

## <a name="text-value"></a>文本值

指定要评估的脚本。

## <a name="remarks"></a>备注

如果使用此元素，则在定义选择条件时，不能指定[PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)元素。

## <a name="see-also"></a>另请参阅

[用于配置的控件的 ItemSeclectionCondition 的 PropertyName 元素（格式）](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[用于配置的控件的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
