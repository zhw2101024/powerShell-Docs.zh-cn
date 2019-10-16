---
title: TableControl 的 TableColumnHeader 的 Label 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365166"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a>Label Element for TableColumnHeader for TableControl (Format)

定义在列顶部显示的标签。 定义表视图时使用此元素。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） TableControl 元素（format） TableHeaders 元素 for TableControl （Format） TableColumnHeader 元素 for TableHeaders for TableControl （Format） Label 元素 forTableColumnHeader for TableControl （Format）

## <a name="syntax"></a>语法

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `Label` 元素的属性、子元素和父元素。 每个列只允许有一个标签。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableControl 的 TableHeaders 的 TableColumnHeader 元素（格式）](./tablecolumnheader-element-format.md)|定义表中某一列的数据的标签、宽度和对齐方式。|

## <a name="text-value"></a>文本值

指定在表的列顶部显示的文本。 列标签没有受限制的字符。

## <a name="remarks"></a>备注

如果未指定标签，则使用在行中显示其值的属性的名称。

有关表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。

## <a name="example"></a>示例

此示例演示一个标签为 "Column 1" 的 @no__t 0 元素。

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
