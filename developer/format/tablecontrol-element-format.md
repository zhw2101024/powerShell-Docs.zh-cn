---
title: TableControl 元素 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054571"
---
# <a name="tablecontrol-element-format"></a>TableControl Element (Format)

定义一个视图，以表格式。

ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式）

## <a name="syntax"></a>语法

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`TableControl`元素。 必须指定表的行。 所有其他子元素是可选的。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[TableControl （格式） 的自动调整大小元素](./autosize-element-for-tablecontrol-format.md)|可选元素。<br /><br /> 指定列的大小和列数会调整基于数据的大小。|
|[TableControl （格式） 的 HideTableHeaders 元素](./hidetableheaders-element-format.md)|可选元素。<br /><br /> 指示是否未显示表的标头。|
|[TableControl （格式） 的 TableHeaders 元素](./tableheaders-element-format.md)|必需的元素。<br /><br /> 定义标签、 宽度和表视图的列的数据的对齐方式。|
|[TableControl （格式） 的 TableRowEntries 元素](./tablerowentries-element-for-tablecontrol-format.md)|可选元素。<br /><br /> 提供了表视图的定义。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[视图元素 （格式）](./view-element-format.md)|定义一个视图，它用于显示一个或多个对象的成员。|

## <a name="remarks"></a>备注

表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。

## <a name="example"></a>示例

此示例演示`TableControl`用来显示的属性的元素[System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)对象。

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>...</TableHeaders>
    <TableRowEntries>...</TableRowEntries>
  </TableControl>
</View>

```

## <a name="see-also"></a>另请参阅

[创建表视图](./creating-a-table-view.md)

[视图元素 （格式）](./view-element-format.md)

[TableControl （格式） 的自动调整大小元素](./autosize-element-for-tablecontrol-format.md)

[HideTableHeaders 元素 （格式）](./hidetableheaders-element-format.md)

[TableHeaders 元素 （格式）](./tableheaders-element-format.md)

[TableRowEntries 元素 （格式）](./tablerowentries-element-for-tablecontrol-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
