---
title: Expand 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368736"
---
# <a name="expand-element-format"></a>Expand Element (Format)

指定为此定义扩展集合对象的方式。

配置元素（格式） DefaultSettings 元素（格式） EnumerableExpansions 元素（格式） EnumerableExpansion 元素（格式） Expand 元素（格式）

## <a name="syntax"></a>语法

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `Expand` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 元素（格式）](./enumerableexpansion-element-format.md)|定义特定 .NET 集合对象在视图中显示的方式。|

## <a name="text-value"></a>文本值

指定以下值之一：

- EnumOnly：仅显示集合中对象的属性。

- CoreOnly：仅显示集合对象的属性。

- Both：显示集合中的对象的属性和集合对象的属性。

## <a name="remarks"></a>备注

此元素用于定义集合对象和集合中的对象的显示方式。 在这种情况下，集合对象引用支持**system.object**接口的任何对象。

默认行为是只显示集合中对象的属性。

## <a name="see-also"></a>另请参阅

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
