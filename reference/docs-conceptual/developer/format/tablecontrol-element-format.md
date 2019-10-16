---
title: TableControl 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368196"
---
# <a name="tablecontrol-element-format"></a>TableControl Element (Format)

定义视图的表格格式。

ViewDefinitions 元素（格式） View 元素（Format） TableControl 元素（Format）

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

以下各节介绍 `TableControl` 元素的属性、子元素和父元素。 您必须指定表中的行。 所有其他子元素都是可选的。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableControl 的 AutoSize 元素（Format）](./autosize-element-for-tablecontrol-format.md)|可选元素。<br /><br /> 指定是否根据数据大小调整列大小和列数。|
|[TableControl 的 HideTableHeaders 元素（格式）](./hidetableheaders-element-format.md)|可选元素。<br /><br /> 指示是否不显示表的标头。|
|[TableControl 的 TableHeaders 元素（格式）](./tableheaders-element-format.md)|必需的元素。<br /><br /> 为表视图的列定义标签、宽度和数据的对齐方式。|
|[TableControl 的 TableRowEntries 元素（格式）](./tablerowentries-element-for-tablecontrol-format.md)|可选元素。<br /><br /> 提供表视图的定义。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 元素（格式）](./view-element-format.md)|定义一个视图，该视图用于显示一个或多个对象的成员。|

## <a name="remarks"></a>备注

有关表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。

## <a name="example"></a>示例

此示例演示一个 `TableControl` 元素，该元素用于显示[Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)对象的属性。

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

[View 元素（格式）](./view-element-format.md)

[TableControl 的 AutoSize 元素（Format）](./autosize-element-for-tablecontrol-format.md)

[HideTableHeaders 元素（格式）](./hidetableheaders-element-format.md)

[TableHeaders 元素（格式）](./tableheaders-element-format.md)

[TableRowEntries 元素（格式）](./tablerowentries-element-for-tablecontrol-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
