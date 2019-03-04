---
title: 视图 （格式） 的控件的 CustomEntries CustomEntry 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6739205-2bc9-4507-b2af-d19d548c2057
caps.latest.revision: 6
ms.openlocfilehash: b92b99d88992cf13dbf7bfbe88aad603615f3138
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858773"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a>CustomEntry Element for CustomEntries for Controls for View (Format)

提供控件的定义。 定义一个视图，可以使用的控件时，将使用此元素。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 控件元素 （格式） 控制元素的控件的视图 （格式） CustomEntries 元素的控件的控件的视图 （格式） CustomControl 元素CustomControl CustomEntries 视图 （格式） 的控件的视图 （格式） CustomEntry 元素

## <a name="syntax"></a>语法

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`CustomEntry`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[视图 （格式） 的控件的 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|可选元素。<br /><br /> 定义使用此控件定义或要使用此定义中必须存在的条件的.NET 类型。|
|[视图 （格式） 的控件的 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-controls-for-view-format.md)|必需的元素。<br /><br /> 定义该控件显示数据的方式。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[视图 （格式） 的 CustomControl CustomEntries 元素](./customentries-element-for-customcontrol-for-view-format.md)|提供控件的定义。|

## <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[视图 （格式） 的 CustomControl CustomEntries 元素](./customentries-element-for-customcontrol-for-view-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
