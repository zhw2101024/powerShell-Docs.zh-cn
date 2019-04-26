---
title: ExpressionBinding 元素视图 （格式） 的控件的 CustomItem |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065933"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a>ExpressionBinding Element for CustomItem for Controls for View (Format)

定义由控件显示的数据。 定义一个视图，可以使用的控件时，将使用此元素。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 控件元素 （格式） 控制元素的控件的视图 （格式） CustomEntries 元素的控件的控件的视图 （格式） CustomControl 元素CustomControl CustomEntries CustomEntry CustomItem 视图 （格式） 的控件的视图 （格式） ExpressionBinding 元素的控件的视图 （格式） CustomItem 元素的控件的视图 （格式） CustomEntry 元素

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

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`ExpressionBinding`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|`CustomControl Element`|可选元素。<br /><br /> 定义此控件使用的控件。|
|[ExpressionBinding 的 Controls 的视图 （格式） 的 CustomControlName 元素](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|可选元素。<br /><br /> 指定公共控件或视图控件的名称。|
|[ExpressionBinding 的 Controls 的视图 （格式） 的 EnumerateCollection 元素](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|可选元素。<br /><br /> 指定显示的元素的集合。|
|[ExpressionBinding 的 Controls 的视图 （格式） 的 ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|可选元素。<br /><br /> 定义要在使用此控件中必须存在的条件。|
|[ExpressionBinding 的视图 （格式） 的控件的属性名称元素](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|可选元素。<br /><br /> 指定控件显示其值的.NET 属性。|
|[ExpressionBinding 的 Controls 的视图 （格式） 的脚本块元素](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|可选元素。<br /><br /> 指定控件显示其值的脚本。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[视图 （格式） 的控件的 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-controls-for-view-format.md)|定义由控件显示的数据和显示方式。|

## <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[视图 （格式） 的控件的 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-controls-for-view-format.md)

[ExpressionBinding 的 Controls 的视图 （格式） 的 CustomControlName 元素](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[ExpressionBinding 的 Controls 的视图 （格式） 的 EnumerateCollection 元素](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[ExpressionBinding 的 Controls 的视图 （格式） 的 ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[ExpressionBinding 的视图 （格式） 的控件的属性名称元素](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[ExpressionBinding 的 Controls 的视图 （格式） 的脚本块元素](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
