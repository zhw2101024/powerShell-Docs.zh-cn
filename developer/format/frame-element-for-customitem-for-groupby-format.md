---
title: 元素对 CustomItem 的帧的 GroupBy （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065591"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a>Frame Element for CustomItem for GroupBy (Format)

定义如何显示数据，如向左或向右移位数据。 定义如何显示一组新对象时，将使用此元素。

GroupBy （格式） 的 GroupBy （格式） CustomEntry 元素 CustomControl CustomEntries 元素的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素CustomControl CustomEntry CustomItem 为 GroupBy （格式） 的 GroupBy （格式） 框架元素的 GroupBy （格式） CustomItem 元素

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
|[GroupBy （格式） 的帧的 FirstLineHanging 元素](./firstlinehanging-element-for-frame-for-groupby-format.md)|可选元素。<br /><br /> 指定向左移动数据的第一行的字符数。|
|[GroupBy （格式） 的帧的 FirstLineIndent 元素](./firstlineindent-element-for-frame-for-groupby-format.md)|可选元素。<br /><br /> 指定向右移动数据的第一行的字符数。|
|[GroupBy （格式） 的帧的 LeftIndent 元素](./leftindent-element-for-frame-for-groupby-format.md)|可选元素。<br /><br /> 指定左边距远离数据向右移的字符数。|
|[GroupBy （格式） 的帧的 RightIndent 元素](./rightindent-element-for-frame-for-groupby-format.md)RightIndent 元素|可选元素。<br /><br /> 指定数据向右移离开右边距的字符数。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[GroupBy （格式） 的 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-groupby-format.md)|定义由控件显示的数据和显示方式。|

## <a name="remarks"></a>备注

不能指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md)并[FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md)中相同的元素`Frame`元素。

## <a name="see-also"></a>另请参阅

[GroupBy （格式） 的帧的 FirstLineHanging 元素](./firstlinehanging-element-for-frame-for-groupby-format.md)

[GroupBy （格式） 的帧的 FirstLineIndent 元素](./firstlineindent-element-for-frame-for-groupby-format.md)

[GroupBy （格式） 的帧的 LeftIndent 元素](./leftindent-element-for-frame-for-groupby-format.md)

[GroupBy （格式） 的帧的 RightIndent 元素](./rightindent-element-for-frame-for-groupby-format.md)

[GroupBy （格式） 的 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-groupby-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
