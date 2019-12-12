---
title: EnumerableExpansion 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368746"
---
# <a name="enumerableexpansion-element-format"></a>EnumerableExpansion Element (Format)

定义特定 .NET 集合对象在视图中显示的方式。

配置元素（格式） DefaultSettings 元素（格式） EnumerableExpansions 元素（格式） EnumerableExpansion 元素（格式）

## <a name="syntax"></a>语法

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `EnumerableExpansion` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-enumerableexpansion-format.md)|可选元素。<br /><br /> 定义通过此定义扩展哪些 .NET 集合对象。|
|[Expand 元素（格式）](./expand-element-format.md)|指定为此定义扩展集合对象的方式。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansions 元素（格式）](./enumerableexpansions-element-format.md)|定义 .NET 集合对象在视图中显示时的扩展方式。|

## <a name="remarks"></a>备注

此元素用于定义集合对象和集合中的对象的显示方式。 在这种情况下，集合对象引用支持**system.object**接口的任何对象。

默认行为是只显示集合中对象的属性。

## <a name="see-also"></a>另请参阅

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
