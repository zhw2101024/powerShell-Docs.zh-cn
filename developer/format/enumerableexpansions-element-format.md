---
title: EnumerableExpansions 元素 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860253"
---
# <a name="enumerableexpansions-element-format"></a>EnumerableExpansions Element (Format)

定义显示在视图中时如何展开.NET 集合对象。

配置元素 （格式） DefaultSettings 元素 （格式） EnumerableExpansions 元素 （格式）

## <a name="syntax"></a>语法

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`EnumerableExpansions`元素。 可以使用的子元素的数目没有限制。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 元素 （格式）](./enumerableexpansion-element-format.md)|可选元素。<br /><br /> 定义显示在视图中时进行扩展的特定.NET 集合对象。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[DefaultSettings 元素 （格式）](./defaultsettings-element-format.md)|定义应用于的格式设置文件的所有视图的常见设置。|

## <a name="remarks"></a>备注

此元素用于定义如何显示集合对象和集合中的对象。 在这种情况下，集合对象是指任何支持的对象**System.Collections.ICollection**接口。

## <a name="see-also"></a>另请参阅

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
