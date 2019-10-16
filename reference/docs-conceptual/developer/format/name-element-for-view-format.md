---
title: View 的 Name 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362636"
---
# <a name="name-element-for-view-format"></a>Name Element for View (Format)

指定用于标识视图的名称。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） Name 元素（Format）

## <a name="syntax"></a>语法

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `Name` 元素的属性、子元素和父元素。 每个视图只允许一个 @no__t 0 元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 元素（格式）](./view-element-format.md)|定义一个视图，该视图用于显示一个或多个 .NET 对象的成员。|

## <a name="text-value"></a>文本值

为视图指定唯一的友好名称。 此名称可以包含对视图类型（如表视图或列表视图）的引用、使用视图的对象或对象集、返回对象的命令或这些对象的组合。

## <a name="remarks"></a>备注

有关不同视图类型的详细信息，请参阅下列主题：[表视图](./creating-a-table-view.md)、[列表视图](./creating-a-list-view.md)、[宽视图](./creating-a-wide-view.md)和[自定义视图](./creating-custom-controls.md)。

## <a name="example"></a>示例

下面的示例演示一个 `View` 元素，该元素定义[system.serviceprocess. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)对象的表视图。 视图的名称为 "service"。

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

[创建宽视图](./creating-a-wide-view.md)

[创建自定义控件](./creating-custom-controls.md)

[View 元素（格式）](./view-element-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
