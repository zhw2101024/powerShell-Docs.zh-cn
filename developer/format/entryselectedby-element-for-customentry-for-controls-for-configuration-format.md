---
title: 配置 （格式） 的控件的 CustomEntry EntrySelectedBy 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059212"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a>EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)

定义使用公共控件或要在使用此控件中必须存在的条件的定义的.NET 类型。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

配置 （格式） 的配置 （格式） 的配置 （CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素CustomControl CustomEntry 的 Controls 的配置 （格式） 的配置 （格式） EntrySelectedBy 元素的控件的格式） CustomEntry 元素

## <a name="syntax"></a>语法

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`EntrySelectedBy`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[配置 （格式） 的控件的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 定义必须存在要使用的常见控件定义的条件。|
|[配置 （格式） 的控件的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 指定一组使用公共控件的此定义的.NET 类型。|
|[EntrySelectedBy 配置 （格式） 的控件的类型名称元素](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 指定将使用公共控件的此定义的.NET 类型。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[配置 （格式） 的控件的 CustomControl CustomEntry 元素](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|提供了一个常用的控件的定义。|

## <a name="remarks"></a>备注

至少，每个定义必须至少一个.NET 类型、 所选内容集或指定的选择条件。 没有任何最大限制为的类型、 所选内容集或可以指定的选择条件数。

## <a name="see-also"></a>另请参阅

[配置 （格式） 的控件的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[配置 （格式） 的控件的 EntrySelectedBy SelectionSetName 元素](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[配置 （格式） 的控件的 CustomControl CustomEntry 元素](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[EntrySelectedBy 配置 （格式） 的控件的类型名称元素](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
