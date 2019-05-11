---
title: GroupBy （格式） 的脚本块元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229320"
---
# <a name="scriptblock-element-for-groupby-format"></a>ScriptBlock Element for GroupBy (Format)

指定其值发生更改时启动新的组的脚本。

视图 （格式） 的 GroupBy （格式） 的脚本块元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素

## <a name="syntax"></a>语法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`ScriptBlock`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[视图 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)|定义一组.NET 对象的显示方式。|

## <a name="text-value"></a>文本值

指定计算的脚本。

## <a name="remarks"></a>备注

此脚本的值发生更改时，PowerShell 将启动一个新的组。

当指定此元素时，不能指定[PropertyName](propertyname-element-for-groupby-format.md)元素，用于启动新的组。

## <a name="see-also"></a>另请参阅

[GroupBy （格式） 的属性名称元素](propertyname-element-for-groupby-format.md)

[视图 （格式） 的 GroupBy 元素](groupby-element-for-view-format.md)

[编写 PowerShell 格式设置文件](writing-a-powershell-formatting-file.md)
