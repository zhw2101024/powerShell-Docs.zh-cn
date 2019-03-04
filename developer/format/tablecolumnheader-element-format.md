---
title: TableColumnHeader 元素 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: 15f47c97ac5d55cb76e153af86672b3ffaf176c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858593"
---
# <a name="tablecolumnheader-element-format"></a>TableColumnHeader Element (Format)

定义该标签，列的宽度和表的列标签的对齐方式。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableHeaders 元素 TableControl （格式） 的 TableHeaders TableControl （格式） TableColumnHeader 元素

## <a name="syntax"></a>语法

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`TableColumnHeader`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[TableControl （格式） 的 TableColumnHeader 的标签元素](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|可选元素。<br /><br /> 定义显示在列顶部的标签。 如果未不指定任何标签，则使用其值显示在行中的属性的名称。|
|[TableControl （格式） 的 TableColumnHeader 的 width 元素](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|必需的元素。<br /><br /> 指定列的宽度 （以字符为单位）。|
|[TableControl （格式） 的 TableColumbnHeader 的对齐方式元素](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|可选元素。<br /><br /> 指定如何显示的列的标签。 如果指定不对齐，则标签左侧对齐。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[TableHeaders 元素 （格式）](./tableheaders-element-format.md)|定义表视图的列。|

## <a name="remarks"></a>备注

指定表的每个列的标头。 列会显示的顺序在`TableColumnHeader`元素的定义。

表必须具有相同数量的`TableColumnHeader`元素作为`TableRowEntry`元素。 列标题定义如何显示表顶部的文本。 行项定义的表的行中显示的数据。

表视图的组件的详细信息，请参阅[表视图](./creating-a-table-view.md)。

## <a name="example"></a>示例

下面的示例演示两个`TableColumnHeader`元素。 第一个元素定义一个列和其标签为"列 1"，已包含 16 个字符的宽度上左边对齐其标签。 第二个元素定义一个列，其标签为"第 2 列"，宽度为 10 个字符，并且其标签居中列中。

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

[TableContrl （格式） 的 TableColumnHeader 的对齐方式元素](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[创建表视图](./creating-a-table-view.md)

[TableControl （格式） 的 TableColumnHeader 的标签元素](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[TableControl （格式） 的 TableHeaders 元素](./tableheaders-element-format.md)

[TableColumnHeader TableControl 元素 （格式） 的宽度](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
