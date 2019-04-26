---
title: TableControl （格式） 的使用的 TableColumnHeader 标签元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065744"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a>Label Element for TableColumnHeader for TableControl (Format)

定义显示在某一列顶部的标签。 定义表视图时，将使用此元素。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableHeaders 元素 TableControl （格式） 标签元素 TableHeaders TableControl （格式） TableColumnHeader 元素TableControl （格式） 的 TableColumnHeader

## <a name="syntax"></a>语法

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`Label`元素。 每个列所允许只有一个标签。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[TableControl （格式） 的 TableHeaders TableColumnHeader 元素](./tablecolumnheader-element-format.md)|定义标签、 宽度和表的列的数据的对齐方式。|

## <a name="text-value"></a>文本值

指定的表的列的顶部显示的文本。 有无受限的字符的列标签。

## <a name="remarks"></a>备注

如果未不指定任何标签，则使用其值显示在行中的属性的名称。

表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。

## <a name="example"></a>示例

此示例显示了`TableColumnHeader`其标签为"列 1"的元素。

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>另请参阅

[创建表视图](./creating-a-table-view.md)

[TableColumnHeader 元素 （格式）](./tablecolumnheader-element-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
