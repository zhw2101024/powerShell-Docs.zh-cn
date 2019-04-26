---
title: GroupBy （格式） 的帧的 FirstLineHanging 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cdcf66e-96a5-47b5-9269-b4330bde29f2
caps.latest.revision: 6
ms.openlocfilehash: 08db1f2d89c3fe6c1e9a5a522de3071425042c3f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065808"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a>FirstLineHanging Element for Frame for GroupBy (Format)

指定向左移动数据的第一行的字符数。 定义如何显示一组新对象时，将使用此元素。

GroupBy （格式） 的 GroupBy （格式） CustomEntry 元素 CustomControl CustomEntries 元素的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素CustomControl CustomEntry GroupBy （格式） 的帧的 GroupBy （格式） FirstLineHanging 元素 CustomItem GroupBy （格式） 框架元素的 GroupBy （格式） CustomItem 元素

## <a name="syntax"></a>语法

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`FirstLineHanging`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[GroupBy （格式） 的 CustomItem 的框架元素](./frame-element-for-customitem-for-groupby-format.md)|定义如何显示数据，如向左或向右移位数据。|

## <a name="text-value"></a>文本值

指定你想要迁移数据的第一行的字符数。

## <a name="remarks"></a>备注

如果指定此元素，则不能指定[FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md)元素。

## <a name="see-also"></a>另请参阅

[GroupBy （格式） 的帧的 FirstLineIndent 元素](./firstlineindent-element-for-frame-for-groupby-format.md)

[GroupBy （格式） 的 CustomItem 的框架元素](./frame-element-for-customitem-for-groupby-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
