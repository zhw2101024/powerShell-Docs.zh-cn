---
title: ListControl （格式） 的 ListEntry 的 Listitem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858583"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a>ListItems Element for ListEntry for ListControl (Format)

定义属性和其值显示在列表视图的行中的脚本。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素的元素列表控件 （格式） ListEntry ListControl （格式） 的 ListControl （格式） Listitem 元素

## <a name="syntax"></a>语法

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述的特性、 子元素和父元素的`ListItems`元素。 可以指定的子元素的数目没有限制。 子元素的顺序定义值显示在列表视图中的顺序。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[ListControl （格式） 的 ListItem 元素](./listitem-element-for-listitems-for-listcontrol-format.md)|必需的元素。<br /><br /> 定义属性或其值显示的列表视图的脚本。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[ListControl （格式） 的 ListEntry 元素](./listentry-element-for-listcontrol-format.md)|提供列表视图中的定义。|

## <a name="remarks"></a>备注

有关此类型的视图的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。

## <a name="example"></a>示例

此示例演示定义列表视图的三个行的 XML 元素。

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

[ListControl （格式） 的 ListEntry 元素](./listentry-element-for-listcontrol-format.md)

[ListControl （格式） 的 ListItem 元素](./listitem-element-for-listitems-for-listcontrol-format.md)

[创建列表视图](./creating-a-list-view.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
