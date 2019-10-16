---
title: TableHeaders 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361816"
---
# <a name="tableheaders-element-format"></a>TableHeaders Element (Format)

定义表中各列的标头。

ViewDefinitions 元素（格式） View 元素（format） TableControl 元素（format） TableHeaders 元素 for TableControl （Format）

## <a name="syntax"></a>语法

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍 `TableHeaders` 元素的属性、子元素和父元素。 对于要显示的对象的每个属性，都必须有一个子元素。 列标题信息按指定子元素的顺序显示。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableColumnHeader 元素（格式）](./tablecolumnheader-element-format.md)|可选元素。<br /><br /> 定义表视图的列的数据标签、宽度和对齐方式。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableControl 元素（格式）](./tablecontrol-element-format.md)|定义视图的表格格式。|

## <a name="remarks"></a>备注

有关表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。

## <a name="example"></a>示例

此示例显示了一个用于定义两个列标题的 @no__t 0 元素。

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

[TableColumnHeader 元素（格式）](./tablecolumnheader-element-format.md)

[TableControl 元素（格式）](./tablecontrol-element-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
