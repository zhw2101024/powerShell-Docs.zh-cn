---
title: EntrySelectedBy 视图 （格式） 的控件的类型名称元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 52003450-07ca-41e5-b075-8b6b03fc6e88
caps.latest.revision: 6
ms.openlocfilehash: 30215734ef832d778b08d3d7be224ff8d88b0579
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853203"
---
# <a name="typename-element-for-entryselectedby-for-controls-for-view-format"></a>TypeName Element for EntrySelectedBy for Controls for View (Format)

指定将使用该控件的此定义的.NET 类型。 定义一个视图，可以使用的控件时，将使用此元素。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 控件元素 （格式） 控制元素的控件的视图 （格式） CustomEntries 元素的控件的控件的视图 （格式） CustomControl 元素CustomControl CustomEntries EntrySelectedBy 视图 （格式） 的控件的视图 （格式） 类型名称元素的控件的视图 （格式） CustomEntry 元素的控件

## <a name="syntax"></a>语法

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`TypeName`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[视图 （格式） 的控件的 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|定义使用此控件定义或要使用此定义中必须存在的条件的.NET 类型。|

## <a name="text-value"></a>文本值

指定.NET 类型的完全限定的名称，例如`System.IO.DirectoryInfo`。

## <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[视图 （格式） 的控件的 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
