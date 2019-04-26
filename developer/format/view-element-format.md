---
title: 查看元素 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083716"
---
# <a name="view-element-format"></a>View Element (Format)

定义一个视图，显示一个或多个.NET 对象。 可在格式设置文件中定义的视图数目没有限制。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式）

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

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`View`元素。 必须指定一个且只有一个控件子元素，并且必须指定的视图和使用视图的对象的名称。 定义自定义控件，如何对分组对象，并指定是否该视图带外都是可选的。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[视图 （格式） 的控件元素](./controls-element-for-view-format.md)|可选元素。<br /><br /> 定义一组可以按其从视图中的名称引用的控件。|
|[CustomControl 元素 （格式）](./customcontrol-element-for-groupby-format.md)|可选元素。<br /><br /> 定义自定义控件的视图格式。|
|[视图 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)|可选元素。<br /><br /> 定义如何对.NET 对象的成员进行分组。|
|[ListControl 元素 （格式）](./listcontrol-element-format.md)|可选元素。<br /><br /> 定义视图以列表格式。|
|[视图 （格式） 的名称元素](./name-element-for-view-format.md)|必需的元素。<br /><br /> 指定用来引用该视图的名称。|
|[TableControl 元素 （格式）](./tablecontrol-element-format.md)|可选元素。<br /><br /> 定义视图以表格格式。|
|[视图 （格式） 的 ViewSelectedBy 元素](./viewselectedby-element-format.md)|必需的元素。<br /><br /> 定义此视图显示的.NET 对象。|
|[WideControl 元素 （格式）](./widecontrol-element-format.md)|可选元素。<br /><br /> 定义范围内 （单个值） 的视图的列表格式。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[ViewDefinitions 元素 （格式）](./viewdefinitions-element-format.md)|定义用于显示对象的视图。|

## <a name="remarks"></a>备注

有关不同的视图和自定义控件的组件的详细信息，请参阅以下主题：

- [表视图组件](./creating-a-table-view.md)

- [列表视图组件](./creating-a-list-view.md)

- [宽的视图组件](./creating-a-wide-view.md)

- [自定义控件](./creating-custom-controls.md)

## <a name="example"></a>示例

此示例演示`View`定义的表视图元素[System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)对象。

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

[ViewDefinitions 元素 （格式）](./viewdefinitions-element-format.md)

[视图 （格式） 的名称元素](./name-element-for-view-format.md)

[ViewSelectedBy 元素 （格式）](./viewselectedby-element-format.md)

[视图 （格式） 的控件元素](./controls-element-for-view-format.md)

[视图 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)

[TableControl 元素 （格式）](./tablecontrol-element-format.md)

[ListControl 元素 （格式）](./listcontrol-element-format.md)

[WideControl 元素 （格式）](./widecontrol-element-format.md)

[CustomControl 元素 （格式）](./customcontrol-element-for-groupby-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
