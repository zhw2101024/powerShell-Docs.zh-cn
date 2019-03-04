---
title: 视图 （格式） 的控件的帧的 FirstLineHanging 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53694f08-57f7-4185-b443-1636a0918afc
caps.latest.revision: 8
ms.openlocfilehash: 387340cd9b0aae2ad0419b187d96ab4fee183d5a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858713"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-view-format"></a>FirstLineHanging Element for Frame for Controls for View (Format)

指定向左移动数据的第一行的字符数。 定义一个视图，可以使用的控件时，将使用此元素。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 控件元素 （格式） 控制元素的控件的视图 （格式） CustomEntries 元素的控件的控件的视图 （格式） CustomControl 元素CustomControl CustomEntries CustomEntry CustomItem 视图 （格式） FirstLineHanging 元素的控件的视图 （格式） 框架元素的控件的视图 （格式） CustomItem 元素的控件的视图 （格式） CustomEntry 元素控件的视图 （格式） 的框架

## <a name="syntax"></a>语法

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`FirstLineHanging`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[CustomItem 视图 （格式） 的控件的框架元素](./frame-element-for-customitem-for-controls-for-view-format.md)|定义如何显示数据，如向左或向右移位数据。|

## <a name="text-value"></a>文本值

指定你想要迁移数据的第一行的字符数。

## <a name="remarks"></a>备注

如果指定此元素，则不能指定[FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md)元素。

## <a name="see-also"></a>另请参阅

[视图 （格式） 的控件的帧的 FirstLineIndent 元素](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[CustomItem 视图 （格式） 的控件的框架元素](./frame-element-for-customitem-for-controls-for-view-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
