---
title: 配置 （格式） 的控件的 CustomControl CustomEntry 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066458"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a>CustomEntry Element for CustomControl for Controls for Configuration (Format)

提供了一个常用的控件的定义。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

配置 （格式） 的配置 （格式） 的配置 （CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素CustomControl 配置 （格式） 的控件的格式） CustomEntry 元素

## <a name="syntax"></a>语法

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`CustomEntry`元素。 必须指定的定义显示的项。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[配置 （格式） 的控件的 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 定义使用公共控件或要在使用此控件中必须存在的条件的定义的.NET 类型。|
|[有关配置控件 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|必需的元素。<br /><br /> 定义由控件显示的数据和显示方式。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[配置 （格式） 的 CustomControl CustomEntries 元素](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|提供了一个常用的控件的定义。|

## <a name="remarks"></a>备注

在大多数情况下，只有一个定义需要为每个常见的自定义控件，但可以有多个定义，如果你想要使用相同的控件来显示不同的.NET 对象。 在这些情况下，可以为每个对象或对象集提供一个单独的定义。

## <a name="see-also"></a>另请参阅

[配置 （格式） 的 CustomControl CustomEntries 元素](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[有关配置控件 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
