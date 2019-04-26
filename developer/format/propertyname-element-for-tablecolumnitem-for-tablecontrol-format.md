---
title: TableControl （格式） 的 TableColumnItem PropertyName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb26d72c-2f77-4801-badf-0537ccc55e31
caps.latest.revision: 10
ms.openlocfilehash: 6e86b6a0874b385703121802bc8108a0410442cd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064594"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a>PropertyName Element for TableColumnItem for TableControl (Format)

指定其值显示在一行的列中的属性。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableRowEntries 元素 （格式） TableRowEntry 元素 （格式） TableColumnItems 元素 （格式） TableColumnItem 元素 （格式）TableColumnItem （格式） 的属性名称元素

## <a name="syntax"></a>语法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`PropertyName`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[TableColumnItem 元素 （格式）](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|定义属性或其值显示在一行的列中的脚本。|

## <a name="text-value"></a>文本值

指定显示其值的属性的名称。

## <a name="remarks"></a>备注

表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。

## <a name="example"></a>示例

此示例演示`TableColumnItem`指定的元素`Status`的属性[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)对象。

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>另请参阅

[创建表视图](./creating-a-table-view.md)

[TableColumnItem 元素 （格式）](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
