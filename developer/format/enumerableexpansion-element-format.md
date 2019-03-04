---
title: EnumerableExpansion 元素 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856833"
---
# <a name="enumerableexpansion-element-format"></a>EnumerableExpansion Element (Format)

定义如何特定对象在视图中显示时进行扩展的.NET 集合。

配置元素 （格式） DefaultSettings 元素 （格式） EnumerableExpansions 元素 （格式） EnumerableExpansion 元素 （格式）

## <a name="syntax"></a>语法

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`EnumerableExpansion`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion （格式） 的 EntrySelectedBy 元素](./entryselectedby-element-for-enumerableexpansion-format.md)|可选元素。<br /><br /> 定义此定义的扩展的.NET 集合对象。|
|[展开元素 （格式）](./expand-element-format.md)|指定如何为此定义扩展的集合对象。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansions 元素 （格式）](./enumerableexpansions-element-format.md)|该对象在视图中显示时进行扩展的.NET 集合定义的不同方式。|

## <a name="remarks"></a>备注

此元素用于定义如何显示集合对象和集合中的对象。 在这种情况下，集合对象是指任何支持的对象**System.Collections.ICollection**接口。

默认行为是仅显示属性的对象的集合中。

## <a name="see-also"></a>另请参阅

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
