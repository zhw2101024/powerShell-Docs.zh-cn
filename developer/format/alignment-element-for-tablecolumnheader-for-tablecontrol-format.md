---
title: TableControl （格式） 的 TableColumnHeader 的对齐方式元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff85e83a-c9c2-4c37-accc-e6a27c182f3c
caps.latest.revision: 19
ms.openlocfilehash: 16b41535109ca503e679a135f5ba30054e33de5b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853753"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a>Alignment Element for TableColumnHeader for TableControl (Format)

定义如何显示列标题中的数据。

元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableHeaders 元素 （格式） TableColumnHeader 元素 （格式） 对齐方式的配置元素 TableColumnHeader （格式）

## <a name="syntax"></a>语法

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述的特性、 子元素和父元素的`Alignment`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableColumnHeader 元素 （格式）](./tablecolumnheader-element-format.md)|定义标签、 宽度和表的列的数据的对齐方式。|

## <a name="text-value"></a>文本值

指定以下值之一。 这些值不区分大小写。

如果未指定此元素，这左对齐的数据显示在左侧列中是默认值。

右对齐显示在右侧列中的数据。

Center 中心显示的列中的数据。

## <a name="remarks"></a>备注

表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。

## <a name="example"></a>示例

此示例显示了`TableColumnHeader`左边对齐其数据的元素。

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
