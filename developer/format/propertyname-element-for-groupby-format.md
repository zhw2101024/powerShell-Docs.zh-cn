---
title: GroupBy （格式） 的属性名称元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075862"
---
# <a name="propertyname-element-for-groupby-format"></a>PropertyName Element for GroupBy (Format)

指定其值发生更改时启动新的组的.NET 属性。

视图 （格式） 的 GroupBy （格式） 的属性名称元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素

## <a name="syntax"></a>语法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`PropertyName`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[视图 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)|定义一组.NET 对象的显示方式。|

## <a name="text-value"></a>文本值

指定.NET 属性名称。

## <a name="remarks"></a>备注

此属性的值发生更改时，Windows PowerShell 启动新的组。

当指定此元素时，不能指定[ScriptBlock](./scriptblock-element-for-groupby-format.md)元素，用于启动新的组。

## <a name="example"></a>示例

下面的示例演示如何启动新的组的属性值发生更改时。

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

有关完整的格式设置文件，其中包含此元素的示例，请参阅[宽的视图 (GroupBy)](./wide-view-groupby.md)。

## <a name="see-also"></a>另请参阅

[视图 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)

[GroupBy （格式） 的脚本块元素](./scriptblock-element-for-groupby-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
