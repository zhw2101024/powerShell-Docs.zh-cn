---
title: ViewSelectedBy 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361436"
---
# <a name="typename-element-for-viewselectedby-format"></a>TypeName Element for ViewSelectedBy (Format)

指定视图显示的 .NET 对象。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） ViewSelectedBy 元素（format） ViewSelectedBy 的 TypeName 元素（format）

## <a name="syntax"></a>语法

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `TypeName` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ViewSelectedBy 元素（格式）](./viewselectedby-element-format.md)|定义视图显示的 .NET 对象。|

## <a name="text-value"></a>文本值

指定 .NET 类型的完全限定名，如 `System.IO.DirectoryInfo`。

## <a name="remarks"></a>备注

有关此元素在不同视图中的使用方式的详细信息，请参阅[创建表视图](./creating-a-table-view.md)、[创建列表视图](./creating-a-list-view.md)、[创建宽视图](./creating-a-wide-view.md)和[自定义视图组件](./creating-custom-controls.md)。

## <a name="example"></a>示例

下面的示例演示如何为列表视图指定[Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)对象。 表、宽视图和自定义视图使用相同的架构。

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

[创建宽视图](./creating-a-wide-view.md)

[创建自定义控件](./creating-custom-controls.md)

[ViewSelectedBy 元素（格式）](./viewselectedby-element-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
