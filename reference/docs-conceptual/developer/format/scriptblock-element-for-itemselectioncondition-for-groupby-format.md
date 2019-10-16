---
title: GroupBy 的 ItemSelectionCondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58d25835-4636-4c58-9f6c-0332b9318051
caps.latest.revision: 6
ms.openlocfilehash: 4045196e306e766cd805b3e7ae31bfcb3de184ee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364826"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a>ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)

指定触发条件的脚本。 如果此脚本的计算结果为 `true`，则满足条件，并使用控件。 此元素在定义如何显示新的对象组时使用。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（format）对于 GroupBy （format） CustomEntries 元素，用于元素的 CustomControl 元素（format）CustomControl for GroupBy （format） CustomItem 元素 for CustomEntry for groupby （format） ExpressionBinding 元素 for CustomItem for groupby （format） ScriptBlock 元素 for ItemSelectionCondition for groupby （format） ScriptBlock 元素ItemSelectionCondition for GroupBy （Format）

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
|[GroupBy 的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|定义要使用此控件必须存在的条件。|

## <a name="text-value"></a>文本值

指定要评估的脚本。

## <a name="remarks"></a>备注

如果使用此元素，则在定义选择条件时，不能指定[PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)元素。

## <a name="see-also"></a>另请参阅

[GroupBy 的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[GroupBy 的 ItemSelectionCondition 的 PropertyName 元素（Format）](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
