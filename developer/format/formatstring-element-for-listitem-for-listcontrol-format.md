---
title: ListControl （格式） 的列表项的 FormatString 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065608"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a>FormatString Element for ListItem for ListControl (Format)

指定格式模式，它定义如何显示的属性或脚本的值。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素的元素 ListControl （格式） ListEntry ListControl （格式） 的 ListControl （格式） Listitem 元素ListControl （格式） 格式说明符 ListControl （格式） 的 ListItem 元素的 ListItem 元素

## <a name="syntax"></a>语法

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`FormatString`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[ListItem 元素 （格式）](./listitem-element-for-listitems-for-listcontrol-format.md)|定义属性或其值显示在列表视图的行中的脚本。|

## <a name="text-value"></a>文本值

指定用于设置数据格式的模式。 例如，可以使用此模式的类型的任何属性的值进行格式[System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {{0:hh}: {0:mm}。

## <a name="remarks"></a>备注

创建表视图、 列表视图、 宽视图或自定义视图时，可以使用格式字符串。 有关格式设置显示在视图中的一个值的详细信息，请参阅[格式显示数据](./formatting-displayed-data.md)。

在列表视图中使用格式字符串的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。

## <a name="example"></a>示例

下面的示例演示如何定义的值的格式设置字符串`StartTime`属性。

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a>另请参阅

[创建列表视图](./creating-a-list-view.md)

[ListItem 元素 （格式）](./listitem-element-for-listitems-for-listcontrol-format.md)

[编写 Windows PowerShell 格式设置和文件类型](./writing-a-powershell-formatting-file.md)
