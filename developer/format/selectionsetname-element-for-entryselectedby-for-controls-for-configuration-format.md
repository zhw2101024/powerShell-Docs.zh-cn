---
title: 配置 （格式） 的控件的 EntrySelectedBy SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860903"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a>SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)

指定一组使用控件的此定义的.NET 类型。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

配置 （格式） 的配置 （格式） 的配置 （CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素CustomControl CustomEntry EntrySelectedBy 的 Controls 的配置 （格式） 的配置 （格式） SelectionSetName 元素的控件的配置 （格式） EntrySelectedBy 元素的控件的格式） CustomEntry 元素

## <a name="syntax"></a>语法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`SelectionSetName`元素。

### <a name="attributes"></a>特性

无

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[配置 （格式） 的控件的 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|定义使用此控件定义或要使用此定义中必须存在的条件的.NET 类型。|

## <a name="text-value"></a>文本值

指定所选内容集的名称。

## <a name="remarks"></a>备注

每个控件定义必须至少一个类型名称、 选择集或定义的选择条件。

当你想要在多个视图中定义的一组使用的对象时通常使用的选项集。 有关定义的选项集的详细信息，请参阅[定义所选内容设置](./defining-selection-sets.md)。

## <a name="see-also"></a>另请参阅

[配置 （格式） 的控件的 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
