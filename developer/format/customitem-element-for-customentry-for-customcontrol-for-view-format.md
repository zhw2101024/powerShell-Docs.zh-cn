---
title: CustomItem 元素的视图 （格式） 的 CustomControl CustomEntry |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066402"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a>CustomItem Element for CustomEntry for CustomControl for View (Format)

定义由自定义控件视图中显示的数据和显示方式。 定义自定义控件视图时，将使用此元素。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素 （格式） CustomEntries 元素 CustomControl 视图 （格式） 的视图 （格式） CustomItem 元素 CustomEntries CustomEntry 元素CustomEntry 视图 （格式）

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
|[为视图 （格式） 的 CustomControl CustomItem ExpressionBinding 元素](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 定义由控件显示的数据。|
|[为视图 （格式） 的 CustomControl CustomItem 的框架元素](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 定义由自定义控件视图中显示的数据和显示方式。|
|[CustomItem 视图 （格式） 的自定义控件的新行元素](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 将空白的行添加到控件的显示。|
|[为视图 （格式） 的 CustomControl CustomItem 的文本元素](./text-element-for-customitem-for-customview-for-view-format.md)|可选元素。<br /><br /> 指定由控件显示的数据的其他文本。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[为视图 （格式） 的 CustomControl CustomEntries CustomEntry 元素](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|提供自定义控件视图的定义。|

## <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[视图 （格式） 的 CustomEntries CustomEntry 元素](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[为视图 （格式） 的 CustomControl CustomItem ExpressionBinding 元素](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[为视图 （格式） 的 CustomControl CustomItem 的框架元素](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[为视图 （格式） 的 CustomControl CustomItem 的换行元素](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[为视图 （格式） 的 CustomControl CustomItem 的文本元素](./text-element-for-customitem-for-customview-for-view-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
