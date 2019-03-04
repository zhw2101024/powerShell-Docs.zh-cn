---
title: 配置 （格式） 的控件的 CustomItem ExpressionBinding 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855133"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a>ExpressionBinding Element for CustomItem for Controls for Configuration (Format)

定义由控件显示的数据。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

配置 （格式） 的配置 （格式） 的配置 （CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素CustomControl CustomEntry 配置 ExpressionBinding CustomItem 配置 （格式） 的控件元素的控件的配置 （格式） CustomItem 元素的控件的格式） CustomEntry 元素

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
|[配置 （格式） 的控件的 ExpressionBinding 的 CustomControlName 元素](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 指定公共控件或视图控件的名称。|
|[配置 （格式） 的控件的 ExpressionBinding 的 EnumerateCollection 元素](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 指定控件将显示个集合的元素。|
|[配置 （格式） 的控件的 ExpressionBinding 的 ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 定义要在使用此公共控件中必须存在的条件。|
|[ExpressionBinding 的配置 （格式） 的控件的属性名称元素](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 指定其值显示的一个常用的控件的.NET 属性。|
|[ExpressionBinding 的 Controls 的配置 （格式） 的脚本块元素](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 指定其值显示的一个常用的控件的脚本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[有关配置控件 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|定义由自定义控件视图中显示的数据和显示方式。|

## <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[有关配置控件 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
