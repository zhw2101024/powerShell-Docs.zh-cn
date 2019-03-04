---
title: CustomEntry 元素的视图 （格式） 的 CustomControl CustomEntries |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861813"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a>CustomEntry Element for CustomEntries for CustomControl for View (Format)

提供自定义控件视图的定义。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素 （格式） CustomEntries 元素 CustomControl CustomEntries 视图 （格式） 的视图 （格式） CustomEntry 元素

## <a name="syntax"></a>语法

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`CustomEntry`元素。 必须指定的定义显示的项。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[视图 （格式） 的 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 定义使用的自定义控件视图或必须存在要使用此定义的条件的定义的.NET 类型。|
|[视图 （格式） 的 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|定义自定义控件定义的控件。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[视图 （格式） 的 CustomControl CustomEntries 元素](./customentries-element-for-customcontrol-for-view-format.md)|提供了自定义控件视图的定义。 自定义控件视图必须指定一个或多个定义。|

## <a name="remarks"></a>备注

在大多数情况下，只有一个定义需要为每个自定义控件视图，但可以有多个定义，如果你想要使用相同的视图以显示不同的.NET 对象。 在这些情况下，可以为每个对象或对象集提供一个单独的定义。

## <a name="see-also"></a>另请参阅

[视图 （格式） 的 CustomControl 元素](./customcontrol-element-for-view-format.md)

[视图 （格式） 的 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[视图 （格式） 的 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
