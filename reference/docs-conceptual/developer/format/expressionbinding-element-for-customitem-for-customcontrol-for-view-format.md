---
title: 用于 CustomControl for View （Format）的 CustomItem 的 ExpressionBinding 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363146"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a>ExpressionBinding Element for CustomItem for CustomControl for View (Format)

定义控件显示的数据。 定义自定义控件视图时，将使用此元素。

Configuration Element （Format） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素 for View （format） CustomEntries 元素 for CustomControl for CustomEntry for CustomEntries for View （Format） CustomControl 元素 for view （Format） CustomItem 元素 for CustomEntry for CustomControl for view （Format） ExpressionBinding 元素 for CustomItem for CustomControl for View （Format）

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
|[用于 View 的 CustomControl 的 ExpressionBinding 的 CustomControlName 元素（格式）](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 指定公共控件或视图控件的名称。|
|[用于 View 的 CustomControl 的 ExpressionBinding 的 EnumerateCollection 元素（格式）](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 指定显示集合的元素。|
|[用于 View 的 CustomControl 的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|可选元素。<br /><br /> 定义要使用此控件必须存在的条件。|
|[View 的 ExpressionBinding for CustomControl 的 PropertyName 元素（Format）](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 指定其值由控件显示的 .NET 属性。|
|[用于 View 的 ExpressionBinding for CustomCustomControl 的 ScriptBlock 元素（格式）](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 指定其值由控件显示的脚本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[用于 View 的 CustomControl 的 CustomEntry 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|定义自定义控件视图显示的数据及其显示方式。|

## <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[用于 View 的 CustomControl 的 ExpressionBinding 的 CustomControlName 元素（格式）](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[用于 View 的 CustomControl 的 ExpressionBinding 的 EnumerateCollection 元素（格式）](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[用于 View 的 CustomControl 的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[View 的 ExpressionBinding for CustomControl 的 PropertyName 元素（Format）](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[用于 View 的 ExpressionBinding for CustomControl 的 ScriptBlock 元素（格式）](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[用于 View 的 CustomControl 的 CustomEntry 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
