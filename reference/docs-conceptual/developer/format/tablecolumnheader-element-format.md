---
title: TableColumnHeader 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: d3ad7fa563def17d43ce4dc64d155b65b650521f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361846"
---
# <a name="tablecolumnheader-element-format"></a>TableColumnHeader Element (Format)

定义标签、列的宽度和表中某一列的标签对齐方式。

TableColumnHeader for TableHeaders 的 TableControl （Format） TableControl 元素的配置元素（格式） ViewDefinitions 元素（格式） TableControl 元素（format） TableHeaders 元素（format）

## <a name="syntax"></a>语法

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `TableColumnHeader` 元素的属性、子元素和父元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableControl 的 TableColumnHeader 的 Label 元素（Format）](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|可选元素。<br /><br /> 定义在列顶部显示的标签。 如果未指定标签，则使用在行中显示其值的属性的名称。|
|[TableControl 的 TableColumnHeader 的 Width 元素（Format）](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|必需的元素。<br /><br /> 指定列的宽度（以字符为字符）。|
|[TableControl 的 TableColumnHeader 的对齐元素（格式）](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|可选元素。<br /><br /> 指定列的标签的显示方式。 如果未指定对齐方式，则在左侧对齐标签。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableHeaders 元素（格式）](./tableheaders-element-format.md)|定义表视图的列。|

## <a name="remarks"></a>备注

为表的每个列指定标题。 列按定义 `TableColumnHeader` 元素的顺序显示。

表必须与 `TableRowEntry` 元素具有相同数量的 `TableColumnHeader` 元素。 列标题定义表顶部的文本的显示方式。 行条目定义在表的行中显示的数据。

有关表视图的组件的详细信息，请参阅[表视图](./creating-a-table-view.md)。

## <a name="example"></a>示例

下面的示例演示两个 `TableColumnHeader` 元素。 第一个元素定义其标签为 "列 1" 的列，宽度为16个字符，其标签在左侧对齐。 第二个元素定义标签为 "Column 2" 的列，其宽度为10个字符，标签在列中居中。

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

[TableControl 的 TableColumnHeader 的对齐元素（格式）](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[创建表视图](./creating-a-table-view.md)

[TableControl 的 TableColumnHeader 的 Label 元素（Format）](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[TableControl 的 TableHeaders 元素（格式）](./tableheaders-element-format.md)

[TableControl 元素的 TableColumnHeader 宽度（格式）](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
