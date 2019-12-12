---
title: TableControl 的 TableColumnHeader 的对齐元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff85e83a-c9c2-4c37-accc-e6a27c182f3c
caps.latest.revision: 19
ms.openlocfilehash: 16b41535109ca503e679a135f5ba30054e33de5b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364376"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a>Alignment Element for TableColumnHeader for TableControl (Format)

定义列标题中的数据的显示方式。

TableColumnHeader 的 ViewDefinitions 元素（格式）视图元素（格式） TableControl 元素（格式） TableHeaders 元素（格式） TableColumnHeader 元素（格式）对齐元素（格式）

## <a name="syntax"></a>语法

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍 `Alignment` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableColumnHeader 元素（格式）](./tablecolumnheader-element-format.md)|定义表中某一列的数据的标签、宽度和对齐方式。|

## <a name="text-value"></a>文本值

指定下列值之一。 这些值不区分大小写。

如果未指定此元素，则在左侧的列中将显示数据左对齐。

右对齐显示在右侧列中的数据。

居中将列中显示的数据居中。

## <a name="remarks"></a>备注

有关表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。

## <a name="example"></a>示例

此示例演示一个 `TableColumnHeader` 元素，其数据在左侧对齐。

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>另请参阅

[创建表视图](./creating-a-table-view.md)

[TableColumnHeader 元素（格式）](./tablecolumnheader-element-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
