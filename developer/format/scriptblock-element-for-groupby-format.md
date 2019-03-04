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
ms.openlocfilehash: 41a6aaa24e5850bd390c8e3b6505cc88fc80b7b5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856203"
---
# <a name="scriptblock-element-for-groupby-format"></a>ScriptBlock Element for GroupBy (Format)

指定其值发生更改时启动新的组的脚本。

视图 （格式） 的 GroupBy （格式） 的脚本块元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素

## <a name="syntax"></a>语法

```xml
<ScriptBolck>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`ScriptBlock`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[视图 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)|定义一组.NET 对象的显示方式。|

## <a name="text-value"></a>文本值

指定计算的脚本。

## <a name="remarks"></a>备注

此脚本的值发生更改时，Windows PowerShell 启动新的组。

当指定此元素时，不能指定[PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676)元素，用于启动新的组。

## <a name="see-also"></a>另请参阅

[GroupBy （格式） 的属性名称元素](./propertyname-element-for-groupby-format.md)

[视图 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
