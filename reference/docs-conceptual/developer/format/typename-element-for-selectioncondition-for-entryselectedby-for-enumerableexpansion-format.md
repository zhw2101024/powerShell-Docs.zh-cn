---
title: EnumerableExpansion 的 SelectionCondition for EntrySelectedBy 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d9100ab7-fbdc-4c0d-bb56-57669ef42b95
caps.latest.revision: 9
ms.openlocfilehash: 316e54d11647aedc1552a0bb74b943de7e4e3588
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361576"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)

指定触发条件的 .NET 类型。

用于 EnumerableExpansion 的 DefaultSettings 元素（format） EnumerableExpansions 元素（format） EnumerableExpansions 元素（format） EntrySelectedBy 元素用于 EntrySelectedBy for EnumerableExpansion （Format）的 SelectionCondition 的 EnumerableExpansion （格式） TypeName 元素

## <a name="syntax"></a>语法

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `TypeName` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|定义扩展此定义的集合对象时必须存在的条件。|

## <a name="text-value"></a>文本值

指定 .NET 类型的完全限定名，如 `System.IO.DirectoryInfo`。

## <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[EnumerableExpansion 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
