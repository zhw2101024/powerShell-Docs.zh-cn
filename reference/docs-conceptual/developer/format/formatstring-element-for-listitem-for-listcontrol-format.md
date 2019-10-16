---
title: ListControl 的的格式字符串元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363016"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a>FormatString Element for ListItem for ListControl (Format)

指定一个定义如何显示属性或脚本值的格式模式。

ListEntry 的 ListControl （format） ListControl 元素的配置元素（格式） ViewDefinitions 元素（格式） ListControl 元素（format） ListEntries 元素（format）用于 ListControl 的 ListControl （格式）格式字符串元素的元素（格式）

## <a name="syntax"></a>语法

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `FormatString` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[元素（格式）](./listitem-element-for-listitems-for-listcontrol-format.md)|定义其值显示在列表视图的行中的属性或脚本。|

## <a name="text-value"></a>文本值

指定用于设置数据格式的模式。 例如，你可以使用此模式来[设置类型为](/dotnet/api/System.TimeSpan)system.string： {0： MMM} {0： dd} {0： HH}： {0： mm} 的任何属性的值的格式。

## <a name="remarks"></a>备注

创建表视图、列表视图、宽视图或自定义视图时，可以使用格式字符串。 有关设置视图中显示的值的格式的详细信息，请参阅[设置显示的数据的格式](./formatting-displayed-data.md)。

有关在列表视图中使用格式字符串的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。

## <a name="example"></a>示例

下面的示例演示如何为 `StartTime` 属性的值定义格式字符串。

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a>另请参阅

[创建列表视图](./creating-a-list-view.md)

[元素（格式）](./listitem-element-for-listitems-for-listcontrol-format.md)

[编写 Windows PowerShell 格式设置和类型文件](./writing-a-powershell-formatting-file.md)
