---
title: GroupBy （格式） 的 CustomEntry CustomItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066385"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a>CustomItem Element for CustomEntry for GroupBy (Format)

定义由自定义控件视图中显示的数据和显示方式。 定义如何显示一组新对象时，将使用此元素。

GroupBy （格式） 的 GroupBy （格式） CustomItem 元素 CustomControl CustomEntries 元素的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素GroupBy （格式） 的 CustomEntry

## <a name="syntax"></a>语法

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`CustomItem`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[GroupBy （格式） 的 CustomItem ExpressionBinding 元素](./expressionbinding-element-for-customitem-for-groupby-format.md)|可选元素。<br /><br /> 定义由控件显示的数据。|
|[GroupBy （格式） 的 CustomItem 的框架元素](./frame-element-for-customitem-for-groupby-format.md)|可选元素。<br /><br /> 定义由自定义控件视图中显示的数据和显示方式。|
|[GroupBy （格式） 的 CustomItem 的换行元素](./newline-element-for-customitem-for-groupby-format.md)|可选元素。<br /><br /> 将空白的行添加到控件的显示。|
|[GroupBy （格式） 的 CustomItem 的文本元素](./text-element-for-customitem-for-groupby-format.md)|可选元素。<br /><br /> 指定由控件显示的数据的其他文本。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[GroupBy （格式） 的 CustomControl CustomEntry 元素](./customentry-element-for-customcontrol-for-groupby-format.md)|提供自定义控件视图的定义。|

## <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[GroupBy （格式） 的 CustomControl CustomEntry 元素](./customentry-element-for-customcontrol-for-groupby-format.md)

[GroupBy （格式） 的 CustomItem ExpressionBinding 元素](./expressionbinding-element-for-customitem-for-groupby-format.md)

[GroupBy （格式） 的 CustomItem 的框架元素](./frame-element-for-customitem-for-groupby-format.md)

[GroupBy （格式） 的 CustomItem 的换行元素](./newline-element-for-customitem-for-groupby-format.md)

[GroupBy （格式） 的 CustomItem 的文本元素](./text-element-for-customitem-for-groupby-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
