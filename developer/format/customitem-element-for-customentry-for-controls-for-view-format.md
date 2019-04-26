---
title: 视图 （格式） 的控件的 CustomEntry CustomItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066373"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a>CustomItem Element for CustomEntry for Controls for View (Format)

定义由控件显示的数据和显示方式。 定义一个视图，可以使用的控件时，将使用此元素。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 控件元素 （格式） 控制元素的控件的视图 （格式） CustomEntries 元素的控件的控件的视图 （格式） CustomControl 元素CustomControl CustomEntries CustomEntry 视图 （格式） 的控件的视图 （格式） CustomItem 元素的控件的视图 （格式） CustomEntry 元素

## <a name="syntax"></a>语法

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`CustomItem`元素。 有关详细信息，请参阅备注。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[ExpressionBinding CustomItem 视图 （格式） 的控件元素](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|可选元素。<br /><br /> 定义由控件显示的数据。|
|[CustomItem 视图 （格式） 的控件的框架元素](./frame-element-for-customitem-for-controls-for-view-format.md)|可选元素。<br /><br /> 定义如何显示数据，如向左或向右移位数据。|
|[CustomItem 视图 （格式） 的控件的新行元素](./newline-element-for-customitem-for-controls-for-view-format.md)|可选元素。<br /><br /> 将空白的行添加到控件的显示。|
|[CustomItem 视图 （格式） 的控件的文本元素](./text-element-for-customitem-for-controls-for-view-format.md)|可选元素。<br /><br /> 向控件显示的文本，例如圆括号或大括号。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[视图 （格式） 的控件的 CustomEntries CustomEntry 元素](./customentry-element-for-customentries-for-controls-for-view-format.md)|提供控件的定义。|

## <a name="remarks"></a>备注

指定的子元素时`CustomItem`元素，请记住以下：

- 必须按以下顺序添加的子元素： `ExpressionBinding`， `NewLine`， `Text`，和`Frame`。

- 可以指定的序列数没有最大限制。

- 在每个序列中，没有最大限制数`ExpressionBinding`可以使用的元素。

## <a name="see-also"></a>另请参阅

[ExpressionBinding CustomItem 视图 （格式） 的控件元素](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[CustomItem 视图 （格式） 的控件的框架元素](./frame-element-for-customitem-for-controls-for-view-format.md)

[CustomItem 视图 （格式） 的控件的新行元素](./newline-element-for-customitem-for-controls-for-view-format.md)

[CustomItem 视图 （格式） 的控件的文本元素](./text-element-for-customitem-for-controls-for-view-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
