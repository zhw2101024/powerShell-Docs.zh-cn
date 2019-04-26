---
title: 对的帧元素 CustomItem 控件的配置 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065556"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a>Frame Element for CustomItem for Controls for Configuration (Format)

定义如何显示数据，如向左或向右移位数据。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

配置 （格式） 的配置 （格式） 的配置 （CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素CustomControl CustomEntry CustomItem 的 Controls 的配置 （格式） 的配置框架元素的控件的配置 （格式） CustomItem 元素的控件的格式） CustomEntry 元素

## <a name="syntax"></a>语法

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`Frame`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|`CustomItem Element`|所需的元素|
|[配置 （格式） 的控件的帧的 FirstLineHanging 元素](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 指定向左移动数据的第一行的字符数。|
|[配置 （格式） 的控件的帧的 FirstLineIndent 元素](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 指定向右移动数据的第一行的字符数。|
|[配置 （格式） 的控件的帧的 LeftIndent 元素](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 指定左边距远离数据向右移的字符数。|
|[配置 （格式） 的控件的帧的 RightIndent 元素](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 指定数据向右移离开右边距的字符数。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[有关配置控件 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|定义由控件显示的数据和显示方式。|

## <a name="remarks"></a>备注

不能指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)并[FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)中相同的元素`Frame`元素。

## <a name="see-also"></a>另请参阅

[配置 （格式） 的控件的帧的 FirstLineHanging 元素](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[配置 （格式） 的控件的帧的 FirstLineIndent 元素](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[配置 （格式） 的控件的帧的 LeftIndent 元素](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[配置 （格式） 的控件的帧的 RightIndent 元素](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[有关配置控件 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
