---
title: ListControl 的标记元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362886"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a>Label Element for ListItem for ListControl (Format)

指定在行的属性或脚本值左侧显示的标签。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（format） ListEntries 元素 for ListControl （format） ListEntry 元素 for ListControl for ListItems 元素（Format） ListControl 的 ListItems for ListControl （Format） Label 元素的元素

## <a name="syntax"></a>语法

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `Label` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ListControl 的 ListItems 元素（格式）](./listitem-element-for-listitems-for-listcontrol-format.md)|定义其值显示在列表视图的行中的属性或脚本。|

## <a name="text-value"></a>文本值

指定要在属性或脚本值左侧显示的标签。

## <a name="remarks"></a>备注

如果未指定标签，则显示属性或脚本的名称。 有关在列表视图中使用标签的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。

## <a name="example"></a>示例

下面的示例演示如何向行中添加标签。

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a>另请参阅

[创建列表视图](./creating-a-list-view.md)

[元素（格式）](./listitem-element-for-listitems-for-listcontrol-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
