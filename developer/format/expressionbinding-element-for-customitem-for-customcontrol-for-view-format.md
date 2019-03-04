---
title: ExpressionBinding 元素的视图 （格式） 的 CustomControl CustomItem |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860683"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a>ExpressionBinding Element for CustomItem for CustomControl for View (Format)

定义由控件显示的数据。 定义自定义控件视图时，将使用此元素。

视图 （格式） 的视图 （格式） 的视图 (CustomControl CustomEntries CustomEntry 元素 CustomControl CustomEntries 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素格式） 的视图 （格式） 的视图 （格式） 的 CustomControl CustomItem ExpressionBinding 元素 CustomControl CustomEntry CustomItem 元素

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

以下各节描述了特性、 子元素和父元素的`ExpressionBinding`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|`CustomControl Element`|可选元素。<br /><br /> 定义此控件使用的控件。|
|[为视图 （格式） 的 CustomControl ExpressionBinding 的 CustomControlName 元素](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 指定公共控件或视图控件的名称。|
|[为视图 （格式） 的 CustomControl ExpressionBinding 的 EnumerateCollection 元素](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 指定显示的元素的集合。|
|[为视图 （格式） 的 CustomControl ExpressionBinding 的 ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|可选元素。<br /><br /> 定义要在使用此控件中必须存在的条件。|
|[为视图 （格式） 的 CustomControl ExpressionBinding 的 PropertyName 元素](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 指定控件显示其值的.NET 属性。|
|[为视图 （格式） 的 CustomCustomControl ExpressionBinding 的脚本块元素](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 指定控件显示其值的脚本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[为视图 （格式） 的 CustomControl CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|定义由自定义控件视图中显示的数据和显示方式。|

## <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[为视图 （格式） 的 CustomControl ExpressionBinding 的 CustomControlName 元素](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[为视图 （格式） 的 CustomControl ExpressionBinding 的 EnumerateCollection 元素](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[为视图 （格式） 的 CustomControl ExpressionBinding 的 ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[为视图 （格式） 的 CustomControl ExpressionBinding 的 PropertyName 元素](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[为视图 （格式） 的 CustomControl ExpressionBinding 的脚本块元素](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[为视图 （格式） 的 CustomControl CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
