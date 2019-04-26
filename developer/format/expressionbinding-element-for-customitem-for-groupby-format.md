---
title: GroupBy （格式） 的 CustomItem ExpressionBinding 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065897"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a>ExpressionBinding Element for CustomItem for GroupBy (Format)

定义由控件显示的数据。 定义如何显示一组新对象时，将使用此元素。

GroupBy （格式） 的 GroupBy （格式） CustomEntry 元素 CustomControl CustomEntries 元素的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素CustomControl GroupBy （格式） 的 GroupBy （格式） 的 GroupBy （格式） 的 CustomItem ExpressionBinding 元素 CustomEntry CustomItem 元素

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
|[GroupBy （格式） 的 ExpressionBinding 的 CustomControlName 元素](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|可选元素。<br /><br /> 指定公共控件或视图控件的名称。|
|[GroupBy （格式） 的 ExpressionBinding 的 EnumerateCollection 元素](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)GroupBy （格式） 的 ExpressionBinding 的 EnumerateCollection 元素|可选元素。<br /><br /> 指定显示的元素的集合。|
|[GroupBy （格式） 的 ExpressionBinding 的 ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|可选元素。<br /><br /> 定义要在使用此控件中必须存在的条件。|
|[GroupBy （格式） 的 ExpressionBinding 的 PropertyName 元素](./propertyname-element-for-expressionbinding-for-groupby-format.md)|可选元素。<br /><br /> 指定控件显示其值的.NET 属性。|
|[ExpressionBinding 的 GroupBy （格式） 的脚本块元素](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|可选元素。<br /><br /> 指定控件显示其值的脚本。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[GroupBy （格式） 的 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-groupby-format.md)|定义由自定义控件视图中显示的数据和显示方式。|

## <a name="see-also"></a>另请参阅

[GroupBy （格式） 的 ExpressionBinding 的 CustomControlName 元素](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[GroupBy （格式） 的 ExpressionBinding 的 EnumerateCollection 元素](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[GroupBy （格式） 的 ExpressionBinding 的 ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[GroupBy （格式） 的 ExpressionBinding 的 PropertyName 元素](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[ExpressionBinding 的 GroupBy （格式） 的脚本块元素](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[GroupBy （格式） 的 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-groupby-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
