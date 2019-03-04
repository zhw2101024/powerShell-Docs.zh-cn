---
title: TableHeaders 元素 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856873"
---
# <a name="tableheaders-element-format"></a>TableHeaders Element (Format)

定义表的列的标头。

TableControl （格式） 的 ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableHeaders 元素

## <a name="syntax"></a>语法

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述的特性、 子元素和父元素的`TableHeaders`元素。 必须是要显示的对象的每个属性的子元素。 列标头信息显示在指定的子元素的顺序。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableColumnHeader 元素 （格式）](./tablecolumnheader-element-format.md)|可选元素。<br /><br /> 定义标签、 宽度和表视图的列的数据的对齐方式。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableControl 元素 （格式）](./tablecontrol-element-format.md)|定义一个视图，以表格式。|

## <a name="remarks"></a>备注

表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。

## <a name="example"></a>示例

此示例显示了`TableHeaders`元素，用于定义两个列标题。

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
  <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a>另请参阅

[创建表视图](./creating-a-table-view.md)

[TableColumnHeader 元素 （格式）](./tablecolumnheader-element-format.md)

[TableControl 元素 （格式）](./tablecontrol-element-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
