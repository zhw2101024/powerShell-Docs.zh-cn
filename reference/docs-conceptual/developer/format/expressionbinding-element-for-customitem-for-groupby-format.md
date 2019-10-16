---
title: GroupBy （Format）的 CustomItem 的 ExpressionBinding 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368626"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a>ExpressionBinding Element for CustomItem for GroupBy (Format)

定义控件显示的数据。 此元素在定义如何显示新的对象组时使用。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（format）对于 GroupBy （format） CustomEntries 元素，用于元素的 CustomControl 元素（format）CustomControl for groupby （format） CustomItem 元素 for CustomEntry for groupby （format） ExpressionBinding 元素 for GroupBy （Format）

## <a name="syntax"></a>语法

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `ExpressionBinding` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|`CustomControl Element`|可选元素。<br /><br /> 定义此控件使用的控件。|
|[GroupBy 的 ExpressionBinding 的 CustomControlName 元素（格式）](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|可选元素。<br /><br /> 指定公共控件或视图控件的名称。|
|[GroupBy 的 ExpressionBinding 的 EnumerateCollection 元素（格式）](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)GroupBy 的 ExpressionBinding 的 EnumerateCollection 元素（格式）|可选元素。<br /><br /> 指定显示集合的元素。|
|[GroupBy 的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|可选元素。<br /><br /> 定义要使用此控件必须存在的条件。|
|[GroupBy 的 ExpressionBinding 的 PropertyName 元素（Format）](./propertyname-element-for-expressionbinding-for-groupby-format.md)|可选元素。<br /><br /> 指定其值由控件显示的 .NET 属性。|
|[GroupBy 的 ExpressionBinding 的 ScriptBlock 元素（格式）](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|可选元素。<br /><br /> 指定其值由控件显示的脚本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[GroupBy 的 CustomEntry 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-groupby-format.md)|定义自定义控件视图显示的数据及其显示方式。|

## <a name="see-also"></a>另请参阅

[GroupBy 的 ExpressionBinding 的 CustomControlName 元素（格式）](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[GroupBy 的 ExpressionBinding 的 EnumerateCollection 元素（格式）](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[GroupBy 的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[GroupBy 的 ExpressionBinding 的 PropertyName 元素（Format）](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[GroupBy 的 ExpressionBinding 的 ScriptBlock 元素（格式）](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[GroupBy 的 CustomEntry 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-groupby-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
