---
title: ListControl （格式） 的 ListEntries 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856783"
---
# <a name="listentries-element-for-listcontrol-format"></a>ListEntries Element for ListControl (Format)

提供了列表视图的定义。 列表视图中必须指定一个或多个定义。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素 （格式）

## <a name="syntax"></a>语法

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`ListEntries`元素。 必须指定至少一个子元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ListEntry 元素 （格式）](./listentry-element-for-listcontrol-format.md)|提供列表视图中的定义。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ListControl 元素 （格式）](./listcontrol-element-format.md)|定义视图以列表格式。|

## <a name="remarks"></a>备注

有关列表视图的详细信息，请参阅[列表视图](./creating-a-list-view.md)。

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

[ListControl 元素 （格式）](./listcontrol-element-format.md)

[ListEntry 元素 （格式）](./listentry-element-for-listcontrol-format.md)

[列表视图](./creating-a-list-view.md)

[编写 Windows PowerShell 格式设置和文件类型](./writing-a-powershell-formatting-file.md)
