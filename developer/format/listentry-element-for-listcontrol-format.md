---
title: ListControl （格式） 的 ListEntry 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862243"
---
# <a name="listentry-element-for-listcontrol-format"></a>ListEntry Element for ListControl (Format)

提供列表视图中的定义。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素 （格式） ListEntry 元素 （格式）

## <a name="syntax"></a>语法

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`ListEntry`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ListEntry （格式） 的 EntrySelectedBy 元素](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|可选元素。<br /><br /> 定义使用此列表视图定义或要使用此定义中必须存在的条件的.NET 对象。|
|[Listitem 元素 （格式）](./listitems-element-for-listentry-for-listcontrol-format.md)|必需的元素。<br /><br /> 定义属性和其值将由列表视图的脚本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ListEntries 元素 （格式）](./listentries-element-for-listcontrol-format.md)|提供了列表视图的定义。|

## <a name="remarks"></a>备注

列表视图是以列表格式显示属性值或为每个对象的脚本值。 有关列表视图的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。

## <a name="example"></a>示例

此示例显示了定义的列表视图的 XML 元素[System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)对象。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a>另请参阅

[创建列表视图](./creating-a-list-view.md)

[ListEntry （格式） 的 EntrySelectedBy 元素](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[ListEntries 元素 （格式）](./listentries-element-for-listcontrol-format.md)

[Listitem 元素 （格式）](./listitems-element-for-listentry-for-listcontrol-format.md)

[编写 Windows PowerShell 格式设置和文件类型](./writing-a-powershell-formatting-file.md)
