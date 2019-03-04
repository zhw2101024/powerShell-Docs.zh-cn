---
title: 范围图 （格式） 的 CustomControl FirstLineHanging 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6ac3d86-0529-4b93-9bc7-ee94fcef9618
caps.latest.revision: 8
ms.openlocfilehash: ae4ad8ae3e6cb5d1174dc001b30aa84dd182a606
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860233"
---
# <a name="firstlinehanging-element-for-frame-for-customcontrol-for-view-format"></a>FirstLineHanging Element for Frame for CustomControl for View (Format)

指定向左移动数据的第一行的字符数。 定义自定义控件视图时，将使用此元素。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素 （格式） CustomEntries 元素 CustomControl 视图 （格式） 的视图 （格式） CustomItem 元素 CustomEntries CustomEntry 元素CustomEntry CutomControlView （格式） 的视图 （格式） 的 CustomControl 的帧的视图 （格式） FirstLineHanging 元素 CustomControl CustomItem 框架元素

## <a name="syntax"></a>语法

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`FirstLineHanging`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[为视图 （格式） 的 CustomControl CustomItem 的框架元素](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|定义如何显示数据，如向左或向右移位数据。|

## <a name="text-value"></a>文本值

指定你想要迁移数据的第一行的字符数。

## <a name="remarks"></a>备注

如果指定此元素，则不能指定[FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)元素。

## <a name="see-also"></a>另请参阅

[范围图 （格式） 的 CustomControl FirstLineIndent 元素](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[为视图 （格式） 的 CustomControl CustomItem 的框架元素](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
