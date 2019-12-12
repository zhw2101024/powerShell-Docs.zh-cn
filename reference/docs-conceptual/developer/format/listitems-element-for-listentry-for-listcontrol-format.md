---
title: ListControl （Format）的 ListEntry 的 ListItems 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362736"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a>ListItems Element for ListEntry for ListControl (Format)

定义其值显示在列表视图的行中的属性和脚本。

用于 ListControl 的 ListItems （format） ListEntry 元素的配置元素（格式） ViewDefinitions 元素（格式） ListControl 元素（格式） ListEntries 元素（格式）元素

## <a name="syntax"></a>语法

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍 `ListItems` 元素的属性、子元素和父元素。 对于可以指定的子元素数没有限制。 子元素的顺序定义值在列表视图中的显示顺序。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ListControl 的元素（格式）](./listitem-element-for-listitems-for-listcontrol-format.md)|必需的元素。<br /><br /> 定义其值由列表视图显示的属性或脚本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ListControl 的 ListEntry 元素（格式）](./listentry-element-for-listcontrol-format.md)|提供列表视图的定义。|

## <a name="remarks"></a>备注

有关此类视图的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。

## <a name="example"></a>示例

此示例显示了用于定义列表视图的三行的 XML 元素。

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>.NetTypeProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>.NetTypeProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
  </ListEntry>
```

## <a name="see-also"></a>另请参阅

[ListControl 的 ListEntry 元素（格式）](./listentry-element-for-listcontrol-format.md)

[ListControl 的元素（格式）](./listitem-element-for-listitems-for-listcontrol-format.md)

[创建列表视图](./creating-a-list-view.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
