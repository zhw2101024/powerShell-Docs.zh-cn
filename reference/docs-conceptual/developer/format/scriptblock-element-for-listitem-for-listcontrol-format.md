---
title: ListControl 的的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364806"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a>ScriptBlock Element for ListItem for ListControl (Format)

指定其值在行中显示的脚本。

用于 ListEntry 的 ListEntries for ListControl （Format） ListItems 元素的 ListControl （Format） ListEntry 元素的 Configuration Element （Format） ViewDefinitions 元素（格式） ListControl 元素（format） ListEntries 元素对于 ListControl （Format）的 ListControl （格式） ListItems 的 ListControl （格式） ScriptBlock 元素

## <a name="syntax"></a>语法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `ScriptBlock` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[元素（格式）](./listitem-element-for-listitems-for-listcontrol-format.md)|定义其值显示在列表视图的行中的属性或脚本。|

## <a name="text-value"></a>文本值

指定其值在行中显示的脚本。

## <a name="remarks"></a>备注

如果指定此元素，则不能指定[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)元素。

有关在列表视图中指定脚本的详细信息，请参阅[列表视图](./creating-a-list-view.md)。

## <a name="example"></a>示例

下面的示例演示如何指定显示其值的属性。

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a>另请参阅

[ListControl 的名称名称元素（格式）](./propertyname-element-for-listitem-for-listcontrol-format.md)

[创建列表视图](./creating-a-list-view.md)

[ListControl 的 ListItems 元素（格式）](./listitem-element-for-listitems-for-listcontrol-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
