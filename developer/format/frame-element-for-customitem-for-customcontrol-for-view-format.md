---
title: 对的帧元素的 CustomItem CustomControl 视图 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: a7ee550527ec1cb00b4ed83478992c7ab54dbdb6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861703"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a>Frame Element for CustomItem for CustomControl for View (Format)

定义如何显示数据，如向左或向右移位数据。 定义自定义控件视图时，将使用此元素。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素 （格式） CustomEntries 元素 CustomControl 视图 （格式） 的视图 （格式） CustomItem 元素 CustomEntries CustomEntry 元素CustomEntry CutomControlView （格式） 的视图 （格式） 的 CustomControl CustomItem 框架元素

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

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`Frame`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|`CustomItem Element`|所需的元素|
|[FirstLineHanging 元素](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 指定向左移动数据的第一行的字符数。|
|[FirstLineIndent 元素](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 指定向右移动数据的第一行的字符数。|
|[LeftIndent 元素](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 指定左边距远离数据向右移的字符数。|
|[RightIndent 元素](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 指定数据向右移离开右边距的字符数。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[视图 （格式） 的 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|定义由控件显示的数据和显示方式。|

## <a name="remarks"></a>备注

不能指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)并[FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)中相同的元素`Frame`元素。

## <a name="see-also"></a>另请参阅

[FirstLineHanging 元素](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[FirstLineIndent 元素](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[LeftIndent 元素](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[RightIndent 元素](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[视图 （格式） 的 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
