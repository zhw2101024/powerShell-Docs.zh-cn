---
title: ListControl 的 ListEntry 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362746"
---
# <a name="listentry-element-for-listcontrol-format"></a>ListEntry Element for ListControl (Format)

提供列表视图的定义。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（format） ListEntries 元素（format） ListEntry 元素（Format）

## <a name="syntax"></a>语法

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `ListEntry` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ListEntry 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|可选元素。<br /><br /> 定义使用此列表视图定义的 .NET 对象，或使用此定义必须存在的条件。|
|[ListItems 元素（格式）](./listitems-element-for-listentry-for-listcontrol-format.md)|必需的元素。<br /><br /> 定义其值由列表视图显示的属性和脚本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ListEntries 元素（格式）](./listentries-element-for-listcontrol-format.md)|提供列表视图的定义。|

## <a name="remarks"></a>备注

列表视图是显示每个对象的属性值或脚本值的列表格式。 有关列表视图的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。

## <a name="example"></a>示例

此示例显示了为[system.serviceprocess. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)对象定义列表视图的 XML 元素。

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

[ListEntry 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[ListEntries 元素（格式）](./listentries-element-for-listcontrol-format.md)

[ListItems 元素（格式）](./listitems-element-for-listentry-for-listcontrol-format.md)

[编写 Windows PowerShell 格式设置和类型文件](./writing-a-powershell-formatting-file.md)
