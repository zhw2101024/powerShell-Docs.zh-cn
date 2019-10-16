---
title: TableControl 的 TableColumnItem 的对齐元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b07a53df-64f1-49b0-8cea-c993b3f1f76b
caps.latest.revision: 10
ms.openlocfilehash: 1bc936b94ee6fd6239e9e3c4afcdb8f14fbe36eb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369076"
---
# <a name="alignment-element-for-tablecolumnitem-for-tablecontrol-format"></a>Alignment Element for TableColumnItem for TableControl (Format)

定义行的列中数据的显示方式。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） TableControl 元素（格式） TableRowEntries 元素（格式） TableRowEntry 元素（格式） TableColumnItems 元素（格式） TableColumnItem 元素（格式）TableColumnItem 的对齐元素（格式）

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
|[TableColumnItem 元素（格式）](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|定义表中某一列的数据的标签、宽度和对齐方式。|

## <a name="text-value"></a>文本值

指定下列值之一。 （这些值不区分大小写。）

向左移动列中显示的数据。 （如果未指定此元素，则这是默认值。）

向右移动列中显示的数据。

居中将列中显示的数据居中。

## <a name="remarks"></a>备注

有关表视图的组件的详细信息，请参阅[表视图](./creating-a-table-view.md)。

## <a name="see-also"></a>另请参阅

[表视图](./creating-a-table-view.md)

[TableColumnItem 元素（格式）](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)
