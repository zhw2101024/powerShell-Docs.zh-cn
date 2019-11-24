---
title: TableControl 的 TableColumnHeader 的 Width 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367866"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a>Width Element for TableColumnHeader for TableControl (Format)

定义列的宽度（以字符为字符）。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） TableControl 元素（format） TableHeaders 元素 for TableControl （format） TableColumnHeader 元素 TableHeaders for TableControl （Format） Width 元素TableColumnHeader for TableControl （Format）

## <a name="syntax"></a>语法

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述定义列标题时使用的 `Width` 元素的特性、子元素和父元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableControl 的 TableHeaders 的 TableColumnHeader 元素（格式）](./tablecolumnheader-element-format.md)|定义表的列的数据的标签、宽度和对齐方式。|

## <a name="text-value"></a>文本值

如果可能，请指定大于所显示属性值长度的宽度（字符数）。

## <a name="remarks"></a>备注

有关表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。

## <a name="example"></a>示例

下面的示例演示一个宽度为16个字符的 `TableColumnHeader` 元素。

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>另请参阅

[创建表视图](./creating-a-table-view.md)

[TableControl 的 TableHeader 的 TableColumnHeader 元素（格式）](./tablecolumnheader-element-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
