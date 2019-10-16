---
title: TableControl 的 TableRowEntries 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368146"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a>TableRowEntries Element for TableControl (Format)

定义表中的行。

TableControl 的 Configuration 元素（格式） ViewDefinitions 元素（格式） TableControl 元素（format） TableRowEntries 元素（format）

## <a name="syntax"></a>语法

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍 `TableRowEntries` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableControl 的 TableRowEntries 的 TableRowEntry 元素（格式）](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|必需的元素。<br /><br /> 定义在表的行中显示的数据。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableControl 元素（格式）](./tablecontrol-element-format.md)|定义视图的表格格式。|

## <a name="remarks"></a>备注

您必须为表视图指定一个或多个 `TableRowEntry` 元素。 对于可以添加的 @no__t 0 个元素，其顺序并没有最大限制。

有关表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。

## <a name="example"></a>示例

下面的示例演示一个 `TableRowEntries` 元素，该元素定义一个行，该行[显示了 system.exception 对象的](/dotnet/api/System.Diagnostics.Process)两个属性的值。

```xml
<TableRowEntries>
  <TableRowEntry>
    <EntrySelectedBy>
      <TypeName>System.Diagnostics.Process</TypeName>
    </EntrySelectedBy>
    <TableColumnItems>
      <TableColumnItem>
        <PropertyName> Property for first column</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName> Property for second column</PropertyName>
      </TableColumnItem>
    </TableColumnItems>
  </TableRowEntry>
</TableRowEntries>

```

## <a name="see-also"></a>另请参阅

[创建表视图](./creating-a-table-view.md)

[TableControl 元素（格式）](./tablecontrol-element-format.md)

[TableRowEntry 元素（格式）](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
