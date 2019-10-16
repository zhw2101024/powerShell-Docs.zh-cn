---
title: TableControl （Format）的 TableColumnItems 的 TableColumnItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 9e6cffc7476ef01124d95ecbf287d9788b0324c9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368226"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a>TableColumnItem Element for TableColumnItems for TableControl (Format)

定义其值显示在行的列中的属性或脚本。

TableRowEntry for TableRowEntries 的 TableControl （Format） TableControl 元素的配置元素（格式） ViewDefinitions 元素（格式） TableControl 元素（format） TableRowEntries 元素（format）TableColumnItems 的 TableControlEntry for TableControl （Format） TableColumnItem 元素的 TableColumnItems 元素（Format）

## <a name="syntax"></a>语法

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍 `TableColumnItem` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableControl 的 TableColumnItem 的对齐元素（格式）](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|可选元素。<br /><br /> 定义行的列中数据的显示方式。|
|[TableControl 的 TableColumnItem 的格式字符串元素（格式）](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|指定用于设置行的列中数据的格式的格式模式。|
|[TableControl 的 TableColumnItem 的 PropertyName 元素（Format）](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|可选元素。<br /><br /> 指定显示其值的属性的名称。|
|[TableControl 的 TableColumnItem 的 ScriptBlock 元素（格式）](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|可选元素。<br /><br /> 指定其值显示在行的列中的脚本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableControl 的 TableControlEntry 的 TableColumnItems 元素（格式）](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|定义其值显示在行中的属性或脚本。|

## <a name="remarks"></a>备注

可以在行的每个列中指定对象或脚本的属性。 如果未指定子元素，则该项是占位符，不显示任何数据。

有关表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。

## <a name="example"></a>示例

此示例演示一个 `TableColumnItem` 元素，该元素显示[system.object](/dotnet/api/System.Diagnostics.Process)对象的 @no__t 属性的值。

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>另请参阅

[创建表视图](./creating-a-table-view.md)

[TableControl 的 TableColumnItem 的对齐元素（格式）](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableColumnItems 元素（格式）](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[TableControl 的 TableColumnItem 的格式字符串元素（格式）](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableControl 的 TableColumnItem 的 PropertyName 元素（Format）](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableControl 的 TableColumnItem 的 ScriptBlock 元素（格式）](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
