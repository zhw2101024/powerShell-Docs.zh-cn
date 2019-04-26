---
title: 视图 （格式） 的名称元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065064"
---
# <a name="name-element-for-view-format"></a>Name Element for View (Format)

指定用于标识该视图的名称。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 名称元素 （格式）

## <a name="syntax"></a>语法

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`Name`元素。 只有一个`Name`元素允许为每个视图。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[视图元素 （格式）](./view-element-format.md)|定义一个视图，它用于显示一个或多个.NET 对象的成员。|

## <a name="text-value"></a>文本值

指定视图的唯一友好名称。 此名称可以包含对哪些对象或一组对象使用的视图中，哪些命令将返回对象或这些项的组合 （如表视图或列表视图） 视图的类型的引用。

## <a name="remarks"></a>备注

有关不同类型的视图的详细信息，请参阅以下主题：[表视图](./creating-a-table-view.md)，[列表视图](./creating-a-list-view.md)，[宽视图](./creating-a-wide-view.md)，并且[自定义视图](./creating-custom-controls.md)。

## <a name="example"></a>示例

下面的示例演示`View`定义的表视图元素[System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)对象。 视图的名称为"service"。

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a>另请参阅

[创建列表视图](./creating-a-list-view.md)

[创建表视图](./creating-a-table-view.md)

[创建较宽的视图](./creating-a-wide-view.md)

[创建自定义控件](./creating-custom-controls.md)

[视图元素 （格式）](./view-element-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
