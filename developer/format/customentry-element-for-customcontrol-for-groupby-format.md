---
title: GroupBy （格式） 的 CustomControl CustomEntry 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066465"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a>CustomEntry Element for CustomControl for GroupBy (Format)

提供控件的定义。 定义如何显示一组新对象时，将使用此元素。

GroupBy （格式） 的 GroupBy （格式） CustomEntry 元素 CustomControl CustomEntries 元素的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素GroupBy （格式） 的 CustomControl

## <a name="syntax"></a>语法

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`CustomEntry`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[GroupBy （格式） 的 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-groupby-format.md)|可选元素。<br /><br /> 定义使用此控件定义或要使用此定义中必须存在的条件的.NET 类型。|
|[GroupBy （格式） 的 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-groupby-format.md)|必需的元素。<br /><br /> 定义该控件显示数据的方式。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[GroupBy （格式） 的 CustomControl CustomEntries 元素](./customentries-element-for-customcontrol-for-groupby-format.md)|提供控件的定义。|

## <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[GroupBy （格式） 的 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-groupby-format.md)

[GroupBy （格式） 的 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-groupby-format.md)

[GroupBy （格式） 的 CustomControl CustomEntries 元素](./customentries-element-for-customcontrol-for-groupby-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
