---
title: ViewDefinitions 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361416"
---
# <a name="viewdefinitions-element-format"></a>ViewDefinitions Element (Format)

定义用于显示 .NET 对象的视图。 这些视图可以采用表格格式、列表格式、宽格式和自定义控件格式显示对象的属性和脚本值。

Configuration 元素（Format） ViewDefinitions （Format XML）元素

## <a name="syntax"></a>语法

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍 `ViewDefinitions` 元素的属性、子元素和父元素。 对于可以在格式设置文件中定义的视图数量没有限制，可以按任意顺序添加它们。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[View 元素（格式）](./view-element-format.md)|定义用于显示一个或多个 .NET 对象的视图。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[配置元素（格式）](./configuration-element-format.md)|表示格式设置文件的顶级元素。|

## <a name="remarks"></a>备注

有关不同视图类型的组件的详细信息，请参阅以下主题：

- [创建表视图](./creating-a-table-view.md)

- [创建列表视图](./creating-a-list-view.md)

- [创建宽视图](./creating-a-wide-view.md)

- [自定义控件](./creating-custom-controls.md)

## <a name="example"></a>示例

此示例演示一个 @no__t 0 元素，该元素包含表视图和列表视图的父元素。

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <TableControl>...</TableControl>
    </View>
    <View>
      <ListControl>...</ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a>另请参阅

[配置元素（格式）](./configuration-element-format.md)

[View 元素（格式）](./view-element-format.md)

[创建表视图](./creating-a-table-view.md)

[创建列表视图](./creating-a-list-view.md)

[创建宽视图](./creating-a-wide-view.md)

[自定义控件](./creating-custom-controls.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
