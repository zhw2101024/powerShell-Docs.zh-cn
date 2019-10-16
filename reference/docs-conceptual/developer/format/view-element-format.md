---
title: View 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361456"
---
# <a name="view-element-format"></a>View Element (Format)

定义一个视图，该视图显示一个或多个 .NET 对象。 对于可在格式设置文件中定义的视图数没有限制。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（格式）

## <a name="syntax"></a>语法

```xml
<View>
  <Name>Friendly name of view.</Name>
  <ViewSelectedBy>...</ViewSelectedBy>
  <Controls>...</Controls>
  <GroupBy>...</GroupBy>
  <TableControl>...</TableControl>
  <ListControl>...</ListControl>
  <WideControl>...</WideControl>
  <CustomControl>...</CustomControl>
</View>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `View` 元素的属性、子元素和父元素。 您必须指定一个且仅有一个控件子元素，并且您必须指定视图的名称和使用视图的对象。 定义自定义控件，如何对对象分组，并指定视图是否带外是可选的。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[View 的 Controls 元素（格式）](./controls-element-for-view-format.md)|可选元素。<br /><br /> 定义一组可从视图中的名称引用的控件。|
|[CustomControl 元素（格式）](./customcontrol-element-for-groupby-format.md)|可选元素。<br /><br /> 定义视图的自定义控件格式。|
|[View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)|可选元素。<br /><br /> 定义 .NET 对象成员的分组方式。|
|[ListControl 元素（格式）](./listcontrol-element-format.md)|可选元素。<br /><br /> 定义视图的列表格式。|
|[View 的 Name 元素（Format）](./name-element-for-view-format.md)|必需的元素。<br /><br /> 指定用于引用视图的名称。|
|[TableControl 元素（格式）](./tablecontrol-element-format.md)|可选元素。<br /><br /> 定义视图的表格格式。|
|[View 的 ViewSelectedBy 元素（Format）](./viewselectedby-element-format.md)|必需的元素。<br /><br /> 定义此视图显示的 .NET 对象。|
|[WideControl 元素（格式）](./widecontrol-element-format.md)|可选元素。<br /><br /> 定义视图的宽（单值）列表格式。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ViewDefinitions 元素（格式）](./viewdefinitions-element-format.md)|定义用于显示对象的视图。|

## <a name="remarks"></a>备注

有关不同视图和自定义控件的组件的详细信息，请参阅以下主题：

- [表视图组件](./creating-a-table-view.md)

- [列表视图组件](./creating-a-list-view.md)

- [宽视图组件](./creating-a-wide-view.md)

- [自定义控件](./creating-custom-controls.md)

## <a name="example"></a>示例

此示例演示一个 `View` 元素，该元素定义[system.serviceprocess. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)对象的表视图。

```xml
<ViewDefinitions>
  <View>
    <Name>service</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a>另请参阅

[ViewDefinitions 元素（格式）](./viewdefinitions-element-format.md)

[View 的 Name 元素（Format）](./name-element-for-view-format.md)

[ViewSelectedBy 元素（格式）](./viewselectedby-element-format.md)

[View 的 Controls 元素（格式）](./controls-element-for-view-format.md)

[View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)

[TableControl 元素（格式）](./tablecontrol-element-format.md)

[ListControl 元素（格式）](./listcontrol-element-format.md)

[WideControl 元素（格式）](./widecontrol-element-format.md)

[CustomControl 元素（格式）](./customcontrol-element-for-groupby-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
