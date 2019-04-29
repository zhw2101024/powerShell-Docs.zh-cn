---
title: ViewSelectedBy （格式） 的类型名称元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083750"
---
# <a name="typename-element-for-viewselectedby-format"></a>TypeName Element for ViewSelectedBy (Format)

指定视图显示的.NET 对象。

元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ViewSelectedBy 元素 （格式） 类型名称的配置元素 ViewSelectedBy （格式）

## <a name="syntax"></a>语法

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`TypeName`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[ViewSelectedBy 元素 （格式）](./viewselectedby-element-format.md)|定义视图所显示的.NET 对象。|

## <a name="text-value"></a>文本值

指定.NET 类型的完全限定的名称，例如`System.IO.DirectoryInfo`。

## <a name="remarks"></a>备注

有关如何在不同的视图中使用此元素的详细信息，请参阅[创建表视图](./creating-a-table-view.md)，[创建列表视图](./creating-a-list-view.md)，[创建较宽的视图](./creating-a-wide-view.md)，和[自定义视图组件](./creating-custom-controls.md)。

## <a name="example"></a>示例

下面的示例演示如何指定[System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)列表视图的对象。 相同的架构用于表中，宽，和自定义视图。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>另请参阅

[创建列表视图](./creating-a-list-view.md)

[创建表视图](./creating-a-table-view.md)

[创建较宽的视图](./creating-a-wide-view.md)

[创建自定义控件](./creating-custom-controls.md)

[ViewSelectedBy 元素 （格式）](./viewselectedby-element-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
