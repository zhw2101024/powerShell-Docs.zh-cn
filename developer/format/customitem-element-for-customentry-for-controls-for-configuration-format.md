---
title: 配置 （格式） 的控件的 CustomEntry CustomItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066424"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a>CustomItem Element for CustomEntry for Controls for Configuration (Format)

定义由控件显示的数据和显示方式。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

配置 （格式） 的配置 （格式） 的配置 （CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素CustomControl CustomEntry 的 Controls 的配置的配置 （格式） CustomItem 元素的控件的格式） CustomEntry 元素

## <a name="syntax"></a>语法

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`CustomItem`元素。 有关详细信息，请参阅备注。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[配置 （格式） 的控件的 CustomItem ExpressionBinding 元素](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 定义由控件显示的数据。|
|[CustomItem 配置 （格式） 的控件的框架元素](./frame-element-for-customitem-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 定义如何显示数据，如向左或向右移位数据。|
|[配置 （格式） 的控件的 CustomItem 的换行元素](./newline-element-for-customitem-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 将空白的行添加到控件的显示。|
|[CustomItem 配置 （格式） 的控件的文本元素](./text-element-for-customitem-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 向控件显示的文本，例如圆括号或大括号。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[配置 （格式） 的控件的 CustomControl CustomEntry 元素](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|提供控件的定义。|

## <a name="remarks"></a>备注

指定的子元素时`CustomItem`元素，请记住以下：

- 必须按以下顺序添加的子元素： `ExpressionBinding`， `NewLine`， `Text`，和`Frame`。

- 可以指定的序列数没有最大限制。

- 在每个序列中，没有最大限制数`ExpressionBinding`可以使用的元素。

## <a name="see-also"></a>另请参阅

[配置 （格式） 的控件的 CustomItem ExpressionBinding 元素](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[CustomItem 配置 （格式） 的控件的框架元素](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[配置 （格式） 的控件的 CustomItem 的换行元素](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[CustomItem 配置 （格式） 的控件的文本元素](./text-element-for-customitem-for-controls-for-configuration-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
