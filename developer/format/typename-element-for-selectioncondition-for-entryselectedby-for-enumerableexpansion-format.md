---
title: 有关 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 的 TypeName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d9100ab7-fbdc-4c0d-bb56-57669ef42b95
caps.latest.revision: 9
ms.openlocfilehash: 316e54d11647aedc1552a0bb74b943de7e4e3588
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083886"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)

指定触发条件的.NET 类型。

用于为 EntrySelectedBy EnumerableExpansion （格式） SelectionCondition 元素的配置元素 DefaultSettings 元素 （格式） EnumerableExpansions 元素 （格式） EnumerableExpansions 元素 （格式） EntrySelectedBy 元素有关 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition EnumerableExpansion （格式） TypeName 元素

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
|[EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|定义要展开此定义的集合对象必须存在的条件。|

## <a name="text-value"></a>文本值

指定.NET 类型的完全限定的名称，例如`System.IO.DirectoryInfo`。

## <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
