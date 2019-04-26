---
title: TableControl （格式） 的 TableColumnHeader 的 width 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083614"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a>Width Element for TableColumnHeader for TableControl (Format)

定义列的宽度 （以字符为单位）。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableHeaders 元素 TableControl （格式） TableColumnHeader 元素 TableHeaders TableControl （格式） 的宽度元素TableControl （格式） 的 TableColumnHeader

## <a name="syntax"></a>语法

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述的特性、 子元素和父元素的`Width`定义列标题时使用的元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[TableControl （格式） 的 TableHeaders TableColumnHeader 元素](./tablecolumnheader-element-format.md)|定义标签、 宽度和对齐方式的表的列的数据。|

## <a name="text-value"></a>文本值

在所有可能的当指定的显示的属性值的长度大于宽度 （以字符为单位）。

## <a name="remarks"></a>备注

表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。

## <a name="example"></a>示例

下面的示例演示`TableColumnHeader`元素，其宽度为 16 个字符。

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>另请参阅

[创建表视图](./creating-a-table-view.md)

[TableControl （格式） 的 TableHeader TableColumnHeader 元素](./tablecolumnheader-element-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
