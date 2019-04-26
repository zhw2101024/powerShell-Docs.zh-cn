---
title: 配置 （格式） 的控件的 SelectionCondition 的 TypeName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 477c8711-fffc-4f92-af45-6d4f80990474
caps.latest.revision: 7
ms.openlocfilehash: 60f02f3240c5574e1b1f9027b060bd9af89a11d2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083937"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a>TypeName Element for SelectionCondition for Controls for Configuration (Format)

指定触发条件的.NET 类型。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

配置 （格式） 的配置 （格式） 的 Controls 的 CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素配置 （格式） 的 Controls 的配置 （格式） 的 Controls 的配置 （格式） SelectionCondition 元素，用于为 CustomEntry 的 EntrySelectedBy CustomEntry EntrySelectedBy 元素 CustomControl CustomEntry 元素SelectionCondition 的 Controls 的配置 （格式） 的配置 （格式） TypeName 元素

## <a name="syntax"></a>语法

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`TypeName`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[为配置 （格式） 的 CustomEntry EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|定义必须存在要使用的控件定义的条件。|

## <a name="text-value"></a>文本值

指定.NET 类型的完全限定的名称，例如`System.IO.DirectoryInfo`。

## <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[为配置 （格式） 的 CustomEntry EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
