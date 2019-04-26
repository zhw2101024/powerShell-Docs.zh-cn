---
title: TableControl （格式） 的 TableRowEntry TableColumnItems 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: d05437aaa9652e7f81d0854d1a746acffe145699
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075386"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a>TableColumnItems Element for TableRowEntry for TableControl (Format)

定义属性或其值显示在一行中的脚本。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableRowEntries 元素 TableControl （格式） 的 TableRowEntries TableControl （格式） TableRowEntry 元素TableControl （格式） 的 TableControlEntry TableColumnItems 元素

## <a name="syntax"></a>语法

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述的特性、 子元素和父元素的`TableColumnItems`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[TableControl （格式） 的 TableColumnItems TableColumnItem 元素](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|必需的元素。<br /><br /> 定义属性或其值显示在一行的列中的脚本。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[TableControl （格式） 的 TableRowEntries TableRowEntry 元素](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|定义表的行中显示的数据。|

## <a name="remarks"></a>备注

一个`TableColumnItem`元素是必需的行的每个列。 第一个条目显示在第一列，第二个条目中的第二个列，依此类推。

表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。

## <a name="example"></a>示例

下面的示例演示`TableColumnItems`定义的三个属性的元素[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)对象。

```xml
<TableColumnItems>
  <TableColumnItem>
    <PropertyName>Status</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>Name</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>DisplayName</PropertyName>
  </TableColumnItem>
</TableColumnItems>

```

## <a name="see-also"></a>另请参阅

[创建表视图](./creating-a-table-view.md)

[TableColumnItem 元素 （格式）](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[TableRowEntry 元素 （格式）](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
