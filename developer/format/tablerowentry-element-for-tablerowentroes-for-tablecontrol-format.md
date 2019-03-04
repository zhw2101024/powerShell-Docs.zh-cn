---
title: TableControl （格式） 的 TableRowEntroes TableRowEntry 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 001d46debde61f928c338b2f68112fb201f96216
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853583"
---
# <a name="tablerowentry-element-for-tablerowentroes-for-tablecontrol-format"></a>TableRowEntry Element for TableRowEntroes for TableControl (Format)

定义表的行中显示的数据。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableRowEntries 元素 TableControl （格式） 的 TableRowEntries TableControl （格式） TableRowEntry 元素

## <a name="syntax"></a>语法

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`TableRowEntry`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableControl （格式） 的 TableRowEntry EntrySelectedBy 元素](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|必需的元素。<br /><br /> 定义其属性值显示的行中的对象。|
|[TableControl （格式） 的 TableRowEntry TableColumnItems 元素](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|必需的元素。<br /><br /> 定义属性或其值将显示的脚本。|
|[元素为 TableRowEntry 包装以 TableCntrol （格式）](./wrap-element-for-tablerowentry-for-tablecontrl-format.md)|可选元素。<br /><br /> 指定在下一行显示超过列宽的文本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableControl （格式） 的 TableRowEntries 元素](./tablerowentries-element-for-tablecontrol-format.md)|定义表的行。|

## <a name="remarks"></a>备注

一个`TableColumnItems`元素和一个`EntrySelectedBy`必须指定元素。

表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。

## <a name="example"></a>示例

下面的示例演示`TableRowEntry`显示的两个属性的值将行定义的元素[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)对象。

```xml
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
```

## <a name="see-also"></a>另请参阅

[创建表视图](./creating-a-table-view.md)

[TableControl （格式） 的 TableRowEntry EntrySelectedBy 元素](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[TableControl （格式） 的 TableRowEntry TableColumnItems 元素](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[TableControl （格式） 的 TableRowEntries 元素](./tablerowentries-element-for-tablecontrol-format.md)

[TableControl （格式） 的 TableRowEntries TableRowEntry 元素](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[元素为 TableRowEntry 包装以 TableCntrol （格式）](./wrap-element-for-tablerowentry-for-tablecontrl-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
