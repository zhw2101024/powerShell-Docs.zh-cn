---
title: FormatString 元素 WideControl （格式） 的 WideItem |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860933"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a>FormatString Element for WideItem for WideControl (Format)

指定格式模式，它定义如何在视图中显示的属性或脚本的值。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） WideControl 元素 （格式） WideEntries 元素 （格式） WideEntry 元素的元素 WideControl （格式） WideItem WideControl （格式） FormatString 元素有关 WideItem 为 WideControl （格式）

## <a name="syntax"></a>语法

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`FormatString`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[WideControl （格式） 的 WideItem 元素](./wideitem-element-for-widecontrol-format.md)|定义属性或其值显示在列表视图的行中的脚本。|

## <a name="text-value"></a>文本值

指定用于设置数据格式的模式。 例如，可以使用此模式的类型的任何属性的值进行格式[System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {{0:hh}: {0:mm}。

## <a name="remarks"></a>备注

创建表视图、 列表视图、 宽视图或自定义视图时，可以使用格式字符串。 有关格式设置显示在视图中的一个值的详细信息，请参阅[格式显示数据](./formatting-displayed-data.md)。

有关宽视图中使用格式字符串的详细信息，请参阅[创建较宽的视图](./creating-a-wide-view.md)。

## <a name="example"></a>示例

下面的示例演示如何定义的值的格式设置字符串`StartTime`属性。

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a>另请参阅

[创建较宽的视图](./creating-a-wide-view.md)

[WideControl （格式） 的 WideItem 元素](./wideitem-element-for-widecontrol-format.md)

[编写 Windows PowerShell 格式设置和文件类型](./writing-a-powershell-formatting-file.md)
