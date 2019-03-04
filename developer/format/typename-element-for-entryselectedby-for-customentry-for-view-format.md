---
title: TypeName 元素的视图 （格式） 的 CustomEntry EntrySelectedBy |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858833"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a>TypeName Element for EntrySelectedBy for CustomEntry for View (Format)

指定将使用此定义的自定义控件视图的.NET 类型。 可以为定义指定的类型的数量没有限制。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素 （格式） CustomEntries 元素 CustomControl 视图 （格式） 的视图 （格式） EntrySelectedBy CustomEntries CustomEntry 元素CustomEntry 视图 （格式） 的视图 （格式） 的 CustomEntry EntrySelectedBy TypeName 元素的元素

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
|[视图 （格式） 的 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|定义使用此自定义控件的视图定义的.NET 类型或要使用此定义中必须存在的条件。|

## <a name="text-value"></a>文本值

指定.NET 类型的完全限定的名称，例如`System.IO.DirectoryInfo`。

## <a name="remarks"></a>备注

每个自定义控件的视图定义必须至少一个类型名称、 选择集或定义的选择条件。

有关组件的自定义控件视图的详细信息，请参阅[创建自定义控件](./creating-custom-controls.md)。

## <a name="see-also"></a>另请参阅

[创建自定义控件](./creating-custom-controls.md)

[视图 （格式） 的 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
