---
title: WideControl 的 WideItem 的格式字符串元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363026"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a>FormatString Element for WideItem for WideControl (Format)

指定定义属性或脚本值在视图中显示方式的格式模式。

配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素 for WideControl （format）的元素对于 WideItem for WideControl （Format）

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
|[WideControl 的 WideItem 元素（格式）](./wideitem-element-for-widecontrol-format.md)|定义其值显示在列表视图的行中的属性或脚本。|

## <a name="text-value"></a>文本值

指定用于设置数据格式的模式。 例如，你可以使用此模式来[设置类型为](/dotnet/api/System.TimeSpan)system.string： {0： MMM} {0： dd} {0： HH}： {0： mm} 的任何属性的值的格式。

## <a name="remarks"></a>备注

创建表视图、列表视图、宽视图或自定义视图时，可以使用格式字符串。 有关设置视图中显示的值的格式的详细信息，请参阅[设置显示的数据的格式](./formatting-displayed-data.md)。

有关在宽视图中使用格式字符串的详细信息，请参阅[创建宽视图](./creating-a-wide-view.md)。

## <a name="example"></a>示例

下面的示例演示如何为 `StartTime` 属性的值定义格式字符串。

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a>另请参阅

[创建宽视图](./creating-a-wide-view.md)

[WideControl 的 WideItem 元素（格式）](./wideitem-element-for-widecontrol-format.md)

[编写 Windows PowerShell 格式设置和类型文件](./writing-a-powershell-formatting-file.md)
